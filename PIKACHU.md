# PIKACHU

## 1) calculation sample
# Pikachu 质押计算示例 — 100 U

> 基于 `contracts/Pikachu.sol`（version 1.0）  
> 常量：`CYCLE_INTERVAL = 3 days`，`REWARD_GRACE_PERIOD = 1 days`

---

## 路径说明

| 订单类型 | 最小金额 | 100 U 是否可用 |
|----------|----------|----------------|
| `USDT_ONLY` | 100–300 U（100 的整数倍） | ✅ |
| `USDT_AND_VT` | 200–600 U（100 的整数倍） | ❌ 最低 200 U |

本文主场景为 **USDT_ONLY · 100 U · grace 内续单**；文末附 200 U（VT+U）对照。

---

## 场景 A：USDT_ONLY · 100 U · 正常续单（grace 内）

### 假设

- 质押用户已绑定推荐关系，**有 1 个合格直推上级**
- 上级 `groupSales ≥ 1000 U` → **V1**，`getCommunityPercent = 2%`
- 上级链仅这一层（无更高等级上级）
- `claim` 条件：`block.timestamp > cycleEnd`

### 时间线

| 时间 | 操作 | 说明 |
|------|------|------|
| T0 | `buy(100, USDT_ONLY)` | 付 **100 USDT**，周期 3 天 |
| T0 + 3d | `cycleEnd` | 第一单周期结束 |
| T0 + 3d ～ T0 + 4d | `buy(100, USDT_ONLY)` 续单 | grace 内，解锁上一单 |
| T0 + 3d 之后 | `claim()` | 第一单 `cycleEnd` 已过 |

### Step 1 — 第一次 `buy(100 U)`

```
支付：100 USDT → 合约
订单 #1：amount = 100，claimable = 0（待续单解锁）
cycleEnd = T0 + 3 days
```

### Step 2 — grace 内续单 `buy(100 U)`

对 **上一单 #1** 写入：

```
claimableReward    = 100 × 3%  = 3 USDT
claimablePrincipal = 100 USDT
```

同时再付 **100 USDT**，创建 **订单 #2**（新周期 3 天）。

**累计自付：200 USDT**（100 + 100）

---

## Step 3 — `claim()` 结算订单 #1

### 3.1 本金（Principal）— USDT

| 项目 | 计算 | 金额 (USDT) |
|------|------|-------------|
| 毛本金 | `claimablePrincipal` | **100.0000** |
| 社区运营费 0.3% | 100 × 0.3% | 0.3000 |
| 神秘盒 0.1% | 100 × 0.1% | 0.1000 |
| 节点 0.1% | 100 × 0.1% | 0.1000 |
| **本金 fee 合计** | 0.5% | **0.5000** |
| **质押用户实收本金** | 100 − 0.5 | **99.5000** |

> 代码位置：`Pikachu.sol` 289–298 行，fee 从本金扣，receiver 收 USDT。

---

### 3.2 静态收益（Reward）— 3 USDT

毛收益 `totalReward = 3 USDT`，按 **70% 静态 / 30% 动态**（304–305 行）：

| 项目 | 计算 | 金额 (USDT) |
|------|------|-------------|
| 静态池 passive | 3 × 70% | **2.1000** |
| 动态池 active | 3 × 30% | **0.9000** |

#### 静态部分 fee（0.5%，307–316 行）

| 项目 | 计算 | 金额 (USDT) |
|------|------|-------------|
| 社区运营 0.3% | 2.1 × 0.3% | 0.0063 |
| 神秘盒 0.1% | 2.1 × 0.1% | 0.0021 |
| 节点 0.1% | 2.1 × 0.1% | 0.0021 |
| **静态 fee 合计** | 0.5% | **0.0105** |
| **质押用户实收静态** | 2.1 − 0.0105 | **2.0895** |

#### 动态部分 — 1 个 V1 上级（2% 级差，321–350 行）

动态 bonus 按 **`totalReward × 级差%`** 计算，不是按 `totalActive` 计算。

| 步骤 | 计算 | 金额 (USDT) |
|------|------|-------------|
| 级差比例 | `2% − 0%` | **2%** |
| 上级 gross bonus | `3 × 2%` | **0.0600** |
| → LP 池 9% | 0.06 × 9% | 0.0054 |
| → 节点 1% | 0.06 × 1% | 0.0006 |
| **上级实收** | 0.06 × 90% | **0.0540** |
| `distAmount` | | **0.0600** |
| marketing leftover | `0.9 − 0.06` | **0.8400** |

| 角色 | 动态部分实收 |
|------|-------------|
| 质押用户 | **0**（动态不给 staker） |
| V1 上级 | **0.0540** |
| marketing | **0.8400** |
| LP（内部 swap 加池） | **0.0054** |
| 节点（并入 `totalNodeRewards`） | **+0.0006** |

---

### 3.3 各方汇总（本笔 claim）

#### 质押用户（claimer）

| 来源 | USDT |
|------|------|
| 本金 | 99.5000 |
| 静态收益 | 2.0895 |
| 动态收益 | 0 |
| **合计** | **101.5895** |

#### V1 上级

| 来源 | USDT |
|------|------|
| 社区动态 bonus | **0.0540** |

#### 平台 / 池子

| 接收方 | 来源 | USDT |
|--------|------|------|
| `communityOpReceiver` | 本金 0.3 + 静态 0.0063 | **0.3063** |
| `mysteryPoolReceiver` | 本金 0.1 + 静态 0.0021 | **0.1021** |
| `nodeRewardsReceiver` | 本金 0.1 + 静态 0.0021 + 动态 0.0006 | **0.1047** |
| `marketingBeneficiary` | 动态 leftover | **0.8400** |
| LP（`_swapAndAddLiquidity`） | 动态 9% | **0.0054** |

**校验：** 101.5895 + 0.054 + 0.3063 + 0.1021 + 0.1047 + 0.8400 + 0.0054 ≈ **103**（= 本金 100 + 毛收益 3）✅

---

### 3.4 用户资金总账（到第一次 claim 止）

| 项目 | USDT |
|------|------|
| 第一次 buy | −100 |
| 第二次 buy（续单） | −100 |
| 第一次 claim 收入 | +101.5895 |
| **净现金** | **−98.4105** |
| 仍锁定 | 订单 #2 质押 **100 U**（下一周期） |

**单周期净 yield（已释放的 100 U 本金）：**

```
毛 yield = 3% = 3 U
扣用户侧 fee ≈ 0.5%×100 + 0.5%×2.1 ≈ 0.5105 U
净 yield ≈ 2.4895 U  → 约 2.49% on 100 U principal
```

---

### 3.5 与「无上级」对比

| 项目 | 无上级 | 有 V1 上级 |
|------|--------|------------|
| 质押用户 claim | 101.5895 | **101.5895**（不变） |
| 上级收入 | 0 | **+0.0540** |
| marketing | 0.9000 | **0.8400**（少 0.06） |

有上级时，**质押用户到手不变**；动态池 0.9 U 里只有 **0.06 U** 分给上级，其余 **0.84 U** 仍进 marketing。

---

## 场景 B：续单逾期（grace 后 1 天）

假设：`cycleEnd + 1 day + 1 day` 才续单 → `daysElapsed = 1`

```
claimableReward    = 0
claimablePrincipal = 100 × 95% = 95 USDT
```

**claim 用户实收：**

| 项目 | 计算 | USDT |
|------|------|------|
| 本金 fee 0.5% | 95 × 0.5% | 0.475 |
| **用户本金** | | **94.525** |
| 静态收益 | 0 | **0** |
| **合计** | | **94.525** |

---

## 场景 C：USDT_AND_VT · 200 U（100 USDT + 100 VT）

一次 `buy(200, USDT_AND_VT)` 创建两单：

| 订单 | amount | 预设 claimable |
|------|--------|----------------|
| VT #1 | 100 VT | reward = 3 USDT, principal = 100 VT |
| USDT #2 | 100 USDT | 0（要等下一组 buy 解锁） |

### VT #1 在 `cycleEnd` 后 `claim()`（无需续单即可 claim VT）

**本金 VT：**

| 步骤 | 计算 | VT |
|------|------|-----|
| 毛 principal | | 100 |
| burn 3% → dead | | −3 |
| 剩余 | | 97 |
| fee 0.5% | 97 × 0.5% | 0.485 |
| **用户实收 VT** | | **96.515** |

**收益 3 USDT**（静态部分与场景 A 相同，假设有 V1 上级）：

- 质押用户静态：**2.0895 USDT**
- V1 上级动态：**0.0540 USDT**
- marketing leftover：**0.8400 USDT**

**VT #1 claim 用户总收：**

```
96.515 VT + 2.0895 USDT
```

USDT #2 仍要等 **下一次 buy(200)** 续单后才有 `claimable`，再 `claim`。

---

## 公式速查（100 U 本金，grace 正常路径，有 V1 上级）

```
毛收益     = 100 × 3%                    = 3 U
毛本金     = 100 U

本金到手   = 100 × (1 - 0.5%)            = 99.5 U
静态到手   = 3 × 70% × (1 - 0.5%)        = 2.0895 U
上级动态   = 3 × 2% × 90%                = 0.054 U
marketing  = 0.9 - 3 × 2%                = 0.84 U

质押用户 claim 合计 = 99.5 + 2.0895       = 101.5895 U
```

---

## 社区等级与动态比例（`getCommunityPercent`）

| 团队业绩 (groupSales) | 等级 | 动态比例 |
|----------------------|------|----------|
| < 1,000 U | — | 0%（不合格） |
| ≥ 1,000 U | V1 | 2% |
| ≥ 3,000 U | V2 | 4% |
| ≥ 5,000 U | V3 | 6% |
| ≥ 10,000 U | V4 | 10% |
| ≥ 50,000 U | V5 | 14% |
| ≥ 100,000 U | V6 | 18% |
| ≥ 500,000 U | V7 | 22% |
| ≥ 1,000,000 U | V8 | 26% |
| ≥ 5,000,000 U | V9 | 28% |
| ≥ 10,000,000 U | V10 | 30% |

### 其他等级示例（单上级、无更高层）

| 上级等级 | gross bonus | 上级实收 (×90%) | marketing leftover |
|----------|-------------|-----------------|-------------------|
| V1 (2%) | 0.06 | 0.054 | 0.84 |
| V3 (6%) | 0.18 | 0.162 | 0.72 |
| V10 (30%) | 0.90 | 0.810 | 0 |

---

## 相关代码位置

| 逻辑 | 文件 | 行号 |
|------|------|------|
| 续单解锁 claimable | `Pikachu.sol` | 127–156 |
| claim 循环 | `Pikachu.sol` | 231–254 |
| USDT 本金 fee | `Pikachu.sol` | 289–298 |
| 静态 / 动态拆分 | `Pikachu.sol` | 301–351 |
| 社区等级比例 | `Pikachu.sol` | 415–430 |


## 2) things to take note of
1. new tree, dun mix with previous pokemon tree.
2. pikachu contract will call pcs to add liquidity, so add pikachu contract in exclude list of TCG contract.

## 3) Useful Links/Sources
1. (plan) https://docs.google.com/spreadsheets/d/11_BJNzQ6BhfHJ_796o_kKDucsH9490JLhd3rIg3zOH4/
2. (reference code) https://github.com/nextfi-now/contracts
3. (verbal version)
   
   <img width="400" height="567" alt="image" src="https://github.com/user-attachments/assets/30f76d06-2c32-4702-b1c3-4919c2587aa6" />


# PokeDao Staking System Requirements

## 1. Staking Rewards

**Weekly Staking Yield based on number of direct referrals:**

- 0 referrals → **4% / week** 
- 1 referral → **5% / week** 
- 2 referrals → **6% / week**
- 3 referrals → **7% / week**
- 4 referrals → **8% / week**
- 5 referrals → **9% / week**
- 6 referrals → **10% / week**
- 7 referrals → **11% / week**
- 8 referrals → **12% / week**
- 9 referrals → **13% / week**
- 10 referrals → **14% / week**

**Rules:**
- Passive income yield is **4%**.
- Direct referrals must stake an **amount equal to or greater than the user’s own stake** in order to increase static yield.
- Each additional qualified referral increases **+1% weekly yield**.
- The **incremental weekly yield (1%–10%) is treated as active income**
- Every 7 days pending roi will consolidate as confirmed roi.
- Pending roi will forfeit if user unstake early.
- Pending roi is calculated every block.
- User always has one staking order even multiple stake is made (more easy to work with max cap).
- Pending roi will consume max-cap-quota.
- Unstake early will remove pending roi from max-cap-quota.
- Restake will restart new 7 days (This will cause early unstaking fee fall back to 20%).
- Min stake amount: $100.
- Max stake amount: $1000.

## 2. Active Income — Generation Bonus

**Referral generations unlocked by number of direct referrals:**

- V1 → 1 referral → **2 generations** (50% / 5%)
- V2 → 2 referrals → **4 generations** (50% / 3% × 3)
- V3 → 3 referrals → **6 generations** (50% / 3% × 5)
- V4 → 4 referrals → **8 generations** (50% / 3% × 7)
- V5 → 5 referrals → **10 generations** (50% / 3% × 9)
- V6 → 6 referrals → **12 generations** (50% / 3% × 11)
- V7 → 7 referrals → **14 generations** (50% / 3% × 13)
- V8 → 8 referrals → **16 generations** (50% / 3% × 15)
- V9 → 9 referrals → **18 generations** (50% / 3% × 17)
- V10 → 10 referrals → **20 generations** (50% / 3% × 19)


**Rules:**
- Derived from **passive income**.
- Each **1 direct referral unlocks 2 generations**.
- Direct referrals must stake **equal or higher amount** to unlock generations.
- **1st generation:**
    - Receives **50%** of the generation’s staking yield.
    - Allowed to earn from **larger stake**.
- **2nd–20th generations:**
    - Receive **3%** each of the generation’s staking yield.
    - Settlement limited to **same staking amount only**.

**Example:**

- User stakes **100U** and directly refers **10 users staking 100U** → unlocks **20**
    **generations**.
- If **1st generation user stake = 1000U** :
    - Reward = **1000 × 4% × 50% = 20U**
- If **2nd–20th generations user stake = 1000U** :
    - Calculated only on **100U cap**
      Reward = **100 × 4% × 3% = 0.12U per generation**

## 3. Active Income — Community Bonus

**Community bonus distribution tiers:**

- P1 → **10% pool share** → **Small zone requires 10,000**
- P2 → **20%** → Requires **50,000**
- P3 → **30%** → Requires **100,000**
- P4 → **40%** → Requires **300,000**
- P5 → **50%** → Requires **500,000**
- P6 → **60%** → Requires **1,000,000**
- P7 → **70%** → Requires **3,000,000**
- P8 → **80%** → Requires **5,000,000**
- P9 → **90%** → Requires **10,000,000**
- P10 → **100%** → Requires **30,000,000**

**Pool Source:**

- Derived from **passive roi income (4%)**.
- Triggered when user claim.
- Assessment depth limited to **30 generations**.


## 4. Income Distribution Structure

All **Active Income** are distributed as:
- **70% FATOKEN**
- **30% Blind Box Tickets ($10 Pool Ticket Applied)**

All **Passive Income** are distributed as:
- **100% FATOKEN**

FATOKEN (Fake A Token)
- aBnBUsdt

## 5. Exit Rule (3× Cap)

- Total **Staking + Active rewards capped at 3×** of staking amount. Reward after hit max cap will flush.
- After reaching **3×** , user must **re-stake** to continue earning.
- Exited stake **no longer generates staking rewards**.

## 6. Unstaking & Redemption Rules

**Early unstaking fee: (Principal+Interest)**

- Month 1 → **20%**
- Month 2 → **15%**
- Month 3 → **10%**
- Month 4+ → **5%**

**Additional rules:**

- Redemption processed within **7 days**.
- Upon exit, **previous position and ranking are reset**.
- **Full redemption only** (partial withdrawal not allowed).

## 7. Live Addresses

| Address | Purpose |
|--|--|
| 0x219c6f27553151932b10f20108499c5c7722e2d6 | USDT Collector#1 | 
| 0x3a621d4317f789efc78a9a50036cb7f82b93642a | USDT Collector#2 | 
| 0x4f1f6a990678f19f95d87cc77f85266ed86c7dda | USDT Collector#3 | 
| 0x5c188ae0d4133e2bb1752d9200da0f1a3b51d26a | USDT Collector#4 | 
| 0x6cdf9f30b118c36496359320cf9acd6e7e44f4d1 | USDT Collector#5 | 
| 0x6ff4ed7451357f883d57c69c2bb5a7b1f8d85322 | USDT Collector#6 | 
| 0x71f826da07a6416873fe273e5c2f0f4f467cb4e6 | USDT Collector#7 | 
| 0x8c11be5506a0510ab0d16692f28373fb1b9d49dd | USDT Collector#8 | 
| 0xa03c798da6fd952f88a76e8478eb2c52fcd68937 | USDT Collector#9 | 
| 0xa7ca3ec8dc7bdc0ef883ae1caa5602e3bf8c35c9 | USDT Collector#10 | 
| 0xd77A41E95b7bE2AF6a72429B2F010e065078B20B | USDT Collector#11 | 




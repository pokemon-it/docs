# PokeDao Staking System Requirements

## 1. Staking Rewards

**Weekly Staking Yield based on number of direct referrals:**

- 0 referrals → **4% / week** (16% / month)
- 1 referral → **5% / week** (20% / month)
- 2 referrals → **6% / week** (24% / month)
- 3 referrals → **7% / week** (28% / month)
- 4 referrals → **8% / week** (32% / month)
- 5 referrals → **9% / week** (36% / month)
- 6 referrals → **10% / week** (40% / month)
- 7 referrals → **11% / week** (44% / month)
- 8 referrals → **12% / week** (48% / month)
- 9 referrals → **13% / week** (52% / month)
- 10 referrals → **14% / week** (56% / month)

**Rules:**
- Passive income yield is **4%**.
- Direct referrals must stake an **amount equal to or greater than the user’s own stake**
    in order to increase static yield.
- Each additional qualified referral increases **+1% weekly yield**.
- The **incremental weekly yield (1%–10%) is treated as active income**

## 2. Active Income — Generation Bonus

**Referral generations unlocked by number of direct referrals:**

- V1 → 1 referral → **2 generations** (50% / 5%)
- V2 → 2 referrals → **4 generations** (50% / 5% × 3)
- V3 → 3 referrals → **6 generations** (50% / 5% × 5)
- V4 → 4 referrals → **8 generations** (50% / 5% × 7)
- V5 → 5 referrals → **10 generations** (50% / 5% × 9)
- V6 → 6 referrals → **12 generations** (50% / 5% × 11)
- V7 → 7 referrals → **14 generations** (50% / 5% × 13)
- V8 → 8 referrals → **16 generations** (50% / 5% × 15)
- V9 → 9 referrals → **18 generations** (50% / 5% × 17)
- V10 → 10 referrals → **20 generations** (50% / 5% × 19)


**Rules:**
- Derived from **passive income**.
- Each **1 direct referral unlocks 2 generations**.
- Direct referrals must stake **equal or higher amount** to unlock generations.
- **1st generation:**
    - Receives **50%** of the generation’s staking yield.
    - Allowed to earn from **larger stake**.
- **2nd–20th generations:**
    - Receive **5%** each of the generation’s staking yield.
    - Settlement limited to **same staking amount only**.

**Example:**

- User stakes **100U** and directly refers **10 users staking 100U** → unlocks **20**
    **generations**.
- If **1st generation user stake = 1000U** :
    - Reward = **1000 × 4% × 50% = 20U**
- If **2nd–20th generations user stake = 1000U** :
    - Calculated only on **100U cap**
      Reward = **100 × 4% × 5% = 0.2U per generation**

## 3. Active Income — Global Bonus Pool

**Global bonus distribution tiers:**

- VIP1 → **30% pool share** → Requirement: **2 Community 50,000U**
- VIP2 → **10%** → Requires **2 Community VIP1**
- VIP3 → **10%** → Requires **2 Community VIP2**
- VIP4 → **10%** → Requires **2 Community VIP3**
- VIP5 → **10%** → Requires **2 Community VIP4**
- VIP6 → **10%** → Requires **2 Community VIP5**
- VIP7 → **10%** → Requires **2 Community VIP6**
- VIP8 → **5%** → Requires **2 Community VIP7**
- VIP9 → **5%** → Requires **2 Community VIP8**

**Pool Source:**

- Derived from **total platform 4% staking rewards (passive income)**.
- Assessment depth limited to **30 generations**.

**Example:**

- Total platform stake = **1,000,000U**
- Staking reward = **1,000,000 × 4% = 40,000U (Make it manipulatable)** 
- VIP1 pool = **40,000 × 30% = 12,000U**


Users meeting **2 Community 50,000U requirement** can enter VIP1 pool and receive
**weighted global dividend based on own team performance**.

## 4. Income Distribution Structure

All **Active Income** are distributed as:
- **70% VUSDT**
- **30% Blind Box Tickets ($10 Pool Ticket Applied)**

All **Passive Income** are distributed as:
- **100% VUSDT**

## 5. All Reward Calculation & Claim

- Rewards are **calculated every minute**.
- Rewards can be **claimed once every 7 days**.

## 6. Exit Rule (3× Cap)

- Total **Staking + Active rewards capped at 3×** of staking amount.
- After reaching **3×** , user must **re-stake** to continue earning.
- Exited stake **no longer generates staking rewards**.

## 7. Unstaking & Redemption Rules

**Early unstaking fee: (Principal+Interest)**

- Month 1 → **20%**
- Month 2 → **15%**
- Month 3 → **10%**
- Month 4+ → **5%**

**Additional rules:**

- Redemption processed within **7 days**.
- Upon exit, **previous position and ranking are reset**.
- **Full redemption only** (partial withdrawal not allowed).



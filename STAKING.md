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
- **70% ABC**
- **30% Blind Box Tickets ($10 Pool Ticket Applied)**

All **Passive Income** are distributed as:
- **100% ABC**

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



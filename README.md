# Pokedao (CRM)

## 1) NFT
- Two packages: a) $1000 & b) $10000
- Reward is capped by 200% of nft value. e.g $1000 NFT has $2000 quota to receive reward.
- NFT's quota will reduce when user receive reward.
- Quota calculation includes both passive and active income.
- One user can stake more than one NFT.
- NFT can sell in marketplace 

## 2) ROI

| Round | Daily Interest (%) |
|--|--|
| 1 | 0.3 |
| 2 | 0.33 |
| 3 | 0.36|
| 4 | 0.39 |
| 5 | 0.40 |
| 6 | 0.43| 
| 7 | 0.46 | 
| 8 | 0.49 |
| 9 | 0.50 |
| 10 | 0.53 |
| 11 | 0.56 |
| 12 | 0.59 |
| 13 | 0.60 |
| 14 | 0.63 |
| 15 | 0.66 |
| 16 | 0.69  |
| 17 | 0.7  |

- Passive bonus.
- 1 round = 7 days.
- NFT will continue generate reward even after round 17 and capped by 200% of nft value.
- Reward is only claimable when round ends. During active round, user can view accumulated rewards in real time but not allow to claim it.
- if user surrended before round end, he will lost accumulative reward of that specific round.
- Example 1. At day 17 * 7 th, total payout percentage is 60.34%.
- Example 2. no payout when user unstake nft at day 3.
- Example 3. payout is 0.3% * 7 when user unstake nft at day 7 and round is ended.

## 3) Matching ROI (Group Bonus)

| Rank Name | Small Leg Sales | Percentage (%) |
|---|---|---|
| P1 | 5K | 10 |
| P2 | 10K | 20 |
| P3 | 50K | 30 |
| P4 | 100K | 40 |
| P5 | 300K | 45 |
| P6 | 500K | 50 |
| P7 | 1M | 55 |
| P8 | 3M | 60 |
| P9 | 5M | 65 |
| P10 | 10M | 70 |

- Active bonus.
- Overriding + ROI Matching
- Reward = roi bonus * percentage, therefore this bonus will distribute only when user claim roi bonus.
- Max directs is 30. Exclude direct with biggest sales and sum the rest (29 directs) to determine user's rank.
- Upline will not entitle if pass up roi bonus is from direct with biggest sales.

## 4) Leadership Bonus

| Referred Users | Level | Percentage (%) |
|---|---|---|
| 1 | 1 | 10% |
| 3 | 2 | 20% | 
| 5 | 3 | 30% | 
| 7 | 4 | 40% | 
| 9 | 5 | 50% | 

- Active bonus.
- L1 only matching MR * 10% while L2 onward only matching LB.
- Calculation example.
```
A (50%)
 \
  B (40%)
   \
    C (30%)
     \
      D (20%)
       \
        E (10%), MR = $2000
         \ 
          F (10%), MR = $1000
           \ 
            G, MR = $1000

G, LB = 0
F entitles 10% with 1 level, LB = ($1000 * 10%) = $100
E entitles 10% with 1 level, LB = ($1000 * 10%) = $100 
D entitles 20% with 2 levels, LB = ($2000 * 10%) + ($100 * 20%) = $220 
C entitles 30% with 3 levels, LB = (0) + ($100 * 20%) + ($100 * 30%) = $50
B entitles 40% with 4 levels, LB  = (0) + ($220 * 20%) + ($100 * 30%) + ($100 * 40%) = $114
A entitles 50% with 5 levels, LB = (0) + ($50 * 20%) + ($220 * 30%) + ($100 * 40%) + ($100 * 50%) = $166 

(MR) Matching ROI, (LB) Leadership Bonus
```

## 5) Tree
- Same tree shared between crm and marketplace.
- Since max directs is fixed with 30, user allow to remove specific direct and removing direct will park under root.
- Remove direct will deduct uplines's group sales, this will only affects crm's group sales.
- Only user with real sales through buy pack or nft stake can enroll to tree.

# Marketplace 
## 1) Pack Logic
- Each group (happen at contract level, it is hidden from frontend) has many pools, at starting company will launch 3 pools, which is `Basic` ($10), `Pro` ($50) & `Master`($100) respectively.
- Admin insert unrevealed card into each pool. e.g 1000 cards in basic pool, 1000 cards in pro & 1000 cards in master
- Player buy a pack then contract will randomly choose 1 card from targetted pool. Odd change accordingly.
- In anytime admin can add new unrevealed card to pool. Odd change accordingly.
- Player can trigger buy back and receive buy back amount within 1 hour. Buy back card will fallback to pool again.
- After 1 hour, the reveal card still belong to platform until player update receive status only nft owner will switch to him.
- Buy pack amount will stay in contract until admin claim it.
- Ready admin a method to claim back redundant usdt from buypack contract.
- Manipulation.
  - Admin can mark specific card to prevent it from purchase by normal user.
  - Admin must prefill company address. so contract will run manipulation if sender is from company address.
  - Admin can set 2 types of manipulate behaviour for company address.
    - a) follow normal randomization (win normal nft).
    - b) can only win valued nft.
  - e.g if there are 3 valued nfts in the pool, and company address is set with `only win valued nft`, then either 1 of 3 valued nfts will open when company buy pack.

## 2) Pack Bonus

| Rank Name | % | Personal Sales | Group Sales | Referred users  |
|--|--|--|--|--|
| V1 | 4 | 100 | 0 |3|
| V2 | 8 | 100 | 0 |6|
| V3 | 12 | 100 | 0 |9|
| V4 | 16 | 300 | 10K|9|
| V5 | 20 | 300 | 30K |9|
| V6 | 22 | 300 | 60K |9|
| V7 | 24 | 400 | 100K | 9|
| V8 | 26 | 400 | 150K| 9|
| V9 | 28 | 500 | 300K | 9|
| V10 | 30 | 1000 | 500K | 9|

- Overriding bonus. Leftover amount will go to marketing beneficiary.
- Buy back tax is 20%. e.g a pack's buy back amount is $50, after tax player will only receive $40.
- Max payout is 30% of buy back tax. e.g if pack's buy back amount is $50, 30% of $10 or $3 will use to distribute this bonus.
- Max depth is 30.
- Bonus is distributed right away when user does buy back.
- Month is maintained by `monthIndex`. e.g 682 (monthIndex) is from 8/12/2025 to 7/1/2026 while 683 is from 7/1/2025 to 7/1/2026 + 30D.
- Every month user need maintain personal sales
  - user will be qualified by 1st month and 2nd month for `first month purchase`.
  - 3rd month is qualified only if user purchase at 2nd month, else 3rd amonth will always be disqualified.
  - after `first month purchase`, purchase is to maintain next month.
- Group sales will maintain 6 months only, 7th month will flush first month, 8th month will flush 2nd month. e.g let say current monthIndex is 690, my group sales is accm of monthIndex 690 + 689 + 688 + 687 + 686 + 685.
- A referred user is qualified only if he does maintain personal sales (minimum $100).

# Addresses

| Address | Purpose |
|--|--|
| 0x71887b82DAFb18d56b39Df0c964070b0f71Cb2B1 | Pack's Marketing Beneficiary |
| 0xbd20ed3D8CACE246DC213Ab0530943A8B778Ce62 | Pack's Sales Beneficiary | 

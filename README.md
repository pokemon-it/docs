# Pokedao

## 1) NFT
- Two packages: a) $1000 & b) $10000
- Reward is capped by 200% of nft value. e.g $1000 package has $2000 quota to receive reward.
- NFT's quota will reduce when user receive reward.
- Quota calculation includes both passive and active income.
- One user can stake more than one NFT.

## 2) ROI
- 1 round = 7 days 
- Round and interest table.

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

- NFT will continue generate reward even after round 17 and capped by 200% of nft value.
- Each round lasts 7 days. Users may claim rewards only after that round ends. During an running round, users can view accumulated rewards in real time but not allow to claim it.
- if user surrended before round end, he will lost accumulative reward of that round.
- Example 1. At day 17 * 7 th, total payout percentage is 60.34%.
- Example 2. no payout when user unstake nft at day 3.
- Example 3. payout is 0.3% * 7 when user unstake nft at day 7 and round is ended.

## 3) Group Bonus

| Rank Name | Small Leg Sales | % |
|---|---|---|
| P1 | 0 | 10 |
| P2 | 0 | 20 |
| P3 | 0 | 30 |
| P4 | 0 | 40 |
| P5 | 0 | 50 |
| P6 | 0 | 55 |
| P7 | 0 | 60 |
| P8 | 0 | 65 |
| P9 | 0 | 70 |

- Overriding.
- Base amount of % is roi bonus. Mean this bonus will distribute when user claim roi bonus.
- Max directs is 30. Exclude direct with biggest sales then sum the rest (29 directs) to determine user's rank.
- Upline will not entitle if pass up roi bonus is from direct with biggest sales.
- 

# Marketplace 
## 1) Pack Logic
- Each group (happen at contract level, it is hidden from frontend) has many pools, at starting company will launch 3 pools, which is `Basic` ($10), `Pro` ($50) & `Master`($100) respectively.
- Admin insert unrevealed card into each pool. e.g 1000 cards in basic pool, 1000 cards in pro & 1000 cards in master
- Player buy a pack then contract will randomly choose 1 card from targetted pool. Odd change accordingly.
- In anytime admin can add new unrevealed card to pool. Odd change accordingly.
- Player can trigger buy back and receive buy back amount within 1 hour. Buy back card will fallback to pool again.
- After 1 hour, the reveal card still belong to platform until player update receive status only nft owner will switch to him.
- When buy pack, only profit part will directly transfer to profit beneficiary on the spot.
  - ✅ Has profit. e.g pack amount $100, buy back $50 and bonus $30. Profit = 100 - (50 + 30) = 20.
  - ❌ Has no profit. e.g pack amount $100, buy back $1500 and bonus $30, Profit = 100 - (1500 + 30) = -1430.
- Ready admin a method to claim back redundant usdt from buypack contract.
- Manipulation. Admin can mark specific card to prevent it from user purchase.

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
- Max payout per pack order is 30%.
- Max depth is 30.
- Bonus is distributed right away when user buy pack.
- Month is maintained by `monthIndex`. e.g 682 (monthIndex) is from 8/12/2025 to 7/1/2026 while 683 is from 7/1/2025 to 7/1/2026 + 30D.
- Every month user need maintain personal sales
  - user will be qualified by 1st month and 2nd month for `first month purchase`.
  - 3rd month is qualified only if user purchase at 2nd month, else 3rd amonth will always be disqualified.
  - after `first month purchase`, purchase is to maintain next month.
- Group sales will maintain 6 months only, 7th month will flush first month, 8th month will flush 2nd month. e.g let say current monthIndex is 690, my group sales is accm of monthIndex 690 + 689 + 688 + 687 + 686 + 685.
- A referred user is qualified only if he does maintain personal sales (minimum $100).
   

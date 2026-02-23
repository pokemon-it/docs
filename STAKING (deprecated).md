
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



# Marketplace 
## 1) Pack Logic
- Each group (happen at contract level, it is hidden from frontend) has many pools, at starting company will launch 3 pools, which is `Basic` ($10), `Pro` ($50) & `Master`($100) respectively.
- Admin insert unrevealed card into each pool. e.g 1000 cards in basic pool, 1000 cards in pro & 1000 cards in master
- Player buy a pack then contract will randomly choose 1 card from targetted pool. Odd change accordingly.
- In anytime admin can add new unrevealed card to pool. Odd change accordingly.
- Player can trigger buy back and receive buy back amount within 1 hour. Buy back card will fallback to pool again.
- after 1 hour, the reveal card still belong to platform until player update receive status only nft owner will switch to him.
### 1.1) Bonus

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
- Bonus is distributed right away when user buy pack. no overpay as pack amount $100 is enough to cover both buy back ($50) and bonus ($30). 
- Month is maintained by `monthIndex`. e.g 682 (monthIndex) is from 8/12/2025 to 7/1/2026 while 683 is from 7/1/2025 to 7/1/2026 + 30D.
- Every month user need maintain personal sales, user will be qualified by this month and next month for first time purchase, next month if he purchase nothing then he is not qualified for month after next month.
- Group sales will maintain 6 months only, 7th month will flush first month, 8th month will flush 2nd month. e.g let say current monthIndex is 690, my group sales is accm of monthIndex 690 + 689 + 688 + 687 + 686 + 685.
- A referred user is qualified only if he does maintain personal sales (minimum $100).
   

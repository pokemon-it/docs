# Marketplace 
## 1) Pack Logic
- Each group (happen at contract level, it is hidden from frontend) has many pools, at starting company will launch 3 pools, which is `Basic` ($10), `Pro` ($50) & `Master`($100) respectively.
- Admin insert unrevealed card into each pool. e.g 1000 cards in basic pool, 1000 cards in pro & 1000 cards in master
- Player buy a pack then contract will randomly choose 1 card from targetted pool. Odd change accordingly.
- In anytime admin can add new unrevealed card to pool. Odd change accordingly.
- If not satisfy, player can trigger buy back and get back 90% within 1 hour.
- after 1 hour, the reveal card still belong to platform until player update receive status only nft owner will switch to him.
### 1.1) Bonus
- Overriding bonus.

| Rank Name | % | Personal Sales | Group Sales | Direct  |
|--|--|--|--|--|
| V1 | 4 | 100 | 0 |3|
| V2 | 8 | 100 | 0 |6|
| V3 | 12 | 100 | 0 |9|
| V4 | 16 | 300 | 10K|0|
| V5 | 20 | 300 | 30K |0|
| V6 | 22 | 300 | 60K |0|
| V7 | 24 | 400 | 100K | 0|
| V8 | 26 | 400 | 150K| 0|
| V9 | 28 | 500 | 300K | 0|
| V10 | 3O | 1000 | 500K | 0|

- Max depth is 30.
- Bonus is distributed right away when user buy pack.
- Month is maintaned by `monthIndex`. e.g 682 (monthIndex) is from 8/12/2025 to 7/1/2026 while 683 is from 7/1/2025 to 7/1/2026 + 30D.
- Every month user need maintain personal sales, user will qualify for this month and next month for first time purchase, next mo if he didnt purchase anything then he is not qualified for next next month.
- Group sales will maintain 6 months only, 7th month will flush first month, 8th month will flush 2nd month. e.g let say current monthIndex is 690, my group sales is accm of monthIndex 690 + 689 + 688 + 687 + 686 + 685.
- Direct number (V1-V3) once hit then is permanent.
   

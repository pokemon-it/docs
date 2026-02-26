# Marketplace 
## 1) Pack Logic
- Each group (happen at contract level, it is hidden from frontend) has many pools, at starting company will launch 3 pools, which is `Basic` ($10), `Pro` ($50) & `Master`($100) respectively.
- Admin insert unrevealed card into each pool. e.g 1000 cards in basic pool, 1000 cards in pro & 1000 cards in master
- Player buy a pack then contract will randomly choose 1 card from targetted pool. Odd change accordingly.
- In anytime admin can add new unrevealed card to pool. Odd change accordingly.
- Player can trigger buy back and receive buy back amount within 30 min. Buy back card will fallback to pool again.
- After 30 min, the reveal card still belong to platform until player update receive status only nft owner will switch to him.
- Buy pack amount will stay in contract until admin claim it.
- Ready admin a method to claim back redundant usdt from buypack contract.
- Manipulation.
  - Admin can mark specific card to prevent it from purchase by normal user.
  - Admin must prefill company address. so contract will run manipulation if sender is from company address.
  - Admin can set 2 types of manipulate behaviour for company address.
    - a) follow normal randomization (win normal nft).
    - b) can only win valued nft.
  - e.g if there are 3 valued nfts in the pool, and company address is set with `only win valued nft`, then either 1 of 3 valued nfts will open when company buy pack.
- `Capital Protection Mechanism (Daily Limit)`
  - First 10 packs openings per round.
  - Trigger 3 rounds per day per user.
  - Example below is for $10 pack:
    - 10 packs × 10 USD = $100 cost
    - If the total buy back value after 10 openings is $80,
    - the platform compensates 2 additional 10 USD packs.
    - Compensated packs is not real sales, do not generate turnover or volume thus no bonus distributed.
  - A user can own different ticket wallets for different pool.

## 2) Buy Back
- `Buy Back Tax (BBT)` is 20% (default) of card value, 10-30% adjustable timely and all nft cards will be affected once change.
- `Buy Back Value (BBV)` = card value - BBT.
- COST = pack amount.
- BBT allocation.

| % | Usage |
|--|--|
| 20 | Platform fees (Nodes) |
| 80 | Bonus |

## 3) Pack Bonus

| Rank Name | % | Personal Sales | Group Sales |
|--|--|--|--|
| P1 | 20 | 100 | 1,000 |
| P2 | 30 | 200 | 10,000 |
| P3 | 40 | 300 | 100,000 |
| P4 | 50 | 500 | 1,000,000 
| P5 | 60 | 1,000 | 5,000,000 |
| P6 | 70 | 3,000 | 20,000,000 |
| P7 | 75 | 5,000 | 100,000,000 | 
| P8 | 80 | 10,000 | 300,000,000 | 
- This bonus percentage will time against TAX amount.
- Max depth is 30.
- Overriding bonus. Leftover amount will go to marketing beneficiary.
- Bonus is distributed from bonus portion of `Buy Back Tax`.
- Bonus allocation.

| % | Usage |
|--|--|
| 70 | User's actual receive |
| 30 | Platform Fees |

- Bonus is distributed right away when user does buy back.
- Month is maintained by `monthIndex`. e.g 682 (monthIndex) is from 8/12/2025 to 7/1/2026 while 683 is from 7/1/2025 to 7/1/2026 + 30D.
- Both `group sales` and `personal sales` will maintain for 3 months only, 4th month will flush 1st month, 5th month will flush 2nd month. e.g let say current monthIndex is 690, my group sales is accm of monthIndex 690 + 689 + 688.

## 4) Currencies

| Token | In | Out | 
|--|--|--|
| USDT | Swap From VUSDT | Swap To VUSDT |
| VUSDT | Buy Back, Bonus | Buy Pack, Swap To USDT |
| Pool Ticket | Capital Protection Triggered | Buy Pack |

- 1 VUSDT = 1 USDT, VUSDT is mirror token of USDT.
- A user can own different ticket wallets for different pool.

## 5) Phase 2 Todo
- When deposit, USDT > Atoken > VUSDT
- When withdaw, VUSDT > Atoken > USDT
- Atoken docs: https://aave.com/docs/aave-v3/smart-contracts/tokenization.
- Rotate multiple Atoken collector (previously known as USDT collector).

## 6) Live Addresses

| Address | Purpose |
|--|--|
| 0x53Adec8A46231e8FF4a52428076e26AD2c445Df5 | VUSDT |
| 0x498d3e29e3df158f541d9eaa0dc01d182380ff59 | Pack Contract |
| 0xa9f4e0aa5b8f3b2d6f0ade5198988e2e50cc3cce | Bonus Contract |
| 0xae811338e6b4993c95b0ac43431339428f185aa4 | Referral Contract |
| 0x97f1299b61c1d0ad20f7d6287003a471ad411b5f | NFT Contract |
| ?? | Marketplace Contract |
| 0x71887b82DAFb18d56b39Df0c964070b0f71Cb2B1 | Marketing Beneficiary |
| 0xbd20ed3D8CACE246DC213Ab0530943A8B778Ce62 | USDT Collector | 

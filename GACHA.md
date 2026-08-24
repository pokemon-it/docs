# Gacha
## 1) First Pool Setup
- Buyback: 10%
- Pack size: 50k
- Price per pack: 10u (buy with USDT)
- Total nft: 5000
- Biggest prizes: 1000u value card
- Reward: same as buypack

## 2) Draw Algorithm
- admin arrange and insert nft randomly into pool.
- technically, first nft in the pool is marked as 0 position, while last nft is marked as 4999 position.
- player's pack number follows sequence and is incremental. e.g technically, if first player bought 10 packs, then he will own pack number from 0 to 9.
- when all packs sold, programmer trigger open draw and contract will pick a random number between 0 to 4999 as `start position`.
- let say opened `start position` is 123.
- first player will receive nft with position between 123 to 133 from pool.

## 3) Flow
- players buy gacha packs.
- packs sold all.
- programmer trigger open draw.
- player trigger claim to know what he win.
- player either accept card or do buy back (this step is same as buy pack).
- buy back nft will flow back to admin, not to pool (gacha pool cannot be reuse).

## 4) Bonus
- Share same bonus/ranking/tree/sales accumulation with buy pack, except payout is in USDT instead of VUSDT.

## 5) Buy Back
- Same as buy pack, except buy back tax may will change and payout is in USDT instead of VUSDT.

## 6) Capital Protection
- No capital protection, no free ticket.



  

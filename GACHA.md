# Gacha
## Pool Setup
- Buyback: 10%
- Pack size: 50k
- Price per pack: 10u (buy with USDT)
- Total nft: 5000
- Biggest prizes: 1000u value card
- Reward: same as buypack

## Draw Algorithm
- admin arrange insert nft randomly into pool.
- technically, first nft in the pool is marked as 0 position, while last nft is marked as 4999 position.
- player's pack number follows sequence and incremental. e.g technically, if first player bought 10 packs, then he will own pack number from 0 to 9.
- when all packs sold, programmer trigger open draw and contract will pick a random number between 0 to 4999 as `start position`.
- let say opened `start position` is 123.
- first player will receive nft with position between 123 to 133 from pool.

## Bonus
- Share same bonus & ranking mechanism with buy pack, except payout is in USDT instead of VUSDT.
- Share same sales (both personal & group) contribution way with buy pack.

## Capital Protection

  

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
- Share same bonus & ranking mechanism with buy pack, except payout is in USDT instead of VUSDT.
- Share same sales (both personal & group) contribution way with buy pack.

## 5) Buy Back
- Same as buy pack.

## 6) Capital Protection

## 7) Live Addresses

| Address | Purpose |
|--|--|
| 0x9d887267F86C294a0f02859a3ED29DBf4A99E425 | Gacha |
| 0x15B818B332162EA6Ee96addb8c4Da5b33823B45D | Gacha NFT |
| 0x972f6175c5fda13351064ddaea9d246b00727dfe | USDT Collector#1 |
| 0xe4efa1f6216c62917e23d9a033d68a3215d131b5 | USDT Collector#2 |
| 0x1878c677d71c9adabab509d7ddfa606f7f14412a | USDT Collector#3 |
| 0xcf41b0e35fa9197ce94858013a0fded3e443d14e | USDT Collector#4 |
| 0x80f728bd121f723b6104ed7e0b5145c891f557a3 | USDT Collector#5 |
| 0x747d0b1819711fdb1564d2620246926e652cb144 | USDT Collector#6 |
| 0x4706e46a68d0901cfa6169cdfa17890c2e0e8088 | USDT Collector#7 |
| 0xc0655bab10ba8b4e8dbb6b09b5a5c28a85daceb9 | USDT Collector#8 |
| 0x7fe4ab191644544cac6aa3f6cf5af7e1c3057b55 | USDT Collector#9 |
| 0xd3547081eb048b71580e19472f8df781eac0e460 | USDT Collector#10 |

  

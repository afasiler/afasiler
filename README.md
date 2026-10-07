# Ahmet Furkan Asiler

Computer Engineering @ Ankara University. Ankara.

I work on AI and low-level system design. Most of what I do sits where the two meet: models small enough for microcontroller-class targets — kilobytes of RAM, no OS, no `malloc`, so 1-bit weights, bit-packed frames and every buffer placed ahead of time — and the allocators and memory layout that make them fit. Down there the model and the memory are the same problem. I also train at ordinary scale, where none of that is a constraint.

**Projects**

- [afalloc](https://github.com/afasiler/afalloc) — a memory allocator written from scratch in C on top of `mmap`. The current one is a chunked pool allocator with two pools, one persistent and one scratch that is rewound wholesale instead of freed block by block. Segregated size-class free lists make allocation and free O(1); chunks are mapped lazily and chained as a pool fills; a spinlock makes it thread-safe and `afa_prefault` takes the first-touch page faults out of the hot path. It is tested with a randomized stress test under ASan/UBSan, ThreadSanitizer and CI on gcc and clang, and benchmarked against glibc `malloc`, including where it loses (the README lists its limits). The two earlier designs, a first-fit allocator with coalescing and a boundary-tag arena with O(1) backward coalescing, are kept in the repo for comparison.

- **minecraft-hypixel-trading-model** (private) — a reinforcement learning trader for a virtual commodity market. Most of the work is in the environment rather than the algorithm: relative spread, order imbalance and log returns as features, the game's 124-hour political cycle encoded cyclically, the 1.25% sales tax priced into every exit, and reward divided by rolling volatility so a lucky trade in a calm market doesn't outrank a good one in a violent market. The data comes from a collector that has been recording every tracked item minute by minute for months.

**Recent work** (internship projects, so the code is private)

- Satellite monitoring of reservoirs in Türkiye: estimating surface area, water level and volume from Sentinel-2 with a U-Net, calibrated and checked against official records, plus chlorophyll-a and turbidity models validated with scene- and region-grouped splits so the scores aren't inflated by spatial leakage.
- Turkish call-center analytics: speaker diarization and Whisper feeding a shared BERTurk backbone with separate heads for customer emotion, purchase decision and agent fraud.
- OCR for tire sidewall labels: text detection and recognition that turns photos into structured fields.

**Stack:** C, Python, Java, SQL, PyTorch, XGBoost

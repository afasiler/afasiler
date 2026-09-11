# Ahmet Furkan Asiler

Computer Engineering @ Ankara University. Ankara.

I work on AI and low-level system design. Most of what I do sits where the two meet: models small enough for microcontroller-class targets — kilobytes of RAM, no OS, no `malloc`, so 1-bit weights, bit-packed frames and every buffer placed ahead of time — and the allocators and memory layout that make them fit. Down there the model and the memory are the same problem. I also train at ordinary scale, where none of that is a constraint.

**Projects**

- [afalloc](https://github.com/afasiler/afalloc) — three memory allocators written from scratch in C. A 1 MiB `mmap` region with first-fit, block splitting and forward coalescing; a boundary-tag arena whose footers hold back-pointers, which makes backward coalescing O(1); and a two-region variant built for a per-frame inference loop, where one chunk persists for the whole run and the scratch chunks are dropped wholesale by resetting a frontier instead of being freed block by block. Every header carries a magic number that is verified on free, so a foreign or corrupted pointer is caught rather than quietly eating the heap.

- [minecraft-hypixel-trading-model](https://github.com/afasiler/minecraft-hypixel-trading-model) — a reinforcement learning trader for a virtual commodity market. Most of the work is in the environment rather than the algorithm: relative spread, order imbalance and log returns as features, the game's 124-hour political cycle encoded cyclically, the 1.25% sales tax priced into every exit, and reward divided by rolling volatility so a lucky trade in a calm market doesn't outrank a good one in a violent market. The data comes from a collector that has been recording every tracked item minute by minute for months.

**Stack:** C, Python, Java, PyTorch

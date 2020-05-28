## Key-Value Storage Engines

Three different storage engine designs:
- B tree
- Log structured merge tree
- Log and index (mostly hash index) on unordered data, eg, [FASTER](https://www.microsoft.com/en-us/research/uploads/prod/2018/03/faster-sigmod18.pdf)


## Faster: A Concurrent Key-Value Store with In-Place Updates

A few contributions:
- Augment standard epoch-based synchronization into a generic framework that faciiltates lazy propagation of global changes to all threads via trigger actions
- Concurrent latch-free resizable cache-friendly hash index
- HybridLog: a new hybrid log that seamlessly combines in-place updates with a traditional append-only log

I don't quite understand the epoch-based synchronization thing. The throughput seems quite amazing, at 160M op/s! Source code is [here](https://github.com/microsoft/FASTER)


## RadixSpline: A Single-Pass Learned Index

One-pass learnt index for LSM. Interesting idea to apply single-pass training while merging two data files.

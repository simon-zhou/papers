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

## The Buffer Tree: A New Technique for Optimal I/O Algorithms

Having a buffer for each node seems promissing in the sense that lots of insert/update operations can be batched. This is not too different from B tree implementation, eg, in PG. In-memory disk pages will be flushed at a later stage. The only improvement is for tree navigation. In B tree we have to navigate to leaf node for every update/insert operations while in buffer tree these can be batched, as long as there is more than one data change are on the same page.

Compared with LSM, the improvement on IO is also not that huge because LSM is already optimized for upsert/deletion.

## The Bw-Tree: A B-tree for New Hardware Platforms

I read a few paragraphs of this paper but couldn't get how it's different from B tree.

## ARIES: A Transaction Recovery Method Supporting Fine-Granularity Locking and Partial Rollbacks Using Write-Ahead Logging

I haven't read it in details but this is a must read. PG doesn't have undo log while Oracle has it.

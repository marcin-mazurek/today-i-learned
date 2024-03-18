# Cache eviction strategies
A **cache eviction strategy** determines how items are removed from a cache when it becomes full.

Common strategies:

1. **Least Recently Used (LRU)**: Removes items not accessed recently, assuming recent items will likely be accessed again.
1. **Least Frequently Used (LFU)**: Removes least accessed items, predicting frequent past access indicates future access.
1. **Most Recently Used (MRU)**: Opposite of LRU. Evicts the most recently accessed items, beneficial when recent items are less likely to be reused.
1. **Time To Live (TTL)**: Assigns a lifespan to items, removing them post-expiry. Useful for time-sensitive data.

Naive strategies (not recommended):

1. **First In, First Out (FIFO)**: Removes the oldest items first.
1. **Random Replacement (RR)**: Randomly chooses items for eviction.

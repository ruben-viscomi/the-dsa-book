The HashMap is a data structure used to store a collection of key - value pairs.
This allows to access access the value, given the key in "constant time".
Even though this data structure provides a theoretical `O(1)` access time, it's worth noting that it uses a hashing algorithm to compute the index from the given key. This simply means that the access time is actually given by the algorithm used for hashing.

## Usages
It's commonly used to optimize algorithms, that are running in  `O(n²)` or more in time complexity. This is because we're sacrificing memory in order to get the almost constant time access to elements stored with a strategic key.
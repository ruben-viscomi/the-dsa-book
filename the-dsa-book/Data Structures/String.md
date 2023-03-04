Stored in contiguous memory, Strings are a specialization of [[Array|Arrays]] used for text purpose.
They differ from [[Array|Arrays]] due to the use of `\0` special character, which is implicitly used to delimit the end of the string in memory.

Strings are generally stored in the heap, whenever a dynamic size is required.
It mostly depends on the language implementation, in case strings are supported.
Whenever it's not the case, it's always possible to implement your own version through the use of [[Array]] of characters and heap memory allocation, in case of mutable strings.
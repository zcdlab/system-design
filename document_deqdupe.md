# Document Dedupe

## Basic
We can sue checksum to check if current document has seen before. The checksum is usually 64 bits and we can use MD5 or SHA to calculate the checksum.

## Storage

We need to consider the storage cost of saving the checksum. Since it is 64-bit checksum, we need to take extra 8 bits to save it for each document.
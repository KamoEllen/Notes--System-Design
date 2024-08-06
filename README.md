# Notes--System-Design
hi . Learning system design , will build database and api from scratch with new language. excited ! Public for friends to see :) learn with me.

##database
-way to access data that wont be on ur device

## what I want from the database
-fast reads
-fast writes
-if off , data isnt lost.

## When methods r useful (pros and cons)a
-search in array for thing u want to read and write
-not good enough
-solution : use append only log , we overwrite 
-search from bottom to top 
-hash map , constant time access , if we cant fit on disk that'd suck , if its small data set its nice
-indexes , keep extra pieces of metadata on every write so we can track whichh values on diff rows r the same. If there is index on every column then writes will take a long time so that sucks.
-hash indexs , all keys need to fit in memory , it works slow on disks but fast on RAM . 
-SSTables and LSM trees , on ram we write to in memory buffer ,have self balancing tree & when we take it once its full it'd be sorted(tree traversal) write it to sstable file held on disk. if database crash that'd suck.Keep second log that tracks changes made on tree. reset tree n write key.
-duplicate key, overwrite key ? thats wasting storage , compress ?
-duplicate key will have updated value , linear time operation to compress , merge it in linear time.
-reading value (sstable & lsm) keep small hash table that can fit in memory . run binary search split and u can search.
-reads r slow (sstables n lsm) 
-b-trees , uses pointers. take references . traverse thru tree to find n update or read. to write if theres space in block then we can write there, but if not , split block in two add key n update the parent block. 
-write ahead log , write changes so if all crash u have backend. all keys next to each other in range r near in drive.





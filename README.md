# SW64_CAT
This is initial version of swcat that I started on Mar 20, the linux kernel version is linux 4.4 head at 6fceef9be2e86ce03da2ed4c6c3f289c1c870195
 
See [Intel CAT](https://software.intel.com/en-us/articles/introduction-to-cache-allocation-technology "Intel CAT") for detail

If you really want to do sth for SW64, please contact me or issue a pull request.


## cache allocation detail

6A processor has a 32 way associative last level cache, which is partitioned into 4 parts. Each part of LLC is reserved for a group of 4 cores. 
Cross llc group memory access will cause long ld/st latency, hence a cat tech is needed.
bit 8 and bit 7 are used to index the 4 llc groups. 

# 中文版本

## cache分配细节

6A处理器16个处理器核，分为4个核组，每个核组4个处理器核，共享L3cache.
L3 cache大小为32MB，每个核组使用8MB。
由于跨核组访问内存延迟大，为解决这个问题，需要对核组内应用进行cache访问隔离。
bits8\:7 用来索引核组。
       |19 ...  | 9     8     7  |
                 core group





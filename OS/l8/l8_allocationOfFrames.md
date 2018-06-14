# Allocation of Frames

each process needs minimal number of pages  
determined by 指令集的结构  

### fix-sized allocation
#### equal allocation 
完全等分  
#### proportional allocation  
依据进程所占的空间大小，来按比例等分   

### priority allocation  
use a proportional allocation scheme using priorities rather than size  

如果遇到了page fault,可以选择  

* local replacement  **之前讲的都是局部置换！**  
* global replacement:replace the lower priority process's frame   



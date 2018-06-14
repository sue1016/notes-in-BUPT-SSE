# paging
### TLB  
     
      是为了解决每次执行指令都需要两次访问内存 
      命中--> 一次块表 + 一次内存 访问   
 <font color="purple">      没命中--> 一次块表+两次内存 访问 </font> 


### 计算 有效访问时间EAT 
>p58

### memory protection  
protection bit   
  
      valid/invalid bit attached to each entry in the page table  

PTBR
    
           页表基址寄存器  
PTLR

           页表线长寄存器  

### share pages  
copy  -> waste

share page -> 
* shared code 

           不管逻辑号是多少，为了共享，映射到物理号都是一样的  

* private code and data
           其他的，都可以散落在其他逻辑号的页。

### Structure of the page table

>如果一个进程就超过了最大页表量该怎么办？

* 多级页表  
<font color = "purple">二级页表需要访问3次内存</font>   
>访问内存次数增长快，怎么办？  

* Hashed Page Table  
  
     1.页号放入哈希表里去，找到物理页框号  
     2.拿物理页框号对进行比对  
     3.如果..提取
查询效率更高，但是要解决冲突。
 
* 反置页表
好处：不用每个进程存一个页表，整个系统就只需要维护一张表  
坏处：
      1.检索时间开销比较大 
      2.还是可以用hash table来优化检索效率，不需要比对，直接映射  


# Page replacement
> 如果没有free frame怎么办？   
 
find some pages in memory,but really not in use,swap it out  

### Basic page replacement
* find the location of the desired page on disk  
* find a free frame  
-- if there is,use it
-- if not,use a page replacement algorithm to select a victim frame  
* bring the desired page into the (newly) free frame;update the page and the frame tables  
* restart the process  

处于缺页中断时，该进程处于阻塞状态  

> How do we select a particular replacement algorithm?   

In general, we want the one with the **lowest page-fault rate**.  

          We evaluate an algorithm by running it on a particular string of memory references and computing the number of page faults. The string of memory references is called a reference string.  

          Obviously, as the number of frames available increases, the number of page faults decreases.. Of course, adding physical memory increases the number of frames.
          
> example 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2, 1, 2, 0, 1, 7, 0, 1 .for a memory with three frames  

<font color=red>注意题目问的是replace次数，还是page fault的次数</font>  

### FIFO replacement algorithm  
We can create a FIFO queue to hold all pages in memory.
We replace the page at the head of the queue. When a page is brought into memory, we insert it at the tail of the queue  
         
         eg:For our example reference string, our three frames are initially empty. The first three references (7, 0, 1) cause page faults and are brought into these empty frames. The next reference (2) replaces page 7, because page 7 was brought in first. Since 0 is the next reference and 0 is already in memory, we have no fault for this reference. The first reference to 3 results in replacement of page 0, since it is now first in line. Because of this replacement, the next reference, to 0, will fault. Page 1 is then replaced by page 0. This process continues as shown in Figure 9.12. Every time a fault occurs, we show which pages are in our three frames. There are fifteen faults altogether.

#### Belady’s anomaly  
for some page-replacement algorithms, the page-fault rate may increase as the number of allocated frames increases.**只有FIFO会出现这种现象,后面的算法都不会出现**   


### Optimal replacement algorithm  
the algorithm that has the lowest page-fault rate of all algorithms and will never suffer from **Belady’s anomaly**    
Replace the page that will not be used for the longest period of time   
  
         eg:For example, on our sample reference string, the optimal page-replacement algorithm would yield nine page faults  
         The first three references cause faults that fill the three empty frames. The reference to page 2 replaces page 7, because page 7 will not be used until reference 18, whereas page 0 will be used at 5, and page 1 at 14. The reference to page 3 replaces page 1, as page 1 will be the last of the three pages in memory to be referenced again. With only nine page faults, optimal replacement is much better than a FIFO algorithm, which results in fifteen faults. (If we ignore the first three, which all algorithms must suffer, then optimal replacement is twice as good as FIFO replacement.) In fact, no replacement algorithm can process this reference string in three frames with fewer than nine faults.

实现困难，一般做标杆，来衡量其他算法的好坏。  

### LRU replacement algorithm  
LRU replacement associates with each page the time of that page’s last use.  
When a page must be replaced, LRU chooses the page that has not been used for the longest period of time.We can think of this strategy as the optimal page-replacement algorithm looking backward in time, rather than forward.   
Like optimal replacement, LRU replacement does not suffer from Belady’s anomaly
      
eg: [LRU replacement algorithm example](https://postimg.cc/image/wwdf1qynp/)   

#### Counter implement  
every page entry has a counter;把时间放进entry里  
当要置换时，只需要看其页表里的counter项，时间越早的就置换出去  

#### Stack implement  
双向链表实现堆栈（可以实现移动，跟传统的栈不同）
[Stack implement example](https://postimg.cc/image/lmpaku139/)

### LRU-Approximation Page Replacement   

#### reference bit/Additional-reference-bits    
前面的是最高位，是当前的访问情况  
[Additional-reference-bits example](https://postimg.cc/image/rowxatho5/)

#### Second change(clock) algorithm  
先使用FIFO,选择这个页，  
看reference bit，  
是0置换出去，    
是1，则先保留，然后置为0，再给他一次机会，  

### Counter-based replacement algorithm  
counter :被访问次数  

#### LFU 
选择在过去被访问次数最少的换出去
有点像aging  
#### MFU
选择在过去被访问次数最少的换出去  


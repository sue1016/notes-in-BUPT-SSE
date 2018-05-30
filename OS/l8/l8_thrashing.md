# Thrashing
  
### 定义 
            
            In fact, look at any process that does not have “enough” frames. If the process does not have the number of frames it needs to support pages in active use, it will quickly page-fault. At this point, it must replace some page.
             
            However, since all its pages are in active use, it must replace a page that will be needed again right away. Consequently, it quickly faults again, and again, and again, replacing pages that it must bring back in immediately.  
            
            This high paging activity is called thrashing. A process is thrashing if it is spending more time paging than executing.
            
            是一种恶性循环，fage fault rate太高，处于阻塞状态，cpu利用率低，增加道数，越来越缺  
> 如何解决 

### working-set strategy

进程的推进是从一个局部到另一个局部

<img src="https://s26.postimg.cc/peey12nuh/2018-05-30_10.20.21.png">  
---------
<img src="https://s26.postimg.cc/inygrmsyx/2018-05-30_10.20.00.png">  
---------
<img src="https://s26.postimg.cc/jdh941qyh/2018-05-30_10.22.33.png">   

### Page-Fault Frequency 

####定义

             The specific problem is how to prevent thrashing. Thrashing has a high page-fault rate. Thus, we want to control the page-fault rate. When it is too high, we know that the process needs more frames. Conversely, if the page-fault rate is too low, then the process may have too many frames. We can establish upper and lower bounds on the desired page-fault rate (Figure 9.21). If the actual page-fault rate exceeds the upper limit, we allocate the process another frame. If the page-fault rate falls below the lower limit, we remove a frame from the process. Thus, we can directly measure and control the page-fault rate to prevent thrashing.   
      


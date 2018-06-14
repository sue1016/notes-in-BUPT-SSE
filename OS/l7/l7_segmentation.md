# segmentation
* 段名  
* 段长  长度可变  

             分段，段是单元  
             分页，页是单元  

STBR  ...基址...  
STLR  ...线长...  

segment table: base + limit
            
               base(contains the starting physical address where the segments reside in memory)  
               limit(specifies the length of segment)  
               不能直接映射，因为页表页的大小一样可以随便映射，但是段的大小不一，不能直接映射。
   
>与分页最大的不同是？
 不是叠加而是直接相加，因为得到的直接是基地址，而不是物理页框号  







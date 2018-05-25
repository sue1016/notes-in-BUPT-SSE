# demand paging
不用全部装入实存
只需要在需要的时候，在访问具体页面的时候，才装入  

请调：  
首先在页表中看在不在，    
如果是invalid,则给一个page not found错误  
如果valid,但只是不在实际内存，则换入，然后改变页表（改成在实存中）  

预调：根据经验事先调入一些  

swapper vs pager(以页为单位的lazy swapper)  

###Basic Concepts  

#### the modified page table mechanism

* valid bit: v--in memory i--not in memory    
if i  ===> page fault ==intepret=> 换入  
* reference bit :标示页面访问情况  
* dirty/modified bit: 记录页面是否被修改，如修改-->写会，如没修改-->不写回 提高了效率。**换出的时候要看是否被修改，然后看是否需要写回**。  





#### page fault
first reference to a page wiil trap to OS

##### page fault handling  

* OS look at an internal table to decide    
  --invalid reference => abort   
  --just not in memory => bring to memory    
* get an empty frame from the free frame list    
* swap page into frame   
  --page out/in  
* modify the internal tables & set validation bit    
* **restart** the instruction that caused the page fault   


#### address translation   
#### secondary memory  

### Performance of Demand paging   

EAT:  effective access time
p:  page fault rate 

EAT = (1-P) * memory access + p * page fault time 

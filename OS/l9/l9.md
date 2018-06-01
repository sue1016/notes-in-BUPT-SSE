# OS Lecture 9: File-System Interface 

---

## File Concept  
  
非易失 nonvolatile  
a file is a logical storage  unit  

## File Attributes  

* name   
* identifier
* type  
* location  
* size  
* protection-access-control  
* time,date,and user identification  

> 文件的属性放在哪   

>>放在目录里边（目录也保存在外存上）  

## file operations    

### 操作 

* create : 分配空间+创建目录项 
* write : write pointer  
* read : read pointer   
* reposition with file:also known as seek   
* delete: release space + erase the directory entry    
* truncate: 只是把内容修改了，属性没有改变  

Other:  

* for file: append,rename  
* for file attribute:chown,chmod  
* for directory & directory entries:    
   * open:找到表目 --> 放到内存 --> 
   * close:写回属性   

### open file table

记录了打开了哪些，读到了哪里
 
两极访问：  

* 对每个进程都有个open file table（记录一些与进程相关的信息）   
      * file pointer 读到了那些信息，写到了哪些信息  
      * access control:访问模式，可读可写可执行 
* 同时整个系统也有一个open file table（记录一些通用的信息）    
      * file-open count: 记录被打开的次数  （几个进程统一打开）
      * disk location of the file

 
## file Structure   

* None 无结构 的 字节流  
* Simple record structure
* Complex Structures  

#### internal file structure  

>how to locate an offset  within a file?
>> 字节流 ---如何-映射到-->  块
>>> 把字节流打包成块 再映射  
>>>> 也可能出现内碎片  

## Access method  

*sequential access  
### direct access   

## Directory Structure  
以文件形式存放在磁盘上
sorry a ,后面没有集中精力，就不记了  



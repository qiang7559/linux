
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;1。 安装一个新的硬盘  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; 添加硬盘：：：：`echo "- - -" > /sys/class/scsi_host/host1/scan   `   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;2。 查看新硬盘的设备名，       
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; `ls      /dev / sd* `  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;3。 在新的硬盘上创建一个主分区，  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; 创建  /dev /sdb2&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;**创建磁盘用 +++  表示**   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;4。 将新创建的分区的格式化为  ext4  文件系统   并加上 /home  卷标  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; `mkfs.ex4   +++  -L  /home  `       
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;5。 创建  / home 目录临时挂载点 ，并将分区挂载到临时挂载点上      
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; `mkdir / mnt / home  ;  mount  +++  / mnt /home  `   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; df	显示挂载是否成功  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;6。 切换单用户模式，以防系统错误  ，  将除了  root  用户之外的用户提出    
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; `init  1  `       
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;7。 切换单用户的模式，远程终端无法使用 ， 只能在  服务器  本机上操作   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; 输入root密码  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;8。 将 / home 目录下的所有内容拷贝到临时挂载点中  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; `cp   -av   / home / *    / mnt  /home  `    
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;9。 进入 / etc / fstab  文件中修改内容  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; `****uid        / home   ext4     defaults    0   0  `   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; 获取+++的uid   ----------    : r ! blkid   +++  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;10。 删除 / home  目录下的内容   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; `rm   -rf  / home / *  `      
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;11。 解除临时挂载点的挂载，将新的分区&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; 挂载到 / home 目录下    
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; `umount   / mnt  / home/  `   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; `mount  +++   /home  `   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; `lsblk  `     
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;12。 删除临时挂载点，切换运行模式，  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; `rm   -rf    /mnt  /home/  `    
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp; `init  6  `     

                                                                2018-10-19      
                                                                待续......

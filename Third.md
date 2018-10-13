### vim末行命令使用

1，赋值 /etc/profile 至 /tmp 目录，用查看替换命令删除 /tmp/profile 文件的行首的空白字符     

&ensp;&ensp;&ensp;&ensp;&ensp;:%s@^\s*@@g&ensp;&ensp;或&ensp;&ensp;%s@^[[:space:]]*@@g   


2，复制  /etc/rc.d/init.d/function 文件至 /tmp 目录，用查看替换命令为 /tmp/function 的每行开头为空白字符的行的行首添加一个 # 号

&ensp;&ensp;&ensp;&ensp;&ensp;:%s@^[^#]@#@g

### 编写脚本
&ensp;&ensp;脚本文件是以 .sh 结尾，必须在$PATH 的路径里编写，完成后脚本文件加 执行权限 
&ensp;&ensp;&ensp;&ensp;&ensp;chmod&ensp;&ensp;+x&ensp;&ensp;file.sh
``` bash
    #!/bin/bash
    echo "hello world"
```
`-rwxr-xr-x 1 root root 910 Oct 10 19:38 f1.sh`   
&ensp;&ensp;直接在当前目录下执行 f1.sh

#### 脚本规范  
&ensp;&ensp;脚本代码开头约定   
&ensp;1. 第一行一般为调用使用的语言  
&ensp;2. 程序名,避免更改文件名为无法找到正确的文件   
&ensp;3. 版本号  
&ensp;4. 更改后的时间   
&ensp;5. 作者相关信息  
&ensp;6. 该程序的作用,及注意事项    
&ensp;7. 最后是各版本的更新简要说明    

#### 检测脚本中的语法错误   
&ensp;&ensp;&ensp;&ensp;bash&ensp;&ensp;-n&ensp;&ensp;/path/to/some_script


#### 生成颜色随机数   
` COLOR=$[RANDOM%7+31] ; echo -e "\e[1;${COLOR}mcolor\e[0m"`
#### 异或，变量交换
`$ a=4 b=6 ; echo $a $b;a=$[a^b];b=$[a^b];a=$[a^b]; echo $a $b`
#### 判断文件的后缀是否为.sh为结尾
`filename=bb.sh;[[ $filename =~ ..*\.sh$ ]] && echo " yes " || echo "no"`

1，编写脚本 /root/bin/sumid.sh ，计算 /etc/passwd 文件中的第10个用户和第20个用户的 ID 之和
``` bash
    #!/bin/bash
    x=`cat /etc/passwd | head -10 | tail -1 | cut -d: -f3`
    y=`cat /etc/passwd | head -20 | tail -1 | cut -d: -f3`
    echo $x $y
    z=$[$x+$y]
    echo $z
    unset x y z
~ 
```
2,编写脚本 /root/bin/sumspace.sh ， 传递两个文件路径作为参数给脚本计算两个文件中所有空白行之和
```bash
    #!/bin/bash
    declare -i var1=`grep '^$' $1 | wc -l `
    declare -i var2=`grep '^$' $2 | wc -l `
    let z=$var1+$var2
    echo "blank line $z"
    unset var1 var2 z
```
3，编写脚本 /root/bin/sumfile.sh , 统计 /etc ，/var ，/usr 目录中共有多少个一级子目录和文件
```bash
    #!/bin/bash
    declare -i l1=`tree -L 1 $1 | wc -l`
    declare -i l2=`tree -L 1 $2 | wc -l`
    declare -i l3=`tree -L 1 $3 | wc -l`
    let z=$l1+$l2+$l3
    echo "primary subdirectory $z"
    unset l1 l2 l3 z
```
4, 编写脚本 /root/bin/alarm.sh文件系统使用空间大于 80% 就报警
```bash
    #!/bin/bash
    disk=`df | grep "^/dev/sd" | tr -s " " "%" | cut -d"%" -f5`
    [ $disk -ge 80 ] && echo "Pay attention to insufficient memory" || echo "I can keep using it"
```
5, 编写脚本 /root/bin/numbers.sh , 在 /etc/passwd 查找两个用户使得 ID 相加 ， 并检测传递的参数为数字，否则直接退出脚本
```bash
    #!/bin/bash
    [ $# -ne 2 ] && echo "Arg number is 2" && exit
    [[ ! "$1" =~ ^[0-9]+$ ]] && echo is not digit && exit
    [[ ! "$2" =~ ^[0-9]+$ ]] && echo is not digit && exit
    uid1=`head -n$1 /etc/passwd | tail -n1 | cut -d: -f3`
    uid2=`head -n$2 /etc/passwd | tail -n1 | cut -d: -f3`
    echo sum=$[uid1+uid2]
    unset uid1 uid2 sum
```

6, 编写脚本 /root/bin/name.sh ，检测用户是否存在 ， 如果存在 就退出，反之创建用户
```bash
    read -p "Please enter a user nama : " name
    read -p "Please create a username and password : " passwd
    useradd $name &> /dev/null  &&   echo $passwd | passwd --stdin $name &> /dev/null ||  { echo "Users already exist" ; exit ;}
    echo "Congratulations, user creation was successful"
    echo $name 
    unset name passwd
    exit`
```
6, 编写脚本 /root/bin/rabbit_chcken.sh , 已知一笼共有 鸡兔 头 35 个 脚 94 个，请问鸡兔个多少个   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;*方法一*
```bash
    #!/bin/bash
    read -p "input the sumheads:" head
    read -p "input the sumfeet:" feet
    [[ "$head" =~ ^[1-9][0-9]*$ ]] && [[ "$feet" =~ ^[1-9][0-9]*$ ]] || { echo wrong format; exit: }
    [ "$head" -gt "$feet" ] && {echo input the corrected number; exit;}
    rabbits=$[$[$feet/2]-$head]
    chicken=$[$head-$rabbits]
    C=$[$chicken*2]
    h=$[$rabbits*4]
    tmp=$[$[$c+$h]/$feet]
    [ ! "tmp" == 1 ] && echo there must be some alien steal my beasty
    echo chicken=$chicken
    echo rabbits=$rabbits
```   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;*方法二*  
```bash
    #!/bin/bash
    read -p "head :" h
    read -p "feet :" f
    ((x=(4*h-f)/2))
    ((y=(f-2*h)/2))
    echo "chook $x rabbit $y"
```

# find
1，查看 /var 目录下属主为 root，且属组为 mail 的所以文件  
`  find /var -user root -group mail `     
2，查看 /var 目录下不属于 root ，gdm 的所有文件 
 ` find /var -not \( -user root -a -user gdm -a -group root -a -group gdm  \) `    
3，查找/var目录下最近一周内其内容修改过,同时属主不为root ,也不是 postfix的文件  ` find /etc  -not \( -group root -a -group postfix \) -mtime -7`    
4、查找当前系统上没有属主或属组,且最近一个周内曾被访问过的文件   
` find /etc -nogroup -nouser -atime -7 `    
5、查找/etc目录下大于1M且类型为普通文件的所有文件   
` find /etc -size +1M -type f`    
6、查找/etc目录下所有用户都没有写权限的文件  
` find /etc -not -perm /222`     
7、查找/etc目录下至少有一类用户没有执行权限的文件   
`  find /etc -not -perm /111`   
8、查找/etc/init.d目录下,所有用户都有执行权限,且其它用户有写权限的文件
`  find /etc/init.d -perm /112`     

# sed
1、删除centos7系统/etc/grub2.cfg文件中所有以空白开头的行行首的空白字符  
` sed -r 's/^[[:blank:]]+//' /data/grub2.cfg`       
2、删除/etc/fstab文件中所有以#开头,后面至少跟一个空白字符的行的行首的和空白字符      
`  sed -r 's/^#[[:blank:]]+//' /data/fstab`    
3、在centos6系统/root/install.log每一行行首增加#号  
` sed -r 's/^(.*)/#\1/' install.log`      
4、在/etc/fstab文件中不以#开头的行的行首增加#号    
` sed -r 's@^[^#]@#@' fstab`   
5、处理/etc/fstab路径,使用sed命令取出其目录名和基名 .  
*目录名* &ensp;&ensp;&ensp;` echo /etc/fstab | sed -nr "s@(^.*/)([^/].*)/?@\1@p"`   
*基名*&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;` echo /etc/fstab | sed -nr "s@(^.*/)([^/].*)/?@\2@p"`       
6、利用sed取出ifconfig命令中本机的IPv4地址     
*方法一* &ensp;&ensp;&ensp;`  ifconfig ens33 | sed -n '2p' | sed -r 's@^[[:space:]].*inet[[:space:]]@@' | sed -r 's@[[:space:]].*@@'`      
*方法二* &ensp;&ensp;&ensp;` ifconfig ens33 | sed -nr "2s/.*t(.*)net.*/\1/gp"`       
*方法三* &ensp;&ensp;&ensp;` ifconfig ens33 | sed -n "2p" | sed "s@.*inet @@" | sed "s@ netmask.*@@"`        
7、统计centos安装光盘中Package目录下的所有rpm文件的以分隔倒数第二个字段的重复次数,    
*方法一* &ensp;&ensp;&ensp;`  ls  *.rpm  |  sed -r ' s@(.*) \ .rpm$ @\1 @'  |   sed -r  's@.* \ . (  [ ^ . ] + )@ \ 1 @' | sort |uniq -c`   
*方法二* &ensp;&ensp;&ensp;` ls  *.rpm | -r 's@ . * \ . ( [ ^ .] + )  \ . rpm $ @ \ 1 @ '  | sort | uniq -c`   
*方法三* &ensp;&ensp;&ensp;` ls  *.rpm | -r 's@ . * \ . (  .* )  \ . rpm $ @ \ 1 @ '  | sort | uniq -c`   
*方法四* &ensp;&ensp;&ensp;` ls  *.rpm |  rev  |   cut  -d.  -f2  |  rev | sort  | uniq  -c`   
*方法五* &ensp;&ensp;&ensp;` ls  *.rpm | grep -oE  " [^.]+ \.rpm$ " | cut -d. -f1 |  sort  | uniq  -c`   
8、统计/etc/init.d/functions文件中每个单词的出现次数,并排序(用grep和 sed两种方法分别实现)   
`  grep -o "[[:alpha:]]*" /etc/init.d/functions  | sort | uniq -c | sort -rn `     
` sed -nre 's/[^[:alnum:]]+/\n/g' -e 's/[0-9]/\n/gp' /etc/init.d/functions|sort|uniq -c|sort -n `   
9、将文本文件的n和n+1行合并为一行, n为奇数行  
*方法一* &ensp;&ensp;&ensp;`sed -n 'N;s/\n//'p /etc/passwd'`        
*方法二 &ensp;&ensp;&ensp;` nl passwd|sed -n 'N;s/\n//p'  '`    
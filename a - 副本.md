## 正则表达式

&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;REGEXP&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;由一类特殊字符及文本字符所编写的模式,其中有些字符(元字符)不表示字符字面意义,而表示控制或通配的功能       
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;分两类                
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;基本正则表达式&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;BRE       
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;扩展正则表达式&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;ERE&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;**grep&ensp;&ensp;&ensp;-E**&ensp;&ensp;&ensp;&ensp;就是扩展正则        
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;正则表达式引擎&ensp;&ensp;&ensp;&ensp;采用不同算法,检查处理正则表达式的软件模块     
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;PCRE (Perl Compatible Regular Expressions)语言     
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;元字符分类&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;字符匹配&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;匹配次数&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;位置锚定&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;分组  


## **grep**  
&ensp;**命令选项**  
        
- --color=auto&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;对匹配到的文本着色显示 
- -v&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;显示不被pattern匹配到的行
- -i&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;忽略字符大小写 
- -n&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;显示匹配的行号
- -c&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;统计匹配的行数
- -o&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;仅显示匹配到的字符串&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;匹配的打印出来
- -q&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;静默模式,不输出任何信息&ensp;&ensp;&ensp;不做任何显示
- -A #&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;after,后#行
- -B #&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;before,前#行
- -C #&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;context,前后各#行
- -e&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;实现多个选项间的逻辑or关系
- -w&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;匹配整个单词 
- -E&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;使用ERE-F:相当于fgrep ,不支持正则表达式


&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;列：&ensp;**grep   -e   'cat'   -e   'dog'    file**

&ensp;**字符匹配:**   

- .&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;匹配任意单个字符       
- []&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;匹配指定范围内的任意单个字符      
- [^]&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;匹配指定范围外的任意单个字符,
- [:alnum:]&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;字母和数字      
- [:alpha:]&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;代表任何英文大小写字符,亦即A-Z, a-z     
- [lower:]&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;小写字母    
- [:upper:]&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;大写字母,    
- [:blank:]&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;空白字符(空格和制表符)   
- [:space:]&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;水平和垂直的空白字符(比[blank:]包含的范围广) 	   
- [:cntrl:]&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;不可打印的控制字符(退格、删除、警铃.)    
- [:digit:]&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;十进制数字   
- [:xdigit:]&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;十六进制数字     
- [:graph:]&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;可打印的非空白字符     
- [:print:]&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;可打印字符    
- [:punct:]&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;标点符号       

&ensp;**匹配次数**    &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;用在要指定次数的字符后面,用于指定前面的字符要出现的次数     

- \*&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;匹配前面的字符任意次,包括0次    
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;*贪婪模式&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;尽可能长的匹配*  
- \.*&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;任意长度的任意字符  
- \\?&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;匹配其前面的字符0或1次,  
- \\+&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;匹配其前面的字符至少1次,    
- \\{n\}&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;匹配前面的字符n次   
- \\{m,n\}&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;匹配前面的字符至少m次,至多n次      
- \\{,n\}&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;匹配前面的字符至多n次         
- \\{n,\}&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;匹配前面的字符至少n次     


&ensp;**位置锚定**   &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;定位出现的位置    

- ^&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;行首锚定 , 用于模式的最左侧    
- $&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;行尾锚定,用于模式的最右侧    
- ^PATTERN$&ensp;&ensp;&ensp;&ensp;用于模式匹配整行    
- ^$&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;空行     
- [:space:]]*$&ensp;&ensp;&ensp;&ensp;&ensp;空白行    
- \ < 或 \ b&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;词首锚定,用于单词模式的左侧    
- \ > 或  \ b&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;词尾锚定;用于单词模式的右侧   
- \ <PATTERN \ >&ensp;&ensp;&ensp;&ensp;匹配整个单词             

&ensp;**分组**  

&ensp;&ensp;&ensp;&ensp;&ensp; :\ &ensp;(&ensp;\\&ensp;)&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;将一个或多个字符捆绑在一起,当作一个整体进行处理   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;如: **\\(root\\\)+**  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;分组括号中的模式匹配到的内容会被正则表达式引擎记录于内部的变量中,这些变量的命名方式为: \1,\2,\3....     
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;\ 1   表示从左侧起第一个左括号以及与之匹配右括号之间的模式所匹配到的字符   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;示例\:\\&ensp;(&ensp;stringl&ensp;\\&ensp;+&ensp;\\&ensp;(&ensp;string2&ensp;\\&ensp;)&ensp;\*&ensp;\\&ensp;) 		  		    
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;\\&ensp;1&ensp;:&ensp;stringl&ensp;\\&ensp;+&ensp;\\&ensp;( string2 \\&ensp;)&ensp;*    
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;\\&ensp;2&ensp;:&ensp;string2      
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;**\1或\2&ensp;&ensp;&ensp;&ensp;匹配前端匹配的结果**  


&ensp;**后向引用**&ensp;&ensp;&ensp;&ensp;&ensp;**引用前面的分组括号中的模式所匹配字符,而非模式本身**  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;或者&ensp;:&ensp;\\|    
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;示例&ensp;:&ensp;a&ensp;\\&ensp;|&ensp;b&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;:&ensp;&ensp;&ensp;&ensp;&ensp;a&ensp;或&ensp;b      
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;C&ensp;\\&ensp;|&ensp;cat&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;:&ensp;&ensp;&ensp;&ensp;C或cat    
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;\\&ensp;(&ensp;C&ensp;\\&ensp;|&ensp;c&ensp;\\&ensp;)&ensp;at&ensp;&ensp;:&ensp;&ensp;&ensp;&ensp;&ensp;Cat或cat   
`grep "^\(.*\):.*/\1$" /etc/passwd`	


## **egrep及扩展的正则表达式**&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;*不用转移加\\*     
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;**egrep=grep&ensp;&ensp;-E**        
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;**egrep&ensp;[OPTIONS]&ensp;PATTERN&ensp;[FILE.]**   
### 扩展正则表达式的元字符
**字符匹配**   
- .&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;任意单个字符
- []&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;指定范围的字符
- [^]&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;不在指定范围的字符

**次数匹配**	               			
- \*&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;匹配前面字符任意次 
- \?:&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;0或1次  
- \+&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;1次或多次 
- {m}&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;匹配m次 					
- {m,n}&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;至少m,至多n次

**位置锚定**   
- ^&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;行首  
- $&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;行尾  
- \\ < , \\ b&ensp;&ensp;&ensp;&ensp;&ensp;语首  
- \\ > , \\ b&ensp;&ensp;&ensp;&ensp;&ensp;语尾  

**分组**&ensp;&ensp;&ensp;&ensp;( )&ensp;&ensp;后向引用:  \ 1 , \ 2,  
&ensp;&ensp;&ensp;&ensp;&ensp;或者 :    
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;或者&ensp;:&ensp;\\|    
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;示例&ensp;:&ensp;a&ensp;\\&ensp;|&ensp;b&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;:&ensp;&ensp;&ensp;&ensp;&ensp;a&ensp;或&ensp;b      
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;C&ensp;\\&ensp;|&ensp;cat&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;:&ensp;&ensp;&ensp;&ensp;C或cat    
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;\\&ensp;(&ensp;C&ensp;\\&ensp;|&ensp;c&ensp;\\&ensp;)&ensp;at&ensp;&ensp;:&ensp;&ensp;&ensp;&ensp;&ensp;Cat或cat

---
### 取IP地址
**方法一**：
`ifconfig   ens33   |   grep   -o   "\([0-9]\{1,3\}\.\)\{3\}[0-9]\{1,3\}" | tail -1`  
**方法二**：
`ifconfig ens33 | grep "\([[:digit:]]\{1,3\}\.\)\{3\}[[:digit:]]\{1,3\}" -o | tail -1`   
**方法三**：
`ifconfig  ens33  | egrep "(([0-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-5])\.){3}([0-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-5])" -o`  
**方法四**
`ifconfig ens33 | grep "[0-9.]\{8,\}" -o | head -1`				


注：方法四利用的是ip的占位符，不严谨&ensp;&ensp;慎用，不规范


-----
                                                                2018-10-1
                                                                    完结
                                                                    。。。
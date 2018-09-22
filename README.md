# 时间
&ensp;&ensp;&ensp;在 *Linux* 中有有两个时间，  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;系统时间 ___date___：由Linux内核通过CPU的工作频率进行的，  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;另一个是硬件时间 ___hwclock,clock___    
&ensp;date &ensp;&ensp;显示和设置系统时间&ensp;&ensp;&ensp;&ensp;`date + %s`&ensp;&ensp;&ensp;&ensp;**当前时间到1790年1月1号多少秒**     


&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;如果硬件的时间与系统时间不对.&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;使用&ensp;**ntpdate**&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;设置本地日期和时间  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;可以使用 __`ntpdate ip`&ensp;&ensp;**ip 是服务器是地址**__&ensp;&ensp;就可以使你的系统时间与远程服务器时间相同。    
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;用 **hwclock [ -w|s ]** 可以更改时间       
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;**-w**&ensp;&ensp;&ensp;&ensp;矫正硬件时间，是以系统时间为准  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;**-s**&ensp;&ensp;&ensp;&ensp;矫正系统时间，是以硬件时间为准


&ensp;&ensp;时区：/etc/localtime	     
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;时区指向/usr/share/zoneinfo/Asia  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;timedatectl&ensp;&ensp;&ensp;&ensp;list-timezones&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;列出所有的时区  
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;timedatectl&ensp;&ensp;&ensp;&ensp;status&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;当前的时区时间   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;timedatectl&ensp;&ensp;&ensp;&ensp;set-timezone&ensp;&ensp;&ensp;&ensp;时区&ensp;&ensp;&ensp;&ensp;更改时区


&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;tzselect&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;选择时区时间 &ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;最终修改的时间文件&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;**/etc/locatime**   
&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;显示日历&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;cal&ensp;&ensp;-y     

# SpringBootQuartz
Quartz with Spring Boot

# 基于spring boot的quartz任务调度

## 1.导入sql脚本到mysql中
## 2.修改demo中的application.yml及其quartz.properties里面的数据库配置信息启动即可。
## 3.访问http://localhost:8080/JobManager.html

# 创建job

## 1.点击添加job
## 2.job名称输入：com.example.demo.job.HelloJob或者是com.example.demo.job.NewJob
## 3.group名称随意
## 4.时间间隔表达式：*/5 * * * * ?  （表示每隔5秒执行一次）
## 5.添加完毕即可在控制台看到job执行情况


# 附：quartz Cron表达式一分钟教程



CronTrigger

CronTriggers往往比SimpleTrigger更有用，如果您需要基于日历的概念，而非SimpleTrigger完全指定的时间间隔，复发的发射工作的时间表。
CronTrigger，你可以指定触发的时间表如“每星期五中午”，或“每个工作日9:30时”，甚至“每5分钟一班9:00和10:00逢星期一上午，星期三星期五“。
即便如此，SimpleTrigger一样，CronTrigger拥有的startTime指定的时间表时生效，指定的时间表时，应停止（可选）结束时间。

Cron Expressions

cron的表达式被用来配置CronTrigger实例。 cron的表达式是字符串，实际上是由七子表达式，描述个别细节的时间表。这些子表达式是分开的空白，代表：

1.        Seconds
2.        Minutes
3.        Hours
4.        Day-of-Month
5.        Month
6.        Day-of-Week
7.        Year (可选字段)
例  "0 0 12 ? * WED" 在每星期三下午12:00 执行,

个别子表达式可以包含范围, 例如，在前面的例子里("WED")可以替换成 "MON-FRI", "MON, WED, FRI"甚至"MON-WED,SAT".

“*” 代表整个时间段.

每一个字段都有一套可以指定有效值，如

Seconds (秒)         ：可以用数字0－59 表示，

Minutes(分)          ：可以用数字0－59 表示，

Hours(时)             ：可以用数字0-23表示,

Day-of-Month(天) ：可以用数字1-31 中的任一一个值，但要注意一些特别的月份

Month(月)            ：可以用0-11 或用字符串  “JAN, FEB, MAR, APR, MAY, JUN, JUL, AUG, SEP, OCT, NOV and DEC” 表示

Day-of-Week(每周)：可以用数字1-7表示（1 ＝ 星期日）或用字符口串“SUN, MON, TUE, WED, THU, FRI and SAT”表示

“/”：为特别单位，表示为“每”如“0/15”表示每隔15分钟执行一次,“0”表示为从“0”分开始, “3/20”表示表示每隔20分钟执行一次，“3”表示从第3分钟开始执行

“?”：表示每月的某一天，或第周的某一天

“L”：用于每月，或每周，表示为每月的最后一天，或每个月的最后星期几如“6L”表示“每月的最后一个星期五”

“W”：表示为最近工作日，如“15W”放在每月（day-of-month）字段上表示为“到本月15日最近的工作日”

““#”：是用来指定“的”每月第n个工作日,例 在每周（day-of-week）这个字段中内容为"6#3" or "FRI#3" 则表示“每月第三个星期五”

1）Cron表达式的格式：秒 分 时 日 月 周 年(可选)。

	字段名                 允许的值                        允许的特殊字符  
	秒                         0-59                               , - * /  
	分                         0-59                               , - * /  
	小时                     0-23                               , - * /  
	日                         1-31                               , - * ? / L W C  
	月                         1-12 or JAN-DEC         , - * /  
	周几                     1-7 or SUN-SAT           , - * ? / L C #  
	年 (可选字段)     empty, 1970-2099      , - * /



	“?”字符：表示不确定的值

	“,”字符：指定数个值

	“-”字符：指定一个值的范围

	“/”字符：指定一个值的增加幅度。n/m表示从n开始，每次增加m

	“L”字符：用在日表示一个月中的最后一天，用在周表示该月最后一个星期X

	“W”字符：指定离给定日期最近的工作日(周一到周五)

	“#”字符：表示该月第几个周X。6#3表示该月第3个周五



 2）Cron表达式范例：

         每隔5秒执行一次：*/5 * * * * ?

         每隔1分钟执行一次：0 */1 * * * ?

         每天23点执行一次：0 0 23 * * ?

         每天凌晨1点执行一次：0 0 1 * * ?

         每月1号凌晨1点执行一次：0 0 1 1 * ?

         每月最后一天23点执行一次：0 0 23 L * ?

         每周星期天凌晨1点实行一次：0 0 1 ? * L

         在26分、29分、33分执行一次：0 26,29,33 * * * ?

         每天的0点、13点、18点、21点都执行一次：0 0 0,13,18,21 * * ?
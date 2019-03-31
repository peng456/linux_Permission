# linux_Permission
linux 的权限模式。值得学习。权限系统。模型等。

今天在docker +  cenntos   +  LNP 时，需要给 nginx 、php-fpm 设置用户。目录权限。以避免安全问题（https://segmentfault.com/a/1190000009909817）

例如：
groupadd -r nginx  
useradd -r -g nginx -s /sbin/nologin -d /usr/local/nginx  -M nginx


这是涉及到linux 的权限模型。

（https://infoq.cn/article/basic-principle-of-Linux-privilege-control）

Linux 系统上最初的安全模型叫 DAC, 全称是 Discretionary Access Control ，翻译为自主访问控制。 ===> 后来增加设计了一个新的安全模型叫 MAC, 全称是 Mandatory Access Control  

二者===》不互斥

liunx  检测顺序  ===》DAC  ==》 Then  MAC（MAC 貌似 是 美国 五角大楼 给写的）

这里讲 DAC 安全模型

liunx 中一等公民： 进程

进程的 权限  是基于用户的。 


（https://www.cnblogs.com/P_Chou/archive/2012/12/02/linux-perm-basic.html）
linux的基础权限体系是基于UGO的===》 用户、用户群组、其他用户  ===》 对文件 or 目录 ===》权限的类别 ：读（R4）、写(W2)、执行(X1)

修改权限
可以选择chmod UGO + RMX （自由组合）  也可以选择数字  chmod 750
位置代表 角色。位置上的内容代表权限类别。

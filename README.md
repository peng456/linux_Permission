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

chgrp：修改文件或文件夹的所属组  
chown：修改文件或文件夹的所属用户


chmod u+s：将文件设置suid  
suid：只对文件有效，表示文件在执行的时候以文件的所属用户的权限执行，比如/usr/bin/passwd，在终端上文件会显示红色，并且U权限中的x会被替换成s



chmod g+s：将文件夹设置sgid  
sgid：通常对文件夹有效，表示在文件夹中建立文件或文件夹的时候继承该文件夹的组用户。G权限中的x会被替换成s



chmod o+t：将文件夹设置sticky
sticky：作用于文件夹，表示在该文件夹下的文件只能由文件的owner删除，其他人可以在文件夹下创建、浏览、但也只能删除自己为owner的文件。O权限中的x会被替换成t




Linux 中的 wheel 组和 staff 组  (https://www.cnblogs.com/jan5/p/3359421.html)  

为什么需要 wheel 组？  
    通常在UNIX下，即使我们是系统的管理员，也不推荐用 root 用户登录来进行系统管理。一般情况下用普通用户登录，在需要 root 权限执行一些操作时，再 su 登录成为 root 用户。但是，任何人只要知道了 root 的密码，就都可以通过 su 命令来登录为 root 用户——这无疑为系统带来了安全隐患。所以，将普通用户加入到 wheel 组，被加入的这个普通用户就成了管理员组内的用户，但如果不对一些相关的配置文件进行配置，这个管理员组内的用户与普通用户也没什么区别——就像警察下班后，没有带枪、穿这便衣和普通人（用户）一样，虽然他的的确确是警察。  
    即只有属于 wheel 组的用户才可以用 su 登录为 root





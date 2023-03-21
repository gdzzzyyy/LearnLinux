1.
在使用SSH登录虚拟机时候，会遇到：
    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!
解决方案：
    $ ssh-keygen -R [虚拟机IP]
->执行：
    Host 123.123.123.123 found: line 51 type RSA
    /Users/hideaki/.ssh/known_hosts updated.
    Original contents retained as /Users/hideaki/.ssh/  known_hosts.old


2.
Centos ping 无法使用，
yum 报错：
    Cannot find a valid baseurl for repo: base/7/x86_64
    Could not retrieve mirrorlist xxxxx
    Could not resolve host: xxxxx

可能的原因是虚拟机centos的网管错误。
本次：
    1 -> nmcli device status 
        -> 查看网卡状态，发现网卡(enp0s2f1u3)处于   disconnected
    2 -> nmcli connection up enp0s2f1u3  
        -> 打开enp0s2f1u3网卡 -> connectied状态
    3 -> nmcli con mod enp0s2f1u3 connection.autoconnect "yes"
        -> 再启动之后，虚拟机的网络设置还是connectied状态


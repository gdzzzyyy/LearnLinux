# day2学习
### 1. Bash 种类
1.  /bin/bash
2.  /bin/tcsh

### 2. bash 的功能
>    1. alias 命令别名设置功能
>>```bash
>>[root@localhost ~]#alias lm='ls -al'
>>```
        

### type学习
>#### type是显示指令是否是内置（使用中的）在bash中，或者是其他外部bash中
>```bash
>[root@localhost ~]# type ls
>ls is aliased to `ls --color=auto'
>
>
>[root@localhost ~]# type -t ls
>alias
>
>[root@localhost ~]# type -a ls
>ls is aliased to `ls --color=auto'
>ls is /usr/bin/ls
>
>[root@localhost ~]# type cd
>cd is a shell builtin
>```
>

### 变量的提取 echo
>
>- 获取  echo
>    1. echo ${变量}
>    2. echo $变量
>
>```bash
>[root@localhost ~]# echo $PATH
>/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin
>```
>
- 记录问题
> ```bash
>[root@localhost ~]# mypath=PATH
>[root@localhost ~]# echo ${mypath}   //为什么这次得到的只是PATH
>PATH
>[root@localhost ~]# echo ${PATH}
>/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin
>[root@localhost ~]# echo $var
> ```

- 如果我想echo ${mypath}和第二次echo的值一致，我应该如何做
> ```bash
>[root@localhost ~]# mypath=$PATH
>[root@localhost ~]# echo ${mypath}
>/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin
> ```

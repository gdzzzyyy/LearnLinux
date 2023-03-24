##Shell学习

>```base
>[root@localhost shell]# vim myShell.sh
>

>#!/bin/bash
>echo "hello world!"

>[root@localhost shell]# ls
>myShell.sh
>[root@localhost shell]# chmod 744 myShell.sh  //给myShell一个可以执行的权限
>[root@localhost shell]# ls
>myShell.sh
>[root@localhost shell]# ./myShell.sh  //执行
>hello world!

#####当shell没有可执行权限，虽然无法执行，但是可以通过 sh 命令来执行
>[root@localhost shell]# chmod 444 myShell.sh
>[root@localhost shell]# ./myShell.sh
>-bash: ./myShell.sh: Permission denied
>[root@localhost shell]# sh ./myShell.sh
>hello world!
>```
>

###显示全部变量
```bash
[root@localhost shell]# set
BASH=/bin/bash
BASHOPTS=checkwinsize:cmdhist:expand_aliases:extquote:force_fignore:histappend:hostcomplete:interactive_comments:login_shell:progcomp:promptvars:sourcepath
BASH_ALIASES=()
BASH_ARGC=()
........

##上述现实的不是很好  可以使用管道符+more等组合
[root@localhost shell]# set | more
BASH=/bin/bash
BASHOPTS=checkwinsize:cmdhist:expand_aliases:extquote:force_fignore:histappend:hostcomplete:interactive_comments:login_shell:progcomp:promptvars:sourcepath
BASH_ALIASES=()
BASH_ARGC=()[root@localhost shell]# set | more
BASH=/bin/bash
BASHOPTS=checkwinsize:cmdhist:expand_aliases:extquote:force_fignore:histappend:hostcomplete:interactive_comments:login_shell:progcomp:promptvars:sourcepath
BASH_ALIASES=()
BASH_ARGC=()
.............
```

###自定义变量
```bash
#
[root@localhost shell]# vim myShell.sh
[root@localhost shell]# ./myShell.sh
A=100
A=

#myShell.sh 内容
##自定义一个A变量
A=100
echo "A=${A}"
##unset 取消A变量
unset A
echo "A=${A}"
```

###自定义静态变量
```bash
[root@localhost shell]# ./myShell.sh
A=99
./myShell.sh: line 13: unset: A: cannot unset: readonly variable
A=99

#myShell.sh 内容
readonly A=99   //设定静态变量
echo "A=${A}"   //输出静态变量
unset A         //unset静态变量   发生报错： unset: A: cannot unset: readonly variable
echo "A=${A}"

A=19
MYNUM=89
echo "$A $MYNUM"   -> 19 89
```

```bash
RESULT=`ls -l /home`
echo ${RESULT}  -> total 0   使用`` 将命令括起来
echo ""
MY_DATE=$(date)
echo "date=$MY_DATE" -> date=Wed Mar 22 03:43:30 JST 2023  使用$() 来执行
```


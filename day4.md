## bash 运算

### 预定义变量
```base
```

### 运算符
```bash
#第一种方式 $((运算式))
RESULT1=$(((2+3)*4))
echo "res=${RESULT1}"

#第二种方式 $[运算式]
RESULT2=$[(2+3)*4]
echo "res2=${RESULT2}"

#第三种方式 expr m + n 
#注1： 符号之间要有空格   
#注2： *-> \* , / , %   乘，除，取余
TEMP=`expr 2 + 3`
RESULT3=`expr $TEMP \* 4`
echo "res3=${RESULT3}"

#求出两个参数的和
SUM=$[$1+$2]
echo "sum=${SUM}"
```
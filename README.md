# Python-29-
Python学习笔记(29)
# p92 函数参数定义_个数可变的位置形参_个数可变的关键字形参
def fun(*args):  #函数定义时的可变的位置参数
    print(args)
    print(args[0])

fun(10)
fun(10,30)
fun(30,43,32)  #以*定义的位置形参结果为一个元组

def funl(**args):
    print(args)

funl(a=10)
funl(a=20,b=30,c=40)  #以**定义的关键字形参结果是一个字典

print('hello','world','java')

def fun2(*args,*a):  #这里程序会报错，可变的位置参数只能是一个
    pass

def fun2(**args,**args):  #这里代码也会报错，可变的关键字参数也只能是一个
    pass

def fun2(*args1,**args2):
    pass  #不会报错

def fun3(**args1,*args2):
    pass  #程序报错  在一个函数的定义过程中，既有个数可变的关键字形参，也有个数可变的位置形参，要求个数可变的位置形参要放在个数可变的关键字形参之前



# p93 函数的参数总结
def fun(a,b,c):  #a,b,c在函数的定义处，所以是形式参数
    print('a'=a)
    print('b'=b)
    print('c'=c)

#函数的调用
fun(10,20,30)  #函数调用时的参数传递，称为位置传参
lst=[11,22,33]
fun(lst)  #程序报错，需要在列表前面加*
fun(*lst)  #在函数调用的时候，将列表中的每个元素都转换为位置实参传入

fun(a=100,c=300,b=200)  #函数的调用，所以是关键字实参
dic={'a':111,'b':222,'c':333}
fun(**dic)  #在函数调用时，将字典中的键值对都转换成关键字实参传入

def fun(a,b=10):  #b是在函数的定义处，所以b是形参，而且进行了赋值，所以b称为默认值形参
    print('a=',a)
    print('b=',b)

def fun2(*args):  #个数可变的位置形参
    pass

def fun3(**args2):  #个数可变的关键字形参
print(args2)

fun2(10,20,30,40)
fun3(a=11,b=22,c=33,d=44,e=55)

def fun4(a,b,*，c,d):  #从*的之后的参数，在函数调用上，只能用关键字参数传递
    print('a=',a)
    print('b=',b)
    print('c=',c)
    print('d=',d)

#调用fun4函数
fun4(10,20,30,40)  #位置实参传递
fun4(a=10,b=20,c=30,d=40)  #关键字实参传递
fun4(10,20,c=30,d=40)  #前两个用位置形参传递，c，d用关键字实参传递
'''需求是c，d只能采用关键字实参传递'''

‘’‘函数定义是的形参的顺序问题’‘’
def fun5(a,b,*,c,d,**args):
    pass
def fun6(*args,**args2):
    pass
def fun7(a,b=10,*args,**args):
    pass
#以上这几种都是可以的



# p93 变量的作用域
def fun(a,b):
    c=a+b  #c称为局部变量，因为c是函数体内进行定义的变量，a，b为函数的形参，作用域也在函数内部，相当于局部变量
    print(c)

print(c)
print(a)  #以上这两个代码报错，这两个代码参数超出了变量的作用域

name='杨老师'  #name的作用域范围为函数内部和外部都可以使用-->称为全局变量
print(name)
def fun2():
    print(name)
#调用函数
fun2()

#def fun3():
    global age=20  #函数内部定义的变量是局部变量，但是用了global，那么就变成了全局变量，因此这两个print都有输出
    print(age)
fun3()
print(age)

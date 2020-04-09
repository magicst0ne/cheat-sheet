数据类型:
------------------------------------------------------------------------
1.声明变量
var varName type
var var1,var2… type
var varName type = Value
var varName1,varName2 type = Value1,Value2
var varName1,varName2 = Value1,Value2
varName1, varName2:=Value1, Value2

2.常量声明
const varName = Value
const varName type = Value
const varName1,varName2 type = Value1,Value2
const varName1,varName2 = Value1,Value2

3.string
string字符串类型值不可改变，只能重新指向新的字符串地址，原来的字符串废弃；但是可以切片，字符串可以使用+进行连接；

4.iota
iota用来声明enum，表示自加1，初始为0

5.array
//声明方式
var arrayName [N]type
arrayName := [N]type{v1,v2…}

var arrayName [...]type
arrayName := [...]type{v1,v2…}

//数组声明可以嵌套

var arrayName [N][N]type
arrayName := [N][N]type{{v1,v2…}…}

6.slice
//声明方式
var sliceName []type
sliceName := []type{v1,v2…}

var sliceName [][]type
sliceName := [][]type{{v1,v2…}…}

slice保存的是引用而非实体
在slice中有一些内置函数，len获取长度，cap获取最大容量，append追加数据，copy用来拷贝数据

7.map

//声明方式
var mapName map[keyType]valueType
mapName = make(map[keyType]valueType)
mapName[k1] = v1

mapName := make(map[keyType]valueType)
mapName[k1] = v1

var mapName = map[keyType]valueType{
	"k1": "v1",
	"k2": "v2",
}

mapName := map[keyType]valueType{
	"k1": "v1",
	"k2": "v2",
}

//嵌套
type mapType map[keyType]valueType
mapName := make(map[keyType]mapType)

mapNameSub := make(mapType)
mapNameSub[k1] = v1
mapName[key1] = mapNameSub
mapName[key2] = mapType{
	"k1": "v1",
	"k2": "v2",
}

// 查找键值是否存在
if v, ok := mapName[k1]; ok {
	fmt.Println(v)
} else {
	fmt.Println("Key Not Found")
}
 
// 遍历map
for k, v := range mapName {
	fmt.Println(k, v)
}

//删除
delete(mapName, k1)

make用于内建类型的内存分配，new用于各种类型的内存分配，new返回指针而make返回非0的值
字典是无序的

流程控制:
------------------------------------------------------------------------
//if语句不需要括号，在if语句中可以声明变量，用分好分割if语句的条件判断

if n := 78;n <= 50 {

} else if n < 20 {
    //do something
} else {
    //do something
}

//for语句类似C语言
for i := 0; i < 10; i++ {
    if i>7 {
        break;
    }
    if i=6 {
        continue;
    }
}
//range和python类似
for _, c := range s {
    fmt.Printf("%c,", c)
}

//break和continue可以跟标号，跳出多重循环。
I:
	for i := 0; i < 2; i++ {
		for j := 0; j < 5; j++ {
			if j == 2 {
				break I
			}
			fmt.Println("hello")
		}
		fmt.Println("hi")
	}



//switch语句不用break，如果想强行执行下面的case可以使用fallthrough

switch finger := 8; finger {
    case 1:
        fmt.Println("1")
    case 2:
        fmt.Println("2")
    case 3, 4:
        fmt.Println("3 or 4")
    default: //default case
        fmt.Println("default")
    }

//goto语句类似C语言，但是跳转到必须在当前函数内定义的标签

func main() {
 
    //goto可以用在任何地方，但是不能夸函数使用
    fmt.Println("11111111111111")
 
    //go to的作用是跳转，中间的语句不执行，无条件跳转
    goto End //goto是关键字， End是用户起的名字， 他叫标签
 
    fmt.Println("222222222222222")
 
End:
    fmt.Println("3333333333333")
 
}


函数：
------------------------------------------------------------------------
//声明：
func funcName(input1 type1, input2 type2) (output1 type1, output2 type2)

//函数作为类型
type typeName func(input1 inputType1 , input2 inputType2 [, ...]) (result1 resultType1 [, ...])

//函数作为类型例子:
type A func(int, int)

func (f A)Serve() {
    fmt.Println("serve2")
}

func serve(int,int) {
    fmt.Println("serve1")
}

func main() {
    a := A(serve)
    a(1,2)
    a.Serve()
}

函数的值操作和指针操作类似C语言，内置类型中的string,slice,map直接使用的是类似的指针传递，不用使用取地址符，但是，如果需要改变slice的长度，则需要取地址传指针。
defer语句用来表示在函数返回前执行的语句。
import用来导入包，package用来导出包，包操作使用.操作符


Struct类型
------------------------------------------------------------------------
//声明方式：

type Person struct {
    name string
    age int
}

匿名方式，匿名方式下A含有B的所有类型

type Student struct {
    Person  // 默认Person的所有字段
    speciality string
}
如果匿名类型中有字段和本身有冲突，可以使用匿名类型+.访问

类型的方法声明：

  func (r ReceiverType) funcName(parameters) (results)
可以使用：type typeName typeLiteral来自定义类型，定义完以后可以使用方法来扩展类型的功能。

需要改变struct内部的值时，需要将ReceiverType定义为*指针类型，但是调用的时候不需要，go语言自动帮你完成了。

方法可以继承，可以重载


interface接口
------------------------------------------------------------------------
type InterfaceName interface用来定义inerface

interface类型定义了一组方法，如果某个对象实现了某个接口的所有方法，则此对象就实现了此接口。

空interface(interface{})不包含任何的method，正因为如此，所有的类型都实现了空interface

一个函数把interface{}作为参数，那么他可以接受任意类型的值作为参数，如果一个函数返回interface{},那么也就可以返回任意类型的值

value, ok = element.(T)，这里value就是变量的值，ok是一个bool类型，element是interface变量，T是断言的类型，如果ok为true则表示，element确实是T类型的。

interface可以嵌套

并发
------------------------------------------------------------------------
使用go关键字+函数名实现并发

使用channel实现线程间通讯，channel通过make构造，使用<-来发送和接受数据。

chan是channel的关键字，后面跟数据类型ch <- v发送数据，v:=<-ch接收数据，ch是chan类型。

  package main
  import "fmt"
  func sum(a []int, c chan int) {
      total := 0
      for _, v := range a {
          total += v
      }
      c <- total  // send total to c
  }

  func main() {
      a := []int{7, 2, 8, -9, 4, 0}
      c := make(chan int)
      go sum(a[:len(a)/2], c)
      go sum(a[len(a)/2:], c)
      x, y := <-c, <-c  // receive from c
      fmt.Println(x, y, x + y)
  }
channel默认是阻塞形式的，可以进行线程同步。

ch := make(chan type, value)构造channel时可通过设置不同的value来设定channl的buffer长度。

close用来关闭channel

使用select+case来选择多个channel

使用select + case <- time.After(5 * time.Second)来设定超时

Goexit 退出当前执行的goroutine，但是defer函数还会继续调用

Gosched 让出当前goroutine的执行权限，调度器安排其他等待的任务运行，并在下次某个时候从该位置恢复执行。

NumCPU 返回 CPU 核数量

NumGoroutine 返回正在执⾏行和排队的任务总数

GOMAXPROCS 用来设置可以运行的CPU核数~

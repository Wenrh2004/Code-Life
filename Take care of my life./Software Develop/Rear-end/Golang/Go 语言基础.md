## 特点

1. 高性能、高并发
2. 语法简单、学习曲线平稳
3. 丰富的标准库
4. 完善的工具链
5. 静态链接
6. 快速编译
7. 跨平台
8. 垃圾回收

## 基础语法

### 语言结构

> Go 语言的基础组成
>
> * 包声明
>
>   定义包名
>
> * 引入包
>
>   声明需要使用的包
>
> * 函数
>
>   程序开始执行的函数
>
> * 变量
>
> * 语句 & 表达式
>
> * 注释

### Go 程序的执行

* `go run xxx.go` 编译执行
* `go build` 生成 二进制文件

### Go 标记

​	Go 程序可以由多个标记组成，可以是关键字、标识符、敞亮、字符串、符号

### Go 行分隔符

​	在 Go 程序中，一行代表一个语句结束

### Go 注释

* `// 单行注释`
* `/* 多行注释 */`

### Go 标识符

​	标识符用来命名变量、类型等程序主题

​	由一个或是多个字母(A-Z和a-z)、数字(0-9)和下划线_组成的序列_

​	第一个字符必须是字母或下划线而不能是数字

### Go 字符串链接

​	Go 的字符串链接可以通过 + 来实现

### Go 关键字

> Go 代码中的25个关键字或保留字
>
> *  break
> * defaul
> * func
> * interface
> * select
> * case
> * defer
> * go
> * map
> * struct
> * chan
> * else
> * goto
> * package
> * switch
> * const
> * fallthrough
> * if
> * range
> * type
> * continue
> * for
> * import
> * return
> * var

> Go 语言中的36个预定义标识符
>
> * append
> * bool
> * byte
> * cap
> * close
> * complex
> * complex64
> * complex128
> * uint16
> * copy
> * false
> * float32
> * float64
> * imag
> * int
> * int8
> * int16
> * uint32
> * int32
> * int64
> * iota
> * len
> * make
> * new
> * nil
> * panic
> * uint64
> * print
> * println
> * real
> * recover
> * string
> * true
> * uint
> * uint8
> * uintptr

## 数据类型

​	数据类型用于声明函数和变量

​	将数据分成所需内存大小不同的数据，可以充分利用内存

* 布尔型

  ​	值为 true 或 false

* 数字类型

  * 整型 int
  * 浮点型 float32、float64
  * 复数

* 字符串类型
>一串固定长度的字符链接起来的字符序列
>由单个字节链接而成
>使用 UTF-8 编码表示 Unicode 文本

* 派生类型

  * 指针类型(Pointer)
  * 数组类型
  * 结构化类型(struct)
  * Channel类型
  * 函数类型
  * 切片类型
  * 接口类型(interface)
  * Map类型

## Go 变量

​	由字母、数字、下划线组成，其中首个字符不能为数字

​	变量可以通过变量名访问

> 变量作用域
>
> * 局部变量
>
>   * 函数内定义的变量
>
>   * 作用域：函数体内
>
>   * 参数和返回值也是局部变量
>
> * 全局变量
>
>   * 函数外定义的变量
>   * 作用域：整个包（到处后可以在外部包使用）
>   * 全局变量可以在任何函数中使用
>
> * 形式参数
>
>   * 函数定义中的变量
>
>   * 会作为函数的局部变量使用

* 变量声明

  `var identifier type`

  * var	变量
  * identifier	标识符
  * type	类型
  
  1. 指定变量类型
  
     ```Go
     package main
     
     import ()
     
     func main() {
       // 声明一个变量并初始化
       var a string = "Go" // var a := "Go"
       
       // 没有初始化成为零值
       var b int
       
       // bool 零值为 false
       var c bool
     }
     ```
  
     
  
  2. 根据值自行判定变量类型
  
     ```Go
     package main
     
     import()
     
     func main() {
       var d = true
     }
     ```
  
* 多变量声明

  `var identifier1,identifier2 type`
  
  ```go
  package main
  
  import ()
  
  var (
    v_age int
    v-sex bool
  )
  
  func main() {
    // 类型相同的多个变量，非全局变量
    var vname1,vname2,vname3 type
    vname1,vname2,vname3 = v1,v2,v3
    var v_name1,v_name2,v_name3 = vname1,vname2,vname3
    v_age1,v_age2,v_age3 := 18,19,20
  }
  ```

## Go 常量

* 显式类型声明

  const identifier type = value

* 隐式类型声明

  Const indetifier = value

```go
// 常量常见用法之一
const (
  Unkown = 0
  Female = 1
  male = 2
)
```

> iota
>
> 特殊常量
>
> 在 const 关键字出现时将被重置为 0（const 内部的第一行之前），const 中每新增一行常量声明将使 iota 技术一次（iota 课理解为 const 语句块中的行索引）

## Go 运算符

* 算术运算符

  | 运算符 | 含义 |
  | :----: | :--: |
  |   +    | 相加 |
  |   -    | 相减 |
  |   *    | 相乘 |
  |   /    | 相除 |
  |   %    | 求余 |
  |   ++   | 自加 |
  |   --   | 自减 |

* 关系运算符

  | 运算符 | 描述                         |
  | ------ | ---------------------------- |
  | ==     | 检查两个值是否相等           |
  | !=     | 检查两个值是否不相等         |
  | >      | 检查左边值是否大于右边值     |
  | <      | 检查左边值是否小于右边值     |
  | >=     | 检查左边值是否大于等于右边值 |
  | <=     | 检查左边值是否小于等于右边值 |

  

* 逻辑运算符

  | 运算符 | 描述            |
  | ------ | --------------- |
  | &&     | 逻辑 AND 运算符 |
  | \|\|   | 逻辑 OR 运算符  |
  | \|     | 逻辑 NOT 运算符 |

* 位运算符

  | p    | q    | p & q | p \| q | p ^ q |
  | ---- | ---- | ----- | ------ | ----- |
  | 0    | 0    | 0     | 0      | 0     |
  | 0    | 1    | 0     | 1      | 1     |
  | 1    | 1    | 1     | 1      | 0     |
  | 1    | 0    | 0     | 1      | 1     |

  | 运算符 | 描述                                                         |
  | ------ | ------------------------------------------------------------ |
  | &      | 按位与运算符"&"是双目运算符。 其功能是参与运算的两数各对应的二进位相与。 |
  | ｜     | 按位或运算符"\|"是双目运算符。 其功能是参与运算的两数各对应的二进位相或 |
  | ^      | 按位异或运算符"^"是双目运算符。 其功能是参与运算的两数各对应的二进位相异或，当两对应的二进位相异时，结果为1。 |
  | <<     | 左移运算符"<<"是双目运算符。左移n位就是乘以2的n次方。 其功能把"<<"左边的运算数的各二进位全部左移若干位，由"<<"右边的数指定移动的位数，高位丢弃，低位补0。 |
  | >>     | 右移运算符">>"是双目运算符。右移n位就是除以2的n次方。 其功能是把">>"左边的运算数的各二进位全部右移若干位，">>"右边的数指定移动的位数。 |

* 赋值运算符

  | 运算符 | 描述                           |
  | ------ | ------------------------------ |
  | =      | 将一个表达式的右值赋给一个左值 |
  | +=     | 相加后再赋值                   |
  | -=     | 相减后再赋值                   |
  | *=     | 相乘后再赋值                   |
  | /=     | 相除后再赋值                   |
  | %=     | 求余后再赋值                   |
  | <<=    | 左移后赋值                     |
  | >>=    | 右移后赋值                     |
  | &=     | 按位与后赋值                   |
  | ^=     | 按位异或后赋值                 |
  | \|=    | 按位或后赋值                   |

* 其他运算符

  | 运算符 | 描述             |
  | ------ | ---------------- |
  | &      | 返回变量储存地址 |
  | *      | 指针变量         |

* *运算符优先级*

  | 优先级 | 运算符                  |
  | ------ | ----------------------- |
  | 5      | \*、/、%、<<、>>、&、&^ |
  | 4      | \、+、-、^              |
  | 3      | ==、!=、<、<=、>、>=    |
  | 2      | &&                      |
  | 1      | \|\|                    |

## Go 语句

* 条件

  * if

  * if...else
  * if 嵌套
  * switch
  * select

* 循环

  * for

    * break

      中断当前 for 循环或跳出 switch 语句

    * continue

      跳过当前循环的剩余语句，然后进行下一轮循环

    * goto

      将控制转移到被标记语句

  * 循环嵌套

## Go 函数

* **函数声明**

```go
func function_name([parameter list])[return_types] {
  函数体
}
```

> * func
>
>   ​	函数由 func 开始声明
>
> * function_name
>
>   ​	函数名
>
> * parameter list
>
>   ​	参数列表，当参数被调用时，可以传递参数，其值称为实际参数
>
>   ​	包括参数类型、顺序、参数个数
>
>   ​	可以不包含参数
>
> * retrun_types
>
>   ​	返回类型
>
>   ​	可省略
>
> * 函数体
>
>   ​	函数定义代码的集合

* **函数调用**

  通过调用函数来执行指定任务

  调用函数需要相函数传递参数，并返回值

  ```go
  package main
  
  import(
  	"fmt"
  )
  
  func main()  {
  	// 定义局部变量
  	var a int = 100
  	var b int = 200
  	var max int
  
  	// 调用函数并返回最大值
  	max = max(a,b)
  	fmt.Printf("最大值：%d\n",max)
  }
  
  func max(num1,num2) int {
  	// 定义局部变量
  	var result int
  
  	// 判断
  	if (num1 > num2) {
  		result = num1
  	}else {
  		result = num2
  	}
  	return result
  }
  ```

* 函数参数

  | 传递类型 | 描述                                                         |
  | -------- | ------------------------------------------------------------ |
  | 值传递   | 调用函数是讲实际参数复制一份传递到函数中，在函数中对参数进行修改并不会影响到实际参数 |
  | 引用传递 | 引用传递是指在调用函数是讲实际参数的地址传递到函数中，在函数中对参数进行的更改将影响实际参数 |

  默认情况下，Go 使用的是值传递

  [^形参]:函数使用参数则该变量呗称为函数的形参

* 函数用法

  | 函数的用法               | 描述                                 |
  | ------------------------ | ------------------------------------ |
  | 函数作为另一个对象的实参 | 函数定义后可作为另一个函数的实参传入 |
  | 闭包                     | 闭包是匿名函数，可在动态编程中使用   |
  | 方法                     | 一个包含了接收者的函数               |

## Go 数组

* 数组定义

  ​	具有相同唯一类型且长度固定的数据项序列

* **一维数组**

  * 数组声明

    `var variable_name [SIZE] variable_type`

    | SIZE                   | 1                 | 2                 |
    | ---------------------- | ----------------- | ----------------- |
    | variable_name [SiZE-1] | variable_name [0] | variable_name [1] |

    

    * var	变量
    * variable_name	数组名
    * SIZE	元素个数
    * variable_type	类型

  * 初始化数组

  ```go
  var variable_name = [5]float32{1000.0,2.0,3.4,7.0,50.0}
  
  variable_name := [5]float32{1000.0,2.0,3.4,7.0,50.0}
  
  var variable_name = [...]float32{1000.0,2.0,3.4,7.0,50.0}
  
  variable := [...]float32{1000.0,2.0,3.4,7.0,50.0}
  ```

  * 访问数组元素

    `var salary variable_type = variabel_name[num]`

    * var
    * salary
    * variable_type
    * variable_name
    * num

  ```go
  // 遍历数组
  package main
  
  import (
    "fmt"
  )
  
  func main(){
    // 声明数组
    var n [10]int
  	// 声明遍历所需变量  
    var i,j int
    
    // 数组 n 初始化元素
    for i = 0;i < 10;i++ {
      n[i] = i + 100
    }
    
    // 遍历数组 n
    for j = 0;j < 10;j++{
      fmt.Printf(n[j])
    
  }
  ```

* **二维数组**

  * 数组声明

    `var arrayName [x][y] variable_type`

  |       | Column 0          | Column 1          | Column 2          | Column 3          |
  | ----- | ----------------- | ----------------- | ----------------- | ----------------- |
  | Row 0 | `arrayName[0][0]` | `arrayName[0][1]` | `arrayName[0][2]` | `arrayName[0][3]` |
  | Row 1 | `arrayName[1][0]` | `arrayName[1][1]` | `arrayName[1][2]` | `arrayName[1][3]` |
  | Row 2 | `arrayName[2][0]` | `arrayName[2][1]` | `arrayName[2][2]` | `arrayName[2][3]` |
  | Row 3 | `arrayName[3][0]` | `arrayName[3][1]` | `arrayName[3][2]` | `arrayName[3][3]` |

  * 初始化数组

    ```go
    package main
    
    import(
      "fmt"
    )
    
    func main() {
    	// 初始化数组  
      a := [2][2]string()
      
    	// 为数组赋值 
      a[0][0] = "C"
      a[0][1] = "C++"
      a[1][0] = "Java"
      a[1][1] = "Python"
      
      // 打印数组
      fmt.Println(a)
    }
    ```

  * 访问数组元素

    ```go
    package main
    
    import(
      "fmt"
    )
    
    func main() {
      // 声明
      var a = [5][2]int{ {0,1},{2,3},{4,5},{6,7},{8,9} }
    
      // 遍历数组
      var i,j int
      for i = 0,i < 5,i++ {
        for j = 0,j < 2,j++{
          fmt.Printf("a[%d][%d] = %d",i,j,a[i][j])
        }
      }
    }
    ```

    ```go
    package main
    
    import(
      "fmt"
    )
    
    func main() {
      // 声明
      animals = [][]string()
      
      // 创建一维数组
      row1 := []string{"fish","shark","eel"}
      row2 := []string("cat","dog")
      row3 := []string("brid")
      
      // append() 函数 将一维数组插入二维数组
      animals = append(animals,row1)
      animals = append(animals,row2)
      animals = append(animals,row3)
      
      // 遍历数组
      for i := range animals {
        fmt.Printf("Row:%v\n",i)
        fmt.Printf(animals[i])
      }
    }
    ```

* 函数调用

  * 形参设定数组大小

    `void myFunction(param [10]int){}`

  * 形参未设定大小

    `void myFunction(param []int){}`

    ```go
    package main
    
    import(
      "fmt"
    )
    
    func main() {
    	// 声明数组
      var balance = [5]int {1000,2,3,17,50}
      var avg float32
      
      // 数组作为参数(形参)传递给函数
      avg = getAverage(balance,5)
      // 输出函数平均值
      fmt.Printf("平均值为：%f",avg)
    }
    
    func getAverage(arr [5]int,size int) float32 {
      var i,sum int
      var avg float32
      
      for i = 0;i < size;i++ {
        sum += arr[i]
      }
      
      avg = flooat32(sum) / float32(size)
      
      return avg
    }
    ```

## Go 指针

​	指针变量指向一个值的内存地址

* 声明指针

  `var var_name *var-type`

  ```go
  var ip *int // 指向整形
  var ip *float32 // 指向浮点型
  ```

* 指针使用

  ```go
  package main
  
  import (
    "fmt"
  )
  
  func main() {
    var a int = 20 // 声明实际变量
    var ip *int // 声明指针类型
    
    ip = &a //指针变量储存地址	为指针变量赋值
    
    fmt.Printf("a 变量的地址：%x\n",&a)
    
    // 指针变量的存储地址
    fmt.Printf("ip 变量存储的指针地址：%x\n",ip)
    
    // 使用指针访问值
    fmt.Printf("*ip 变量的值：%d\n",*ip)
  }
  ```

* 空指针

  ​	当一个指针被定义后没有分配到任何变量是，值为 nil

  ​	nil 指代零值或空值

  ​	指针变量的缩写通常为ptr

  ```go
  package main
  
  import(
    "fmt"
  )
  
  func main() {
    var ptr *int
    
    fmt.Printf("ptr 的值为：%x\n",ptr)
  }
  ```

  > 空指针的判断
  >
  > ```go
  > // 非空指针
  > if(ptr != nil)
  > // 空指针
  > if(ptr == nil)
  > ```

* 指针数组

  ​	保存数组时需要借助指针

  * 声明指针数组

    `var ptr [arr]*ptr-type`

    ```go
    package main
    
    import(
      "fmt"
    )
    
    const arr int = 3 // 定义一个数组 长度为3
    
    func main() {
      a := []int{10,100,1000}
      var i int // 声明遍历数组所需变量
      var ptr [arr]*int // 声明整数类型指针
      
      for i = 0; i < arr; i++ {
        ptr[i] = &a[i] // 整数地址赋值给指针
      }
      
      for i = 0; i < arr; i++ {
        fmt.Printf("a[%d] = %d\n",i,*ptr[i])
      }
    }
    ```

* 指向指针的指针变量

  ​	如果一个指针变量存放的优势另一个指针变量的地址，则称这个指针变量为指向指针的指针变量

  * 声明指向指针的变量

    `var ptr **int`

    ```go
    package main
    
    import(
      "fmt"
    )
    
    func main() {
      var a int
      var ptr *int
      var pptr **int
      
      a = 3000
      
      // 指针 ptr 地址
      ptr = &a
      
      // 指向指针 ptr 地址
      pptr = &ptr
      
      // 获取 pptr 的值
      fmt.Printf("变量 a = %d\n",a)
      fmt.Printf("指针变量 *ptr = %d\n",*ptr)
      fmt.Printf("指向指针的指针变量 **pptr = %d\n",**pptr)
    }
    ```

* 指针作为函数参数

  ​	

  ```go
  package main
  
  import(
    "fmt"
  )
  
  func main() {
    // 定义局部变量
    var a int = 100
    var b int = 200
    
    fmr.Printf("交换前 a 的值：%d\n",a)
    fmt.Printf("交换前 b 的值：%d\n",b)
    
    // 调用函数用于交换值
    // &a 指向 a 变量地址
    // &b 指向 b 变量地址
    swap(%a,%b)
    
    fmt.Printf("交换后 a 的值：%d\n",a)
    fmt.Ptintf("交换后 b 的值：%d\n",b)
  }
  
  func swap (x *int,y *int) {
    var temp int
    temp = *x
    *x = *y
    *y = temp
  }
  ```

  

## Go 结构体

​	结构体是由一系列具有相同类型或不同类型的数据构成的数据集合

​	数组可以存储同一类型的数据，但在结构体重我们可以为不同项定义不同的数据类型

* 声明结构体

  ​	

  ```go
  type struct_variable_type struct {
    member definition
    member definition
  	...
  	member definition
  }
  ```

  > 一旦定义了结构体类型，就只能用于变量的声明
  >
  > 语法格式：
  >
  > `variable_name := struvture_variable_type{value1,value2...valuen}`
  >
  > `varible_name := structure_variable_type{key1:value1,key2:value2,...,keyn:valuen}`

  ```go
  package main
  
  import(
    "fmt"
  )
  
  type Books struct {
    title string
    author string
    subject string
    book_id int
  }
  
  func main() {
    // 创建结构体
    fmt.Println(Books{title:"Go 语言"，author:"King Yen",subject:"Go 语言笔记"，book_id:01})
    /* 简写 */
    fmt.Println(Books{"Go 语言","King Yen","Go 语言笔记",01})
    
    // 忽略字段为 0 或 空
    fmt.Println(Books{title:"Go 语言",author:"King Yen"})
  }
  ```

* 访问结构体函数

  ​	`结构体.成员名`

  ```go
  package main
  
  import(
    "fmt"
  )
  
  type Books struct {
    title string
    author string
    subject string
    book_id int
  }
  
  func main() {
    var Book1 Books // 声明 Book1 为 Books 类型
    var Book2 Books // 声明 Book2 为 Books 类型
    
    // Book1 描述
    Book1.title = "Go 语言"
    Book1.author = "King Yan"
    Book1.subject = "Go 语言笔记"
    Book1.book_id = 01
    // Book2 描述
    Book2.title = "Python 语言"
    Book2.author = "King Yen"
    Book2.subject = "Python 笔记"
    Book2.book_id = 02
    
    // 输出 Book1
    fmt.Print("Book 1 title:%s\n",Book1.title)
    fmt.Print("Book 1 author:%s\n",Book1.author)
    fmt.Print("Book 1 subject:%s\n",Book1.subject)
    fmt.Print("Book 1 book_id:%s\n",Book1.book_id)
    // 输出 Book2
    fmt.Print("Book 2 title:%s\n",Book2.title)
    fmt.Print("Book 2 author:%s\n",Book2.author)
    fmt.Print("Book 2 subject:%s\n",Book2.subject)
    fmt.Print("Book 2 book_id:%s\n",Book2.book_id)
  }
  ```

* 结构体作为函数参数

  ```go
  package main
  
  
  import(
    "fmt"
  )
  
  type Books struct {
    title string
    author string
    subject string
    book_id int
  }
  
  func main() {
    var Book1 Books // 声明 Book1 为 Books 类型
    var Book2 Books // 声明 Book2 为 Books 类型
    
    // Book1 描述
    Book1.title = "Go 语言"
    Book1.author = "King Yan"
    Book1.subject = "Go 语言笔记"
    Book1.book_id = 01
    // Book2 描述
    Book2.title = "Python 语言"
    Book2.author = "King Yen"
    Book2.subject = "Python 笔记"
    Book2.book_id = 02
    
    // 输出 Book1
    printBook(Book1)
    // 输出 Book2
    printBook(Book2)
  }
  
  func printBook(book Books) {
    fmt.Print("Book title:%s\n",Book1.title)
    fmt.Print("Book author:%s\n",Book1.author)
    fmt.Print("Book subject:%s\n",Book1.subject)
    fmt.Print("Book book_id:%s\n",Book1.book_id)
  }
  ```

* 结构体指针

  * 声明结构体

    `var struct_pointer *Books`

    > 以上定义的指针变量可以存储结构体变量的地址

  * 查看结构体变量地址

    `struct_pointer = &Book1`

  * 使用结构体指针访问结构体成员

    `struct_pointer.title`

  ```go
  package main
  
  import(
    "fmt"
  )
  
  type Books struct {
    title string
    author string
    subject string
    book_id int
  }
  
  func main() {
    var Book1 Books // 声明 Book1 为 Books 类型
    var Book2 Books //声明 Book2 为 Books 类型
    
    // Book1 描述
    // Book1 描述
    Book1.title = "Go 语言"
    Book1.author = "King Yan"
    Book1.subject = "Go 语言笔记"
    Book1.book_id = 01
    // Book2 描述
    Book2.title = "Python 语言"
    Book2.author = "King Yen"
    Book2.subject = "Python 笔记"
    Book2.book_id = 02
    
    // 打印 Book1 信息
    printBook(&Book1)
    // 打印 Book2 信息
    printBook(&Book2)
  }
  
  func printBook(book *Books) {
    fmt.Print("Book title:%s\n",Book1.title)
    fmt.Print("Book author:%s\n",Book1.author)
    fmt.Print("Book subject:%s\n",Book1.subject)
    fmt.Print("Book book_id:%s\n",Book1.book_id)
  }
  ```


## Go 切片(Slice)

​	长度不是固定的，可以追加元素，在追加时可能使切片的容量增加

​	切片是对数组的抽象

* 声明切片

  > 通过声明一个未指定大小的数组来定义切片

  `var identifier []type`

  > 使用 make() 函数来创建切片

  `var slice1 []type = make([]type,len)`

  `slice1 := make([]type,len)`

  > 可以指定切片容量(其中 capacity 为可选参数)

  `make([]T,length,capacity)`

  [^len]:这里的 len 是数组长度并且也是切片的原始长度

* 初始化切片

  * 直接初始化切片

    `s :=[] int{1,2,3}`

    > [] 是切片的类型
    >
    > {1,2,3} 初始化值依次是1,2,3
    >
    > cap = len = 3

  * 数组 arr 的引用

    `s := arr[:]`

  * 将数组 arr 中从下表 startindex 到 endlnex-1 的元素创建一个新的切片

    `s := arr[startIndex:]`

  * 默认 endIndex 时将表示一直到最后一个元素

    `s := arr[:endIndex]`

  * 默认 startIndex 时将表示一直到最后一个元素

    `s := arr[:startIndex:endIndex]`

  * 通过切片 s 初始化切片 s1

    `s := make([]int,len,cap)`

  > 通过内置函数 make() 初始化切片s，[]int 标识为其他元素类型为 int 的切片

* len() 和 cap() 函数

  * len() 函数
    * 切片是可索引的，并且可以由 len() 方法获取长度
  * cap() 函数
    * 切片提供了计算容量的方法 cap() 测量切片最长可达到多少

  ```go
  package main
  
  import(
    "fmt"
  )
  
  func main() {
    var numbers = make([]int,3,5)
    
    printSlice(numbers)
  }
  
  func printSlice(x []int){
    fmt.Printf("len=%d cap=%d slice=%v\n",len(x),cap(x),x)
  }
  ```

* 空(nil)切片

  > 一个切片在为初始化之前默认为 nil，长度为 0

  ```go
  package main
  
  import(
    "fmt"
  )
  
  func main() {
    var numbers []int // 通过未定义长度的数组创建切片
    
    printSlice(numbers)
  }
  
  func printSlice(x []int){
    fmt.Printf("len=%d cap=%d slice=%v",len(x),cap(x),x)
  }
  ```

* 切片截取

  > 可以通过设置上下限来设置街区切片[lower-bound;upper-bound]

  ```go
  package main
  
  import(
    "fmt"
  )
  
  func main() {
    // 创建切片
    numbers := []int{0,1,2,3,4,5,6,7,8}
    printSlice(numbers)
    
    // 打印原始切片
    fmt.Println("numbers ==",numbers)
    
    // 打印子切片从索引1(包含)到索引4(不包含)
    fmt.Println("numbers[1:4] ==",numbers[1:4])
    
    // 默认下限为0
    fmt.Println("numbers[:3] ==",numbers[:3])
    
    // 默认上限为len(s)
    fmt.Println("numbers[4:] ==",numbers[4:])
    
    numbers1 := make([]int,0,5)
    printSlice(numbers1)
    
    // 打印子切片从索引0(包含)到索引2(不包含)
    number2 := numbers[:2]
    printSlice(number2)
    
    // 打印子切片从索引2(包含)到索引5(不包含)
    number3 := numbers[2:5]
    printSlice(number3)
  }
  
  func printSlice(x []int) {
    fmt.Printf("len=%d cap=%d slice=%v\n",len(x),cap(x),x)
  }
  ```

* append() 与 copy() 函数

  ```go
  package main
  
  import(
    "fmt"
  )
  
  func main() {
    var numbers []int
    printSlice(numbers)
    
    // 允许追加空切片
    numbers = append(numbers,0)
    printSlice(numbers)
    
    // 向切片添加一个元素
    numbers = append(numbers,1)
    printSlice(numbers)
    
    // 同时添加多个元素
    numbers = append(numbers,2,3,4)
    printSlice(numbers)
    
    // 创建切片 numbers1 是之前切片的两倍容量
    numbers1 := make([]int,len(numbers),(cap(numbers))*2)
    
    // 拷贝 numbers 的内容到 numbers1
    copy(numbers1,numbers)
    printSlice(numbers1)
  }
  
  func printSlice(x []int) {
    fmt.Printf("len=%d cap=%d slice=%v\n",len(x),cap(x),x)
  }
  ```

## Go 范围（Range）

​	range 关键字用于 for 虚幻中迭代数组(array)、切片(slice)、通道(channel)或集合(map)的元素。在数组和切片中它返回元素的索引和索引对应的值，在集合中返回 key-value 对

* for 循环

  ```go
  for key,value := range oldMap { // key 和 value 可以省略
    newMap[key] = value
  }
  ```

  ```go
  package main
  
  import(
    "fmt"
  )
  
  var pow = []int{1,2,4,8,18,32,64,128}
  
  func main() {
    for i,v := range pow {
      fmt.Println("2**%d = %d",i,v)
    }
  }
  ```

  > for 循环的 range 格式可省略 key 和 value
  >
  > ```go
  > package main
  > 
  > import(
  >   "fmt"
  > )
  > 
  > func main() {
  >   map1 := make(map[int]float32)
  >   map1[1] = 1.0
  >   map1[2] = 2.0
  >   map1[3] = 3.0
  >   map1[4] = 4.0
  >   
  >   // 读取 key 和 value
  >   for key,value := range map1 {
  >     fmt.Println("key is:%d - value is:%f",key,value)
  >   }
  >   
  >   // 读取 key
  >   for key := range map1 {
  >     fmt.Println("key is:%d",key)
  >   }
  >   
  >   // 读取 value
  >   for _,value := range map1 {
  >     fmt.Println("value is:%f",value)
  >   }
  > }
  > ```

* 数组、切片

  ```go
  package main
  
  import(
    "fmt"
  )
  
  func main() {
    nums := []int{2,3,4}
    sum := 0
    for _,num := range nums {
      sum += num
    }
    fmt.Println("sum:",sum)
    for i,num := range nums {
      if num == 3 {
        fmt.Println("index:",i)
      }
    }
  }
  ```

* 集合

  ```go
  package main
  
  import(
  	"fmt"
  )
  
  func main() {
    kvs := map[string]string{"a":"apple","b":"banana"}
    for k,v := range kvs {
      fmt.Println("%s -> %s",k,v)
    }
  }
  ```

* 字符串

  ```go
  package main
  
  import(
  	"fmt"
  )
  
  func main() {
    for i,c := rango "go" {
      fmt.Println(i,c)
    }
  }
  ```

  

## Go 集合（Map）

> * Map 是一种无序的键值对的集合
> * Map 最重要的一点是通过 key 来快速检索数据，key 类似于索引，指向数据的值
> * Map 是一种集合，所以可以像迭代数组和切片一样进行迭代。但是 Map 是无序的，遍历 Map 时返回的键值对的顺序也是不确定的
> * 在获取 Map 的值是，如果键不存在，返回该类型的零值
> * Map 时引用类型，若果将一个 Map 传递给一个函数或者赋值给另一个变量，都会指向同一个底层数据结构，因此对 Map 的修改会影响到所有引用它的变量

* 声明 Map

  * 使用 make 函数

    `map_variable := make(map[KeyType]ValueType,initialCapacity)`

    > * KeyType 键的类型
    > * ValueType 值的类型
    > * initialCapacity 可选参数，用于指定 Map 的初始容量

  * 使用 map 关键字

    `map_variable := map[KeyType] ValueType {...}`

  ```go
  // 创建一个空的 Map
  m := make(map[string]int)
  
  // 创建一个初始容器为10的 Map
  m := make(map[string]int,10)
  
  // 使用字面量创建 Map
  m := map[string]int{
    "apple":1,
    "banana":2,
    "brange":3,
  }
  
  // 获取元素 获取键值对
  v1 := m["apple"]
  v2,ok := m["pear"] // 如果键不存在，ok 的值为 false，v2 的值为该类型的零值
  
  // 修改元素 修改键值对
  m["apple"] = 5
  
  // 获取 Map 长度
  len := len(m)
  
  // 遍历 Map
  for k,v := range m {
    fmt.Printf("key=%s,value=%d\n",k,v)
  }
  
  // 删除键值对
  delete(m,"banana")
  ```

  ```go
  package main
  
  import(
    "fmt"
  )
  
  func main() {
    // 创建集合
    var siteMap map[string]string
    siteMap = make(map[string]string)
    
    // Map 插入 key - value 对
    siteMap ["Google"] = "谷歌"
    siteMap ["Baidu"] = "百度"
    siteMap ["Tesla"] = "特斯拉"
    siteMap ["Wiki"] = "维基百科"
    siteMap ["Apple"] = "苹果"
    
    // 使用键输出 Map 值
    for site := range siteMap {
      fmt.Println(site,"Map:",siteMap [site])
    }
    
    // 查看元素在集合中是否存在
    name,ok := siteMap ["Facebook"] //存在 true 不存在 false
    /* fmt.Println(capital)
    	 fmt.Println(ok) */
    if (ok) {
      fmt.Println("Facebook 的 Map 是"，name)
    } else {
      fmt.Println("Facebook 的 Map 不存在")
    }
    
    // 删除元素
    delete(siteMap,"Baidu")
    fmt.Println("删除后的 Map 为：")
    
    // 使用键输出 Map 值
    for size := range siteMap {
      fmt.Println(site,"Map:",siteMap [site])
    }
  }
  ```

## Go 类型转换

## Go 接口

## Go 错误处理

## Go 并发
# NandToTeris

## *The World Above*

### Boolean Logic

- 布尔门（Boolean gate）：对布尔函数（Boolean function）的物理实现

- 布尔代数（Boolean Algebra）：输入输出数值均为布尔型数值的函数

- 布尔代数的描述方法：

  - 真值表表示法（Truth Table Representation）描述布尔函数最简单的方法。枚举出函数所有可能的输入变量组合，然后写出每一种组合所对应的函数输出值。

  - 规范表示法( Canonical Representation ) ：每个布尔函数都至少由一个布尔表达式来描述， 称之为规范表示法。

    - 布尔表达式（Boolean Expressions）：在输入变量上使用布尔算子（Boolean oporator）来描述布尔函数。基本的布尔算子有“And”（只有在x和y都为1时，x And y的值等于1），“Or”（x或者y中只要有一个为1时，x Or y的值为1），以及“Not”（当x为0时，Not x为1）。我们将使用常用的计算符号来表示这些算子：x · y或者(xy)代表x And y，x + y代表x Or y，$\overline{\text{x}}$代表Not x。

- 2-输入变量的布尔函数( Two-Input Boolean Functions )：2个输入变量能构成16个布尔函数。具体见下图。

    ![image-20211115142921487](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211115142921487.png)

    - Nand 函数以及Nor 函数在理论上还有个有趣的特征：And/Or/Not 算子都可以只用Nand 或Nor 函数来建构。
    - 既然每个布尔函数都能够通过规范表示法由And、Or和Not构成， 那么每个布尔函数也能仅使用Nand 或Nor函数来构成。

- 门（gate）:实现布尔函数的物理设备，在本书里，和芯片(chip) 的概念可交换使用，但是门的概念一般用于描述简单的芯片。

- 输入管脚(input pins )：实现布尔函数输入变量的物理设备，如果布尔函数有n个输入变量，门将会有n个输入管脚。

- 输出管脚(output pins )：实现布尔函数输入变量的物理设备，如果布尔函数有m个返回的二进制，门将会有n个输出管脚。

- 复杂的门电路也是由很多基本的门组成的。

- 最简单的门是由微小的开关设备（称为晶体管， transistors ) 构成。

- 复合门（Composite Gates）：所有的逻辑门都有相同输入和输出的语义表达0 和1, 它们可以连起来构成具有任意复杂度的复合门电路

- 逻辑设计(logic design)：给定门的描述（外部接口）， 通过应用已经实现的门， 找到有效的方法来实现它。从效率的角度上来说， 基本原则是用尽可能少的门来实现尽可能多的功能。

- 门的外部接口(interface) ：输入和输出管脚。

- 基本门（Primitive Gates）:一系列基本模块，其他的门电路可以通过这些模块来构建，包括Nand门、与门、或门、非门等。
  ![image-20211115150738163](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211115150738163.png)
  
- 硬件仿真器中提供的内置芯片

  - Nand门 
    > 芯片名： Nand
    > 输入： a, b
    > 输出： out
    > 功能： If a=b=1 then out=0 else out=1    
    
  - Not门  
    > 芯片名： Not
    > 输入： in
    > 输出： out
    > 功能： If in=0 then out=1 else out=0
    
  - And门
    > 芯片名： And
    > 输入： a, b
    > 输出： out
    > 功． 能： If a=b=1 then out=1 else out=0
    
  - Or门
    > 芯片名： Or
    > 输入： a, b
    > 输出： out
    > 功能： If a=b=0 then out=0 else out=1
    
  - Xor门
    > 芯片名： Xor
    > 输入： a, b
    > 输出： out
    > 功能： If a≠b then out=1 else out =0 
    
  - Multiplexor门  
    > 芯片名： Mux
    > 输入： a, b, sel
    > 输出： out
    > 功能： If sel=0 then out=a else out =b
    
  - Demultiplexor门
    > 芯片名： DMux
    > 输入： in, sel
    > 输出： a, b
    > 功能： If sel=0 then (a=in, b= 0) else (a=0 b=in)
    
  - 多位Not (Multi-Bit Not)门
    > 芯片名： Not 16
    > 输入： in [16]   // 16-bit 管脚
    > 输出： out [16]
    > 功能： For i=0 .. 15 out[i] =Not(in[i])
    
  - 多位And (Multi-Bit And)门 
    > 芯片名： And16
    > 输入： a[16] , b[16J
    > 输出： out [16J
    > 功能： For i=0 .. 15 out [i] =And(a[i], b[i]) 
    
  - 多位Or (Multi-Bit Or)门  
    > 芯片名： Or16
    > 输入： a[16] , b[16]
    > 输出： out [16]
    > 功能： For i=0 .. 15 out[i] =Or(a [i] , b[i]) 
    
  - 多位Multiplexor (Multi-Bit Multiplexor )门
    > 芯片名： Mux 16
    > 输入： a[16) , b[16) , sel
    > 输出： out [16)
    > 功能： If sel =0 then for i=0 .. 15 out[i]=a[i]
    >             else for i=0 .. 15 out[i]=b[i]
    
  - 多通道Or (Multi-Way Or)门
    > 芯片名： OrBWay
    > 输入： in [8]
    > 输出： out
    > 功能： out=Or (in [0] , in [1] , ... , in [ 7] ) 
    >
    > 说明：对于一个n位的Or门， 当n位输入变量中任意一位或一位以上为1, 输出就为1, 否则就为0
    
  - 多通道／多位Multiplexor (Multi-Way/Multi-Bit Multiplexor )门
    > 芯片名： Mux4Way16
    > 输入： a[16] , b[16] , c[16] , d[16], sel [2]
    > 输出： out [16]
    > 功能： If sel=00 then out =a else if sel=01 then out=b
    >             else if sel=10 then out=c else if sel=11 then out=d
    > 说明： 上述赋值操作都是16-位操作． 比如， "out=a" 意指"for i=0 .. 15 out [i]=a[i] "
    
    
    > 芯片名： Mux8Way16
    > 输入： a[16] , b[16] , c[16] , d[16], e[16] , f[16] , g[16] , h[16], sel [3]
    > 输出： out [16]
    > 功能： If sel=000 then out =a else if sel=001 then out=b
    >             else if sel=010 then out=c ... else if sel=111 then out=h
    > 说明： 上述赋值操作都是16-位操作． 比如， "out=a" 意指"for i=0 .. 15 out [i]=a[i] "
    
  - 多通道／多位Demultiplexor (Multi-Way/Multi-Bit Demultiplexor)门
    > 芯片名：DMux4Way
    > 输入： in, sel [2]
    > 输出： a, b, c, d
    > 功能： If sel=00 then {a=in, b=c=d=0}
    > 			else if sel=01 then {b=in, a=c=d=0}
    > 			else if sel=10 then {c=in, a=b=d=0}
    > 			else if sel=11 then {d=in, a=b=c=0 }
    
    
    > 芯片名： DMux8Way
    > 输入： in, sel [3]
    > 输出： a, b, c, d, e, f, g, h
    > 功能： If sel=000 then {a=in, b=c=d=e=f=g=h=0}
    > 			else if sel=001 then {b=in, a=c=d=e=f=g=h=0}
    > 			else if sel=010 ...
    >
    > ​			...
    >
    > ​			else if sel=111 then {h=in, a=b.=c=d=e=f=g=0}
#### Proj1 心得

- 构建门时可先从真值表着眼，分析输入输出的规律
- Not 用 Nand 构造，可以是两值相同，也可以是其中一值为正

## *Abstractions*



## *The World Below*

## *High-Level Language Land*

## *The Road Down to Hardware Land*

## *Hardware Land*
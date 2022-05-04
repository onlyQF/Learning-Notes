# how to use global variables in c/cpp

1:在 一个头文件中先声明全局变量，如 header.h
```
#ifndef HEADER_H
#define HEADER_H

// any source file that includes this will be able to use "global_x"
extern int global_x;//用extern 声明全局变量 global_x

void print_global_x();

#endif
```
2：在其他代码文件中使用该全局变量

1：在source1.cpp中使用
  ```
#include "header.h"//先将头文件包括进来

// since global_x still needs to be defined somewhere,
// we define it (for example) in this source file
int global_x; 
//*在这里定义一次，记住变量可以多次声明但是只能定义一次，因此在这里定义一次后，在其他文件中使用只需要声明不可以再次定义*//

int main()
{
    //set global_x here:
    global_x = 5;//在这里使用全局变量

    print_global_x();//在这里使用全局函数
}

```
 2：在source 2中使用全局函数
 ```
#include <iostream>
#include "header.h"

void print_global_x()//在其他文件中定义了该全局函数
{
    //print global_x here:
    std::cout << global_x << std::endl;
}

```

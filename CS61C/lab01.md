## 练习 1
```c
#include <stdio.h>

/* Only change any of these 4 values */
#define V0 3
#define V1 3
#define V2 1
#define V3 3

int main(void) {
    int a;
    char *s;

    /* This is a print statement. Notice the little 'f' at the end!
     * It might be worthwhile to look up how printf works for your future
     * debugging needs... */
    printf("Berkeley eccentrics:\n====================\n");

    /* for loop */
    for (a = 0; a < V0; a++)
    {
        printf("Happy ");
    }
    printf("\n");

    /* switch statement */
    switch (V1)
    {
    case 0:
        printf("Yoshua\n");
    case 1:
        printf("Triangle Man\n");
        break;
    case 2:
        printf("Chinese Erhu Guy\n");
    case 3:
        printf("Yoshua\n");
        break;
    case 4:
        printf("Dr. Jokemon\n");
        break;
    case 5:
        printf("Hat Lady\n");
    default:
        printf("I don't know these people!\n");
    }

    /* ternary operator */
    s = (V3 == 3) ? "Go" : "Boo";

    /* if statement */
    if (V2) {
        printf("%s BEARS!\n", s);
    } else {
        printf("%s CARDINAL!\n", s);
    }

    return 0;
}
```

## 练习 2
`hello.c`:
```c
#include <stdio.h>

int main(int argc, char *argv[]) {
    int i;
    int count = 0;
    int *p = &count;

    for (i = 0; i < 10; i++) {
        (*p)++; // Do you understand this line of code and all the other permutations of the operators? ;)
    }

    printf("Thanks for waddling through this program. Have a nice day.");
    return 0;
}
```

使用 `-g` 标志编译 `hello.c`
```shell
gcc -g -o hello hello.c
```

```shell
gdb hello.c
```

- Q1: While you’re in a gdb session, how do you **set the arguments** that will be passed to the program when it’s run?

比如传递 1 2 3 至 args，那么此时 

gdb 中：
```shell
 set args 1 2 3
```

![|550](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250225232111369.png)

|          |                                           |
| -------- | --------------------------------------- |
| args\[ /home/birdy/code/cs61c-su20/lab01/hello o  o  |
| args\[                                               |
| args                                                 |
| ar                                                   |

- How do you **create a breakpoint**?
	- 比如要给 main 函数加断点，使用 `b main`
	- ![|525](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250225232257339.png)
- How do you **execute the next line of C code** in the program after stopping at a breakpoint?
	- 使用  `next` 或者 `n`
- If the next line of code is a function call, you’ll execute the whole function call at once if you use your answer to #3 . (If not, consider a different command for #3 !) How do you tell GDB that you **want to debug the code inside the function** (i.e. step into the function) instead? (If you changed your answer to #3 , then that answer is most likely now applicable here.)
	- 也就是步入函数内部，用 `step` 或者 `s`
- How do you **continue the program after stopping** at a breakpoint?
	- `continue` 或者 `c`
- How can you **print the value of a variable** (or even an expression like 1+2) in gdb?
	- `print [变量名]`
	- ![|191](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250225232526722.png)
- How do you configure gdb so it **displays the value of a variable after every step**?
	- `display [变量名]`
	- ![|650](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250225232754159.png)
- How do you **show a list of all variables and their values** in the current function?
	- `info locals`
- How do you **quit** out of gdb?
	- `quit` 或者 `q`

## 练习 3
比如我们想创建一个 `name.txt` 文件并且在里面写入 `Birdy`
```shell
echo Birdy > name.txt
```

之后如果
```shell
cat name.txt
```
则会输出 `Birdy`

一种简单的通过文件来进行输入的方式：
```shell
./int_hello < name.txt
```
![|500](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250225234021837.png)

在 gdb 中，可以用
```shell
run < name.txt
```

![|575](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250225234115757.png)

```ad-tip
`>` 是输出重定向符号，用于将命令的输出写入文件(覆盖)。
`>>` 是追加模式。

`<` 是输入重定向符号，用于将文件内容作为命令的输入。
```

## 练习 4
### 安装 valgrind
```shell
sudo apt update
```

```shell
sudo apt install valgrind
```

### 练习
```shell
gcc -o segfault_ex segfault_ex.c
gcc -o no_segfault_ex no_segfault_ex.c
```

```ad-note
The sizeof keyword gives the amount of storage, in bytes, associated with a variable or a type (including aggregate types).
返回一个对象或者类型所占的内存字节数
```

```c
#include <stdio.h>
int main() {
    int a[5] = {1, 2, 3, 4, 5};
    unsigned total = 0;
    for (int j = 0; j < sizeof(a); j++) {
        total += a[j];
    }
    printf("sum of array is %d\n", total);
}
```

此段代码中的 `sizeof(a)` 相当于就是 $5\times4=20$

## 练习 5
```c
#include <stddef.h>
#include "ll_cycle.h"

int ll_has_cycle(node *head) {
    /* your code here */
    node *tortoise, *hare;
    tortoise = head;
	
	// important!!!
    if(head == NULL)
        return 0;

    hare = tortoise->next;

    while(hare != NULL && hare->next != NULL && tortoise != NULL) {
        if(hare == tortoise)
            return 1;
        tortoise = tortoise->next;
        hare = hare->next->next;
    }

    return 0;
}
```

![|725](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250226000916109.png)


一开始我没有考虑到 `head == NULL` 的情况，导致出现段错误。
![|675](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250226000848522.png)


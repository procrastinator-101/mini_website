#**Function pointers in C**

##**Definition**
A function pointer is a pointer (i.e variable holding some address) that points to a piece of code, the function it points to.

##**Syntax**
>function\_return\_datatype (\*pointer\_name)(function\_arguments\_datatype)
##**exemple 1**
```c
#include <stdio.h>

void say_hello(void)
{
	printf("hello\n");
}

int main()
{
	void	(*ptr)(void);

	ptr();
}
```

>ptr : is pointer to a function that returns nothing(void) and that takes no arguments(void)
>say\_hello is a function just prints "hello" on stdout.

##**exemple 2**
```c
#inlcude <stdio.h>

int sum(int a, int b)
{
	return (a + b);
}

int main()
{
	int (*ptr)(int, int);
	printf("sum = %d\n", ptr(1, 3));

}
```

>ptr : is a pointer to function that returns an int and takes two arguments of type int;
>sum : is a function that calculates the sum of two integers;

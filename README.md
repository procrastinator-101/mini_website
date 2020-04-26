# Function pointers in C

## Definition
A function pointer is a pointer (i.e variable holding some address) that points to a piece of code, the function it points to.

## Syntax
>function\_return\_datatype (\*pointer\_name)(function\_arguments\_datatype)

## Exemple 1
```c
#include <stdio.h>

void say_hello(void)
{
	printf("hello\n");
}

int main()
{
	void	(*ptr)(void);

	ptr = say_hello;
	ptr();
	return (0);
}
```

>ptr : is pointer to a function that returns nothing(void) and that takes no arguments(void)</br>
say\_hello is a function just prints "hello" on stdout

## Exemple 2
```c
#inlcude <stdio.h>

int sum(int a, int b)
{
	return (a + b);
}

int main()
{
	int (*ptr)(int, int);

	ptr = sum;
	printf("sum = %d\n", ptr(1, 3));
	return (0);
}
```

>ptr : is a pointer to function that returns an int and takes two arguments of type int  
>sum : is a function that calculates the sum of two integers

## Example 3
```c
#include <stdio.h>

char *fill_buffer(char *buffer, int size, char (*ptr1)(void))
{   
    for (int i = 0; i < size - 1; i++)
        buffer[i] = ptr1();
    buffer[size - 1] = 0;
    return (buffer);
}  
   
char get_character(void)
{   
    char c;

    scanf("%c", &c);
    printf("c = %d\n", c);
    return (c);
}

int main()
{  
    char buffer[10];
    char *(*ptr)(char*, int, char(*)(void));
    char (*ptr1)(void);

    ptr = fill_buffer;
    ptr1 = get_character;
    ptr(buffer, 10, ptr1);
    printf("%s\n", buffer);
    return (0);
}
```
## Example 4
```c
#include <stdio.h>

int *fill_array(int *arr, int size, int (*ptr1)(int))
{
    for (int i = 0; i < size; i++)
        arr[i] = ptr1(i);
    return (arr);
}

int get_number(int a)
{
    int num;

    scanf("%d", &num);
    return (num * a);
}

int main()
{
    int arr[5];
    int *mat;
    int *(*ptr)(int *, int, int(int));
    int (*ptr1)(int);

    ptr = fill_array;
    ptr1 = get_number;
    mat = ptr(arr, 5, ptr1);
    for (int i = 0; i < 5; i++)
        printf("%d\n", mat[i]);
    return (0);
}
```

# vs2013-1-30
#define _CRT_SECURE_NO_WARNINGS 1
//指针是个变量，存放内存单元的地址（编号）。
#include<stdio.h>
int main()
{
	int a = 10;//在内存中开辟一块空间
	int *p = &a;//这里我们对变量a取出他的地址，可以使用&操作符。
	             //将a的地址存放在p变量中 ，p就是一个指针变量。
	return 0;
}
//指针就是变量，用来存放地址的变0量。（存放在指针中的值都被当成地址处理）。
//在32位的机器上，地址是32个0或者1组成二进制序列，那地址就得用4个字节的空间来存储，所以一个指针变量的大小就应该是4个字节。
//如果在64位机器上，如果有64个地址线，那一个指针变量的大小是8个字节，才能存放一个地址。
//总结：指针是用来存放地址的，地址是唯一标示一块地址空间的。
//      指针的大小在32位平台是4个字节，在64位平台是8个字节。


int main()
{
	printf("%d\n", sizeof(char*));//4
	printf("%d\n", sizeof(short*));//4
	printf("%d\n", sizeof(int*));//4
	printf("%d\n", sizeof(double*));//4

	return 0;
}

int main()
{
	int a = 0x11223344;
	int* pa = &a;
	*pa = 0;
	//char* pc=&a;

	//printf("%p\n",pa);
	//printf("%p\n",pc);

	return 0;
}

int main()
{
	int a = 0x11223344;
	//int* pa = &a;
	//*pa = 0;
	char* pc=&a;
	*pc = 0;
	//printf("%p\n",pa);
	//printf("%p\n",pc);

	return 0;
}
//指针类型决定了指针进行解引用操作的时候，能够访问空间的大小
//int*p: *p能够访问4个字节
//char*p: *p能够访问1个字节
//double*p: *p能够访问8个字节

int main()
{
	int n = 0x11223344;
	char *pc = (char *)&n;
	int *pi = &n;
	*pc = 0;//重点在调试的过程中观察内存的变化。
	*pi = 0;//重点在调试的过程中观察内存的变化。
	return 0;
}

//指针+-整数
int main()
{
	int n = 10;
	char *pc = (char*)&n;
	int *pi = &n;

	printf("%p\n", &n);
	printf("%p\n", pc);
	printf("%p\n", pc+1);
	printf("%p\n", pi);
	printf("%p\n", pi+1);
	return 0;

}

int main()
{
	int a = 0x11223344;
	int* pa = &a;
	char* pc = &a;
	printf("%p\n", pa);//0095FB58
	printf("%p\n", pa+1);//0095FB5C
	printf("%p\n", pc);//0095FB58
	printf("%p\n", pc+1);//0095FB59
	return 0;

}

int main()
{
	int arr[10] = { 0 };
	int* p = arr;//数组名-首元素的地址
	int i = 0;
	for (i = 0; i < 10; i++)
	{
		*(p + i) = 1;
	}
	return 0;
	
}

int main()
{
	char *pc = NULL;
	int *pi = NULL;
	short *ps = NULL;
	long *pl = NULL;
	float *pf = NULL;
	double *pd = NULL; 
	return 0;

}

//野指针
//1.指针未初始化
int main()
{
	int *p;//局部变量指针未初始化，默认为随机值
	*p = 20;
	return 0;
}

//2.指针越界访问
int main()
{
	int arr[10] = { 0 };
	int *p = arr;
	int i = 0;
	for (i = 0; i <= 11; i++)
	{
		//当指针指向的范围超出数组arr的范围时，p就是野指针
		*(p++) = i;
	}
	return 0;
}

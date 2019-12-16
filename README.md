# HIT-Online-Judge
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
//一区间内回文素数
//n位数未知
//1.0暴力搜索  应降低时间复杂度
//2.0  除了11以外的所有位数为偶数的回文数都不是质数。能被11整除
// 3.0  不需要判断回文数，而是需要构造符合条件的回文数，然后判断其是否是素数。
int Isprime(int n);
int IsHuiwen(int n);
int getlength(int n);
int main()
{
    int a,b,i,len2,t,sum,tmp;
    scanf("%d %d",&a,&b);
    len2=getlength(b);

    if(len2%2)
        len2=(len2+1)/2;
    else
        len2=len2/2;
    t=pow(10,len2);
    for(i=a;i<t;i++)
    {
        if(i==5||i==7)printf("%d\n",i);
        else if(i==9)printf("11\n");//*10+从中间开始的数
        else for(sum=i,tmp=i/10;tmp!=0;tmp=tmp/10)
        {
            sum=sum*10+tmp%10;
        }
        if(Isprime(sum)&&sum<=b)printf("%d\n",sum);
        if(sum>b)break;
    }
    return 0;
}
int Isprime(int n)
{
    int i;
   /* for(i=2;i<=sqrt(n);i++)
    {
        if(n%i==0)return 0;算质数算法优化
    }
    return 1;*/
        if(n%2 == 0)//这题没算2，3，从5开始的if(n==2||n==3)return 1;
	    return 0;

	for(i = 3; i<= sqrt(n); i += 2)
	    if(n%i == 0)
        return 0;
	return 1;
}
/*int IsHuiwen(int n)
{
    int i,j=0,a[10];
    for(i=1;n/i!=0;i=i*10)//count 位数
    {
        a[j]=n/i%10;//各位对应数是多少
        j++;
    }
    j=j-1;
    for(i=0;i<=j;i++,j--)
    {
        if(a[i]!=a[j])return 0;
    }
    return 1;
no need
}*/
int getlength(int n)
{
    //计算位数
    int i,j=0;
    for(i=1;n/i!=0;i=i*10)//count 位数
    {

        j++;
    }
    return j;
}

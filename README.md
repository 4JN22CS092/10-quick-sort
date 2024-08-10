Quick Sort:
#include<stdio.h>
#include<stdlib.h>
#include<conio.h>
#include<time.h>
int a[100000],n;
int partition(int lower,int upper)
{
int l, i, j, t, key ;
i = lower + 1 ;
j = upper;
key = a[lower] ;
while ( j >= i )
{
while ( a[i] <=key&&i<=upper)
i++ ;
while ( a[j] > key && j>lower)
j-- ;
if ( j >= i )
{
t = a[i] ;
a[i] = a[j] ;
a[j] = t ;
}
}
t = a[lower] ;
a[lower] = a[j] ;
a[j] = t ;
return j ;
}
void quick(int low,int high)
{
int j;
if(low<high)
{
j=partition(low,high);
quick(low,j-1);
quick(j+1,high);
}
}
void main()
{
int i;
clock_t s,e;
printf("enter the size of unsorted list\n");
scanf("%d",&n);
for(i=0;i<n;i++)
{
a[i]=rand(); //avg case
//a[i]=i; //Best Case
//a[i]=n-i; //Worst case
}
printf("an unsorted list is\n");
for(i=0;i<n;i++)
{
printf("%d ",a[i]);
}
printf("\n");
s=clock();
for(i=0;i<n;i++)
quick(0,n-1);
e=clock();
printf("a sorted list is:\n");
for(i=0;i<n;i++)
{
printf("%ld ",a[i]);
}
printf("\n total time taken=%f\n",((double)(e-s))/CLOCKS_PER_SEC);
}

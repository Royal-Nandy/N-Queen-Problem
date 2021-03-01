#include <stdio.h>
#include <math.h>
int board[30],count=0;
void queen(int);
void main()
{
int i,n;
printf("Queen Implementation\n");
printf("Enter the number of Queen\n");
scanf("%d",&n);
queen(n);
printf("\n Total solutions =%d",count);
}
int placeQueen(int pos)
{
int i;
for(i=1;i<pos;i++)
{
if((board[i]==board[pos])|| ((abs(board[i]-board[pos])==abs(i-pos))))
return 0;
}
return 1;
}
void printSolution(int n)
{
int i,j;
count++;
printf("\n\nsolution [%d] :\n", count);
for(i=1;i<=n;i++)
{
for(j=1;j<=n;j++)
{
if(board[i]==j)
printf("Q\t");
else
printf("*\t");
}
printf("\n");
}
}
void queen(int n)
{
int k=1;
board[k]=0;
while(k!=0)
{
board[k]=board[k]+1;
while((board[k]<=n) && !placeQueen(k))
board[k]++;
if(board[k]<=n)
{
if(k==n)
printSolution(n);
else
{
k++;
board[k]=0;
}
}
else
k--;
}
}

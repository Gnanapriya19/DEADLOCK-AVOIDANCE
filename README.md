PROGRAM:
#include<stdio.h>
void main()
{
int pno,rno,i,j,prc,count,t,total; count=0;
clrscr();
printf("\n Enter number of process:"); scanf("%d",&pno);
printf("\n Enter number of resources:"); scanf("%d",&rno);
for(i=1;i< =pno;i++)
{
flag[i]=0;
}
printf("\n Enter total numbers of each resources:"); for(i=1;i<= rno;i++)
scanf("%d",&tres[i]);
printf("\n Enter Max resources for each process:"); for(i=1;i<= pno;i++)
{
printf("\n for process %d:",i); for(j=1;j<= rno;j++)
scanf("%d",&max[i][j]);
}
printf("\n Enter allocated resources for each process:"); for(i=1;i<= pno;i++)
{
printf("\n for process %d:",i); for(j=1;j<= rno;j++)
scanf("%d",&allocated[i][j]);
}
printf("\n available resources:\n"); for(j=1;j<= rno;j++)
{
avail[j]=0; total=0;
for(i=1;i<= pno;i++)
{
total+=allocated[i][j];
}
avail[j]=tres[j]-total; work[j]=avail[j];
printf("	%d \t",work[j]);
}
do
{
for(i=1;i<= pno;i++)
{
for(j=1;j<= rno;j++)
{
need[i][j]=max[i][j]-allocated[i][j];
}
}
printf("\n Allocated matrix	Max	need"); for(i=1;i<= pno;i++)
{
printf("\n"); for(j=1;j<= rno;j++)
{
printf("%4d",allocated[i][j]);
}
printf("|"); for(j=1;j<= rno;j++)
{
printf("%4d",max[i][j]);
}
printf("|"); for(j=1;j<= rno;j++)
{
 }
prc=0;
 
printf("%4d",need[i][j]);
}
 
for(i=1;i<= pno;i++)
{
if(flag[i]==0)
{
prc=i;
for(j=1;j<= rno;j++)
{
if(work[j]< need[i][j])
{
prc=0; break;
}
}
}
if(prc!=0) break;
}


if(prc!=0)
{
printf("\n Process %d completed",i); count++;
printf("\n Available matrix:"); for(j=1;j<= rno;j++)
{
work[j]+=allocated[prc][j]; allocated[prc][j]=0; max[prc][j]=0; flag[prc]=1;
printf("	%d",work[j]);
}
}
}while(count!=pno&&prc!=0); if(count==pno)
printf("\nThe system is in a safe state!!");
else
printf("\nThe system is in an unsafe state!!");
getch();
}


OUTPUT
Enter number of process:5 Enter number of resources:3
Enter total numbers of each resources:10 5 7 Enter Max resources for each process:
for process 1: 7 5 3
for process 2: 3 2 2
for process 3: 9 0 2
for process 4: 2 2 2
for process 5: 4 3 3
Enter allocated resources for each process: for process 1: 0 1 0
for process 2: 3 0 2
for process 3: 3 0 2
for process 4: 2 1 1
for process 5: 0 0 2
available resources:
2	3	0

Allocated matrix	Max	need

0	1	0|	7	5	3|	7	4	3
3	0	2|	3	2	2|	0	2	0
3	0	2|	9	0	2|	6	0	0
2	1	1|	2	2	2|	0	1	1
0	0	2|	4	3	3|	4	3	1
Process 2 completed
Available matrix:  5  3   2 Allocated matrix	Max	need
0	1	0|	7	5	3|	7	4	3
0	0	0|	0	0	0|	0	0	0
3	0	2|	9	0	2|	6	0	0
2	1	1|	2	2	2|	0	1	1
0	0	2|	4	3	3|	4	3	1
Process 4 completed
Available matrix:  7  4   3 Allocated matrix	Max	need
0	1	0|	7	5	3|	7	4	3
0	0	0|	0	0	0|	0	0	0
3	0	2|	9	0	2|	6	0	0
0	0	0|	0	0	0|	0	0	0
0	0	2|	4	3	3|	4	3	1
Process 1 completed
Available matrix:   7   5	3 Allocated matrix	Max	need
0	0	0|	0	0	0|	0	0	0
0	0	0|	0	0	0|	0	0	0
3	0	2|	9	0	2|	6	0	0
0   0   0|  0   0   0|  0	0  0
0   0   2|  4   3   3|  4	3  1
Process 3 completed
Available matrix:   10	5 5 Allocated matrix	Max	need
0	0	0|	0	0	0|	0	0	0
0	0	0|	0	0	0|	0	0	0
0	0	0|	0	0	0|	0	0	0
0	0	0|	0	0	0|	0	0	0
0	0	2|	4	3	3|	4	3	1
Process 5 completed
Available matrix:   10	5 7 The system is in a safe state!! 
RESULT:
Thus the program to implement the deadlock avoidance was executed
and verified.


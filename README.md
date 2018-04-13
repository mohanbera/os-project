#include<stdio.h>

int main()

{

printf(" ***************welcome to Shortest Job First Scheduling *************\n");
printf(" *********************************************************************\n");

int n,p[10];

for(int i=0;i<10;i++)
{
	p[i]=i+1;
}

int minTime,k=1,btime=0;

int bt[10],temp,at[10],wt[10],tt[10],ta=0,sum=0;

float wavg=0,tavg=0,tsum=0,wsum=0;


printf("Enter the number of processes you want in your system:\n");

scanf("%d",&n);

 

for(int i=0;i<n;i++)

{

printf("\tENTER THE BURST TIME OF %d PROCESS :",i+1);

scanf(" %d",&bt[i]);

printf("\tENTER THE ARIVAL TIME OF %d PROCESS :",i+1);

scanf(" %d",&at[i]);

}
 

for(int i=0;i<n;i++)

{

for(int j=0;j<n;j++)

{

if(at[i]<at[j])

{

temp=p[j];

p[j]=p[i];

p[i]=temp;

temp=at[j];

at[j]=at[i];

at[i]=temp;

temp=bt[j];

bt[j]=bt[i];

bt[i]=temp;

}

}

}

 /*WE HAVE TO SORT IN INCREASING ORDER BEACAUSE IT IS SHORTEST JOB FIRST SECHEDULING*/

for(int j=0;j<n;j++)

{

btime=btime+bt[j];

minTime=bt[k];

for(int i=k;i<n;i++)

{

if (btime>=at[i] && bt[i]<minTime)

{

temp=p[k];

p[k]=p[i];

p[i]=temp;

temp=at[k];

at[k]=at[i];

at[i]=temp;

temp=bt[k];

bt[k]=bt[i];

bt[i]=temp;

}

}

k++;

}

wt[0]=0;

for(int i=1;i<n;i++)

{

sum=sum+bt[i-1];

wt[i]=sum-at[i];

wsum=wsum+wt[i];

}

 

wavg=(wsum/n);

for(int i=0;i<n;i++)

{

ta=ta+bt[i];

tt[i]=ta-at[i];

tsum=tsum+tt[i];

}

 

tavg=(tsum/n);

 

printf("ooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo\n");

printf("\n \t\t\tHERE IS THE SCHEDULING:-\n");

printf("ooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo\n");

printf("\nProcess\t Burst\t Arrival\t Waiting\t Turn-around" );

printf("\nooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo\n");

for(int i=0;i<n;i++)

{

printf("\n p%d\t %d\t %d\t\t %d\t\t\t%d",p[i],bt[i],at[i],wt[i],tt[i]);

}

printf("\nooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo\n");
printf("\n\nAVERAGE WAITING TIME : %f",wavg);

printf("\nAVERAGE TURN AROUND TIME : %f",tavg);

return 0;

}
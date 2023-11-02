# OS-EX.6-IMPLEMENTATION-OF-INTER-PROCESS-COMMUNICATION-USING-PIPE

# AIM:
To implement round robin scheduling algorithm

# ALGORITHM:
The round-robin (RR) scheduling algorithm is designed especially for timesharing systems. It is similar to FCFS scheduling, but preemption is added to switch between processes. A small unit of time, called a time quantum(or time slice), is defined. The ready queue istreated as a circular queue.Process Burst Time Quantum Time = 4 ms P1 24 P2 3 P3 3

STEPS:

1.Start the process

2.Get the number of elements to be inserted

3.Get the value for burst time for individual processes

4.Get the value for time quantum

5.Make the CPU scheduler go around the ready queue allocating CPU to each processfor the time interval specified

6.Make the CPU scheduler pick the first process and set time to interrupt after quantum.And after it's expiry dispatch the process

7.If the process has burst time less than the time quantum then the process is released bythe CPU

8.If the process has burst time greater than time quantum then it is interrupted by the OSand the process is put to the tail of ready queue and the schedule selects nextprocess from head of the queue

9.Calculate the total and average waiting time and turnaround time

10.Display the results

# PROGRAM:
```
#include<stdio.h>
main()
{
int st[10],bt[10],wt[10],tat[10],n,tq; int
i,count=0,swt=0,stat=0,temp,sq=0;
float awt,atat;
printf("enter the number of processes");
scanf("%d",&n);
printf("enter the burst time of each process /n");
for(i=0;i<n;i++)
{
printf(("p%d",i+1);
scanf("%d",&bt[i]);
st[i]=bt[i];
}
printf("enter the time quantum");
scanf("%d",&tq);
while(1)
{
for(i=0,count=0;i<n;i++)
{
temp=tq;
if(st[i]==0)
{
count++;
continue;
}
if(st[i]>tq)
st[i]=st[i]-tq;
else
if(st[i]>=0)
{
temp=st[i];
st[i]=0;
}
sq=sq+temp;
tat[i]=sq;
}
if(n==count)
break;
}
for(i=0;i<n;i++)
{
wt[i]=tat[i]-bt[i];
swt=swt+wt[i];
stat=stat+tat[i];
}
awt=(float)swt/n;
atat=(float)stat/n;
printf("process no\t burst time\t waiting time\t turnaround time\n");
for(i=0;i<n;i++)
printf("%d\t\t %d\t\t %d\t\t %d\n",i+1,bt[i],wt[i],tat[i]); printf("avg
wt time=%f,avg turn around time=%f",awt,atat);
}
```

# OUTPUT:
![image](https://github.com/Thanikasreeb/OS-EX.6-IMPLEMENTATION-OF-INTER-PROCESS-COMMUNICATION-USING-PIPE/assets/119557910/52eb771d-ce1d-41ef-81f6-bbdb57be1874)

# RESULT :
Thus we got the output for the above experiment.

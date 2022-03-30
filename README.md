# FCFS-Scheduling-program-in-c
#include<stdio.h>
#include<conio.h>
#define maxsize 100
void main()
{
    /** wt=waiting time, tat=turn around time,  **/
    int Process[maxsize],BurstTime[maxsize],i,ProcessNumber,pft[maxsize],wt[maxsize],tat[maxsize],rt[maxsize],ArrivalTime=0;
    int AverageWaitingTime=0,AverageTurnAroundTime=0;

    printf("How many Process do you want : \n");
    scanf("%d",&ProcessNumber);


    for(i=0;i<ProcessNumber;i++)
    {
        printf("Enter Process %d \t:",i);
        scanf("%d",&Process[i]);
    }

    printf("\n");

    for(i=0;i<ProcessNumber;i++)
    {
        printf("Enter BurstTime of Process %d \t: ",i);
        scanf("%d",&BurstTime[i]);
    }
    pft[0]=ArrivalTime+BurstTime[0];
    for(i=0;i<ProcessNumber;i++)
    {
        wt[i]=(pft[i]-(ArrivalTime+BurstTime[i]));
        tat[i]=pft[i]-ArrivalTime;
        rt[i]=tat[i]-wt[i];
        pft[i+1]=pft[i]+BurstTime[i+1];


    }
    printf("\n Process !! BurstTime !! Arrival time !! WaitingTime !! TurnAroundTime !! ResponseTime !! ProcessFinishTime\n");
    for(i=0;i<ProcessNumber;i++)
    {
        printf("%5d %10d %13d %15d %16d %17d %18d\n",Process[i],BurstTime[i],ArrivalTime,wt[i],tat[i],rt[i],pft[i]);
    }
    for(i=0;i<ProcessNumber;i++)
    {
        AverageWaitingTime=AverageWaitingTime+wt[i];
        AverageTurnAroundTime=AverageTurnAroundTime+tat[i];
    }
    printf("Average_Waiting_Time: %d\n",AverageWaitingTime/ProcessNumber);
    printf("Average_Turn_Around_Time: %d\n", AverageTurnAroundTime/ProcessNumber);
    getch();
}

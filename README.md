# FCFS-for-different-arrival-time-unsorted-
first come first serve algorithm for different arrival times which are unsorted
#include<iostream>
using namespace std;
class block{
	public:
    int id;
	int at;
	int bt;
	int wt;
	bool visited;
};
void swap(block *xp, block *yp)
{
    block temp = *xp;
    *xp = *yp;
    *yp = temp;
}
void bubbleSort(block *arr, int n)
{
    int i, j;
    for (i = 0; i < n-1; i++)
    for (j = 0; j < n-i-1; j++)
        if (arr[j].at > arr[j+1].at)
            swap(&arr[j], &arr[j+1]);
}
void bubbleSort1(block *arr, int n)
{
    int i, j;
    for (i = 0; i < n-1; i++)
    for (j = 0; j < n-i-1; j++)
        if (arr[j].id > arr[j+1].id)
            swap(&arr[j], &arr[j+1]);
}
int main()
{
    int b;
    cin>>b;
    block *n=new block[b];
    for(int i=0;i<b;i++){
        n[i].id=i;
        cin>>n[i].at;
    }
    for(int i=0;i<b;i++){
        cin>>n[i].bt;
    }
    for(int i=0;i<b;i++){
        n[i].wt=0;
    }

    bubbleSort(n,b);
    int y=0;
    for(int i=0;i<b;i++){
        int x=0;

        for(int j=0; j<i; j++)
            n[i].wt+=n[j].bt;

        if(i>0)
            x=n[i].at-n[i-1].at-n[i-1].bt;

        if(x>0)
            y+=x;

        n[i].wt = n[i].wt - n[i].at + n[0].wt+y;
    }
    bubbleSort1(n,b);
    for(int i=0;i<b;i++)
    {
        cout<<n[i].at<<" "<<n[i].bt<<" "<<n[i].wt<<endl;
    }
return 0;
}

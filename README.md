#include <fstream>
using namespace std;
ifstream fin("colorare.in");
ofstream fout("colorare.out");

int A[101][101];
int X[101],n;
char C[5][21];

void afisare()
{
    for(int i=1;i<=n;i++)
        fout<<i<<" "<<C[X[i]]<<"\n";
    fout<<endl;
}

int valid(int k)
{
    for(int i=1;i<k;i++)
        if(A[i][k]==1 && X[i]==X[k]) return 0;
    return 1;
}

int alege(int k)
{
    for(int i=1;i<=4;i++)
        {
            X[k]=i;
            if(valid(k)) return i;
        }
    return 0;
}

void colorare()
{
    for(int i=1;i<=n;i++)
        X[i]=alege(i);
}

int main()
{
    int t1,t2;
    fin>>n;
    for(int i=1;i<=4;i++)
        fin>>C[i];
    while(fin>>t1>>t2)
    {
        A[t1][t2]=1;
        A[t2][t1]=1;
    }
    colorare();
    afisare();
    return 0;

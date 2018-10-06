# Climbing-The-Leaderboard
#include <math.h>
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <assert.h>
#include <limits.h>
#include <stdbool.h>

int main() {
    int n,i,j,t,scores_i,k;
    scanf("%i", &n);
  
    int *scores = malloc(sizeof(int) * n);
    scanf("%i",&scores[0]);
    for (scores_i = 1,k=1; k < n;k++ )
    {
       scanf("%i",&t);
       if(t !=scores[scores_i-1])
       {
           scores[scores_i]=t; //scoring only distinct scores so that index gives the rank
           scores_i++;
       }
     }
    n=scores_i;
    int m,rank;
    j=n-1;//will store last index or the last rank
    scanf("%i", &m);
    int *alice = malloc(sizeof(int) * m);
    for (int alice_i = 0; alice_i < m; alice_i++) {
       scanf("%i",&alice[alice_i]);
    }
    for(i=0;i<m;i++)
    {
        while(j>=0 && alice[i]>scores[j])
            j--;
        if(j==-1)
            rank=1;
        else if(alice[i] == scores[j])
            rank=j+1;
        else if(alice[i] < scores[j])
            rank=j+2;
        printf("%d\n",rank);
    }
    return 0;
}

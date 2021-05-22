# Christmas-tree
Random Christmas tree
#include <stdio.h>
#include <windows.h>
#include <stdlib.h>
#include <time.h>
char w[81][81];
void gotoxy(int x,int y);
void SetColor(int color);

int main(){
 int i,j,k=1,n,d,b,s=1,co,t,u,m=1;
 scanf("%d",&n);
 gotoxy((n+11)*2-2,1);
 printf("★");
 for(i=3;i<=(n+2)*2;i+=2){
  if(i==5){
   t=(n+10-k)*2;
   u=(n+10+k)*2;
  }
  for(j=(n+10-k)*2;j<=(n+10+k)*2;j+=2){
   w[j][i]='#';
  }
  k++;
 }
 k=1;
 for(i=3;i<=(n+2)*2;i+=2){
  for(j=(n+10-k)*2;j<=(n+10+k)*2;j+=2){
   gotoxy(j,i);
   printf("%c",w[j][i]);
   Sleep(10);
  }
  k++;
 }
 for(i=1;i<=4;i++){
  m++;
  gotoxy(t,1+(n+m)*2);
  printf("|");
  gotoxy(u,1+(n+m)*2);
  printf("|");
 }
 k=1;
 while(1){
  srand(time(NULL));
 for(i=3;i<=(n+2)*2;i+=2){
  for(j=(n+10-k)*2;j<=(n+10+k)*2;j+=k+2){
   b=rand()%((n+10+k)*2-(n+10-k)*2+1)+(n+10-k)*2;
   d=rand()%((n+2)*2-3+1)+3;
   co=rand()%16+1;
   SetColor(co);
   if(w[b][d]=='#'){
   w[b][d]='*';
   gotoxy(b,d);
   printf("%c",w[b][d]);
   Sleep(300);
   if(s%2==0){
   gotoxy((n+11)*2-2,1);
   printf("☆");
   }
   else{
   gotoxy((n+11)*2-2,1);
   printf("★");
   }
   Sleep(200);
   w[b][d]='#';
   gotoxy(b,d);
   printf("%c",w[b][d]);
   s++;
   }
  }
  k++;
 }
 k=1;
 }
 return 0;
}

void gotoxy(int x,int y){
 COORD Cur;
 Cur.X=x;
 Cur.Y=y;
 SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE),Cur);
}

void SetColor(int color)
{
 SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), color);
}

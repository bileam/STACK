#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#include<conio.h>
#include<stdbool.h>
#include<ctype.h>
#define MAX_STACK 3

typedef struct
{
    int top;
    char data[3][3];
}STUCK;

STUCK tumpuk;

void inisialisasi(){
tumpuk.top=-1;
}

int isfull()
{
    if(tumpuk.top==MAX_STACK -1)
    return 1;
    else
    return 0;

}

int isEmply(){
if(tumpuk.top==-1)
    return 1;
    else
    return 0;

}

void push(char d[3]){
tumpuk.top++;
strcpy(tumpuk.data[tumpuk.top],d);
}

void pop()
{
    printf("data yang di ambil = %s\n",tumpuk.data[tumpuk.top]);
    tumpuk.top--;
}

void tampil()
{
    for(int i=tumpuk.top;i>=0;i--){
        printf("data: %s\n",tumpuk.data[i]);
    }
}

void clear(){
tumpuk.top = -1;
}

int main(){//lifo
//pop data paling terakhr atau data paling atas
//push mwngirim masuk data
//top batas maksimal
//top harus -1 agar paling ujung sebelum index 0
int pilihan;
inisialisasi();
char dt[3];
do{
    printf("1.push data\n");
    printf("2.pop\n");
    printf("3.cetak\n");
    printf("4.hapus\n");
    printf("5.keluar\n");
    printf("masukan pilihan anda: ");
    scanf("%d",&pilihan);
switch(pilihan){
case 1: if(isfull()!= 1)
        {
            printf("data yang ingin di simpan = ");
            scanf("%s",&dt);
            push(dt);
        }
        else
            printf("array stack sudah penuh!\n");
        break;
case 2:if(isEmply()!=1)
        pop();
        else
            printf("data masih kosong\n");
    break;
case 3:
    if(isEmply()!=1)
        tampil();
    else
        printf("data masih kosong");
    break;
    case 4: clear();
    printf("\narray sudah kosong\n");
    break;
}
getch();
}
while(pilihan !=5);
printf("keluar dari program!!!\n");
getch();
return 0;
}

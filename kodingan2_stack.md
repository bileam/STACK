#include<stdio.h>
#include<stdlib.h>
#include<conio.h>
#include<ctype.h>
#include<string.h>

//langkah 1.menentukan top atau isi datanya untuk sementara yaitu 0;
//membuat tampungan data maxstack contoh 5.berarti cuman bisa manampung 5 data
//dan char stack. untuk nempung data yang di masukan dengan menentukan berapa banyk yang ingin di simpan dan karakternya
int top=0;
int maxstack=5;
char datastack[5][100];

int isEmply(){//jika belum mengisi data
if(top == 0){
    return 1;
}else{
return 0;
}
}

 int isfull(){//jika data sudah fuul atau sudah mencapai batas yaitu 5
 if(top >= maxstack){
    return 1;
 }else{
 return 0;
 }
 }
void displaystack(){//melihat data
int no=1;
if(isEmply()){
    printf("data masi kosong");
}else
    for(int i=top;i>0;i--){
        printf("data ke-%i:%s\n",no,datastack[i-1]);
        no++;
    }
}
void pushstack(){//menambahkan data
    char data[100];
    if(isfull()){
        printf("data telah penuh");getch();
    }else{
    printf("masukan data: ");
    scanf(" %[^\n]",&data);
    strcpy(datastack[top],data);
    top++;
    printf("\ndata telah berhasil di simpan!");
}
}
void popstack(){//menghapus data
if(isfull()){
        printf("data telah penuh");
    }else{
    strcpy(datastack[top-1],"");
    top--;
    printf("data ke yang terakhir di masukan telah di hapus\n");
}
}
void peekstack(){//lihat data berdasarkan posisi
 int posisi,index;
    if(isEmply()){
        printf("data kosong");

    }else{
        displaystack();
        printf("masukan posisi data: ");scanf("%d",&posisi);
        if(posisi>top){
        printf("posisi tidak ada");
            }else{
                index=top;
                for(int i=0;i<posisi;i++){
                index--;
            }
            printf("posisi ke-%d adalah di orang yang ke-%d ",posisi,index+1);
        }

    }

}

void changestack(){
int posisi,index;
char data_pengganti[100];
    if(isEmply()){
    printf("data kaosong");
    }else{
        displaystack();
        printf("masukan posisi yang ingin di ganti: ");scanf("%d",&posisi);
        printf("masukan nama data pengganti: ");scanf(" %[^\n]",&data_pengganti);
        if(posisi>top){
                printf("posisi melampaui batas\n");
        }else{
            index=top;
        for(int i=0;i<posisi;i++){
            index--;
        }
        strcpy(datastack[index],data_pengganti);
        printf("posisi ke %d adalah %s\n",posisi,datastack[index]);
        }
    }

}

void coundstack(){
  if(top==0){
    printf("tidak ada data");
  }else{
printf("jumlah data yang telah di isi yaitu %d",top);
}
}
void destorystack(){
if(isEmply()){
    printf("data masi kosong");
}else{
    for(int i=top;i>0;i--){
 strcpy(datastack[i-1],"");
 top--;
}
}
printf("data berhasil di hapus");
}
int main(){
int pilihan;
do{
        system("cls");
    printf("MENU STACK\n");
    printf("==============\n");
    printf("1.lihat data(display stack)\n");
    printf("2.tambahkan data(push stack)\n");
    printf("3.hapus data(pop stack)\n");
    printf("4.lihat data berdasarkan posisi(peek stack)\n");
    printf("5.ubah data(change stack)\n");
    printf("6.menghitung data(cound stack)\n");
    printf("7.reset data(destory stack)\n");
    printf("8.exit\n");
    printf("masukan pilihan anda: ");scanf("%d",&pilihan);
    switch(pilihan){
    case 1 : system("cls");displaystack();getch();break;//melihat data
    case 2 : system("cls");pushstack();getch();break;//menambahkan data
    case 3 : system("cls");popstack();getch();break;//
    case 4 : system("cls");peekstack();getch();break;
    case 5 : system("cls");changestack();getch();break;
    case 6 : system("cls");coundstack();getch();break;
    case 7 : system("cls");destorystack();getch();break;
    case 8 : exit(EXIT_SUCCESS);break;
    default : printf("pilihan salah\n");
    }
}while(pilihan!=8);

}

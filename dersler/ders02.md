## Makro tanımlama

```C
#define PI 3.14
int main(){

    double r=10, alan;
    alan=r*r*PI;    

}
 ``` 


```C
#define X_15_pos 30
#define X_15_0 1<<X_15_pos
#define X_15_1 2<<X_15_pos

#define X_14_pos 28
#define X_14_0 1<<X_14_pos
#define X_14_1 2<<X_14_pos


int main(){

    // X'le ilgili gerekli tanımlamalar yapıldıktan sonra
    // aşağıdaki gibi bir kullanım yapılabilir.
    // X = X | X_15_0;    
}
 ``` 

## İşaretçiler

```C
int main(){
    
    int a, b, *p1, *p2;
    a=10;
    b=20;
    p1 = &a;
    p2 = &b;
    
    *p1 = *p1 + 2; 
    *p2 = *p2 + 4;

    p2 = &a;
    
    *p1 = *p1 + 2; 
    *p2 = *p2 + 4;
    
    
}
 ``` 


## Tür dönüşümü
```C
int main(){
    
    double a=10.3;
    double tam, ondalik;
    
    tam = (int)a;
    ondalik = a-tam;
    
}
 ``` 

Sayısal bir değerin işaretçi türüne dönüşümü:
```C
#define GPIOB_MODER

int main(){
    
    int adres_verisi;
    adres_verisi = *((int*)0x40020400);
        
}
 ``` 


Tür dönüşümü, işaretçi ve makronun birlikte kullanılması:
```C
#define GPIOB_MODER (*((int*)0x40020400))

int main(){
    
    int adres_verisi;    
    adres_verisi = GPIOB_MODER;
        
}
 ``` 
## Tür tanımlama

```C
typedef unsigned char BOOL;

int main(){
    
    BOOL x;
    x=1;
    x=0;
        
}
 ```


## Yapılar

```C
#include <string.h>
struct calisan{
  char isim[50];
    int sicil;
    float maas;
};

int main(){

    struct calisan calisan1;
    strcpy(calisan1.isim, "isim soyisim");
    calisan1.maas=6571.7;
    calisan1.sicil=1254;

}
 ``` 

Yapı türü tanımlama

```C
#include <string.h>

struct calisan{
  char isim[50];
    int sicil;
    float maas;
};

typedef struct {
  char isim[50];
    int sicil;
    float maas;
}calisan_x;

int main(){

    struct calisan calisan1;
    calisan_x calisan2;
    
    strcpy(calisan1.isim, "isim soyisim");
    calisan1.maas=6571.7;
    calisan1.sicil=1254;
    
    strcpy(calisan2.isim, "isim2 soyisim2");
    calisan2.maas=7571.7;
    calisan2.sicil=2254;
    
}
 ``` 


## yapı türü işaretçisi
```C
#include <string.h>

typedef struct {
    char isim[50];
    int sicil;
    float maas;
}calisan;

int main(){

    calisan calisan1, *p;
    
    strcpy(calisan1.isim, "isim soyisim");
    calisan1.maas=6571.7;
    calisan1.sicil=1254;
    
    p=&calisan1;

    (*p).maas=7500.1;
    (*p).sicil=1255;

    //veya işaretçi için ok operatörü kullanılabilir.
    
    p->maas=7900.1;
    p->sicil=1300;
    
}
 ``` 

## Yapı türü işaretçisi ve tür dönüşümü ile belleğe ulaşma.

```C #include <string.h>
typedef struct {
    int X;
    int Y;
    int Z;
} XYZ;

int main(){
    
    XYZ *p;
    p=(XYZ*)0x40020C00;
    p->X=10;
    p->Y=20;
    p->Z=30;

}
 ``` 


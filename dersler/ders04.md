```C 
#define RCC_AHB1ENR (*((volatile unsigned int*)0x40023830))

#define GPIOD_MODER (*((volatile unsigned int*)0x40020C00))
#define GPIOD_ODR (*((volatile unsigned int*)0x40020C14))
	
#define GPIOA_MODER (*((volatile unsigned int*)0x40020000))
#define GPIOA_IDR (*((volatile unsigned int*)0x40020010))

int main(){
	volatile int i;
	RCC_AHB1ENR |= (1U<<3) | (1U<<0);
	GPIOA_MODER &= ~((1U<<1) | (1U<<0));
	
	GPIOD_MODER = (GPIOD_MODER & ~(1U<<27));
	GPIOD_MODER = (GPIOD_MODER | (1U<<26));
	
	while(1){
		
		if(GPIOA_IDR & (1<<0) ){
			GPIOD_ODR |= 1U<<13;
			for(i=0;i<1000000;i++);
			GPIOD_ODR &= ~(1U<<13);
			for(i=0;i<1000000;i++);
		}	
	}
}
``` 



```C 
 #define RCC_AHB1ENR (*((volatile unsigned int*)0x40023830))
	
typedef struct{
	unsigned volatile int MODER;
	unsigned volatile int OTYPER;
	unsigned volatile int OSPEEDR;
	unsigned volatile int PUPDR;
	unsigned volatile int IDR ;
	unsigned volatile int ODR; 
} GPIO_TypeDef;
#define GPIOD ((GPIO_TypeDef*)0x40020C00)

int main(){
	volatile int i;
	RCC_AHB1ENR |= (1U<<3) ;
	
	GPIOD->MODER |= 1U<<26;
	
	while(1){
		GPIOD->ODR |= 1U<<13;
		for(i=0;i<1000000;i++);
		
		GPIOD->ODR &= ~(1U<<13);
		for(i=0;i<1000000;i++);
	}
}
``` 


```C 
 #define RCC_AHB1ENR (*((volatile unsigned int*)0x40023830))
	
typedef struct{
	unsigned volatile int MODER;
	unsigned volatile int OTYPER;
	unsigned volatile int OSPEEDR;
	unsigned volatile int PUPDR;
	unsigned volatile int IDR ;
	unsigned volatile int ODR; 
} GPIO_TypeDef;
#define GPIOD ((GPIO_TypeDef*)0x40020C00)

int main(){
	volatile int i;
	RCC_AHB1ENR |= (1U<<3) ;
	
	GPIOD->MODER |= 1U<<30 | 1U<<28 | 1U<<26 | 1U<<24;
		
	while(1){
		GPIOD->ODR |= 1U<<15 | 1U<<14 | 1U<<13 | 1U<<12;
		for(i=0;i<1000000;i++);
		
		GPIOD->ODR &= ~(1U<<15 | 1U<<14 | 1U<<13 | 1U<<12);
		for(i=0;i<1000000;i++);
	}
}
``` 



```C 
 #include "stm32f4xx.h"                  // Device header

int main(){
	volatile int i;
	RCC->AHB1ENR |= 1<<3;
	
	GPIOD->MODER |= 1<<24;
	
	while(1){
		GPIOD->ODR |= 1<<12;
		for(i=0;i<1000000;i++);
		GPIOD->ODR &= ~(1U<<12);	
		for(i=0;i<1000000;i++);
	}
}
``` 
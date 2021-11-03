```C
#include "stm32f4xx.h"

int main(){
	volatile int i;
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIODEN;
	
	GPIOD->MODER |= GPIO_MODER_MODER14_0;
	
	while(1){
			GPIOD->ODR |= GPIO_ODR_OD14;
			for(i=0;i<1000000;i++);	
			GPIOD->ODR &= ~GPIO_ODR_OD14;
			for(i=0;i<1000000;i++);
	}
}

```


```C
#include "stm32f4xx.h"

int main(){
	volatile int i;
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIODEN;
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIOAEN;
	
	GPIOD->MODER |= GPIO_MODER_MODER14_0;
	
	while(1){
		if(GPIOA->IDR & GPIO_IDR_ID0){
			GPIOD->ODR |= GPIO_ODR_OD14;
			for(i=0;i<1000000;i++);	
			GPIOD->ODR &= ~GPIO_ODR_OD14;
			for(i=0;i<1000000;i++);
		}
	}
}

```
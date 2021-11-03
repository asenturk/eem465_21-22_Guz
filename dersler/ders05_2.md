```C
#include "stm32f4xx.h"
int main(){
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIODEN;
	GPIOD->MODER |= GPIO_MODER_MODER14_0;
	
	SysTick->LOAD = 2000000;
	SysTick->CTRL |= SysTick_CTRL_ENABLE_Msk;
	
	while(1){
		
			GPIOD->ODR |= GPIO_ODR_OD14;	
			while(!(SysTick->CTRL & SysTick_CTRL_COUNTFLAG_Msk));

			GPIOD->ODR &= ~GPIO_ODR_OD14;
			while(!(SysTick->CTRL & SysTick_CTRL_COUNTFLAG_Msk));
		
	}
}

```


```C
#include "stm32f4xx.h"
int main(){

	RCC->AHB1ENR |= RCC_AHB1ENR_GPIODEN;
	GPIOD->MODER |= GPIO_MODER_MODER14_0;
	
	SysTick->LOAD = 2000000;
	SysTick->CTRL |= SysTick_CTRL_CLKSOURCE_Msk;
	SysTick->CTRL |= SysTick_CTRL_ENABLE_Msk;
	while(1){
		
			GPIOD->ODR |= GPIO_ODR_OD14;
			while(!(SysTick->CTRL & SysTick_CTRL_COUNTFLAG_Msk));
            
			GPIOD->ODR &= ~GPIO_ODR_OD14;
			while(!(SysTick->CTRL & SysTick_CTRL_COUNTFLAG_Msk));
		
	}
}

```
```C
#include "stm32f4xx.h"

int main(){
	RCC->CR |= RCC_CR_HSEON;
	while(!(RCC->CR & RCC_CR_HSEON));
	RCC->CFGR |= RCC_CFGR_SW_0;
	
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIOCEN;
	GPIOC->MODER |= GPIO_MODER_MODER13_0;
	
	SysTick->CTRL |= SysTick_CTRL_CLKSOURCE_Msk;
	SysTick->LOAD = 16 * 5 * 1000; // 5ms gecikme
	SysTick->CTRL |= SysTick_CTRL_ENABLE_Msk;
	
	while(1){
		GPIOC->ODR |= GPIO_ODR_OD13;
		while(!(SysTick->CTRL & SysTick_CTRL_COUNTFLAG_Msk));
		
		GPIOC->ODR &= ~GPIO_ODR_OD13;
		while(!(SysTick->CTRL & SysTick_CTRL_COUNTFLAG_Msk));
	}
}
```
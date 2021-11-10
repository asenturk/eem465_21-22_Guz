```c
#include "stm32f4xx.h"                  // Device header

static volatile unsigned int sayac=0;

void EXTI0_IRQHandler(void);
void EXTI0_IRQHandler(){
	EXTI->PR |= EXTI_PR_PR0;
	sayac++;
	GPIOD->ODR &= ~(0xF << 12);
	GPIOD->ODR |= (sayac & 0xF) << 12;
}

int main(){
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIOAEN;
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIODEN;
	
	GPIOD->MODER |= GPIO_MODER_MODER12_0;
	GPIOD->MODER |= GPIO_MODER_MODER13_0;
	GPIOD->MODER |= GPIO_MODER_MODER14_0;
	GPIOD->MODER |= GPIO_MODER_MODER15_0;
	
	EXTI->IMR |= EXTI_IMR_MR0;
	EXTI->RTSR |= EXTI_RTSR_TR0;
	
	NVIC_EnableIRQ(EXTI0_IRQn);
	
	while(1){}
	
}
```
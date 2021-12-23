```C
#include "stm32f4xx.h" 

static volatile double voltaj;

int main(){
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIOAEN;
	GPIOA->MODER |= GPIO_MODER_MODER0;
	
	RCC->APB2ENR|= RCC_APB2ENR_ADC1EN;
	
	ADC1->CR2 |= ADC_CR2_ADON;
	
	ADC1->CR2 |=  ADC_CR2_CONT;
    
	ADC1->SMPR2 |= ADC_SMPR2_SMP0;
	
	ADC1->CR2 |= ADC_CR2_SWSTART;
	
	while(1){
	    while(!(ADC1->SR & ADC_SR_EOC));
	    voltaj=(ADC1->DR/4095.0)*3.3;
	}
}
```

```C
#include "stm32f4xx.h"  
static volatile double voltaj[2];
static volatile int i=0;
int main(){
	RCC->AHB1ENR |= RCC_AHB1ENR_GPIOAEN;
	GPIOA->MODER |= GPIO_MODER_MODER0;
	GPIOA->MODER |= GPIO_MODER_MODER1;
	
	RCC->APB2ENR|= RCC_APB2ENR_ADC1EN;
	
	ADC->CCR |= ADC_CCR_ADCPRE;
	
    ADC1->CR2 |= ADC_CR2_ADON;
	
    ADC1->CR1 |= ADC_CR1_SCAN;
	ADC1->CR2 |= ADC_CR2_EOCS;
	
	ADC1->CR2 |=  ADC_CR2_CONT;
	
    ADC1->SMPR2 |= ADC_SMPR2_SMP0;
	ADC1->SMPR2 |= ADC_SMPR2_SMP1;
	
    ADC1->SQR1 |= ADC_SQR1_L_0;
	ADC1->SQR3 |= ADC_SQR3_SQ2_0;
	
	ADC1->CR2 |= ADC_CR2_SWSTART;
	
	while(1){
	    while(!(ADC1->SR & ADC_SR_EOC));
	    voltaj[i%2]=(ADC1->DR/4095.0)*3.3;
		i++;
	}
}
```
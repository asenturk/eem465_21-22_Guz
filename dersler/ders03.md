
```C 
int main(){

	int *RCC_AHB1ENR;
	int *GPIOD_MODER;
	int *GPIOD_ODR;
	int i;
	
	RCC_AHB1ENR = (int*)0x40023830;
	*RCC_AHB1ENR = *RCC_AHB1ENR | (1<<3);
	
	GPIOD_MODER = (int*)0x40020C00;
	*GPIOD_MODER = *GPIOD_MODER | (1<<30);
	
	GPIOD_ODR = (int*)0x40020C14;
	while(1){
		*GPIOD_ODR = *GPIOD_ODR | (1<<15);
		for(i=0;i<1000000;i++);
		*GPIOD_ODR = *GPIOD_ODR & ~(1<<15);
		for(i=0;i<1000000;i++);
	}
}

```

```C 
int main(){

	volatile unsigned int RCC_AHB1ENR_adresi=0x40023830;
	volatile unsigned int GPIOD_MODER_adresi=0x40020C00;
	volatile unsigned int GPIOD_ODR_adresi=0x40020C14;
	
	volatile unsigned int *RCC_AHB1ENR, *GPIOD_MODER, *GPIOD_ODR;
	volatile int i;
	
	RCC_AHB1ENR = (volatile unsigned int*)RCC_AHB1ENR_adresi;
	*RCC_AHB1ENR = *RCC_AHB1ENR | (1<<3);
	
	GPIOD_MODER = (volatile unsigned int*)GPIOD_MODER_adresi;
	*GPIOD_MODER = *GPIOD_MODER | (1<<30);
	
	GPIOD_ODR = (volatile unsigned int*)GPIOD_ODR_adresi;
	while(1){
		*GPIOD_ODR = *GPIOD_ODR | (1<<15);
		for(i=0;i<1000000;i++);
		*GPIOD_ODR = *GPIOD_ODR & ~(1<<15);
		for(i=0;i<1000000;i++);
	}
}

```






```C 
#define RCC_AHB1ENR (*((volatile unsigned int*)0x40023830))
#define GPIOD_MODER (*((volatile unsigned int*)0x40020C00))
#define GPIOD_ODR (*((volatile unsigned int*)0x40020C14))
int main(){

	volatile int i;
	RCC_AHB1ENR = RCC_AHB1ENR | (1<<3);
	GPIOD_MODER = GPIOD_MODER | (1<<30);
	while(1){
		GPIOD_ODR = GPIOD_ODR | (1<<15);
		for(i=0;i<1000000;i++);
		GPIOD_ODR = GPIOD_ODR & ~(1<<15);
		for(i=0;i<1000000;i++);
	}
}

```



```C 
#define RCC_AHB1ENR (*((volatile unsigned int*)0x40023830))
#define GPIOD_MODER (*((volatile unsigned int*)0x40020C00))
#define GPIOD_ODR (*((volatile unsigned int*)0x40020C14))
int main(){

	volatile int i;
	RCC_AHB1ENR = RCC_AHB1ENR | (1<<3);
	GPIOD_MODER = GPIOD_MODER | (1<<28);
	while(1){
		GPIOD_ODR = GPIOD_ODR | (1<<14);
		for(i=0;i<1000000;i++);
		GPIOD_ODR = GPIOD_ODR & ~(1<<14);
		for(i=0;i<1000000;i++);
	}
}

```



```C 
#define RCC_AHB1ENR (*((volatile unsigned int*)0x40023830))
#define GPIOD_MODER (*((volatile unsigned int*)0x40020C00))
#define GPIOD_ODR (*((volatile unsigned int*)0x40020C14))
int main(){

	volatile int i;
	RCC_AHB1ENR = RCC_AHB1ENR | (1<<3);
	GPIOD_MODER = GPIOD_MODER | (1<<30);
	GPIOD_MODER = GPIOD_MODER | (1<<28);
	while(1){
		GPIOD_ODR = GPIOD_ODR | (1<<14);
		GPIOD_ODR = GPIOD_ODR | (1<<15);
		for(i=0;i<1000000;i++);
		GPIOD_ODR = GPIOD_ODR & ~(1<<14);
		GPIOD_ODR = GPIOD_ODR & ~(1<<15);
		for(i=0;i<1000000;i++);
	}
}

```



```C 
#define RCC_AHB1ENR (*((volatile unsigned int*)0x40023830))
#define GPIOD_MODER (*((volatile unsigned int*)0x40020C00))
#define GPIOD_ODR (*((volatile unsigned int*)0x40020C14))
int main(){

	volatile int i;
	RCC_AHB1ENR = RCC_AHB1ENR | (1<<3);
	GPIOD_MODER = GPIOD_MODER | (1<<30 | 1<<28);

	while(1){
		GPIOD_ODR = GPIOD_ODR | (1<<15 | 1<<14);

		for(i=0;i<1000000;i++);
		GPIOD_ODR = GPIOD_ODR & ~(1<<15 | 1<<14);
		
		for(i=0;i<1000000;i++);
	}
}

```



```C 
#define RCC_AHB1ENR (*((volatile unsigned int*)0x40023830))
#define GPIOD_MODER (*((volatile unsigned int*)0x40020C00))
#define GPIOD_ODR (*((volatile unsigned int*)0x40020C14))
int main(){

	volatile int i;
	RCC_AHB1ENR = RCC_AHB1ENR | (1<<3);
	GPIOD_MODER = GPIOD_MODER | 0x55U << 24;

	while(1){
		GPIOD_ODR = GPIOD_ODR | 0xFU<<12;

		for(i=0;i<1000000;i++);
		GPIOD_ODR = GPIOD_ODR & ~(0xFU <<12);
		
		for(i=0;i<1000000;i++);
	}
}

```


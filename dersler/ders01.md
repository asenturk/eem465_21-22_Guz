```C
int main(){
	int i;
	i=1;
	i=10;
	i=0x7FFFFFFF;
	i=i+1;
	
}

```



```C
int main(){
	unsigned int i;
	i=1;
	i=10;
	i=0x7FFFFFFF;
	i=i+1;	
}

```








```C
int main(){
	int i;
	i=10;
	i=i<<1;
	i=i<<3;
	i=21;
	i=i>>1;
	i=i>>2;	
}

```

```C
int main(){
	unsigned int i;
	i=1;
	i=i<<31;
	i=i>>10;
}

```

```C
int main(){
	unsigned int a,b,c;
	a=0x3C;
	b=0x5A;
	c= a&b;
	c= a|b;
	c= a^b;
	c= ~a;
}

```

```C
int main(){
	unsigned int a,b,c;
	a=0x3C;
	b=0x5A;
	
	c= a&b;
	c= a|b;
	c= a^b;
	c= ~a;
}

```


```C
int main(){
	unsigned int a;
	a=981;

	a= a | (1<<5) ;
	a= a &  ~(1<<6) ;
	a= a ^ (1<<8)  ;
}
```

- Test için 

```C
if(a & (1 << n)){

}
```

- Bekleme için

```C
while(!(a & (1 << n)));
```
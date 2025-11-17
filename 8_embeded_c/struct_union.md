# Struct,Union,bit-field

# **고정길이 정수(Fixed-width integer)**

>  stdint.h 사용방법을 알아본다. 


<details><summary> 사용이유 </summary>

### 왜 고정된 메모리크기를 가진 정수를 사용하는가?

## 레지스터 조작

> 하드웨어의 레지스터, 특히 특수기능 레지스터는 정확한 사이즈가 정해져있으면서 동시에 해당하는 비트마다 특수한 기능하도록 설계되어있다. 
> 레지스터의 값을 정확하고 안전하게
> 읽고 쓰기위해서는 정확한 사이즈의 자료형을 사용할 필요가 있다.


## 이식성,통신 프로토콜

> 어떤 개발환경에서 개발된 시스템이여도 사이즈를 보장 받을 수 있다는 것은
> 의도된 동작이 어느 시스템에서도 작동함을 의미한다. 이는 정확한 구조를 요구하는
> 통신 프로토콜을 다루는데 있어서 필수이다. 
    


</details><br>


<details><summary> 사용 </summary>

### 키워드

| **type** | **SIZE** | **특징**|
| ---| --- | --- |
| `int8_t` |  1byte | char , -128 ~ 127 |
|  `int16_t`| 2byte  | short,  -655536 ~ 655535 |
|  `int32_t` | 4byte | int,  -약 21억 ~ 약 21억 |
|  `int64_t` | 8byte   | long long,  -약 922경 ~ 약 922경 |
|  `uint8_t` | 1byte  | unsinged char,  0 ~ 255 |
| `uint16_t` | 2byte  | unsinged short,  0 ~ 131072 |
|  `uint32_t`  |  4byte   | unsinged int, 0 ~ 약 42억 |
|  `uint64_t`  | 8byte   | unsinged long long, 0 ~ 약 1844경 |


### 의미 

- **u** : unsigned
- **int** : 정수 자료형
- **t** : type= 자료형임을 표시

### 사용예제

```C
#include<stdint.h>

int main(){

int32_t int32 = 0X7FFFFFFF; 
uint16_t uint16 = 0XFFFF;
uint8_t[3] ={ 0b11111111, 0b11111111, 0b11111111 };

}

```

</details><br>

<details><summary> 다른자료형? </summary>

### 소수
> IEEE 754 표준으로 부동소수를 표현하기 때문에 고정길이에 대한 고려를 하지 않는다.
> - float = 4byte
> - double = 8byte

### char

> C언어 표준으로 항상 1byte로 정의되며 아스키코드를 저장 가능한 1byte는
>  이미 int8_t,uint8_t로도 사용이 가능하기 때문에 따로 고려되지 않는다.

### bool

> false,true의 1bit로 표현이 가능한 값으로 `stdbool.h`에서 제공


</details><br>

# STRUCT
> 구조체 메모리 할당,활용법을 학습한다.

<details><summary> struct사용 </summary>


> 자료형의 집합으로 구조체를 한다.<br>
> 임베디드 개발에서는는 union과 함께 byte단위의 조작,파싱을 하기위해서많이 사용된다. 

```c
struct data{
    int first;
    int second; 

};

int main(){
   struct data A = {1,2};
   struct data B;
   B.first = 1;
   B.second = 2;
}
```

<br>

> 대부분 `typedef`을 사용하여 짧게 나타낸다.
```c
typedef struct data{
    int first;
    int second; 

}data;

int main(){
   data A = {1,2};
   data B;
   B.first = 1;
   B.second = 2;
}
```

<br>

> 구조체 내부에 구조체를 삽입가능하다.

```c
typedef struct data{
    int first;
    int second;

    struct{
        int first;
        int second;
    }inner_struct;

}data;

int main(){
   data A = {1,2,{3,4}};
   
}

```


</details><br>


<details><summary> 메모리 </summary>

## padding

> 구조체에서 맴버에 메모리를 할당 할 때 빠른접근을 위해 word단위로 데이터를 띄워서 저장한다.<br>
> 즉, int, char의 조합으로 5byte( 4 + 1 )이 필요하지만<br>
> 실제로는 4바이트 단위가 cpu에서 접근이 용이하기 때문에 8byte( 4 + 4 )의 메모리를 사용한다.
> 이것을 `padding`이라고 한다.


```c
typedef struct data{
    char first;
    int second;
}data;

int main(){
   data A;
   printf("%p,%p"&A.first,&A.second); // ~~~0, ~~~4;
}

```

## #pragma pack
> padding이 존재해 주소(바이트)단위 접근시 매번 계산하기 번거롭다. <br>
> `#pargama pack(1)`을 사용해 메모리를 그대로 자료형의 크기만큼만 할당하기 위해 패딩을 없앤다.<br>
> 컴파일러마다 패딩 유무의 명령어가 다르지만 #pargma pack은 공용으로 사용이 가능하다.
```c

#pragma pack(1) //  패딩을 없애는 명령어
typedef struct data{
    char first;
    int second;
}data_no_padding;

#pragma pack(4)// 패딩을 사용하는 명령어 - 기본설
typedef struct data{
    int first;
    int second;
}data_padding;

int main(){
   data_no_padding A;
   printf("%p,%p"&A.first,&A.second); // ~~~0, ~~~1;

   data_padding B;
   printf("%p,%p"&B.first,&B.second); // ~~~8, ~~~C;
}

```

</details><br>


# union
> 데이터(byte)단위 파싱에 유용한 union을 학습한다.

<details><summary> union사용 </summary>

## 사용이유

> 메모리에 저장된 값은 어떤 자료형으로 사용되는지에 따라 <br>
> 그 활용이 바뀔 수 있다.

```c
  void *ptr;
  ptr = (char*)malloc(sizeof(char));
  *((char*)ptr) = 65; 
  printf("%d %c", *((char*)ptr), *((char*)ptr));
``` 
void타입의 ptr을 %d, %c사용에 따라서 그 의미가 바뀐다. <br>
메모리공간의 값을 두 가지 이상의 형태로 구분해서 보고싶은경우 `union`이 유용하다.


## 문법

> union의 변수들은 각 시작주소가 모두 같다! <br>
> 차지하는 메모리는 사이즈가 가장 큰 맴버를 기준으로 한다.

```c
typedef union{
    int x;
    char y;
}val;

val A;
A.x =0x44434241; 
printf("%c",A.y); // 'A'
```

`리틀 엔디안`방식으로 저장 되어  <br>
       
A.x 는  0x41 | 0x42 | 0x43 | 0x44 <br>
A.y 는  0x41 <br>
위와 같이 저장되어 0x41을 동시에 사용하게된다.




</details><br>


<details><summary> 활용 </summary>

## byte단위의 파싱


```c
//기본적인 파싱 활용법
typedef union{
    int x;
    char y[4];
}val

val a;
a.X = 0x44434241;

printf("%c,%c,%c,%c",y[0],y[1],y[2],y[3]); // A,B,C,D

``` 


## 구조체맴버

> union에 맴버로 구조체또한 선언이 가능하다.

```c
typedef union{
    int x[4];
    struct{
        char a[4];
        char b[4];
        char c[4];
        char d[4];
    }b;

}val;

val A;
A.x[0] = 0X44434241;
printf("%c,%c,%c,%c",A.b.a[0], A.b.a[1],A.b.a[2],A.b.a[3]); // A,B,C,D
```
**배열인덱스,변수는 순서와 리틀엔디안 순서를 혼동하지 않도록 한다.**



</details><br>

# bitfiled
> byte단위에서 bit단위로 다루는 방법을 학습한다.



<details><summary> 사용방법 </summary>

## 문법
> 기본적으로 구조체나 유니온에서 사용되며 특정 자료형의 n비트만 사용하는 형식이다.

```c
#include<stdint.h>
#pragma pack(1)
typedef struct{
    uint8_t X : 2;
    uint8_t Y : 4;
    uint8_t Z : 2;
}val;

val A;
A.X = 0b01;
A.Y = 0b1010;
A.Z = 0b11;
printf("%d,%d,%d\n",A.X,A.Y,A.Z); // 1,6,3
printf("%x",*((uind_8t*)&A));// ZXY -> 11 1010 01   = 233
```
`#pragma pack(1)`을 사용하여 패딩을 제거했음으로 <br>
위 구조체는 정확히 8bit=1byte만큼을 사용한다.<br>
비트는 상위에 있는 변수가 `lsb`가 된다

## 활용

>union과 구조체를 통해서 미리 필요한 비트단위를 포맷을 정한다.

```C
#include <stdint.h>
#pragma pack(1)

typedef union{
    uint8_t original_data;

    struct{
        uint8_t LSB : 1;
        uint8_t DATA_A : 3;
        uint8_t DATA_B : 3;
        uint8_t MSB : 1;
    }field;

}PASING

uint8_t input_data = 210;

PASING pasing_data  ={ .original_data = input_data};
```

위와 같이 pasing_data에 input_data를 할당하여 필요에 따라<br>
`pasing_data.field.MSB`와 같은 형태로 바로 사용이 가능하다.



</details><br>
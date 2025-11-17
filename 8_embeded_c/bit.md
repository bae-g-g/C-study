# **진수표현,변환방법학습**

# 진수표현


<details><summary> 사용,표현방법</summary>

## 포맷

> 각각 2진수,16진수로 10으로 초기화 한다.
```다
int B = 0b1010;
int X = 0xA;
```
<br>
<br>

> 16진수 출력을 나타낸다. (2진수는 별도의 출력 포맷이 없다.)

```C
printf("%x",X);
```






</details><br>


#  진수변환


<details><summary> api </summary>

## 문자열 -> 정수

### long strtol(char const* str, char** endptr, int base)

> 문자열 형태의 N진수를 숫자로 변환 <stdlib.h> 내장함수 <br>
> long type의 변환값을 리턴, 실패시 0반환 <br>
> string - to - long

```C
char str16[10] = "0XA";
char str2[10] = "0B1010";

int num16 = strtol(str16,NULL,16); 
int num2 = strtol(str2,NULL,2);
```

## 정수 -> 문자열


### int sprintf(char* str, const char* format,...)

>문자열에 지정한 형식으로 저장한다. <br>
> 문자열에 저장 성공시 byte수, 실패시 0 반환 <br>
> 마지막에 '\0'자동 저장 <br수
> 진수 변환뿐 아니라 파싱에 자주사용하는 편리한 api <br>


```
char buf[100];
int num = 10;

sprintf(buf,"%X",num);

printf("%s",buf); // 출력 : A;

```



## 정수 -> 문자열


### int sprintf(char* str, const char* format,...)

>문자열에 지정한 형식으로 저장한다. <br>
> 문자열에 저장 성공시 byte수, 실패시 0 반환 <br>
> 마지막에 '\0'자동 저장 <br수
> 진수 변환뿐 아니라 파싱에 자주사용하는 편리한 api <br>


```
char buf[100];
int num = 10;

sprintf(buf,"%X",num);

printf("%s",buf); // 출력 : A;

```




</details><br>


#  비트연산


<details><summary>set,clear,togle </summary>

> 특정 비트를 1,0으로 변경한다.
> ex) N번 비트를 1,0으로 변경


```C
// N비트를 0으로 변경
int A = 0b01010101;
int N = 4;

A = A & ~(1<<N);

/*
  0101 0101
  1110 1111
&
-----------
  0100 0101

*/
```

```C
// N비트를 1으로 변경
int A = 0b01010101;
int N = 3;

A = A | (1<<N);

/*
  0101 0101
  0000 1000
|
-----------
  0101 1101

*/
```

```C
// N비트를 토글
int A = 0b01010101;
int N = 3;

A = A ^ (1<<N);

/*
  0101 0101
  0000 1000
^
-----------
  0101 1101

*/
```




</details><br>


<details><summary> 추출 </summary>

> 특정 비트를 추출한다.
> ex) N번 비트의 값 추출


```C
// N비트의 값 추출
int A = 0b01010101;
int N = 4;

int ans =  1 & (A>>4); 
/*

A >>4
0000 0101

  0000 0101
& 0000 0001
-----------
  0000 0001

*/
```

</details><br>
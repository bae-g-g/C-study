# [CH07L] Function (Lecture)

## **C Language Learning Road Map**

> 데이터 형식 종류 ➝ 데이터 입력/출력 방식/원리 ➝ 다양한 처리과정

![](https://t9003081320.p.clickup-attachments.com/t9003081320/9ffdfbf7-497a-4a5e-ac73-07ec85a51eea/Picture1.png)

# **Function 함수**

컴퓨터가 해당언어(C Language)로 자료(Data)를 처리하는 방식

main function, custom function/user defined funciton

입력값에 따라 처리 후 결과값을 만들어내는 재사용이 가능한 Code
Code: \[입력값 → 처리 → 결과값\] → 재사용

## **Form 형식**

반환 자료형 ① + 함수이름 ② + (매개변수) ③
{ 함수 시작
Code Blocks ④
return + 반환값(정수/소수/문자/변수); ⑤
} 함수 끝
※ Function Header: 반환 자료형 ① + 함수이름 ② + (매개변수) ③
※ Function Body: Code Blocks ④ return + 반환값(정수/소수/문자); ⑤

예:
메인함수
int main ()
{
printf("Design Embodiment Programming\_C");
return 0;
}
사용자정의 함수
int plus\_calculation (int X, int Y)
{
int Z;
Z = X + Y;
return Z;
}

## **Type 유형**

반환값(Return값) 無
예:
void main ()
{
printf("Design Embodiment Programming\_C");
}

반환값(Return값) 有
예:
아래 내용

## **Structure 구조**

#### **_Function Header_**
#### **Return Type 반환 자료형** ①
반환값(Return Value) 자료형 명시
반환 자료형(Return Type) = 반환값(Return Value) 자료형
예:
반환 자료형 int → return 정수;
반환 자료형 float → return 소수;
반환 자료형 char → return 문자;
반환 자료형 int, float, char → return 변수;

#### **Function Name 함수명** ②
메인 함수 = main
사용자정의 함수 = 메인 함수에서 해당 함수(사용자정의 함수) 호출시 필요 이름 (예: plus\_calculation)
※ snake case 명명 권장

#### **Parameter 매개변수=인자** ③
매개변수=인자(Parameter) = 함수 입력값

자료형 + 변수
예:
int X
메인 함수에서 해당함수(사용자정의 함수) 호출시 ⓐ
→ 메인 함수 변수 초기화값(**인수 Argument**)이 해당함수(사용자정의 함수)에서 초기화되는 위치 ⓑ
예:
// 사용자정의 함수
int plus\_calculation (int X, int Y) ⓑ // X = number\_1, Y = number\_2,
{
int Z;
Z = X + Y;
return Z;
 }

// 메인 함수
int main ()
{
    int number\_1 = 3;
    int number\_2 = 4;
    int number\_sum = 0;

    number\_sum = plus\_calculation(number\_1, number\_2); ⓐ

    printf("%d",  number\_sum);
printf("%d",  plus\_calculation(number\_1, number\_2);

    return 0;
}

※ 자료형: int, float, char, array 통일 O, int, float, char, array 혼합 O
메인 함수 지역변수 형태(자료형) ⓐ = 사용자정의 함수 매개변수 형태(자료형) ⓑ
※ 갯수: 0개 이상 (0개, 1개, 2개, 3개 .......)

#### **_Function Body_**
#### **Code Blocks 실행코드** ④
함수 동작(= Processing)

#### **Return 반환** ⑤
**의미**
함수종료
**위치**
위치에 따라 함수종료 상이 ∴ 위치 중요
예: if, else if, else, while, for 문 내 or 밖
**유형**
변수, 산술연산 → 반환값 고정 X
예:
return X;
return Y + Z;
정수, 소수, 문자 → 반환값 고정 O
예:
return 2023;
retrun 8.625;
return 'A';
**갯수**
0개 이상
0개:
void 함수 → 함수 종료시 반환값(Return값) 0개 cf) return; 형식 작성 가능
1개 이상:
int main 함수, 반환값 자료형 함수(int, float, char, array) → 함수 종료시 그중 반환(Return) 1개

※ int 메인 함수/사용자정의 함수에서 함수의 자료형이 int
1) 반환값(Return값) = 정수 → 함수종료시 정수 반환
2) 반환값(Return값) 작성 X → 함수종료시 Complier/OS 처리에 따라 다른값(쓰레기값) 반환

## **Main Function 메인 함수**
## **\+ Custom Function/User Defined Function 사용자정의 함수**

#### **Concept 개념**
※ 메인 함수내 사용자정의 함수 호출
→ 사용자정의 함수 실행
→ 사용자정의 함수 반환값(Return) 반환
→ 메인 함수내 '사용자정의 함수명(변수)'를 '사용자정의 함수 반환값(Return값)'으로 대체
메인 함수내 '사용자정의 함수명(변수)' = '사용자정의 함수 반환값(Return값)'
예:
// 사용자정의 함수
int plus\_calculation (int X, int Y) // X = number\_1, Y = number\_2, ②
{
int Z; ③
Z = X + Y; ③
return Z; ④
 }

// 메인 함수
int main ()
{
    int number\_1 = 3;
    int number\_2 = 4;
    int number\_sum = 0;

// 함수반환값 초기화 O → 초기화값 출력
    number\_sum = plus\_calculation(number\_1, number\_2); ① ⑤
    printf("%d",  number\_sum);

// 함수반환값 초기화 X → 함수반환값 출력
printf("%d",  plus\_calculation(number\_1, number\_2); ① ⑤

    return 0;
}
※ Compiling
① 메인 함수내 사용자정의 함수 호출
② 메인 함수내 사용자정의 함수에 해당하는 변수 초기화값을 사용자정의 함수의 매개변수에 초기화
③ 사용자정의 함수 Code Blocks 실행
④ 사용자정의 함수 반환값(Return값) 반환
⑤ 메인함수내 '사용자정의 함수명(변수)'를 '사용자정의 함수 반환값(Return값)'으로 대체
메인함수내 '사용자정의 함수명(변수)' = '사용자정의 함수 반환값(Return값)'
→ plus\_calculation(number\_1, number\_2) = Z

사용자정의 함수의 반환값(Return값)을 메인함수 변수에 초기화 X 사용
**a\_function\_1.c**

```plain
#include <stdio.h>

int function(int Y)
{
  Y++;
  return Y;
}

int main()
{
  int X;
  scanf("%d", &X);        // X = 8
  if (function(X) > 5)    // function(8) 호출 → 사용자정의 함수 반환값 9 → function(X) = 9
  {
    X--;                  // X = 8,  X-- = 7
    printf("if-true -- ++: %d\n", function(X));  // function(7) 호출 → 사용자정의 함수 반환값 8
  }
  else
  {
    printf("if-false ++: %d\n", function(X));
  }

  return 0;
}
```

사용자정의 함수의 반환값(Return값)을 메인함수 변수에 초기화 O 사용
**a\_function\_2.c**

```plain
#include <stdio.h>

int function(int Z)
{
  Z++;
  return Z;
}

int main()
{
  int X;
  scanf("%d", &X);      // X = 8
  int Y = function(X);  // function(8) 호출 → 사용자정의 함수 반환값 9 → function(X) = 9 → Y = 9
  if (Y > 5)            // 9 > 5
  {
    Y--;                // 9 - 1 = 8
    printf("if-true ++ --: %d\n", Y); // 8
  }
  else
  {
    printf("if-true ++: %d\n", Y);
  }

  return 0;
}
```

#### **Usage 사용**
사용자정의 함수 여러개 사용
**a\_function\_3.c**

```plain
#include <stdio.h>

int function_1() 
{
    return 97; 
}

int function_2() 
{
    return 98; 
}

int function_3() 
{
    return 99; 
}

int main()
{
    int result = function_1(); 
    printf("함수 function_1 실행종료\n");
    printf("함수 function_1 반환값: %d\n", result);

    printf("함수 function_2 실행종료\n");
    printf("함수 function_2 반환값: %d\n", function_2());

    printf("함수 function_2 실행종료\n");
    printf("함수 function_2 반환값: %d\n", function_3());

    return 0;
}
```

## **Function Declaration & Definition 함수 선언 및 정의**

선언: 함수가 있다
정의: 함수가 무엇이다
cf)
함수: 선언 & 정의 2과정
자료형: 선언 & 초기화 2과정

※ 함수 선언 '동시' 정의
① 사용자정의 함수: Function Header + Function Body
② 메인 함수
**a\_function\_4.c**

```plain
#include <stdio.h>

int function(int Y)  // 함수 선언 '동시' 정의
{
  Y++;
  return Y;
}

int main()
{
  int X;
  scanf("%d", &X);
  if (function(X) > 5)
  {
    X--;
    printf("if-true -- ++: %d\n", function(X));
  }
  else
  {
    printf("if-true ++: %d\n", function(X));
  }

  return 0;
}
```

※ 함수 선언 '후' 정의
① 사용자정의 함수: Function Header
② 메인 함수
③ 사용자정의 함수: Function Header + Function Body
**a\_function\_5.c**

```plain
#include <stdio.h>

int function(int Y);  // 함수 선언

int main()
{
  int X;
  scanf("%d", &X);
  if (function(X) > 5)
  {
    X--;
    printf("if-true -- ++: %d\n", function(X));
  }
  else
  {
    printf("if-true ++: %d\n", function(X));
  }

  return 0;
}

int function(int Y)  // 함수 정의
{
  Y++;
  return Y;
}
```

## **Function Library 함수 라이브러리**

**라이브러리**
헤더파일 `#include <stdio.h>` + 소스코드 `stdio.c`
*   헤더파일: 함수정의
*   소스코드: 함수선언

**내장 함수**
라이버러리 존재 함수
예:
main 함수, scanf, printf

**사용자정의 함수**
사용자가 직접 선언/정의한 함수
사용자정의 함수로 헤더파일과 소스코드도 직접개발 가능 O

## **Return Value 無/有 반환값 무/유**

**반환값(Return값) 無**
반환값(Return) 유형(Type) Void O
반환값(Return값) 필요없는 함수에서 사용
반환값(Return값) 없으므로 Memory 적게 활용
예:
void main 함수

**반환값(Return값) 有**
반환값(Return) 유형(Type) Void X
예:
반환값(Return값) = 0, 1, -1
int main 함수
운영체제(OS) 內 약속
*   0 → 정상종료

운영체제(OS)에 프로그램 종료시 반환값(Return값) 반환 → 운영체제(OS)는 0을 정상으로 처리

*   1 → 비정상종료, -1 → 비정상종료

예:

파일을 여는 프로그램에서 파일이 없어서 열지못할 경우 → 1

파일을 열고 처리하던중 Error 발생으로 종료 → -1
사용자정의 함수
개발자(Developer) 內 약속
*   1 → 정상종료
*   0 → 비정상종료
∵ 사용자정의 함수는 개발자가 Code로 직접 작성 → Code에서 0 = False, 1 = True

**void main vs int main**
과거: void main 함수 → 표준(Standard)
∵ 반환값(Return값) 無 → 1 Byte라도 더 적은 Memory 활용 가능 O
현재: int main 함수 → 표준(Standard)
∵ void main 함수 반환값(Return값) 無 → 프로그램 정상종료? 오류발생 But 그냥종료? 알수 X
void main 함수 → 활용
∵ 다른 Codes와의 호환성을 위해
※ void main 함수 사용권장 X

* * *

Return Value 無 ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2058](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2058))

Return Value 有 ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2078](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2078))

Usability ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2098](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2098))
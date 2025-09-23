# [CH04L] Condition (Lecture)

## **C Language Learning Road Map**

> 데이터 형식 종류 ➝ 데이터 입력/출력 방식/원리 ➝ 다양한 처리과정

![](https://t9003081320.p.clickup-attachments.com/t9003081320/9ffdfbf7-497a-4a5e-ac73-07ec85a51eea/Picture1.png)

# **Conditional Statement 조건문**

컴퓨터가 해당언어(C Language)로 자료(Data)를 처리하는 방식

if, switch case

제어문(Control Statement)
실행 흐름을 변경하는 명령문
→ 조건문(Conditional Statement)
주어진 조건/조건식(Condition/Conditional Expression)이 참(True) ➝ Code Block '한번' 실행

```cpp
Condition/Condtioanl Expression(조건/조건식)    // 조건/조건식: True or False
{
    Code Block                                  // Code Block = {   }내 Code Set 실행O or 실행X
}


```

* * *

## **if**

```cpp
if (조건/조건식)     // 조건/조건식 True or False
{
    Code Block;      // Code Block = {   }내 Code Set 실행O or 실행X
}


```

#### **Form 형식**

if (조건/조건식) ① ↓ Compiling/Running ③
{
Code Block;②
}

#### **Condition/Conditional Expression 조건/조건식** ①

개발자가 상황에 맞게 직접 작성

조건/조건식의 결과값의 Data Type = 정수 or 실수(소수, 무리수)

조건
E.g)
조건의 결과값 0 = false (Code Block 실행 X), 나머지 = true (Code Block 실행 O)

```cpp
float X = 0.5; 
 
if (X)
{
   Code Block
}


```

조건(X)의 결과값의 Data Type = 소수 ➝ 0.5 ➝ true ➝ Code Block 실행 O

조건식
E.g)
조건식(A == B)의 결과값 0 = false (Code Block 실행 X), 1 = true (Code Block 실행 O)

```cpp
char A;
char B;
scanf("%c", &A);   // 문자 X 입력/저장
scanf("%c", &B);   // 문자 Y 입력/저장

if (A == B)        // A == B (A와 B를 비교) 작성 O,  A = B (B를 A에 대입) 작성 X
{
   Code Block
}


```

조건(A == B)의 결과값의 Data Type = 정수 ➝ 0 ➝ false ➝ Code Block 실행 X

#### **Code Block 수행문** ②

조건/조건식 (else: 조건/조건식 無) = True ➝ 해당 Code Block 실행 O

*   조건/조건식 = True ➝ 해당 Code Block 실행 ➝ 조건문 종료

E.g)

조건1/조건식 1 = False

➝ 조건/조건식 1 해당 Code Block 실행 X

조건2/조건식 2 = True

➝ 조건/조건식 2 해당 Code Block 실행 O ➝ 조건문 종료

*   All 조건/조건식 = False ➝ 조건문 종료 (else 有: else 해당 Code Block 실행 후 조건문 종료)

#### **Compiling/Running 실행** ③

1) \[조건1/조건식 1 확인\]
1A) True = Code Block 1 실행 ➝ 조건문 종료
1B) False = 2) \[조건2/조건식 2 확인\]
2A) True = Code Block 2 실행 ➝ 조건문 종료
2B) False = 3) \[조건/조건식 3 확인\]
3A) True = Code Block 3 실행 ➝ 조건문 종료
3B) False = 3) \[조건/조건식 4 확인\]
.
.
.
n) 모든 조건/조건식 실패
nA) else 無 ➝ 조건문 종료
nB) else 有 = Code Block n 실행 ➝ 조건문 종료

#### **Type 유형**

**Type 1: if** ※ if (n = 1 & 필수 O)

if (조건/조건식)
{
Code Block 1
}

![](https://t9003081320.p.clickup-attachments.com/t9003081320/02fcd41e-2b19-4334-91cf-f6c7b677dfbf/1.png)

**Type 2: if + else** ※ if (n = 1 & 필수 O) + else (n = 0 or 1 & 필수 X)

if (조건/조건식)
{
Code Block 1
}
else
{
Code Block 2
}

![](https://t9003081320.p.clickup-attachments.com/t9003081320/49865b98-e6fa-4d04-aa97-00737660a7a8/2.png)

**Type 3: if + else if** ※ if (n = 1 & 필수 O) + else if (n ≥ 0 & 필수 X)

if (조건/조건식)
{
Code Block 1
}
else if (조건/조건식)
{
Code Block 2
}
else if (조건/조건식)
{
Code Block 3
}

![](https://t9003081320.p.clickup-attachments.com/t9003081320/e5c40270-6dd6-4b2a-bc2a-472cd7e10453/3.png)

**Type 4: if + else if + else** ※ if (n = 1 & 필수 O) + else if (n ≥ 0 & 필수 X) + else (n = 0 or 1 & 필수 X)

if (조건/조건식)
{
Code Block 1
}
else if (조건/조건식)
{
Code Block 2
}
else
{
Code Block 3
}

![](https://t9003081320.p.clickup-attachments.com/t9003081320/eaf03100-73df-4919-a842-5bbce5b3983d/4.png)

※ if 조건문 형식에서 { } 다음에 다른 Code 작성 불가
∵ if 문 조건문 = 반드시 if로 시작 → 다음 if 가 나올때 까지 { } 중괄호 다음에 다른 Code 작성 X
➝ if문 ~ Code End = Conditional Statement Block 1개개

E.g)
if (조건/조건식)
{
Code Block 1
}
Code → 작성 X
else
{
Code Block 2
}

* * *

## **switch case**

`Break 有`

```cpp
switch (조건 =  변수)
{
case 변수에 초기화된 값: ①
    Code Block 1;
    break;
case 변수에 초기화된 값: ②
    Code Block 2;
    break;
case 변수에 초기화된 값: ③
    Code Block 3;
    break;
default:
    Code Block 4;
    break;
}


```

`Break 無`

```cpp
switch (조건 =  변수)
{
case 변수에 초기화된 값: ①
    Code Block 1;
    
case 변수에 초기화된 값: ②
    Code Block 2;
    
case 변수에 초기화된 값: ③
    Code Block 3;
    
default:
    Code Block 4;
    
}


```

조건 O/조건식 X (※ if 문: 조건 O/조건식 O)

해당 조건 = True
➝ 해당 Code Block 실행 ➝ break문 실행(break문 無: 조건문 종료 X) ➝ 조건문 종료
E.g)
break문 有
case 변수에 초기화된값: ①의 조건 = False
case 변수에 초기화된값: ②의 조건 = True
▶ Code Block 2 실행 ➝ break문 실행 ➝ 조건문 종료

break문 無
case 변수에 초기화된값: ①의 조건 = False
case 변수에 초기화된값: ②의 조건 = True
▶ Code Block 2 실행 ➝ Code Block 3 실행 ➝ Code Block 4 실행 ➝ 조건문 종료

All 조건 = False ➝ default Code Block 실행 ➝ 조건문 종료
E.g)
case 변수에 초기화된값: ①의 조건 = False
case 변수에 초기화된값: ②의 조건 = False
case 변수에 초기화된값: ③의 조건 = False
▶ Code Block 4 실행 ➝ 조건문 종료

#### **Form 형식**
switch (조건 ) ① ↓ Compiling/Running ③
{
case 변수에 초기화된 값: ②
Code Block;
break;
default:
Code Block;
break;
}

#### **Variable 변수** ①

사용할 변수명 입력

```cpp
int X = 7;

switch (X)
{
case 변수에 초기화된 값:
     Code Block;
     break;
}


```

#### **Case Lable 변수에 초기화된 값** ②

```cpp
int X;
scanf("%d", &X);

switch (X)
{
case 1:
  Code Block 1;
  break;
case 2:
  Code Block 2;
  break;
case 3:
  Code Block 3;
  break;
}


```

정수로 초기화(입력/저장) ➝ 원칙

문자로 초기화(입력/저장) ➝ 해당 ASCII 변환 정수로 처리 (e.g. A = 65 처리)

소수로 초기화(입력/저장) ➝ Compiling Error
1) float 오차 발생
E.g)
float X = 3.1415926 (float 오차 3.141593)
2) float vs double 근사화 발생
float 부동소수점 Format
![](https://t9003081320.p.clickup-attachments.com/t9003081320/e1964ee5-9427-4793-b326-5a29e03d04c4/1.png)
double 부동소수점 Format
![](https://t9003081320.p.clickup-attachments.com/t9003081320/06ad134f-e1c8-4f02-8717-f0ef216195e2/2.png)
E.g)
float A = 0.7;
double B = 0.7;
A : 0 01111110 0110011 00110011 00110011
B : 0 01111111110 0110011 00110011 00110011 00110011 00110011 00110011 00110
※ float: 작은 자료형(메모리소모 작음 ➝ 연산속도 증가)
※ double: 큰 자료형(표현범위 큼 ➝ 정확도 증가)
3) switch case문은 case 조건 단위: 소수점단위로 case 구분 ➝ case 수 증가 ➝ 코드 장문화

#### **Compiling/Running 실행** ③

`break문 有`
1) \[조건 Case 1 확인\]
1A) True = Code Block 1 실행 ➝ break문 실행 ➝ 조건문 종료
1B) False = 2) \[조건 Case 2 확인\]
2A) True = Code Block 2 실행 ➝ break문 실행 ➝ 조건문 종료
2B) False = 3) \[조건 Case 3 확인\]
3A) True = Code Block 3 실행 ➝ break문 실행 ➝ 조건문 종료
3B) False = 4) \[조건 Case 4 확인\]
.
.
.
n) 모든 조건 Case 실패
Default Code Block 실행 ➝ break문 실행 ➝ 조건문 종료

`break문 無`
1) \[조건 Case 1 확인\]
1A) True = Code Block 1 실행 ➝ Code Block 2 실행 ➝ Code Block n 실행 ➝ 조건문 종료
1B) False = 2) \[조건 Case 2 확인\]
2A) True = Code Block 2 실행➝ Code Block n 실행 ➝ 조건문 종료
2B) False = 3) \[조건 Case 3 확인\]
3A) True = Code Block 3 실행➝ Code Block n 실행 ➝ 조건문 종료
3B) False = 4) \[조건 Case 4 확인\]
.
.
.
n) 모든 조건 Case 실패
Default Code Block 실행 ➝ 조건문 종료

#### **Type 유형**

**Type 1: break 有**

switch (조건 = 변수)
{
case 변수에 초기화된 값:
Code Block 1;
break;
case 변수에 초기화된 값:
Code Block 2;
break;
default:
Code Block 3;
break;
}

![](https://t9003081320.p.clickup-attachments.com/t9003081320/a1ae3c60-d59d-4126-a10f-1938c97b9ff0/5.png)

**Type 1: break 無**

switch (조건 = 변수)
{
case 변수에 초/기화된 값:
Code Block 1;
case 변수에 초기화된 값:
Code Block 2;
default:
Code Block 3;
}

![](https://t9003081320.p.clickup-attachments.com/t9003081320/37059dd2-0bd6-4a8b-8ccc-19b94c706bcf/6.png)

* * *

## **Jump Statement 점프문**

`Continue`
조건문 처음으로 이동
➝ if 문: 사용 X
➝ switch case 문: 사용 X
∵ 조건문 1번만 실행
if) 조건문 처음으로 이동하여 여러번 실행 = 반복문 내 조건문이 있는 형식 = 반복문
반복문 처음으로 이동
➝ while 문: 사용 O
➝ for 문: 사용 O

`Break`
해당 조건문 종료
➝ if 문: 사용 X (해당 조건/조건식 = True ➝ 조건문 종료)
➝ switch case 문: 사용 O
해당 반복문 종료
➝ while 문: 사용 O
➝ for 문: 사용 O

`Goto`
Code Complex (a.k.a 스파게티 Code) → 권장 X

* * *

## **if vs switch case**

#### **Common 공통점**
조건 = True
*   if

조건의 결과값 = 1(True) ➝ 해당 Code Block 1회 실행 ➝ 조건문 종료

*   switch case(break 문 有)

조건의 변수값 일치(True) ➝ 해당 Code Block 1회 실행 ➝ break문 실행 ➝ 조건문 종료

#### **Difference 차이점**

|  | **if** | **switch case** |
| ---| ---| --- |
| Condition | 조건 O & 조건식 O | 조건 O & 조건식 X |
| Variable | 조건/조건식의 결과값의 Data Type<br>\= 정수 or 실수(소수, 무리수) | 변수 = 정수(원칙 O)<br>변수 = 문자(원칙 X: ASCII Code 정수 처리)<br>변수 = 소수(Compiling Error) |
| Compiling<br>Running | 해당 조건/조건식 = True<br>➝ 해당 Code Block 실행<br>➝ 조건문 종료 | 해당 조건 = True (break문 有)<br>➝ 해당 Code Block 실행<br>➝ Break문 실행<br>➝ 조건문 종료<br>해당 조건 = True (break문 無)<br>➝ 해당 조건 + 아래 All Code Blocks 실행<br>➝ 조건문 종료 |
| Break | 사용 X | 사용 O |
| Application | 조건/조건식 = Complex & Various<br>: 범위, 계산/산술식/연산식 | 조건의 변수의 초기화된 값 = Fixed & Few<br>: 정수(원칙 O), 문자(원칙 X), 소수(X) |

* * *

If ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2318](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2318))

Switch Case ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2338](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2338))

If vs Switch Case ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2358](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2358))

If without Brace ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2378](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2378))
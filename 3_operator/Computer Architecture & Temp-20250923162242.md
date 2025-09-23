# Computer Architecture & Temp

## **Computer Architecture 컴퓨터구조**

![](https://t9003081320.p.clickup-attachments.com/t9003081320/23580870-fb04-4518-a156-75317cd7bd93/Picture1.png)

![](https://t9003081320.p.clickup-attachments.com/t9003081320/7380f1d5-d1cb-4148-b9b7-b3a8168af6ce/Picture2.png)

### **Assembly Language**

![](https://t9003081320.p.clickup-attachments.com/t9003081320/1a42041e-e8f5-4ec1-a63a-1d7ea8012ae7/Picture1.png)

`C Language → Assembly Language`

[Reference](https://godbolt.org/)

* * *

### **Example)**

**a\_assembly\_1\_arithmetic.c**

```cpp
// 사칙연산
// 1-1
#include <stdio.h>

int main ()
{
    int A = 2;
    int B = 3;
    int C = A + B;

    printf("%d\n", C);
    printf("%d  %d  %d", &C, &B, &A); 
    
    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/b2a60bd2-de99-4949-9463-dd8638eeddb4/1-1.png)

**a\_assembly\_2\_arithmetic.c**

```cpp
// 사칙연산
// 1-2
#include <stdio.h>

int main ()
{
    int A = 2;
    int B = 3;

    printf("%d", A + B);
    
    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/000adb64-eb08-49b7-ba21-ed200ee4fbf3/1-2.png)

**a\_assembly\_3\_arithmetic.c**

```cpp
// 사칙연산
// 2-1
#include <stdio.h>

int main ()
{
    int A;
    int B;
    scanf("%d", &A);
    scanf("%d", &B);

    int C = A + B;
    printf("%d\n", C);
    printf("%d  %d  %d", &C, &B, &A); // 6422036  6422040  6422044
    
    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/6a7c7738-4c5f-4ac7-875d-fb33a2175fdf/2-1.png)
rax → X 방식(TEMP 작동 O)
rsi → X 방식(TEMP 작동 O)
rax → X 방식(TEMP 작동 O)
rsi → X 방식(TEMP 작동 O)

**a\_assembly\_4\_arithmetic.c**

```cpp
// 사칙연산
// 2-2
#include <stdio.h>

int main ()
{
    int A;
    int B;
    scanf("%d", &A);
    scanf("%d", &B);

    printf("%d\n", A + B);
    
    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/60d67df6-33b7-413a-9a45-cfe8a70447a2/2-2.png)
rax → X 방식(TEMP 작동 O)
rsi → X 방식(TEMP 작동 O)
rax → X 방식(TEMP 작동 O)
rsi → X 방식(TEMP 작동 O)

**b\_assembly\_1\_inre\_decre.c**

```cpp
// 증감 연산
// 3-1
#include <stdio.h>

int main ()
{
    int A = 2;

    printf("%d\n", A++);
    printf("%d\n", ++A);
    printf("%d\n", ++A, A++);
    
    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/3f5ef737-3fb6-4658-9890-89007f6c3c6b/3-1.png)
rax → X 방식(TEMP 작동 O)
rax → X 방식(TEMP 작동 O)

**b\_assembly\_2\_inre\_decre.c**

```cpp
// 증감 연산
// 3-2
#include <stdio.h>

int main ()
{
    int A;
    scanf("%d", &A);

    printf("%d\n", A++);
    printf("%d\n", ++A);
    printf("%d\n", ++A, A++);
    
    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/e39a2a15-fcf5-49d2-917f-1d2ac5a0b040/3-2.png)
rax → X 방식(TEMP 작동 O)
rsi → X 방식(TEMP 작동 O)
rax → X 방식(TEMP 작동 O)
rax → X 방식(TEMP 작동 O)

**c\_assembly\_1\_assign.c**

```cpp
// 대입 연산
// 4-1
#include <stdio.h>

int main ()
{
    int A = 2;
    int B = 3;

    printf("%d", A += B, A -= B);
    
    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/cfce5e02-2e11-431b-9182-de70843d1f13/4-1.png)

**c\_assembly\_2\_assign.c**

```cpp
// 대입 연산
// 4-2
#include <stdio.h>

int main ()
{
    int A;
    int B;
    scanf("%d", &A);
    scanf("%d", &B);

    printf("%d", A += B, A -= B);
    
    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/564bb4ce-60d2-485a-bdc3-0fedf86d008a/4-2.png)
rax → X 방식(TEMP 작동 O)
rsi → X 방식(TEMP 작동 O)
rax → X 방식(TEMP 작동 O)
rsi → X 방식(TEMP 작동 O)

**d\_assembly\_1\_array.c**

```cpp
// 배열
// 5-1
#include <stdio.h>

int main ()
{
    int A[2] = {2, 3};

    printf("%d", A[0] + A[1]);
   
    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/2dd6454a-8aea-4a50-8b2a-292007db7f02/5-1.png)
배열내 주소값 저장 → 메모리박스 내용 O/어셈블리 레지스터 내용 X → 확인 X

**d\_assembly\_2\_array.c**

```cpp
// 배열
// 5-2
#include <stdio.h>

int main ()
{
    int A[2];
    for (int i = 0; i < 2; i++)
    {
        scanf("%d", &A[i]);
    }

    printf("%d", A[0] + A[1]);
   
    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/ad142ad9-bdf3-4e06-ac1d-5490d11cd47b/5-2.png)
rax → X 방식(TEMP 작동 O)
rdx → X 방식(TEMP 작동 O)
rsi → X 방식(TEMP 작동 O)

배열내 주소값 저장 → 메모리박스 내용 O/어셈블리 레지스터 내용 X → 확인 X

**e\_assembly\_scanf\_temp.c**

```cpp
#include <stdio.h>

// Case 1
int main ()
{
    int A;
    char B;
    scanf("%d", &A);    // %d 정수자료형  3(4 Bytes) A 주소값(&)을 시작으로 입력/저장: 3→정수
    scanf("%d", &B);    // %d 정수자료형 89(4 Bytes) B 주소값(&)을 시작으로 입력/저장: 89→정수
    printf("%d  %d\n", A, B);  // 선언한 자료형크기(int A: 4 Bytes, char B: 1 Byte) 만큼 각각 정수 1개 출력 

    return 0;
}

// scanf 함수 한줄 작성 X:  이유 1: OS 차이 → 출력 차이,   이유 2: 가시성 ↓ 
// Case 2
int main ()
{
    int A;
    char B;
    scanf("%d %d", &A, &B);    // %d 정수자료형 3, 89(4 Bytes) A, B 주소값(&)을 시작으로 입력/저장: 3→정수, 89→정수
    printf("%d  %d\n", A, B);  // 선언한 자료형크기(int A: 4 Bytes, char B: 1 Byte) 만큼 각각 정수 1개 출력 

    return 0;
}

// scanf 함수 한줄 작성 X:  이유 1: OS 차이 → 출력 차이,   이유 2: 가시성 ↓ 
// Case 3
int main ()
{
    int A;
    char B;
    scanf("%d %d", &B, &A);    // %d 정수자료형 89, 3(4 Bytes) A, B 주소값(&)을 시작으로 입력/저장: 89→정수, 3→정수
    printf("%d  %d\n", A, B);  // 선언한 자료형크기(int A: 4 Bytes, char B: 1 Byte) 만큼 각각 정수 1개 출력 

    return 0;
}


```

※ Case 1: scanf 함수 Different Line(≥ 2 Lines) Code

`Window OS`
Compiling (L←R)
TEMP O: '선' 생성된 TEMP와 '후' 생성된 TEMP는 Different Assembly Sector內 存 → 침범 O

Memory Box + Temp
![](https://t9003081320.p.clickup-attachments.com/t9003081320/4396f52a-c7ba-42a5-876b-af8645bad5dc/Picture1.png)

C Code + Assembly L
![](https://t9003081320.p.clickup-attachments.com/t9003081320/42744c50-17be-4430-950e-216ecb5d23a4/1.png)

※ Case 2: scanf 함수 Same Line(1 Line) Code

`Window OS`
Compiling (L←R)
TEMP O: '선' 생성된 TEMP와 '후' 생성된 TEMP는 Same Assembly Sector內 存 → 침범 X

Memory Box + Temp
![](https://t9003081320.p.clickup-attachments.com/t9003081320/6a86b5fb-c49a-4ae4-b6a3-128676e5c443/Picture6.png)

Code + Assembly L
![](https://t9003081320.p.clickup-attachments.com/t9003081320/1bc95616-0def-4d56-89eb-257ec74840b7/2.png)

※ Case 3: scanf 함수 Same Line(1 Line) Code

`Window OS`
Compiling (L←R)
TEMP O: '선' 생성된 TEMP와 '후' 생성된 TEMP는 Same Assembly Sector內 存 → 침범 X

Memory Box + Temp
![](https://t9003081320.p.clickup-attachments.com/t9003081320/af7633d4-7f59-4cd4-9d4f-f32fd0cb3c96/Picture1.png)

C Code + Assembly L
![](https://t9003081320.p.clickup-attachments.com/t9003081320/6492f1fe-11c2-481a-8acc-2798b7c5f246/3.png)
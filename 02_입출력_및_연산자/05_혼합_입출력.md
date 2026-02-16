# Int vs Float vs Char vs Array

# **int float char array**

※ 선언시/출력시 변수 → 메모리박스 자료형+크기
※ 초기화시 &변수 → 메모리박스 주소값
※ 10진수 정수의 2진수 입력/저장 → 양수: 2진수 입력/저장, 음수: 2의 보수 2진수 입력/저장
→ printf %d 10진수 정수 출력
※ 10진수 소수의 2진수 입력/저장 → 부동소수점 환산 2진수 입력/저장
→ printf %f 10진수 소수 출력
※ 문자의 ASCII Code 변환 10진수의 2진수 입력/저장 → 2진수 입력/저장
→ printf %c 문자 출력

## **Input 입력**

*   선언 '동시' 초기화

E.g)

int A = 97;

→ 4 Bytes 크기 정수 1개(97)를 정수 자료형 4 Bytes 메모리박스(A)만큼 입력/저장

∵ A: 자료형+크기

int A = 'a';

→ 1 Byte 크기 문자 1개(a)를 정수 자료형 4 Bytes 메모리박스(A)만큼 입력/저장

∵ A: 자료형+크기

a = 97 = 01100001 **00000000 00000000 00000000** (Little Endian)

a **만큼**

float B = 8.625

→ 4 Bytes 크기 소수 1개(8.625)를 소수 자료형 4 Bytes 메모리박스(B)만큼 입력/저장

∵ B: 자료형+크기

※ 8.625의 2진수 입력/저장 = 8.625의 부동소수점 환산 2진수 입력/저장

→ 8.625의 2진수 1000.101 입력/저장 X
→ 8.625의 부동소수점 환산 2진수 01000001000010100000000000000000 입력/저장 O

char C = 'a';
→ 1 Byte 크기 문자 1개(a)를 문자 자료형 1 Byte 메모리박스(C)만큼 입력/저장
∵ C: 자료형+크기

char C = 97;

→ 4 Bytes 크기 정수 1개(97)를 문자 자료형 1 Byte 메모리박스(C)만큼 입력/저장

∵ C: 자료형+크기

97 = 01100001 **~~00000000 00000000 00000000~~** (Little Endian)

97 **~~만큼~~**

*   선언 '후' 초기화
E.g)
int A;
scanf("%d", &A);
→ 4 Bytes 크기 정수 1개(%d)를 A 메모리박스의 주소값(&)에 입력/저장
∵ &A: 주소값
E.g)
int A;
scanf("%d", &A); // 'a' 입력/저장

a = 97 = 01100001 **00000000 00000000 00000000** (Little Endian)

a

int A;
scanf("%c", &A); // 'a' 입력/저장

a = 97 = 01100001 **Trash Trash Trash** (Little Endian)

a

float B;
scanf("%f", &B);
→ 4 Bytes 크기 소수 1개(%f)를 B 메모리박스의 주소값(&)에 입력/저장
∵ &B: 주소값

char C;
scanf("%c", &C);
→ 1 Byte 크기 문자 1개(%c)를 C 메모리박스의 주소값(&)에 입력/저장
∵ &C: 주소값

char D\[5\];

scanf("%s", &D);

→ 1 Byte 크기 문자 여러개(%s)를 D 메모리박스의 주소값(&)에 입력/저장

\+ 문자열 마지막에 \\0 = null 문자 자동 생성

∵ &D: 주소값

## **Output 출력**

*   선언한 자료형크기 만큼 printf 출력서식 (초기화된)변수갯수 출력
E.g)
int A;
printf ("%d", A);
→ 선언한 자료형크기 만큼 정수(%d) 10진수 1개 형식(형태 + 크기) 출력
∵ A: 자료형+크기

float B;
printf ("%f", B);
→ 선언한 자료형크기 만큼 소수(%f) 10진수 1개 형식(형태 + 크기)출력
∵ B: 자료형+크기

char C;
printf ("%c, C);
→ 선언한 자료형크기 만큼 문자(%c) 1개 형식(형태 + 크기) 출력
∵ C: 자료형+크기
int C;
scanf("%c", &C); //  정수 97 or 문자 a 입력/저장
printf("%c, C);
→ 4 Bytes 만큼 문자(%c) 1개 출력 (4 Bytes 중 맨앞 1 Byte 출력)

a = 97 = 01100001 **Trash Trash Trash** (Little Endian)

a

char D\[5\];
printf ("%s, D);
→ /0=null 문자 전까지 출력
∵ printf %s 고유 성질

E.g)
`char Z = 1876824;`
→ 4 Bytes 크기 정수 1개(1876824)를 1 Byte 메모리박스(Z)만큼 입력/저장
10진수 1876824 = 2진수 00000000 00011100 10100011 **01011000** (Big Endian)
**01011000** ~~10100011 00011100 00000000~~ (Little Endian)
**입력/저장**

`printf("%d", Z);`
→ 선언한 자료형크기(1 Byte) 만큼 정수(%d) 1개 형식(형태 + 크기) 출력
2진수 **01011000** \= 10진수 88 출력 (10진수 1876824 출력 X)

**h\_io\_0.c**

```cpp
#include <stdio.h>

int main ()
{
    char Z = 1876824;         // 4 Bytes 크기 정수 1개(1876824)를  1 Byte 메모리박스(Z)만큼 입력/저장   
    printf("%d\n", Z);
    char *ptr = &Z;           
    printf("<%c>\n", ptr[0]); // 2진수 01011000 = 10진수 88
    printf("<%c>\n", ptr[1]); // 쓰레기값 ASCII Code 변환
    printf("<%c>\n", ptr[2]); // 쓰레기값 ASCII Code 변환
    printf("<%c>\n", ptr[3]); // 쓰레기값 (예: a ASCII Code 변환 = 01100001)

    printf("<%x>\n", ptr[0]); 
    printf("<%x>\n", ptr[1]); 
    printf("<%x>\n", ptr[2]); 
    printf("<%x>\n", ptr[3]); 
    return 0;
}
```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/65cbb44a-3d3d-41af-b91a-629eedfe66f3/Picture2.png)

char Z = 1876824;
→ 4 Bytes 크기 정수 1개(1876824)를 1 Byte 메모리박스(Z)만큼 입력/저장
10진수 1876824 = 2진수 00000000 00011100 10100011 **01011000**
**01011000** ~~10100011 00011100 00000000~~ (Little Endian)
**입력/저장**
※ printf 정수(%d) 자료형크기(4 Bytes)만큼 정수형태 출력 X
→ 2진수(Little Endian) 01011000 00000000 00000000 01100001 ≠ 10진수 88
쓰레기값
※ 선언한 자료형크기(1 Byte)만큼 정수(%d) 1개 출력 O
→ 2진수(Little Endian) **01011000** 00000000 00000000 01100001
**출력 = 10진수 88**

## **Summary 요약**

![](https://t9003081320.p.clickup-attachments.com/t9003081320/00d07247-f2f4-4607-830d-1be9369b2dd5/Picture1.png)

### **Example)**

**h\_io\_1.c**

```cpp
// 선언 자료형 & 초기화 자료형 일치 O 
// 배열크기 ≥ 정수/소수'열', 문자'열'

// 선언 '동시' 초기화 
#include <stdio.h>

int main()
{
    int A = 2023;     //  정수자료형 2023(4 Bytes) → 선언 정수자료형 크기(4 Bytes) 만큼 입력/저장 
    float B = 20.23;  // 소수자료형 20.23(4 Bytes) → 선언 소수자료형 크기(4 Bytes) 만큼 입력/저장 
    char C = 'X';     // 문자자료형     X(1 Byte)  → 선언 문자자료형 크기(1 Byte)  만큼 입력/저장 
    char D = 88;      //    정수자료형 88(4 Bytes) → 선언 문자자료형 크기(1 Byte)  만큼 입력/저장 
    int E[3];         // int E[4] = {1, 2, 3};
    E[0] = 1;
    E[1] = 2;
    E[2] = 3;
    float F[3];       // float F[4] = {1.1, 1.2, 1.3};
    F[0] = 1.1;
    F[1] = 2.2;
    F[2] = 3.3;
    char G[4] = {0};  // char G[4] = {'A', 'B', 'C', '\0'};
    G[0] = 'A';
    G[1] = 'B';
    G[2] = 'C';
    
    printf("---Data Type: Simultaneous Input & Output---\n");
    printf("<%d> <%f> <%c> <%d> <%c> <%d>\n", A, B, C, C, D, D);     // 선언한 자료형크기 만큼 각각 출력서식 형태로 출력
    printf("---Array Type int: Simultaneous Input & Output---\n");
    printf("<%d> <%d> <%d>\n", E[0], E[1], E[2]);                    // 선언한 자료형크기 만큼 각각 정수 형태로 출력
    printf("---Array Type flaot: Simultaneous Input & Output---\n");
    printf("<%f> <%f> <%f>\n", F[0], F[1], F[2]);                    // 선언한 자료형크기 만큼 각각 소수 형태로 출력
    printf("---Array Type char: Simultaneous Input & Output---\n");
    printf("<%c> <%c> <%c>\n", G[0], G[1], G[2]);                    // 선언한 자료형크기 만큼 각각 문자 형태로 출력
    printf("<%s>\n", G);

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/6c67cef7-da60-4f35-a50f-d061b9f46cd6/Picture1.png)

**h\_io\_2.c**

```cpp
// 선언 자료형 & 입력서식 자료형 & 초기화 자료형 일치 O 
// 배열크기 ≥ 정수/소수'열', 문자'열'

// 선언 '후' 초기화 
#include <stdio.h>

// Case 1: (각각 초기화 → 각각 출력) 반복 
int main()
{
    int A;
    float B;
    char C;
    char D;
    char E;
    char F;
    // int/float 배열:  배열위치지정 → 변수입력,  배열크기 ≥ 변수갯수
    char G[5];

    printf("---data Type: afterwards input & output---\n");
    printf("---input int---\n");
    scanf("%d", &A);         // %d 정수자료형 2023(4 Bytes) A 주소값(&)에 입력/저장  → 문자 엔터 버퍼 유지 
    printf("---output int---\n");
    printf("%d\n", A);       // 선언한 자료형크기 만큼 정수 1개 출력
    printf("---input float---\n");       
    scanf("%f", &B);         // 버퍼 문자 엔터 삭제 → %f 소수자료형 20.23(4 Bytes) B 주소값(&)에 입력/저장입력/저장 → 문자 엔터 버퍼 유지 
    printf("---output float---\n");
    printf("%f\n", B);       // 선언한 자료형크기 만큼 소수 1개 출력
    scanf("%c", &C);         // %c 버퍼 문자자료형 엔터(1 Byte) C 주소값(&)에 입력/저장
    printf("---input char---\n");
    scanf("%c", &D);         // %c 문자자료형 X(1 Byte) D 주소값(&)에 입력/저장 → 문자 엔터 버퍼 유지 
    printf("---output char---\n");
    printf("%c %d\n", D, D); // 선언한 자료형크기 만큼 각각 문자 정수 1개 출력
    scanf("%c", &E);         // %c 버퍼 문자자료형 엔터(1 Byte) E 주소값(&)에 입력/저장
    printf("---input char---\n");
    scanf("%d", &F);         // 선언한 자료형크기 만큼 정수 1개 출력 
                             // %d 정수자료형 88(4 Bytes) F 주소값(&)에 입력/저장 → char F→E→D→C 메모리박스 입력/저장(1 Byte + 1 Byte + 1 Byte + 1 Byte = 4 Bytes) → 문자 엔터 버퍼 유지 
                             // D가 먼저 출력된 후 입력/저장 → D 출력 영향 X  
    printf("---output char---\n");
    printf("%c %d\n", F, F); // 선언한 자료형크기 만큼 각각 문자 정수 1개 출력   

    printf("---array type char: afterwards input & output---\n");
    printf("---input array char---\n");
    scanf("%s", &G);         // 버퍼 문자 엔터 삭제 → G 주소값(&)에 ABCD 입력/저장
    printf("---output array char---\n");
    printf("%s\n", &G);      // 문자열 출력
    
    return 0;
}

// Case 2: 전체 초기화 → 전체 출력 
int main()
{
    int A;
    float B;
    char C;
    char D;
    char E;
    char F;
    // int/float 배열:  배열위치지정 → 변수입력,  배열크기 ≥ 변수갯수
    char G[5];

    printf("---Data Type: Afterwards Input & Output---\n");
    printf("---Input---\n");
    scanf("%d", &A); // %d 정수자료형 2023(4 Bytes) 입력/저장 → 문자 엔터 버퍼 유지 
    scanf("%f", &B); // 버퍼 문자 엔터 삭제 → %f 소수자료형 20.23(4 Bytes) 입력/저장 → 문자 엔터 버퍼 유지 
    scanf("%c", &C); // %c 버퍼 문자자료형 엔터(1 Byte) 입력/저장
    scanf("%c", &D); // %c 문자자료형 X(1 Byte) 입력/저장 → 문자 엔터 버퍼 유지 
    scanf("%c", &E); // %c 버퍼 문자자료형 엔터(1 Byte) 입력/저장
    scanf("%d", &F); // %d 정수자료형 88(4 Bytes) 입력/저장 → char F→E→D→C 메모리박스 입력/저장(1 Byte + 1 Byte + 1 Byte + 1 Byte = 4 Bytes) 
                     // →  if scanf("%c", &F); → %c 문자자료형 X(1 Byte) 입력/저장           
    printf("---Output---\n");
    printf("<%d> <%f> <%c> <%d> <%c> <%d>\n", A, B, D, D, F, F); // 70번째 줄 입력/저장으로 인해 예상 D 출력값 상이:  %c → \0=null  %d →  0  출력
                                                                 // 71번째 줄 수정 입력/저장하면 예상 D 출력값 동일:  %c →  X       %d →  88 출력
    printf("---Array Type char: Afterwards Input & Output---\n");
    printf("---Input---\n");
    scanf("%s", &G); // 버퍼 문자 엔터 삭제 → 입력대기 → ABCD 입력/저장 + \0=null 생성 → 문자 엔터 버퍼 유지 
    printf("---Output---\n");
    printf("%s", &G);
    
    return 0;
}


```

※ Case 1
![](https://t9003081320.p.clickup-attachments.com/t9003081320/1e0dfcb5-ac58-4c46-8f55-78db49a8b23f/Picture41.png)
![](https://t9003081320.p.clickup-attachments.com/t9003081320/5818c8c6-7b0a-4b48-92ef-86558b9ac8e5/Picture5.png)

※ Case 2
![](https://t9003081320.p.clickup-attachments.com/t9003081320/761a42a2-5dda-4f95-9bee-554afc3b3a23/Picture40.png)
![](https://t9003081320.p.clickup-attachments.com/t9003081320/8b806e5c-5123-44b2-a3a1-b55ebd4a641e/Picture6.png)

**h\_io\_3.c**

```cpp
#include <stdio.h>

// Case 1
int main ()
{    
    char A = -1;       // 정수자료형  -1 (4 Bytes) → 선언 문자자료형 크기(1 Byte) 만큼 입력/저장 
                       // 10진수 - 1  =  2진수 11111111  11111111  11111111  11111111 (음수 2의 보수 처리)
                       // 1 Byte = 8 Bits 크기(11111111) 초기화(Little Endian)
    char B = 255;      // 정수자료형 255 (4 Bytes) → 선언 문자자료형 크기 1 Byte 만큼 입력/저장 
                       // 10진수 255  =  2진수 00000000  00000000  00000000  11111111
                       // 1 Byte = 8 Bits 크기(11111111) 초기화(Little Endian)
    printf("%d\n", A); // 선언 자료형크기(1 Byte) 만큼 정수(%d) 1개 출력
                       // 1 Byte = 8 Bits 크기(11111111) 출력:  -1
    printf("%d\n", B); // 선언 자료형크기(1 Byte) 만큼 정수(%d) 1개 출력
                       // 1 Byte = 8 Bits 크기(11111111) 출력:  -1
    return 0;
}

// Case 2
int main ()
{
    char C = 88;       // 정수자료형 88 (4 Bytes) → 선언 문자자료형 크기(1 Byte) 만큼 입력/저장  
                       // 10진수 88  =  2진수 10101010  10101010  10101010  01011000
                       // 1 Bytes = 8 Bits 크기(01011000) 초기화(Little Endian)    
    printf("%d\n", C); // 선언 자료형크기(1 Byte) 만큼 정수(%d) 1개 출력
                       // 1 Bytes = 8 Bits 크기(01011000) 출력:  88
    printf("%c\n", C); // 선언 자료형크기(1 Byte) 만큼 문자(%c) 1개 출력
                       // 1 Bytes = 8 Bits 크기(01011000) 출력:  X
    char D = 0b10101010101010101010101001011000; // 정수자료형 88의 2진수 (4 Bytes) → 선언 문자자료형 크기(1 Byte) 만큼 입력/저장
                                                 // 0b → 2진수 입력서식  10101010  10101010  10101010  01011000
                                                 // 1 Bytes = 8 Bits 크기(01011000) 초기화(Little Endian)    
    printf("%d\n", C); // 선언 자료형크기(1 Byte) 만큼 정수(%d) 1개 출력
                       // 1 Bytes = 8 Bits 크기(01011000) 출력:  88
    printf("%c\n", C); // 선언 자료형크기(1 Byte) 만큼 문자(%c) 1개 출력
                       // 1 Bytes = 8 Bits 크기(01011000) 출력:  X
    return 0;
}

// Case 3-1
int main ()
{
    char E = 1876824;  // 정수자료형 1876824 (4 Bytes) → 선언 문자자료형 크기(1 Byte) 만큼 입력/저장  
                       // 10진수 1876816  =  2진수  00000000  00011100  10100011  01011000
                       // 1 Bytes = 8 Bits 크기(01011000) 초기화(Little Endian)    
    printf("%d\n", E); // 선언 자료형크기(1 Byte) 만큼 정수(%d) 1개 출력
                       // 1 Bytes = 8 Bits 크기(01010000) 출력:  88
    printf("%c\n", E); // 선언 자료형크기(1 Byte) 만큼 정수(%d) 1개 출력
                       // 1 Bytes = 8 Bits 크기(01010000) 출력:  X
    return 0;
}

// Case 3-2
int main()
{
    char F[5] = {0};

    printf("---Input 1876824---\n");  
    scanf("%d", &F);                  // %d 정수자료형 1876824(4 Bytes) F 주소값(&)에 입력/저장
                                      // 10진수 1876816  =  2진수  00000000  00011100  10100011  01011000
                                      // & 주소값에 %d 4 Bytes = 32 Bits 크기 초기화: 01011000  10100011  00011100  00000000 (Little Endian)
    printf("---Output 1876816---\n");
    printf("<<%d>> %d %d <%d>\n ", F[0],  F[1],  F[2],  F[3]); // 출력:  88  -93  28  0
    printf("<<%c>> %c %c <%c>\n ", F[0],  F[1],  F[2],  F[3]); // 출력:   X           0    
    return 0;
}


```

※ Case 1
![](https://t9003081320.p.clickup-attachments.com/t9003081320/e19540b2-ac09-40ad-abc4-cde450e6fa11/Picture5.png)

※ Case 2
![](https://t9003081320.p.clickup-attachments.com/t9003081320/143c755b-6e0f-42f5-bac6-3db1fc5ded93/Picture6.png)

※ Case 3-1
![](https://t9003081320.p.clickup-attachments.com/t9003081320/c3796eb4-c8bb-41d9-8b92-45366c640cac/Picture39.png)

※ Case 3-2
![](https://t9003081320.p.clickup-attachments.com/t9003081320/3b9e6438-bf85-4620-841d-72870c22e559/Picture9.png)

**h\_io\_4.c**

```cpp
// 선언 자료형 & 초기화 자료형 일치 X
// 자료형 1개

// 선언 '동시' 초기화 
#include <stdio.h>

int main()
{
    char A = 'X';    //     문자 X(1 Byte)  → 선언 문자자료형 크기(1 Byte) 만큼 입력/저장 
    char B = 88;     //    정수 88(4 Bytes) → 선언 문자자료형 크기(1 Byte) 만큼 입력/저장 
    int C = 'X';     //     문자 X(1 Byte)  → 선언 정수자료형 크기(4 Byte) 만큼 입력/저장 
    float D = 88.88; // 소수 88.88(4 Bytes) → 선언 문자자료형 크기(4 Byte) 만큼 입력/저장:  소수 88.88.879997 → float 오차

    printf("---Data Type: Simultaneous Input & Output---\n");
    printf("<%d> <%c>\n<%d> <%c>\n<%d> <%c>\n<%f>\n", A, A, B, B, C, C, D); // 선언한 자료형크기 만큼 각각 출력서식 형태로 출력

    return 0;
}


```

※ float 오차 O
E.g)
13 = 8 + 4 + 1 = 2^3 + 2^2 + 2^0
0.8 = 0.5 + 0.25 + 0.0625 \+ ..... = 2^-1 + 2^-2 + 2^-3 \+ ..... → 2진법 변환 정확 X
※ float 오차 X
E.g)
0.5 = 2^-1 → 2진법 변환 정확 O
0.25 = 2^-2 → 2진법 변환 정확 O
0.75 = 0.5 + 0.25 = 2^-1 + 2^-2 → 2진법 변환 정확 O

![](https://t9003081320.p.clickup-attachments.com/t9003081320/156716d7-cb4f-4749-a1f6-702ebdba50aa/Picture1.png)

**h\_io\_5.c**

```cpp
// 선언 자료형 & 초기화 자료형 일치 X
// 배열크기 > 정수/소수'열', 문자'열'

// 선언 '동시' 초기화 
#include <stdio.h>

int main()
{
    char A[4] = {1, 2, 3, '\0'};        // 정수(4 Bytes) → 선언 문자자료형 크기(1 Byte)  만큼 입력/저장 
    char B[4] = {88, 89, 90, '\0'};     // 정수(4 Bytes) → 선언 문자자료형 크기(1 Byte)  만큼 입력/저장 
    char C[4] = {'X', 'Y', 'Z', '\0'};  //  문자(1 Byte) → 선언 문자자료형 크기(1 Byte)  만큼 입력/저장 
    int D[4] = {'X', 'Y', 'Z', '\0'};   //  문자(1 Byte) → 선언 문자자료형 크기(4 Bytes) 만큼 입력/저장 
    float E[4] ={'X', 'Y', 'Z', '\0'};  //  문자(1 Byte) → 선언 문자자료형 크기(4 Bytes) 만큼 입력/저장 

    printf("---Array Type char: Simultaneous Input & Output---\n");
    printf("<%s>\n", A);  // ASCII Code 변환 문자 '표면'출력 X 
    printf("<%s>\n", B);  // ASCII Code 변환 문자  출력 O
    printf("<%s>\n", C);
    printf("---Array Type int: Simultaneous Input & Output---\n");
    printf("<%s>\n", D);  // %s → /0=null  문자 전까지 문자'열' 출력 → 1 Byte(문자)씩 출력: D[0]번째자리의 2번째 Byte가 00000000=\0=null임을 알수 있음
    printf("<%d> <%d> <%d> <%d>\n", D[0], D[1], D[2], D[3]);
    printf("<%c> <%c> <%c> <%c>\n", D[0], D[1], D[2], D[3]); // ASCII Code 변환 문자 출력 → 선언한 자료형크기(4 Bytes)만큼 문자 1개 출력 →  D[0], D[1], D[2], D[3]의 0번째 Byte 출력
    printf("---Array Type float: Simultaneous Input & Output---\n");
    printf("<%s>\n", E);  // %s → /0=null  문자 전까지 문자'열' 출력 → 1 Byte(문자)씩 출력: E[0]번째자리의 2번째 Byte가 00000000=\0=null임을 알수 있음
    printf("<%f> <%f> <%f> <%f>\n", E[0], E[1], E[2], E[3]);
    printf("<%c> <%c> <%c> <%c>\n", E[0], E[1], E[2], E[3]); // ASCII Code 변환 문자 출력 → 선언한 자료형크기(4 Bytes)만큼 문자 1개 출력 →  E[0], E[1], E[2], E[3]의 0번째 Byte 출력

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/cd09ad2c-32c3-4cf2-96a2-5b642c3d8cbf/Picture2.png)

**h\_io\_6.c**

```cpp
// 선언 자료형 & 초기화 자료형 일치 X
// 배열크기 < 정수/소수'열',  배열크기 < 문자'열'

// 선언 '동시' 초기화 
#include <stdio.h>

int main()
{
    char A[2] = {1, 2, 3, '\0'};               // 정수(4 Bytes) → 선언 문자자료형 크기(1 Byte)  만큼 입력/저장 
    char B[2] = {'X', 'Y', 'Z', '\0'};         //  문자(1 Byte) → 선언 문자자료형 크기(1 Byte)  만큼 입력/저장 
    int C[2] = {'X', 'Y', 'Z', '\0'};          //  문자(1 Byte) → 선언 문자자료형 크기(4 Bytes) 만큼 입력/저장 
    int D[2] = {88, 89, 90, '\0'};             // 정수(4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 입력/저장 
    float E[2] = {'X', 'Y', 'Z', '\0'};        //  문자(1 Byte) → 선언 문자자료형 크기(4 Bytes) 만큼 입력/저장 
    float F[2] = {88.88, 89.89, 90.90, '\0'};  // 소수(4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 입력/저장 

    printf("---Array Type char: Simultaneous Input & Output---\n");
    printf("---A---\n");
    printf("<%s>\n", A);   // /0=null 문자 전까지 배열크기 2개 ASCII Code 변환문자 표면출력 X
    printf("---B---\n");  
    printf("<%s>\n", B);   // /0=null 문자 전까지 배열크기 2개 정상출력(+ A[0] ASCII Code 변환문자 표면출력 X)
    printf("---Array Type int: Simultaneous Input & Output---\n");
    printf("---C---\n");
    printf("<%s>\n", C);   // %s → /0=null  문자 전까지 문자'열' 출력 → 1 Byte씩 출력:  C[0]번째자리의 2번째 Byte가 00000000=\0=null임을 알수 있음
    printf("<%d> <%d> <%d> <%d>\n", C[0], C[1], C[2], C[3]); // C[0], C[1] 배열크기 2개 ASCII Code 변환 정수 정상출력 
                                                             // C[2] = B[0]B[1]A[0]A[1]의 2진수의 10진수 출력 = 10진수 33462840 출력(선언한 자료형크기 4 Bytes 만큼 정수 1개 출력)
                                                             // C[3] = A[1]오른쪽 4 Bytes 크기만큼 Trash값의 10진수 출력 = 알수 없음 
    printf("<%c> <%c> <%c> <%c>\n", C[0], C[1], C[2], C[3]); // C[0], C[1] 배열크기 2개 정상출력
                                                             // C[2] = X 출력(선언한 자료형크기 4 Bytes 만큼 문자 1개 1 Byte 출력) = B[0] = 10진수 33462840의 Little Endian 1 Byte = 2진수 01011000 = 10진수 88 = ASCII Code 변환 X 출력
                                                             // C[3] = 10425904(24번째줄 C[3]출력값)의 4 Bytes 크기만큼 문자 1개(ASCII Code 변환문자) 1 Byte 출력 
    printf("---D---\n");
    printf("<%s>\n", D);   // %s → /0=null  문자 전까지 문자'열' 출력 → 1 Byte씩 출력:  D[0]번째자리의 1번째 Byte가 00000000=\0=null임을 알수 있음
    printf("<%d> <%d> <%d> <%d>\n", D[0], D[1], D[2], D[3]); //  D[0], D[1] 배열크기 2개 정상출력
                                                             //  D[2] = C[0], D[3] = C[1]: 88, 89 출력 (선언한 자료형크기 4 Bytes 만큼 정수 1개 출력) 
    printf("<%c> <%c> <%c> <%c>\n", D[0], D[1], D[2], D[3]); //  D[0], D[1] 배열크기 2개 ASCII Code 변환 문자 정상출력
                                                             // D[2] = C[0], D[3] = C[1]: X, Y 출력 (선언한 자료형크기 4 Bytes 만큼 문자 1개 출력)
    printf("---Array Type float: Simultaneous Input & Output---\n");
    printf("---E---\n");
    printf("<%s>\n", E);   // %s → /0=null  문자 전까지 문자'열' 출력 → 1 Byte씩 출력:  E[0]번째자리의 1번째 Byte가 00000000=\0=null임을 알수 있음
    printf("<%f> <%f> <%f> <%f>\n", E[0], E[1], E[2], E[3]); // E[0], E[1] 배열크기 2개 정상출력
                                                             // E[2] = D[0], E[3] = D[1] 0.0. 0.0 출력 (선언한 자료형크기 4 Bytes 만큼 소수 1개 출력)
                                                             // 소수 1개 출력 = 부동소수점 2진수의 10진수 소수 1개 출력:  D[0], D[1] = 88, 89의 2진수 ≠ 88, 89의 부동소수점 2진수
                                                             //   1) 정수자료형 메모리박스 D[0] 초기화 88 = 10진수 88의 2진수 = 00000000  00000000  00000000  01011000 → 소수출력위해 부동소수점 환산 → 소수 1.23314264861e-43 ≒ 0 출력
                                                             //   2) 정수자료형 메모리박스 D[1] 초기화 89 = 10진수 89의 2진수 = 00000000  00000000  00000000  01011001 → 소수출력위해 부동소수점 환산 → 소수 1.24715563325e-43 ≒ 0 출력 
    printf("<%c> <%c> <%c> <%c>\n", E[0], E[1], E[2], E[3]); // ASCII Code 변환 문자 출력 X
    printf("---F---\n");
    printf("<%s>\n", F);   // %s → /0=null  문자 전까지 문자'열' 출력 → 1 Byte씩 출력: E[0]번째자리의 0번째 Byte가 00000000=\0=null이므로 그전까지(F[0], F[1]) 부동소수점 환산 소수 2진수 문자출력
    printf("<%f> <%f> <%f> <%f>\n", F[0], F[1], F[2], F[3]); // F[0], F[1] 배열크기 2개 정상출력 → Float 오차
                                                             // F[2] = E[0], F[3] = E[1]: 88.0. 89.0 출력 (선언한 자료형크기 4 Bytes 만큼 소수 1개 출력)
                                                             //   1) 소수자료형 메모리박스 E[0] 초기화 X = ASCII Code 변환 88의 부동소수점 2진수로 초기화 = 01000010  10110000  00000000  00000000 → 그대로 88.0 출력
                                                             //   2) 소수자료형 메모리박스 E[1] 초기화 Y = ASCII Code 변환 89의 부동소수점 2진수로 초기화 = 01000010  10110010  00000000  00000000 → 그대로 89.0 출력
    printf("<%c> <%c> <%c> <%c>\n", F[0], F[1], F[2], F[3]); // ASCII Code 변환 문자 출력 X

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/6f6eac5c-52e7-44fa-b0f3-96196814e8f8/Picture1.png)

**h\_io\_7.c**

```cpp
#include <stdio.h>

int main()
{
    float A = 'X';      // 자료형 + 크기 인식 O  → 1 Byte 문자 1개(X)를 4 Bytes 소수 자료형 메모리박스(A)만큼 입력/저장 
                        // X의 ASCII Code 10진수 88 → 부동소수점 2진수 01000010  10110000  00000000  00000000 초기화
    printf("%f\n", A);  // 선언한 자료형크기(4 Bytes)만큼 소수 출력:  %f 부동소수점 2진수의 10 진수 소수 출력 → 88.000000 출력

    float B;
    scanf("%c", &B);    // &주소값에 문자 입력저장 X → 1 Byte 문자 1개(X)를 메모리박스(B)의 주소값(&)에 입력/저장
                        // X의 ASCII Code 10진수 88  →  2진수  00000000  00000000  00000000  01011000 초기화
    printf("%f\n", B);  // 선언한 자료형크기(4 Bytes)만큼 소수 출력:  %f 2진수의 부동소수점 환산 10 진수 소수 출력 → 1.23314264861e-43  ≒  0 = 0.000000

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/3438ee8c-ace9-4dc1-8b37-da2ad0878306/3.png)

**h\_io\_8.c**

```cpp
// 선언 자료형 & 입력서식 자료형 & 초기화 자료형 일치 X 
// 자료형 1개

// 선언 '후' 초기화
#include <stdio.h>

// 예: X → 88 → 89 → Y 입력/저장
int main()
{
    char A;
    char B;       
    char C;
    char D;
    char E;
    char F;     
    int G;  
    float H;
    char I;
    char J;

    printf("---input---\n");
    scanf("%c", &A);     // 예: %c 문자자료형 X(1 Byte) A 주소값(&)에 입력/저장 → 문자 엔터 버퍼 유지 
    scanf("%c", &B);     // 예: %c 버퍼 문자자료형 엔터(1 Byte) B 주소값(&)에 입력/저장
    scanf("%d", &C);     // 예: %d 정수자료형 88(4 Bytes) C 주소값(&)에 입력/저장 → 문자 엔터 버퍼 유지 
    scanf("%c", &D);     // 예: %c 버퍼 문자자료형 엔터(1 Byte) D 주소값(&)에 입력/저장  
    scanf("%c", &E);     // 예: %c 문자자료형 89(2 Bytes) E 주소값(&)에 입력/저장 → 문자 앞자리 8(1 Byte) 주소값(&)에 입력/저장 → 문자 뒷자리 9 + 문자 엔터 버퍼 유지  
    scanf("%c", &F);     // 예: %c 문자자료형 9(1 Byte) F 주소값(&)에 입력/저장 → 문자 엔터 버퍼 유지 
    scanf("%d", &G);     // 예: 버퍼 엔터 삭제 → 입력대기 → %d 문자 Y 입력/저장 실패 → 문자 Y엔터 버퍼 유지  
    scanf("%f", &H);     // 예: %f 문자 Y 입력/저장 실패 → 문자 Y엔터 버퍼 유지  
    scanf("%c", &I);     // 예: %c 버퍼 문자자료형 Y(1 Byte) I 주소값(&)에 입력/저장 → 문자 엔터 버퍼 유지
    scanf("%c", &J);     // 예: %c 버퍼 문자자료형 엔터(1 Byte) J 주소값(&)에 입력/저장  
    printf("---Output---\n");
    printf("<%d> <%c>\n<%d> <%c>\n<%d> <%c>\n<%d> <%c>\n<%d>\n<%f>\n<%d> <%c>\n<%d> <%c>\n", A, A, C, C, E, E, F, F, G, H, I, I, J, J);

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/19fae9cb-3063-4dd6-b94f-c1146799ea5d/Picture35.png)

**h\_io\_9.c**

```cpp
// 선언 자료형 & 입력서식 자료형 & 초기화 자료형 일치 O 
// 배열크기 < 정수/소수'열',  배열크기 < 문자'열'

// 선언 '후' 초기화:  자료형 1개 & 자료형 배열
#include <stdio.h>

// 2023 → 20.23 → 스페이스ABCD → 엔터ABCD
int main()
{
    int A;
    float B;
    char C;
    char D;
    char E[2];
    char F[3];

    printf("---input---\n");
    scanf("%d", &A);     // 예: %d 정수자료형 2023(4 Bytes) A 주소값(&)에 입력/저장 → 문자 엔터 버퍼 유지 
    scanf("%f", &B);     // 예: 버퍼 엔터 삭제 → 입력대기 →  %f 소수자료형 20.23(4 Bytes) B 주소값(&)에 입력/저장 → 문자 엔터 버퍼 유지  
    scanf("%c", &C);     // 예: %c 버퍼 문자자료형 엔터(1 Byte) C 주소값(&)에 입력/저장   
    scanf("%c", &D);     // 예: 문자'열' 스페이스ABCD 입력 → %c 버퍼 문자자료형 스페이스(1 Byte) D 주소값(&)에 입력/저장 → 문자 ABCD엔터 버퍼 유지
    scanf("%s", &E);     // 예: %s 문자열자료형 버퍼 ABCD엔터 → 공백문자(엔터)전 E 주소값(&)에 ABCD 입력/저장 + \0=null 문자 생성(char E[2]; 메모리박스 2개 활성화) → 문자 엔터 버퍼 유지
    scanf("%s", &F);     // 예: %s 버퍼 문자 엔터 삭제 → %s 문자열자료형 엔터ABCD엔터 → 첫 문자열 엔터삭제 → 공백문자(엔터)전 F 주소값(&)에 ABCD 입력/저장 + \0=null 문자 생성(char F[3]; 메모리박스 3개 활성화) → 문자 엔터 버퍼 유지
    printf("---Output---\n");
    printf("<%d> <%f> <%c> <%c> <%s> <%s>", A, B, C, D, E, F);

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/0cdf69b8-93fa-40f2-bcc0-3263426cbbe0/Picture1.png)

**h\_io\_10.c**

```cpp
// 선언 자료형 & 입력서식 자료형 & 초기화 자료형 일치 X
// 배열크기 < 정수/소수'열',  배열크기 < 문자'열'

// 선언 '후' 초기화:  자료형 1개 & 자료형 배열
#include <stdio.h>

// X → 123456789AB → 12345
int main()
{
    int A;
    float B;
    char C;
    char D[2] = {0};
    char E[3];
    char F[2];

    printf("---input---\n");
    scanf("%d", &A);    // 예: 입력서식(%d→정수자료형)  초기화변수 문자자료형(문자→X) 매칭 X → scanf 실행 실패 → 초기화변수(문자→X, 엔터) 버퍼 유지
    scanf("%f", &B);    // 예: 입력서식(%f→소수자료형)  초기화변수 문자자료형(문자→X) 매칭 X → scanf 실행 실패 → 버퍼변수(문자→X, 엔터) 유지
    scanf("%c", &C);    // 예: %c 버퍼 문자자료형 X(1 Byte) C 주소값(&)에 입력/저장 → 버퍼변수(문자→엔터) 유지  
    scanf("%c", &D);    // 예: %c 버퍼 문자자료형 엔터(1 Byte) D 주소값(&)에 입력/저장(char D[2]: 메모리박스 2개 활성화)
    scanf("%s", &E);    // 예: %s 문자열자료형 123456789AB 엔터 → 공백문자(엔터)전 E 주소값(&)에 123456789AB 입력/저장 + \0=null 문자 생성(char E[3]; 메모리박스 3개 활성화) → 문자 엔터 버퍼 유지
    scanf("%s", &F);    // 예: %s 버퍼 문자 엔터 삭제 → %s 문자열자료형 12345엔터 → 공백문자(엔터)전 F 주소값(&)에 12345 입력/저장 + \0=null 문자 생성(char F[2]; 메모리박스 2개 활성화) → 문자 엔터 버퍼 유지
    printf("---Output---\n");
    printf("<%d> <%f> <%c> <%s> <%s> <%s> ", A, B, C, D, E, F);

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/272db933-206a-40f6-86e1-7eabb8e5d30e/Picture1.png)
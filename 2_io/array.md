# Array

# **array**

*   정수/소수/문자'열

*   문자'열

`\0 = null`

![](https://t9003081320.p.clickup-attachments.com/t9003081320/b69ac40f-5e74-4f1d-b379-80d646847371/Picture3.png)
문자 0 '초기화'(입력/저장) 공백 '선언'X(메모리박스할당' X)

*   선언(메모리박스 할당)

자료형 변수명\[배열의 크기 = 메모리박스 갯수\]

E.g)
`int A[4];` , `float B[4]`; , `char C[4];`

※ 70-80%: 선언시 메모리박스크기(배열크기) 만큼 자동 \\0=null Set-Up O

※ 10-20%: 선언시 메모리박스 내 쓰레기값 생성

∴ 선언시 메모리박스크기(배열크기) 만큼 자동 \\0=null Set-Up X

**e\_array\_1.c**

```cpp
#include <stdio.h>

// Case 1:  \0=null 문자 Set-Up O?
int main()
{
    int A;
    float B;
    char C;
    char D[5];

    printf("---int A null---\n<%c>\n", A);
    printf("---float B null---\n<%c>\n", B);
    printf("---char C null---\n<%c>\n", C);
    printf("---char D array null---\n<%c> <%c> <%c> <%c> <%c>\n", D[0], D[1], D[2], D[3], D[4]);
    printf("---char D array null X???---\n<%c> <%c> <%c> <%c> <%c>\n", D[5], D[6], D[7], D[8], D[9]);      
 
    return 0;
}

// Case 2:  \0=null 문자 Set-Up 방법
int main()
{
    // Approach 1
    char A[5] = {'\0', '\0', '\0', '\0', '\0'}; //  전체 \0=null 초기화(입력/저장) 
    printf("---char A array null---\n<%c> <%c> <%c> <%c> <%c>\n", A[0], A[1], A[2], A[3], A[4]);

    // Approach 2-1
    char B[5] = {0, };    // 전체 \0=null 초기화(입력/저장) O 
    printf("---char B array null---\n<%c> <%c> <%c> <%c> <%c>\n", B[0], B[1], B[2], B[3], B[4]);

    char C[5] = {'\0', }; // 전체 \0=null 초기화(입력/저장) O 
    printf("---char C array null---\n<%c> <%c> <%c> <%c> <%c>\n", C[0], C[1], C[2], C[3], C[4]);

    char D[5] = {0};      // 전체 \0=null 초기화(입력/저장) O
    printf("---char D array null---\n<%c> <%c> <%c> <%c> <%c>\n", D[0], D[1], D[2], D[3], D[4]);

    char E[5] = {'\0'};   // 전체 \0=null 초기화(입력/저장) O
    printf("---char E array null---\n<%c> <%c> <%c> <%c> <%c>\n", D[0], D[1], D[2], D[3], D[4]);
    

    // Approach 2-2
    char F[5] = {1};      // 전체 1 초기화(입력/저장) X → C[0] = 1 초기화(입력/저장)
    printf("---char F array 1?---\n[<%c> <%d>] [<%c> <%d>] [<%c> <%d>] [<%c> <%d>] [<%c> <%d>]\n", F[0], F[0], F[1], F[1], F[2], F[2], F[3], F[3], F[4], F[4]);

    char G[5] = {0};
    G[0] = '1';           // G[0] = 1;
    printf("---char D array 0 & null---\n[<%c> <%d>] [<%c> <%d>] [<%c> <%d>] [<%c> <%d>] [<%c> <%d>]\n", G[0], G[0], G[1], G[1], G[2], G[2], G[3], G[3], G[4], G[4]);
 
    return 0;
}


```

*   출력

문자 '열'

`printf`함수 + `%s` 문자'열' 출력서식

→ /0=null 문자 전까지 출력 ∵ printf %s 고유 성질
※ 배열선언시 사용 O → 출력가능
※ 배열요소 전체 \\0=null 문자 전까지 출력
E.g)
char C\[5\] = {'A', 'B', 'C', 'D', '\\0'};
printf(“%s”, C);

문자 '1개'
`printf`함수 + `%c` 문자1개 출력서식
→ 선언한 자료형크기 만큼 문자(%c) 1개 형식(형태 + 크기) 출력
※ 배열선언시 사용 X → 출력오류
※ 배열요소 각각 출력 O
E.g) 가능 O
char C\[5\] = {'A', 'B', 'C', 'D', '\\0'};
printf(“%c %c %c %c %c”, C\[0\], C\[1\], C\[2\], C\[3\], C\[4\]);
E.g) 가능 X
char C\[5\] = {'A', 'B', 'C', 'D', '\\0'};
printf(“%c”, C);

정수/소수 '열'
코드작성 要

정수/소수 1개 `printf`함수 + `%d` `%f` 정수/소수1개 출력서식
→ 선언한 자료형크기 만큼 정수/소수(%d/%f) 1개 형식(형태 + 크기) 출력
E.g)
int A\[5\] = {1, 2, 3, 4, 5};
printf(“%d %d %d %d %d”, A\[0\], A\[1\], A\[2\], A\[3\], A\[4\]);

*   초기화(입력/저장)

선언 '동시' 초기화

. 문자

\= { } ➝ 내부서식 ' '

E.g)

char C\[5\] = {'A', 'B', 'C', 'D', '\\0'}; char C\[5\] = {'1', '2', '3', '4', '\\0'};

\= " " ➝ 내부서식 X

E.g)

char C\[5\] = "ABCD\\0"; char C\[5\] = "1234\\0";

※ 배열선언시 \\0=null Set-Up 필요 O ∵ printf %s (\\0=null 문자 전까지 출력) 사용 O

배열크기 = 초기화(입력/저장) 변수값의 갯수 + 1개 이상 (\\0=null 문자 메모리박스 공간)

배열크기 < 초기화(입력/저장) 변수값의 갯수

배열크기 변수갯수 = 메모리박스 '활성화 O' + (초과 변수갯수 = 메모리박스 '생성 X')

E.g)

char C\[2\] = {'A', 'B', 'C', 'D', '\\0'};

printf %s

A B 2개 출력 → 메모리박스 '활성화' 갯수 2개(A, B) \+ 쓰레기값(%)

※ 공백문자(엔터, 스페이스, 탭) 문자인식 O

E.g)

char Z\[6\] = {'A', 'B', ' ', 'C', 'D', '\\0'}; , char Z\[6\] = "12 34\\0";

. 정수/소수

\= { } ➝ 내부서식 X

E.g)

int A\[4\] = {1, 2, 3, 4};

E.g)

float B\[4\] = {1.1, 2.2, 3.3, 4.4}

※ 선언시 \\0=null Set-Up 필요 X ∵ printf %s (\\0=null 문자 전까지 출력) 사용 X

※ 배열크기 ≥ 초기화 변수갯수

**e\_array\_2.c**

```cpp
// 선언 '동시' 초기화
#include <stdio.h>

// Approach 1
int main()
{
    char X[5] = {'\0', '\0', '\0', '\0', '\0'}; // char X[5] = {0};
    // char X[5] = {'A', 'B', 'C', 'D'}; → X를 재'선언'(redefine) X
    // X[5] = {'A', 'B', 'C', 'D'};  → X 배열의 5번째 위치에 문자'열' 초기화 ?!?!? 
    X[0] = 'A'; 
    X[1] = 'B';
    X[2] = 'C';
    X[3] = 'D';
    printf("<%c> <%c> <%c> <%c> <%c>\n", X[0], X[1], X[2], X[3], X[4]);
    printf("%s\n", X);
    return 0;
}

// int main()
// {
//     char X = 'A';
//     X = 'B';
//     return 0;
// }


// Approach 2
int main()
{
    char X[5] = {'A', 'B', 'C', 'D', '\0'}; 
    printf("<%c> <%c> <%c> <%c> <%c>\n", X[0], X[1], X[2], X[3], X[4]);
    printf("%s\n", X); 
    return 0;
}       
     
```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/579aafeb-5b24-421d-a525-d293082aa1db/Picture1.png)

선언 '후' 초기화

. 문자 '열'

`scanf` 함수 + `%s` 문자'열' 입력서식

E.g)

char D\[5\];

scanf("%s", &D);

→ 1 Byte 크기 문자 여러개(%s)를 메모리박스(D)의 주소값(&)에 입력/저장

∵ &D: 주소값

※ 문자열 마지막 \\0=null 문자 생성 O

※ 배열선언시 \\0=null Set-Up 필요 X ∵ scanf %s 문자열 마지막 \\0=null 문자 생성 O
※ 배열크기 = 초기화 변수갯수 + 1개 이상 (\\0=null 문자 생성 공간)

배열크기 < 초기화(입력/저장) 변수갯수

배열크기 변수갯수 = 메모리박스 '활성화 O' + 초과 변수갯수 = 메모리박스 '생성 O'

※ 공백문자(엔터, 스페이스) 문자인식 X
1) 공백문자 '포함' '버퍼' 대기
2) 공백문자 '제외' '메모리박스' 입력/저장
E.g)
ABC엔터 초기화
→ ABC 메모리박스 입력/저장 + \\0=null 문자 생성
E.g)
A스페이스B스페이스C엔터 초기화
→ A 메모리박스 입력/저장 + \\0=null 문자 생성
E.g)
스페이스스페이스ABCD엔터(엔터엔터ABCD엔터)
→ ABCD 메모리박스 입력/저장 + \\0=null 문자 생성

. 문자 1개

`scanf` 함수 + `%c` 문자 1개 입력서식

E.g)

char D\[5\] = {0};

scanf("%c", &D);

→ 1 Byte 크기 문자 1개(%c)를 메모리박스(D)의 주소값(&)에 입력/저장

∵ &D: 주소값

※ 문자열 마지막 \\0=null 문자 생성 X

※ 배열선언시 \\0=null Set-Up 필요 O ∵ printf %s (\\0=null 문자 전까지 출력) 사용 O

※ 배열크기 = 초기화 변수갯수 + 1개 이상 (\\0=null 문자 메모리박스 공간)

※ 공백문자(엔터, 스페이스) 문자인식 O

1) 공백문자 '포함' 버퍼 대기

2) 공백문자 '포함' 메모리박스 입력/저장

. 정수/소수 '열'

`scanf` 함수 존재 無

코드작성 要

배열위치(index) 지정 후 배열요소(element) 각각 초기화 = 배열시작 & 끝 인식 O

※ 배열선언시 \\0=null Set-Up 필요 X ∵ printf %s (\\0=null 문자 전까지 출력) 사용 X

※ 배열크기 ≥ 초기화 변수갯수

**e\_array\_3.c**

```cpp
#include <stdio.h>

// 문자: 선언크기 < 변수갯수
// 예: ABCDE 입력/저장
int main()
{
    char X;
    printf("---input---\n");
    scanf("%s", &X);
    printf("---Output---\n");
    printf("%c\n", X);   // 일반자료형 선언시 사용 O   →  출력가능  
    printf("%s\n", X);   // 일반자료형 선언시 사용 X   →  출력오류  
 
    return 0;
}   
 
```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/b22f6d21-914b-4923-bfae-1e41f81c2108/Picture7.png)

**e\_array\_4.c**

```cpp
#include <stdio.h>
#include <string.h> // string 함수 사용 라이브러리 추가

// 문자'열': 선언크기 < 변수갯수
// 예: ABCDE 입력/저장
int main()
{
    char Y[3];
    printf("---input---\n");
    scanf("%s", &Y);
    printf("---Output---\n");
    printf("%s\n", Y);        // 배열자료형 선언시 사용 O   →  출력가능  
    printf("<%c>\n", Y[5]);
    printf("%d\n", strlen(Y));
    printf("%c\n", Y);        // 배열자료형 선언시 사용 X   →  출력오류  // printf("%c\n", Y[0]);  
 
    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/1fe1ae01-93b1-461d-b92b-304e98ea70b2/Picture2.png)

### **Example)**

**e\_array\_5.c**

```cpp
#include <stdio.h>
#include <string.h> // string 함수 사용 라이브러리 추가

// 공백문자 X
int main()
{
    // 선언 '동시' 초기화
    char X[10] = {'A', 'B', 'C', 'D', '\0'};          // char X[10] = "ABCD\0";    
                                                     // 배열의 크기 10 ≥ 초기화 변수 갯수 4 + 1 이상(\0=null 문자 생성 메모리박스 공간
    printf("%s\n", X);                               // %s → 문자'열' 출력
    printf("%c %c %c %c\n", X[0], X[1], X[2], X[3]); // %c → 배열요소 문자 출력
    printf("%d\n", strlen(X));                       // %d → 문자'열' 길이(strlen = string length) 출력  → \0=null 문자 전까지 길이 출력
    printf("<%c>\n", X[4]);                          // \0=null 문자 초기화 위치

    // 선언 '후' 초기화
    char Z[10];
    printf("--입력--\n");
    scanf("%s", &Z);           // 예: ABCD 입력/저장
                               // 문자 메모리박스 10개 문자'열' 선언 '후' 변수 문자 4개 ABCD 초기화 + 문자 1개 \0=null 생성  →  '초기화' 변수(문자→엔터) 버퍼 유지    
    printf("--출력--\n");
    printf("%s\n", Z);         // %s → 문자'열' 출력
    printf("%c %c %c %c\n", Z[0], Z[1], Z[2], Z[3]); // %c → 배열요소 문자 출력
    printf("%d\n", strlen(Z)); // %d → 문자'열' 길이(strlen = string length) 출력  → \0=null 문자 전까지 길이 출력
    printf("<%c>\n", Z[4]);    // \0=null 문자 생성 위치 

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/e8d9a389-4242-432e-8873-12663b46eb8a/Picture4.png)

**e\_array\_6.c**

```cpp
#include <stdio.h>
#include <string.h> // string 함수 사용 라이브러리 추가

// 공백문자 O
int main()
{
    // 선언 '동시' 초기화
    char X[10] = {'A', 'B', ' ', 'C', 'D', '\0'};                // char X[10] = "AB CD\0";   
                                                                // 배열의 크기 10 ≥ 초기화 변수 갯수 5 + 1 이상(\0=null 문자 생성 메모리박스 공간)
    printf("%s\n", X);                                          // %s → 문자'열' 출력
    printf("%c %c <%c> %c %c\n", X[0], X[1], X[2], X[3], X[4]); // %c → 배열요소 문자 출력:  X[2] = 스페이스
    printf("%d\n", strlen(X));                                  // %d → 문자'열' 길이(strlen = string length) 출력  → \0=null 문자 전까지 길이 출력
    printf("<%c>\n", X[5]);                                     // \0=null 문자 생성 위치 
  
    // 선언 '후' 초기화
    char Z[10];
    printf("--입력--\n");
    scanf("%s", &Z);               // 예: AB스페이스CD 입력/저장[공백문자 제외 AB Z 주소값(&)에 입력/저장]
                                   // 문자 메모리박스 10개 문자'열' 선언 '후' 변수 문자 3개 AB초기화  + 문자 1개 \0=null 생성  →  '초기화' 변수(문자→스페이스CD엔터) 버퍼 유지    
    printf("--출력--\n");
    printf("%s\n", Z);             // %s → 문자'열' 출력
    printf("%c %c\n", Z[0], Z[1]); // %c → 배열요소 문자 출력: X[2] = \0=null
    printf("%d\n", strlen(Z));     // %d → 문자'열' 길이(strlen = string length) 출력  → \0=null 문자 전까지 길이 출력
    printf("<%c>\n", Z[2]);        // \0=null 문자 생성 위치

    printf("--입력--\n");
    scanf("%s", &Z);               //  scanf 실행:  버퍼 변수(문자→스페이스) 삭제  →  버퍼 변수(문자→CD) 초기화 + \0=null 문자 생성  →  버퍼 변수(문자→엔터) 유지   

    printf("--출력--\n");
    printf("%s\n", Z);             // %s → 문자'열' 출력
    printf("%c %c\n", Z[0], Z[1]); // %c → 배열요소 문자 출력: X[2] = \0=null
    printf("%d\n", strlen(Z));     // %d → 문자'열' 길이(strlen = string length) 출력  → \0=null 문자 전까지 길이 출력
    printf("<%c>\n", Z[2]);        // \0=null 문자 생성 위치

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/727e9707-4635-4498-ba92-066f3b11c7eb/Picture5.png)

**e\_array\_7.c**

```cpp
#include <stdio.h>
#include <string.h> // string 함수 사용 라이브러리 추가

// 공백문자 X
int main()
{
    // 선언 '동시' 초기화 (1) → 원칙 X: 배열크기 ≤ 초기화 변수 갯수
    printf("---원칙 X---\n");
    char X[2] = {'A', 'B', 'C', 'D', '\0'};          // char X[2] = "ABCD\0";  
                                                     // 배열의 크기 2 ≤ 초기화 변수 갯수 4 + 1(\0=null 문자 생성 메모리박스 공간)
    printf("%s\n", X);                               // %s → 문자'열' 출력:  정상출력 X(예: AB 출력 X  AB쓰레기값 출력 O)
    printf("%c %c %c %c\n", X[0], X[1], X[2], X[3]); // 정상출력 X(예: A B 출력 X  A B 쓰레기값 출력 O)
    printf("%d\n", strlen(X));                       // %d → 문자'열' 길이(strlen = string length) 출력  → \0=null 문자 전까지 길이 출력
    printf("<%c>\n", X[5]);                          // \0=null 문자 앞까지 길이 출력

    // 선언 '동시' 초기화 (2) → 수정: 권장방식 X 
    printf("---수 정---\n");
    char Y[2] = {'A', 'B', 'C', 'D'};  // 배열의 크기 2 ≤ 초기화 변수 갯수 4 
    Y[2] = '\0';                       // 배열 2번째자리에 \0=null 문자 입력/저장 → 배열끝 강제 생성
    printf("%s\n", Y);                 // %s → 문자'열' 출력:  정상출력 O(예: AB 출력 O)
    printf("%c %c\n", Y[0], Y[1]);     // 정상 출력 O(예: A B 출력 O)
    printf("%d\n", strlen(Y));         // %d → 문자'열' 길이(strlen = string length) 출력  →  \0=null 문자 전까지 길이 출력
    printf("<%c>\n", Y[2]);            // \0=null 문자 앞까지 길이 출력

    // 선언 '후' 초기화 → 원칙 X: 배열크기 ≤ 초기화 변수 갯수
    printf("---원칙 X---\n");
    char Z[2];
    printf("---입력---\n");
    scanf("%s", &Z);                   // 예: ABCD 입력/저장  →  배열의 크기 2 ≤ 초기화 변수 갯수 4 + 1(\0=null 문자 생성 메모리박스 공간)
    printf("---출력---\n");
    printf("%s\n", Z);                 // %s → 문자'열' 출력:  정상출력처럼 보임 → 정상 출력 X:  ABCD 출력 
    printf("%c %c %c %c\n", Z[0], Z[1], Z[2], Z[3]); // 정상출력처럼 보임 → 정상 출력 X:  A B C D 출력 
    printf("%d\n", strlen(Z));         // %d → 문자'열' 길이(strlen = string length) 출력  → \0=null 문자 전까지 길이 출력
    printf("<%c>\n", Z[4]);            // \0=null 문자 생성 위치 

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/9508cb91-cf20-4103-a0ba-3699c3c67b28/Picture25.png)

**e\_array\_8.c**

```cpp
#include <stdio.h>
#include <string.h> // string 함수 사용 라이브러리 추가

// 공백문자 O
int main()
{
    // 선언 '동시' 초기화 → 원칙 X: 배열크기 ≤ 초기화 변수 갯수
    printf("---원칙 X---\n");
    char X[2] = {'A', 'B', ' ', 'C', 'D', '\0'};                    // char X[2] = "AB CD";  
                                                              // 배열의 크기 2 ≤ 초기화 변수 갯수 5 + 1(\0=null 문자 생성 메모리박스 공간)
    printf("%s\n", X);                                        // %s → 문자'열' 출력:  정상출력 X(예: AB스페이스CD 출력 X  AB쓰레기값 출력 O)
    printf("%c %c %c %c %c\n", X[0], X[1], X[2], X[3], X[4]); // 정상출력 X(예: A B 스페이스 C D 출력 X  A B 쓰레기값 출력 O)
    printf("%d\n", strlen(X));                                // %d → 문자'열' 길이(strlen = string length) 출력  → \0=null 문자 전까지 길이 출력
    printf("<%c>\n", X[5]);                                   // \0=null 문자 생성 위치

    // 선언 '후' 초기화 → 원칙 X: 배열크기 ≤ 초기화 변수 갯수
    printf("---원칙 X---\n");
    char Z[2];
    printf("---입력---\n");
    scanf("%s", &Z);               // 예: AB스페이스CD 입력/저장  →  배열의 크기 2 ≤ 초기화 변수 갯수 5 + 1(\0=null 문자 생성 메모리박스 공간)
    printf("---출력---\n");
    printf("%s\n", Z);             // %s → 문자'열' 출력
    printf("%c %c\n", Z[0], Z[1]); // %c → 배열요소 문자 출력: X[2] = \0=null
    printf("%d\n", strlen(Z));     // %d → 문자'열' 길이(strlen = string length) 출력  → \0=null 문자 전까지 길이 출력
    printf("<%c>\n", Z[2]);        // \0=null 문자 생성 위치

    printf("--입력--\n");
    scanf("%s", &Z);               //  scanf 실행:  버퍼 변수(문자→스페이스) 삭제  →  버퍼 변수(문자→CD) 초기화 + \0=null 문자 생성  →  버퍼 변수(문자→엔터) 유지   
    printf("--출력--\n");
    printf("%s\n", Z);             // %s → 문자'열' 출력
    printf("%c %c\n", Z[0], Z[1]); // %c → 배열요소 문자 출력: X[2] = \0=null
    printf("%d\n", strlen(Z));     // %d → 문자'열' 길이(strlen = string length) 출력  → \0=null 문자 전까지 길이 출력
    printf("<%c>\n", Z[2]);        // \0=null 문자 생성 위치

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/a5029e0b-8d5a-410c-994e-1934e5fa361d/Picture6.png)

**e\_array\_9.c**

```cpp
#include <stdio.h>
#include <string.h> // string 함수 사용 라이브러리 추가

// scanf %s
int main()
{
    // 선언 '후' 초기화 → 예: ABCD 입력/저장
    //                       문자 자료형 메모리박스 10개 문자'열' 선언 '후' 변수 문자 ABCD 초기화
    char K[10];

    scanf("%s", &K);           // 입력서식(%s→문자'열') '초기화' 변수자료형(문자'열'→ABCD엔터) 매칭 O
                               // scanf 실행 성공:  K 주소값(&)에 문자 4개 ABCD 입력/저장(공백문자 전까지) + 문자 1개 \0=null 생성  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("%s\n", K);         // %s → 문자 4개 ABCD 출력
    printf("%d\n", strlen(K)); // %d → 문자'열' 길이(strlen = string length) 출력  → \0=null 문자 앞까지 길이 출력
    printf("<%c>\n", K[4]);    // \0=null 문자 생성 위치 
    printf("-------\n");

    scanf("%s", &K);           // scanf 실행:  버퍼 변수(문자→엔터) 삭제  →  입력서식(%s→문자'열') '초기화' 변수자료형(문자'열'→ABCD엔터) 매칭 O
                               // scanf 실행 성공:  K 주소값(&)에 문자 4개 ABCD 입력/저장(공백문자 전까지) + 문자 1개 \0=null 생성  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("%s\n", K);         // %s → 문자 4개 ABCD 출력
    printf("%d\n", strlen(K)); // %d → 문자'열' 길이(strlen = string length) 출력  → \0=null 문자 앞까지 길이 출력
    printf("<%c>\n", K[4]);    // \0=null 문자 생성 위치 
    printf("-------\n");

    scanf("%s", &K);           // scanf 실행:  버퍼 변수(문자→엔터) 삭제  →  입력서식(%s→문자'열') '초기화' 변수자료형(문자'열'→ABCD엔터) 매칭 O
                               // scanf 실행 성공:  K 주소값(&)에 문자 4개 ABCD 입력/저장(공백문자 전까지) + 문자 1개 \0=null 생성  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("%s\n", K);         // %s → 문자 4개 ABCD 출력
    printf("%d\n", strlen(K)); // %d → 문자'열' 길이(strlen = string length) 출력  → \0=null 문자 앞까지 길이 출력
    printf("<%c>\n", K[4]);    // \0=null 문자 생성 위치 
    printf("-------\n");

    scanf("%s", &K);           // scanf 실행:  버퍼 변수(문자→엔터) 삭제  →  입력서식(%s→문자'열') '초기화' 변수자료형(문자'열'→ABCD엔터) 매칭 O
                               // scanf 실행 성공:  K 주소값(&)에 문자 4개 ABCD 입력/저장(공백문자 전까지) + 문자 1개 \0=null 생성  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("%s\n", K);         // %s → 문자 4개 ABCD 출력
    printf("%d\n", strlen(K)); // %d → 문자'열' 길이(strlen = string length) 출력  → \0=null 문자 앞까지 길이 출력
    printf("<%c>\n", K[4]);    // \0=null 문자 생성 위치 
    printf("-------\n");

    scanf("%s", &K);           // scanf 실행:  버퍼 변수(문자→엔터) 삭제  →  입력서식(%s→문자'열') '초기화' 변수자료형(문자'열'→ABCD엔터) 매칭 O
                               // scanf 실행 성공:  K 주소값(&)에 문자 4개 ABCD 입력/저장(공백문자 전까지) + 문자 1개 \0=null 생성  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("%s\n", K);         // %s → 문자 4개 ABCD 출력
    printf("%d\n", strlen(K)); // %d → 문자'열' 길이(strlen = string length) 출력  → \0=null 문자 앞까지 길이 출력
    printf("<%c>\n", K[4]);    // \0=null 문자 생성 위치 
    printf("-------\n");

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/67710580-1a63-403a-8a24-0af39acec66d/Picture6.png)

**e\_array\_10.c**

```cpp
#include <stdio.h>

// scanf %c
int main()
{
    // 선언 '후' 초기화 → 예: ABCD 입력/저장
    //                       문자 자료형 메모리박스 10개 문자'열' 선언 '후' 변수 문자 ABCD 초기화
    char K[10] = {0};

    printf("---Input---\n");
    scanf("%c", &K);           // 입력서식(%c→문자) '초기화' 변수자료형(문자→ABCD엔터) 매칭 O
                               // scanf 실행 성공:  문자 1개 A 입력/저장[%c 문자자료형 A(1 Byte) K 주소값(&)에 입력/저장]  →  '초기화' 변수(문자→BCD엔터) 버퍼 유지
    printf("---Output---\n");
    printf("%s\n", K);         // %s → 문자 1개 A 출력

    printf("---Input---\n");
    scanf("%c", &K);           // 입력서식(%c→문자) '초기화' 변수자료형(문자→BCD엔터) 매칭 O
                               // scanf 실행 성공:  문자 1개 B 입력/저장[%c 문자자료형 B(1 Byte) K 주소값(&)에 입력/저장]  →  '초기화' 변수(문자→CD엔터) 버퍼 유지
    printf("---Output---\n");
    printf("%s\n", K);         // %s → 문자 1개 B 출력

    printf("---Input---\n");
    scanf("%c", &K);           // 입력서식(%c→문자) '초기화' 변수자료형(문자→CD엔터) 매칭 O
                               // scanf 실행 성공:  문자 1개 C 입력/저장[%c 문자자료형 C(1 Byte) K 주소값(&)에 입력/저장]  →  '초기화' 변수(문자→D엔터) 버퍼 유지
    printf("---Output---\n");
    printf("%s\n", K);         // %s → 문자 1개 C 출력

    printf("---Input---\n");
    scanf("%c", &K);           // 입력서식(%c→문자) '초기화' 변수자료형(문자→D엔터) 매칭 O
                               // scanf 실행 성공:  문자 1개 D 입력/저장[%c 문자자료형 D(1 Byte) K 주소값(&)에 입력/저장]  →  '초기화' 변수(문자→엔터) 버퍼 유지
    printf("---Output---\n");
    printf("%s\n", K);         // %s → 문자 1개 D 출력

    printf("---Input---\n");
    scanf("%c", &K);           // 입력서식(%c→문자) '초기화' 변수자료형(문자→엔터) 매칭 O
                               // scanf 실행 성공:  문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) K 주소값(&)에 입력/저장]
    printf("---Output---\n");
    printf("<%s>\n", K);       // %s → 문자 1개 엔터 출력

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/4a7de2e3-e659-49df-8e48-19f839e32783/Picture24.png)

**e\_array\_11.c**

```cpp
// 배열크기 X
// 예: OPQR 입력/저장  /  1234 입력/저장

#include <stdio.h>

int main()
{
    char A[2];
    printf("---Input---\n");
    scanf("%s", &A);            // 입력서식(%s→문자'열') '초기화' 변수자료형(문자'열'→OPQR엔터) 매칭 O
                                // scanf 실행 성공:  A 주소값(&)에 문자 4개 OPQR 입력/저장(공백문자 전까지) + 문자 1개 \0=null 생성(char A[2]; 메모리박스 2개 '활성화' + 3개 '생성')  →  '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("---Output---\n");  
    printf("X 문자열: %s\n", A); // %s → \0=null 문자 전까지 문자 4개 OPQR 출력 

    char B[2];
    printf("---Input---\n");      
    scanf("%s", &B);            // scanf 실행:  버퍼 변수(문자→엔터) 삭제  →  입력서식(%s→문자'열') '초기화' 변수자료형(문자'열'→OPQR엔터) 매칭 O
                                // scanf 실행 성공:  B 주소값(&)애 문자 4개 OPQR 입력/저장(공백문자 전까지) + 문자 1개 \0=null 생성(char B[2]; 메모리박스 2개 '활성화')  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("---Output---\n");
    printf("Y 문자열: %s\n", B); // %s → \0=null 문자 전까지 문자 4개 OPQR 출력 
    printf("X 문자열: %s\n", A); // %s → char B 메모리박스 '초기화' → char A 메모리박스 위치 '초기화'(문자 2개 QR) + 문자 1개 \0=null 생성: \0=null 문자 앞까지 문자 2개 QR 출력

    char C[4];
    printf("---Input---\n");
    scanf("%s", &C);            // scanf 실행:  버퍼 변수(문자→엔터) 삭제  →  입력서식(%s→문자'열') '초기화' 변수자료형(문자'열'→OPQR엔터) 매칭 O
                                // scanf 실행 성공:  C 주소값(&)에 문자 4개 OPQR 입력/저장(공백문자 전까지) + 문자 1개 \0=null 생성(char C[4]; 메모리박스 4개 '활성화')  → '초기화' 변수(문자→엔터) 버퍼 유지   
    printf("---Output---\n");
    printf("Z 문자열: %s\n", C); // %s → \0=null 문자 전까지 문자 4개 OPQR 출력 
    printf("Y 문자열: %s\n", B); // %s → char C 메모리박스 '초기화' → char B 메모리박스 위치  + 문자 1개 \0=null 생성: \0=null 문자 앞까지 문자 0개 출력 → 출력 변수 X   
    printf("X 문자열: %s\n", A); // %s → char B 메모리박스 '초기화' → char A 메모리박스 위치 '초기화'(문자 2개 QR) + 문자 1개 \0=null 생성: \0=null 문자 앞까지 문자 2개 QR 출력

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/49512f74-7ce0-4b68-8df3-f1b5c5cfc369/Picture4.png)

**e\_array\_12.c**

```cpp
// 배열크기 X + 입력서식 %c
// 예: OPQ 입력/저장   /  123 입력/저장 

#include <stdio.h>

int main()
{
    char A[2] = {0};
    printf("---Input---\n");      
    scanf("%c", &A);            // 입력서식(%c→문자) '초기화' 변수자료형(문자→OPQ엔터) 매칭 O
                                // scanf 실행 성공:  문자 1개 O 입력/저장[%c 문자자료형 O(1 Byte) A 주소값(&)에 입력/저장](char A[2]; 메모리박스 2개 '활성화')  → '초기화' 변수(문자→PQ엔터) 버퍼 유지   
    printf("---Output---\n");
    printf("A 문자열: %s\n", A); // %s → \0=null 문자 전까지 문자 1개 O 출력 

    char B[2] = {0};
    printf("---Input---\n");
    scanf("%c", &B);            // 입력서식(%c→문자) 버퍼 변수자료형(문자→PQ엔터) 매칭 O
                                // scanf 실행 성공:  문자 1개 P 입력/저장[%c 문자자료형 P(1 Byte) B 주소값(&)에 입력/저장](char B[2]; 메모리박스 2개 '활성화')  → '초기화' 변수(문자→Q엔터) 버퍼 유지   
    printf("---Output---\n");
    printf("B 문자열: %s\n", B); // %s → \0=null 문자 전까지 문자 1개 P 출력 
    printf("A 문자열: %s\n", A); // %s → \0=null 문자 전까지 문자 1개 O 출력 

    char C[3] = {0};
    printf("---Input---\n");
    scanf("%c", &C);            // 입력서식(%c→문자) 버퍼 변수자료형(문자→Q엔터) 매칭 O
                                // scanf 실행 성공:  문자 1개 Q 입력/저장[%c 문자자료형 Q(1 Byte) C 주소값(&)에 입력/저장](char C[3]; 메모리박스 3개 '활성화')  → '초기화' 변수(문자→엔터) 버퍼 유지   
    printf("---Output---\n");
    printf("C 문자열: %s\n", C); // %s → \0=null 문자 전까지 문자 1개 Q 출력 
    printf("B 문자열: %s\n", B); // %s → \0=null 문자 전까지 문자 1개 P 출력 
    printf("A 문자열: %s\n", A); // %s → \0=null 문자 전까지 문자 1개 O 출력 

    char D[4] = {0};
    printf("---Input---\n");
    scanf("%c", &D);                // 입력서식(%c→문자) 버퍼 변수자료형(문자→엔터) 매칭 O
                                    // scanf 실행 성공:  문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) D 주소값(&)에 입력/저장](char D[4]; 메모리박스 3개 '활성화')
    printf("---Output---\n");
    printf("D 문자열:\n<%s>\n", D); // %s → \0=null 문자 전까지 문자 1개 엔터 출력 
    printf("C 문자열: %s\n", C);    // %s → \0=null 문자 전까지 문자 1개 Q 출력 
    printf("B 문자열: %s\n", B);    // %s → \0=null 문자 전까지 문자 1개 P 출력 
    printf("A 문자열: %s\n", A);    // %s → \0=null 문자 전까지 문자 1개 O 출력 

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/b25e5977-8bad-4224-bd2a-57450e5e07ee/Picture5.png)

**e\_array\_13.c**

```cpp
// 배열크기 X + 입력서식 %c & %s
// 예: OPQR 입력/저장  /  1234 입력/저장

#include <stdio.h>

int main()
{
    char A[2] = {0};
    printf("---Input---\n");
    scanf("%c", &A);            // 입력서식(%c→문자) '초기화' 변수자료형(문자→OPQR엔터) 매칭 O
                                // scanf 실행 성공:  문자 1개 O 입력/저장[%c 문자자료형 O(1 Byte) A 주소값(&)에 입력/저장](char A[2]; 메모리박스 2개 '활성화')  → '초기화' 변수(문자→PQR엔터) 버퍼 유지   
    printf("---Output---\n");
    printf("A 문자열: %s\n", A); // %s → \0=null 문자 전까지 문자 1개 O 출력 

    char B[2];
    printf("---Input---\n");
    scanf("%s", &B);            // 입력서식(%s→문자'열') 버퍼 변수자료형(문자'열'→PQR엔터) 매칭 O
                                // scanf 실행 성공:  B 주소값(&)에 문자 3개 PQR 입력/저장(공백문자 전까지) + 문자 1개 \0=null 생성(char B[2]; 메모리박스 2개 '활성화')  → '초기화' 변수(문자→엔터) 버퍼 유지   
    printf("---Output---\n");
    printf("B 문자열: %s\n", B); // %s → \0=null 문자 전까지 문자 3개 PQR 출력 
    printf("A 문자열: %s\n", A); // %s → char B 메모리박스 '초기화' → char A 메모리박스 위치 '초기화'(문자 1개 R) + 문자 1개 \0=null 생성 : \0=null 문자 앞까지 문자 1개 R 출력

    char C[3] = {0};
    printf("---Input---\n");
    scanf("%c", &C);               // 입력서식(%c→문자) 버퍼 변수자료형(문자→엔터) 매칭 O
                                   // scanf 실행 성공:  문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) C 주소값(&)에 입력/저장](char C[3]; 메모리박스 3개 '활성화') 
    printf("---Output---\n");
    printf("C 문자열:\n<%s>\n", C); // %s → \0=null 문자 전까지 문자 1개 엔터 출력 
    printf("B 문자열: %s\n", B);    // %s → \0=null 문자 잔까지 문자 3개 PQR 출력 
    printf("A 문자열: %s\n", A);    // %s → char B 메모리박스 '초기화' → char A 메모리박스 위치 '초기화'(문자 1개 R) + 문자 1개 \0=null 생성: \0=null 문자 앞까지 문자 1개 R 출력

    char D[4];
    printf("---Input---\n");
    scanf("%s", &D);                // 입력서식(%s→문자'열') 버퍼 변수자료형(문자'열'→OPQR) 매칭 O
                                    // scanf 실행 성공:  D 주소값(&)에 문자 4개 OPQR 입력/저장(공백문자 전까지) + 문자 1개 \0=null 생성(char D[4]; 메모리박스 4개 '활성화')  → '초기화' 변수(문자→엔터) 버퍼 유지   
    printf("---Output---\n");
    printf("D 문자열: %s\n", D);    // %s → \0=null 문자 전까지 문자 4개 OPQR 출력 
    printf("C 문자열:\n<%s>\n", C); // %s → char D 메모리박스 '초기화' → char C 메모리박스 위치 문자 1개 \0=null 생성: \0=null 문자 앞까지 문자 O개 출력 → 출력 변수 X   
    printf("B 문자열: %s\n", B);    // %s → \0=null 문자 전까지 문자 3개 PQR 출력 
    printf("A 문자열: %s\n", A);    // %s → char B 메모리박스 '초기화' → char A 메모리박스 위치 '초기화'(문자 1개 R) + 문자 1개 \0=null 생성: \0=null 문자 앞까지 문자 1개 R 출력

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/b9bac212-2b4a-49db-a061-a9d67db1e966/Picture21.png)

**e\_array\_14.c**

```cpp
// 배열크기 X + 입력서식 %c & %s
// 예: OPQR → OPQRSTUVWXYZ 입력/저장  /  1234 입력/저장 → 12345678 입력/저장

#include <stdio.h>

int main()
{
    char A[2] = {0};
    printf("---Input---\n");
    scanf("%c", &A);            // 입력서식(%c→문자) '초기화' 변수자료형(문자→OPQR엔터) 매칭 O
                                // scanf 실행 성공:  문자 1개 O 입력/저장[%c 문자자료형 O(1 Byte) A 주소값(&)에 입력/저장](char A[2]; 메모리박스 2개 '활성화')  → '초기화' 변수(문자→PQR엔터) 버퍼 유지   
    printf("---Output---\n");
    printf("A 문자열: %s\n", A); // %s → \0=null 문자 전까지 문자 1개 O 출력 

    char B[2] = {0};
    printf("---Input---\n");
    scanf("%c", &B);            // 입력서식(%c→문자) '초기화' 변수자료형(문자→PQR엔터) 매칭 O
                                // scanf 실행 성공:  문자 1개 P 입력/저장[%c 문자자료형 P(1 Byte) B 주소값(&)에 입력/저장](char B[2]; 메모리박스 2개 '활성화')  → '초기화' 변수(문자→QR엔터) 버퍼 유지   
    printf("---Output---\n");
    printf("B 문자열: %s\n", B); // %s → \0=null 문자 전까지 문자 1개 P 출력 
    printf("A 문자열: %s\n", A); // %s → \0=null 문자 전까지 문자 1개 O 출력 

    char C[2];
    printf("---Input---\n");
    scanf("%s", &C);               // 입력서식(%s→문자'열') 버퍼 변수자료형(문자'열'→QR엔터) 매칭 O
                                   // scanf 실행 성공:  C 주소값(&)에 문자 2개 QR 입력/저장(공백문자 전까지) + 문자 1개 \0=null 생성(char C[2]; 메모리박스 2개 '활성화')  → '초기화' 변수(문자→엔터) 버퍼 유지   
    printf("---Output---\n");
    printf("C 문자열: %s\n", C);    // %s → \0=null 문자 전까지 문자 2개 QR 출력 
    printf("B 문자열:\n<%s>\n", B); // %s → char C 메모리박스 '초기화' → char B 메모리박스 위치 '초기화'(문자 1개 \0): \0=null 문자 전까지 문자 O개 출력 → 출력 변수 X   
    printf("A 문자열: %s\n", A);    // %s → \0=null 문자 전까지 문자 1개 O 출력 

    char D[3];
    printf("---Input---\n");
    scanf("%s", &D);            // scanf 실행:  버퍼 변수(문자→엔터) 삭제  →  입력서식(%s→문자'열') '초기화' 변수자료형(문자'열'→OPQRSTUV엔터) 매칭 O
                                // scanf 실행 성공:  D 주소값(&)에 문자 12개 OPQRSTUVWSYZ엔터 입력/저장(공백문자 전까지) + 문자 1개 \0=null 생성(char D[3]; 메모리박스 3개 '활성화')  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("---Output---\n");
    printf("D 문자열: %s\n", D); // %s → \0=null 문자 전까지 문자 12개 OPQRSTUV 출력 
    printf("C 문자열: %s\n", C); // %s → char D 메모리박스 '초기화' → char C 메모리박스 위치 '초기화'(문자 2개 RS): \0=null 문자 전까지 문자 5개 RSTUVWXYZ 출력 
    printf("B 문자열: %s\n", B); // %s → char D 메모리박스 '초기화' → char B 메모리박스 위치 '초기화'(문자 2개 TU): \0=null 문자 전까지 문자 3개 TUVWXYZ 출력 
    printf("A 문자열: %s\n", A); // %s → char D 메모리박스 '초기화' → char A 메모리박스 위치 '초기화'(문자 1개 V) + 문자 1개 \0=null 생성: \0=null 문자 전까지 문자 1개 VWXYZ 출력 

    char E[2] = {0};
    printf("---Input---\n");
    scanf("%c", &E);               // 입력서식(%c→문자) 버퍼 변수자료형(문자→엔터) 매칭 O
                                   // scanf 실행 성공:  문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) C 주소값(&)에 입력/저장](char E[2]; 메모리박스 2개 '활성화') 
    printf("---Output---\n");
    printf("E 문자열:\n<%s>\n", E); // %s → \0=null 문자 전까지 문자 1개 엔터 출력 
    printf("D 문자열: %s\n", D);    // %s → \0=null 문자 전까지 문자 8개 OPQRSTUV 출력 
    printf("C 문자열: %s\n", C);    // %s → char D 메모리박스 '초기화' → char C 메모리박스 위치 '초기화'(문자 2개 RS): \0=null 문자 전까지 문자 5개 RSTUVWXYZ 출력 
    printf("B 문자열: %s\n", B);    // %s → char D 메모리박스 '초기화' → char B 메모리박스 위치 '초기화'(문자 2개 TU): \0=null 문자 전까지 문자 3개 TUVWXYZ 출력 
    printf("A 문자열: %s\n", A);    // %s → char D 메모리박스 '초기화' → char A 메모리박스 위치 '초기화'(문자 1개 V) + 문자 1개 \0=null 생성: \0=null 문자 전까지 문자 1개 VWXYZ 출력 

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/2580e574-db84-4bea-99b3-f0d800c439d8/Picture1.png)
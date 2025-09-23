# One-Dimensional Array

## **One-Dimensional Array 1차원 배열**

### **Concept 개념**

메모리(Memory)에 연속적으로 할당된 '동일' 데이터 유형(Data Type)의 변수 n개 모음

**변수**
동일 데이터 유형(Data Type)의 데이터(Data) 저장 공간
\= 메모리(Memory) 공간
예:
int A;

**배열**
동일 데이터 유형(Data Type)의 변수 확장
예:
int A\[3\];

**구조체**
여러 데이터 유형(Data Type)의 변수 확장
예:
struct {char D\[3\]; float C; float B; int A;} human;
(D = 이름, C = 키, B = 몸무게, A = 나이)

**클라스** (C언어에 無, C++, Python, Java에 有)
구조체 + 함수(라이브러리 내 기본 함수 + 사용자 지정 함수 + 라이브러리 내 사용자 지정 함수)
예:
구조체 변수 human + Diet 함수(몸무게 0.5 kg 감소 함수 → 사용자 지정 함수)
\= human의 Diet 함수를 실행할 때마다 몸무게 0.5 kg 씩 감소하는 프로그램
struct {char D\[3\]; float C; float B; int A; diet} human;

### **Structure 구조**

![](https://t9003081320.p.clickup-attachments.com/t9003081320/3b04dc81-f3d5-484c-afe8-f44cf530bffe/Picture1.png)

**자료형(Data Type)**
int, float, char

**크기(Size)**
배열에 저장할 데이터(Data) 갯수 = 메모리박스(Memory Box) 갯수
선언시 Must Define
선언시 Not Define → 같은 Code Line에서 초기화시(= 선언 '동시' 초기화시) 요소갯수로 Can Define
예:
int A\[\] = {1, 2, 3};
\[ \] 대괄호내 배열크기 지정 X → { } 중괄호내 요소(Element) 갯수 지정 O → 배열크기 지정 O

**요소(Element)**
배열에 저장된 값 = 각 메모리박스(Memory Box)에 저장된 값
예:
int A\[3\] = {1, 2, 3};
1, 2, 3 = 요소(Element)

갯수
정수, 소수: 배열크기 => 요소 갯수
예:
float B\[3\] = {0.5, 0.25, 0.125};

문자: 배열크기 => 요소 갯수 +1
∵ `scanf %s` 문자열 마지막 \\0 = null 문자 자동 초기화
∵ `printf %s` \\0 = null 문자 전까지 출력
예:
char C\[4\] = {X, Y, Z, \\0};
char D\[4\];
scanf("%s", &D); → X, Y, Z 초기화 → \\0 = null 문자 자동 초기화

※ 요소 갯수 = 배열 크기 / 요소 크기
예:
int\[3\] = {1, 2, 3}; → 정수 4 Bytes
요소 갯수 = (3 x 4 Bytes) / 4 Bytes = 3개

**색인(Index)**
배열에 저장된 각 요소(Element)에 접근하기 위한 값 = 각 요소(Element) 초기화 위치
색인(Index)값 = 0 ~ +(배열크기 -1)
예:
배열 첫번째 = 0, 배열 두번째 = 1 ....... 배열 마지막번째 = +(배열크기 -1)

### **Address 주소값**

자료형(Data Type)의 크기만큼 색인(Index) 마다 증가
예:
int A\[0\] 주소값 = 0x1234 → int A\[1\] 주소값 = 0x1238

각 색인(Index)의 주소값 = 각 색인(Index)의 첫번째 Byte의 주소값

![](https://t9003081320.p.clickup-attachments.com/t9003081320/90539707-9274-47fe-b8c1-46b893220dd7/image.png)

### **Define/Initialise 선언/초기화**

**선언**
자료형 + 배열이름(변수명) + 배열크기
예:
int X\[3\];
float Y\[3\];
char Z\[4\];
※ 선언시 메모리박스(Memory Box) 크기(배열크기)만큼 자동 \\0 = null Set-Up X

**출력**
문자 '열'
`printf`함수 + `%s` 문자'열' 출력서식
/0 = null 문자 전까지 출력 ∵ printf %s 고유 성질
※ 배열선언시 사용 O → 출력가능
※ 배열요소 전체 \\0 = null 문자 전까지 출력

문자 '1개'
`printf`함수 + `%c` 문자1개 출력서식
선언한 자료형크기 만큼 문자(%c) 1개 출력
※ 배열선언시 사용 X → 출력오류
※ 배열요소 각각 출력 O
예:
char Z\[4\] = {'A', 'B', 'C', '\\0'};
printf(“%c %c %c”, C\[0\], C\[1\], C\[2\]);

정수/소수 '열'
Code 작성 要
∵ printf %s(문자 '열' 출력서식) 같은 정수/소수 '열' 출력서식 존재 X

정수/소수 '1개'
`printf`함수 + `%d` `%f` 정수/소수1개 출력서식
선언한 자료형크기 만큼 정수/소수(%d/%f) 1개 출력
예:
int X\[3\] = {1, 2, 3};
printf(“%d %d %d”, X\[0\], X\[1\], X\[2\]);

**선언 '동시' 초기화**
문자
`{' ',}`
예:
char Z\[4\] = {'A', 'B', 'C', '\\0'};
`" "`
예:
char Z\[3\] = "ABC\\0";
※ 배열선언시 \\0=null Set-Up 필요 O
∵ printf %s (\\0=null 문자 전까지 출력) 사용 O
※ 배열크기 ≥ 초기화 요소갯수 + 1개(\\0= null 문자 메모리박스 공간)
※ 배열크기 < 초기화 요소갯수
배열크기 변수갯수 = 메모리박스 '활성화 O' + (초과 변수갯수 = 메모리박스 '생성 X')
예:
char C\[2\] = {'A', 'B', 'C', 'D', '\\0'};
A B 2개 출력 → 메모리박스 '활성화' 갯수 2개(A, B) \+ 쓰레기값(%)
※ 공백문자(엔터, 스페이스, 탭) 메모리박스(Memory Box) 문자인식 O
예:
char Z\[6\] = {'A', 'B', ' ', 'C', 'D', '\\0'};
char Z\[6\] = "12 34\\0";

정수/소수
`{ }`
예:
int X\[3\] = {1, 2, 3};
예:
float Y\[3\] = {0.5, 0.25, 0.125}
※ 선언시 \\0 = null Set-Up 필요 X ∵ printf %s (\\0=null 문자 전까지 출력) 사용 X
※ 배열크기 ≥ 초기화 요소갯수

**선언 '후' 초기화**
문자 '열'
`scanf` 함수 + `%s` 문자'열' 입력서식
예:
char Z\[4\];
scanf("%s", &C);
※ 문자열 마지막 \\0 = null 문자 생성 O
※ 배열선언시 \\0 = null Set-Up 필요 X ∵ scanf %s 문자열 마지막 \\0 = null 문자 생성 O
※ 배열크기 ≥ 초기화 변수갯수 + 1개(\\0 = null 문자 생성 공간)
※ 배열크기 < 초기화 변수갯수
배열크기 변수갯수 = 메모리박스 '활성화 O' + (초과 변수갯수 = 메모리박스 '생성 O')
∵ scanf("%s", &C);
→ 선언한 자료형크기와 관계없이
주소값(&)을 시작으로 초기화
예:
char Z\[2\];
scanf("%s", &Z) → A, B, C 초기화
A B C 2+1개 출력 (메모리박스 '활성화' 갯수 2개(A, B) \+ '생성' 갯수 = 2(C , \\0)

※ 공백문자(엔터, 스페이스) 문자인식 X
1) 공백문자 '포함' '버퍼' 입력/저장
2) 공백문자 '제외' '메모리박스' 입력/저장
예:
ABC엔터 초기화
→ ABC 메모리박스 입력/저장 + \\0 = null 문자 생성 → 엔터 버퍼유지
예:
A스페이스B스페이스C엔터 초기화
→ A 메모리박스 입력/저장 + \\0 = null 문자 생성 → 스페이스B스페이스C엔터 버퍼유지
예:
스페이스스페이스ABCD엔터(엔터엔터ABCD엔터)
스페이스스페이스 버퍼삭제 → ABCD 메모리박스 입력/저장 + \\0 = null 문자 생성

문자 1개
`scanf` 함수 + `%c` 문자 1개 입력서식
예:
char Z\[4\] = {0};
∵ \\0=null Set-Up 필요 O
printf %s (\\0=null 문자 전까지 출력) 출력시 쓰레기값(Z\[1\]~\[3\])제외 초기화 문자 1개(Z\[0\])만 출력
scanf("%c", &Z\[0\]);
※ 문자열 마지막 \\0 = null 문자 생성 X
※ 배열선언시 \\0 =null Set-Up 필요 O ∵ printf %s (\\0 = null 문자 전까지 출력) 사용 O
※ 배열크기 = 초기화 변수갯수 + 1개 이상 (\\0 = null 문자 메모리박스 공간)
※ 공백문자(엔터, 스페이스) 문자인식 O
1) 공백문자 '포함' '버퍼' 입력/저장
2) 공백문자 '포함' '메모리박스' 입력/저장

정수/소수 '열'
`scanf` 함수 존재 無
1) Manual 要
예:
int X\[3\];
X\[0\] = 1;
X\[1\] = 2;
X\[2\] = 3;
2) 코드작성 要
배열위치(Index) 지정 후 배열요소(Element) 각각 초기화 = 배열시작 & 끝 인식 O

※ 배열선언시 \\0 = null Set-Up 필요 X ∵ printf %s (\\0 = null 문자 전까지 출력) 사용 X
※ 배열크기 ≥ 초기화 변수갯수

### **Type 유형**

**int 정수 배열**
예:
선언 '동시' 초기화
int X\[3\] = {1, 2, 3}
int Y\[\] ={1, 2, 3};

선언 '후' 초기화
1) Manual 要
예:
int X\[3\];
X\[0\] = 1;
X\[1\] = 2;
X\[2\] = 3;
2) 코드작성 要

**float 소수 배열**
예:
선언 '동시' 초기화
float X\[3\] = {0.5, 0.25, 0.125}
float Y\[\] ={0.5, 0.25, 0.125};

선언 '후' 초기화
1) Manual 要
예:
float Y\[3\];
Y\[0\] = 0.5;
Y\[1\] = 0.25;
Y\[2\] = 0.125;
2) 코드작성 要

**char 문자 배열**
예:
선언 '동시' 초기화
char X\[4\] = {'A', 'B', 'C', '\\0'};
char Y\[\] = {'A', 'B', 'C', '\\0'};
char X\[5\] = {'A', 'B', ' ', 'C', '\\0'};
char Y\[\] = {'A', 'B', ' ', 'C', '\\0'};

char X\[4\] = "ABC\\0";
char Y\[\] = "ABC\\0";
char X\[5\] = "AB C\\0";
char Y\[\] = "AB C\\0";

선언 '후' 초기화
char Z\[4\];
scanf("%s", &Z); → A, B, C 초기화 가능 O
char Z\[\];
scanf("%s", &Z); → A, B, C 초기화 가능 X
∵ 같은 Code Line에서 초기화시(= 선언 '동시' 초기화시) 요소갯수로 배열크기 Can Define

### **Example) int\_float\_char**

**a\_one\_arr\_1.c**

```perl
#include <stdio.h>

int main()
{
    int number_1[3];              // 선언
    int number_2[3] = {0, 1, 2};  // 선언 동시 초기화 1
    int number_3[] = {0, 1, 2};   // 선언 동시 초기화 2

    // 선언 후 초기화 number_1
    number_1[0] = 0;
    number_1[1] = 1;
    number_1[2] = 2;
    printf(" %d\n", number_1[0]);
    printf(" %d\n", number_1[1]);
    printf(" %d\n", number_1[2]);

    printf("===\n");

    // 선언 후 초기화 number_3
    // 재 초기화 가능 O
    printf(" %d\n", number_3[0]);
    printf(" %d\n", number_3[1]);
    printf(" %d\n", number_3[2]);

    printf("===\n");
    
    number_3[0] = 3;
    number_3[1] = 4;
    number_3[2] = 5;
    printf(" %d\n", number_3[0]);
    printf(" %d\n", number_3[1]);
    printf(" %d\n", number_3[2]);

    return 0;
}
```

**a\_one\_arr\_2.c**

```cpp
#include <stdio.h>

int main()
{
    int number_1[3];             // 선언
    int number_2[3] = {0, 1, 2}; // 선언 동시 초기화 1
    int number_3[] = {0, 1, 2};  // 선언 동시 초기화 2

    // 선언 후 초기화 number_1
    for (int i = 0; i < 3; i++)
    {
        number_1[i] = i;
    }
    for (int i = 0; i < 3; i++)
    {
        printf(" %d\n", number_1[i]);
    }

    printf("===\n");

    // 선언 후 초기화 number_3
    for (int i = 0; i < 3; i++)
    {
        printf(" %d\n", number_3[i]);
    }

    printf("===\n");
    
    for (int i = 0; i < 3; i++)
    {
        number_3[i] = i + 3;    // i + 3:  0, 1, 2 대신 3, 4, 5 초기화
    }
    for (int i = 0; i < 3; i++)
    {
        printf(" %d\n", number_3[i]);
    }

    return 0;
}
```

**a\_one\_arr\_3.c**

```perl
#include <stdio.h>

int main()
{
    int array_int[3];
    char array_char[5];
    float array_float[7];

    int array_size;       // 배열 총 Bytes 크기
    int element_size;     // 요소 각 Bytes 크기

    array_size = sizeof(array_int);                                   
    element_size = sizeof(array_int[0]);                              
    printf("  int 배열 크기: %d\n", array_size);                      // 12 Bytes
    printf("  int 요소 크기: %d\n", element_size);                    //  4 Bytes
    printf("  int 배열 크기: %d\n", sizeof(array_int));               // 12 Bytes
    printf("  int 요소 크기: %d\n", sizeof(array_int[0]));            //  4 Bytes
    printf("  int 요소 갯수: %d\n", array_size / element_size);       // 3개

    array_size = sizeof(array_char);
    element_size = sizeof(array_char[0]);
    printf(" char 배열 크기: %d\n", array_size);                      // 5 Bytes
    printf(" char 요소 크기: %d\n", element_size);                    // 1 Byte
    printf(" char 배열 크기: %d\n", sizeof(array_char));              // 5 Bytes
    printf(" char 요소 크기: %d\n", sizeof(array_char[0]));           // 1 Byte
    printf(" char 요소 갯수: %d\n", array_size / element_size);       // 5개

    array_size = sizeof(array_float);
    element_size = sizeof(array_float[0]);
    printf("float 배열 크기: %d\n", array_size);                      // 28 Bytes
    printf("float 요소 크기: %d\n", element_size);                    //  4 Bytes
    printf("float 배열 크기: %d\n", sizeof(array_float));             // 28 Bytes
    printf("float 요소 크기: %d\n", sizeof(array_float[0]));          //  4 Bytes
    printf("float 요소 갯수: %d\n", array_size / element_size);       // 7개

    return 0;
}
```

**a\_one\_arr\_4.c**

```perl
#include <stdio.h>

int main()
{
    int array_int[3];
    char array_char[5];
    float array_float[7];

    // 배열의 주소 =  0번째 색인(Index)/위치 요소 주소
    printf("     array_int 주소: %d\n", &array_int);
    printf("  array_int[0] 주소: %d\n", &array_int[0]);
    printf("  array_int[1] 주소: %d\n", &array_int[1]);
    printf("  array_int[2] 주소: %d\n", &array_int[2]);

    printf("    array_char 주소: %d\n", &array_char);
    printf(" array_char[0] 주소: %d\n", &array_char[0]);
    printf(" array_char[1] 주소: %d\n", &array_char[1]);
    printf(" array_char[2] 주소: %d\n", &array_char[2]);

    printf("   array_float 주소: %d\n", &array_float);
    printf("array_float[0] 주소: %d\n", &array_float[0]);
    printf("array_float[1] 주소: %d\n", &array_float[1]);
    printf("array_float[2] 주소: %d\n", &array_float[2]);

    return 0;
}
```

### **Example) char-string\_1\_concept**

**b\_one\_arr\_string\_1.c**

```perl
#include <stdio.h>

int main()
{
    char array_char_1[10];                                                       // 선언
    char array_char_2[10] = {'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j'};  // 선언 동시 초기화1
    char array_char_3[] = {'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j'};    // 선언 동시 초기화2
    // 아래 Code에 prinf %s(\0 = null 문자 전까지 출력)이 없으므로, \0 = null Set-Up 필요 X

    // 선언 후 초기화 array_char_1 
    // 변수와 마찬가지로 초기화 된 값을 다시 초기화 가능 O
    array_char_1[0] = 'a';
    array_char_1[1] = 'b';
    array_char_1[2] = 'c';
    array_char_1[3] = 'd';
    array_char_1[4] = 'e';
    array_char_1[5] = 'f';
    array_char_1[6] = 'g';
    array_char_1[7] = 'h';
    array_char_1[8] = 'i';
    array_char_1[9] = 'j';

    // 배열 출력 array_char_1 
    printf("%c\n", array_char_1[0]);
    printf("%c\n", array_char_1[1]);
    printf("%c\n", array_char_1[2]);
    printf("%c\n", array_char_1[3]);
    printf("%c\n", array_char_1[4]);
    printf("%c\n", array_char_1[5]);
    printf("%c\n", array_char_1[6]);
    printf("%c\n", array_char_1[7]);
    printf("%c\n", array_char_1[8]);
    printf("%c\n", array_char_1[9]);

    return 0;
}
```

**b\_one\_arr\_string\_2.c**

```plain
#include <stdio.h>

int main()
{
    char array_char_1[10];                                                       // 선언
    char array_char_2[10] = {'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j'};  // 선언 동시 초기화1
    char array_char_3[] = {'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j'};    // 선언 동시 초기화2
    // 아래 Code에 prinf %s(\0=null 문자 앞까지 출력)이 없으므로, \0=null Set-Up 필요 X

    // 선언 후 초기화 가능 X 
    // array_char_1 = {'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j'}; 

    // 선언 후 초기화 array_char_1 
    for (int i = 0; i < 10; i++)
    {
        array_char_1[i] = 97 + i;   // 97 = 'a', 98 = 'b', ...
    }

    // 배열 출력 array_char_1 
    printf("array_char_1 배열 출력\n");
    for (int i = 0; i < 10; i++)
    {
        printf("%c ", array_char_1[i]);
    }
    printf("\n");

    // 선언 후 초기화 array_char_2
    // 변수와 마찬가지로 초기화 된 값을 다시 초기화 가능 O
    for (int i = 0; i < 10; i++)
    {
        array_char_2[i] = 107 + i; // 107 = 'k', 108 = 'l', ...
    }

    // 배열 출력 array_char_2
    printf("array_char_2 배열 출력\n");
    for (int i = 0; i < 10; i++)
    {
        printf("%c ", array_char_2[i]);
    }
    printf("\n");

    return 0;
}
```

**b\_one\_arr\_string\_3.c**

```cpp
#include <stdio.h>

int main()
{
    char array_char_1[10] = {0};          // 선언
    char array_char_2[10] = "abcdefghij"; // 선언 동시 초기화1
    char array_char_3[] = "abcdefghij";   // 선언 동시 초기화2

    // 선언 후 초기화 가능 X 
    // array_char_1 = "abcdefghij";

    // 선언 후 초기화 가능 O array_char_1 
    scanf("%s", &array_char_1);           // abcdefghij 초기화
    
    // 배열 출력 array_char_1 
    printf("array_char_1 배열 출력\n");
    for (int i = 0; i < 10; i++)
    {
        printf("%c ", array_char_1[i]);
    }
    printf("\n");

    // 선언 후 초기화 가능 O array_char_1 
    for (int i = 0; i < 10; i++)
    {
        array_char_1[i] = 107 + i; // 107 = 'k', 108 = 'l', ...
    }

    // 배열 출력 array_char_1 
    printf("array_char_1 배열 출력\n");
    for (int i = 0; i < 10; i++)
    {
        printf("%c ", array_char_1[i]);
    }
    printf("\n");

    // 배열 출력 array_char_2 
    printf("array_char_2 배열 출력\n");
    for (int i = 0; i < 10; i++)
    {
        printf("%c ", array_char_2[i]);
    }
    printf("\n");

    // 배열 출력 array_char_3 
    printf("array_char_3 배열 출력\n");
    for (int i = 0; i < 10; i++)
    {
        printf("%c ", array_char_3[i]);
    }
    printf("\n");

    return 0;
}
```

**b\_one\_arr\_string\_4.c**

```plain
#include <stdio.h>

int main()
{
    // 변수 예시
    int X = 10; // 선언 동시 초기화
    int Y;      // 선언
    Y = 10;     // 변수 정수 1개 초기화

    // 배열 가능 O 
    char array_char_1[10] = "abcdefghij"; // 선언 동시 초기화
    char array_char_2[10];                // 선언  후  초기화
    scanf("%s, &array_char_1");           // 초기화 벙법 1
    array_char_1[0] = 'a';                // 초기화 방법 2
    array_char_1[1] = 'b';
    array_char_1[2] = 'c';
    array_char_1[3] = 'd';
    array_char_1[4] = 'e';
    array_char_1[5] = 'f';
    array_char_1[6] = 'g';
    array_char_1[7] = 'h';
    array_char_1[8] = 'i';
    array_char_1[9] = 'j';
    for (int i = 0; i < 10; i++)          // 초기화 방법 3
    {
        array_char_1[i] = 97 + i;         // 97 = 'a', 98 = 'b', ...
    }

    // 배열 가능 X
    char array_char_3[10];                // 선언
    array_char_3[10] = "abcdefghij";      // 배열 문자열 초기화
    array_char_3[10] = {'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j'}; // 배열 문자열 초기화

    return 0;
}
```

**b\_one\_arr\_string\_5.c**

```perl
#include <stdio.h>

int main()
{
    char array_char_1[10];                                                    // 선언
    char array_char_2[10] = "abcdefghij";                                     // 선언 동시 초기화 1
    char array_char_3[] = "abcdefghij";                                       // 선언 동시 초기화 2
    char array_char_4[] = {'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j'}; // 선언 동시 초기화 3

    int array_size;                                                           // 배열 Bytes 크기
    int element_size;                                                         // 요소 Bytes 크기

    array_size = sizeof(array_char_1);
    element_size = sizeof(array_char_1[0]);
    printf("array_char_1 배열 크기 : %d\n", array_size);                      // 10 Bytes
    printf("array_char_1 요소 크기 : %d\n", element_size);                    //  1 Byte
    printf("array_char_1 배열 크기 : %d\n", sizeof(array_char_1));            // 10 Bytes
    printf("array_char_1 요소 크기 : %d\n", sizeof(array_char_1[0]));         //  1 Byte
    printf("array_char_1 요소 갯수 : %d\n", array_size / element_size);       // 10개

    array_size = sizeof(array_char_2);
    element_size = sizeof(array_char_2[0]);
    printf("array_char_2 배열 크기: %d\n", array_size);                      // 10 Bytes: "  " + 배열크기 선언 O → 자동으로 문자열 끝 \0 = null 생성/인식 X 
    printf("array_char_2 요소 크기: %d\n", element_size);                    //  1 Byte
    printf("array_char_2 배열 크기: %d\n", sizeof(array_char_2));            // 10 Bytes: "  " + 배열크기 선언 O → 자동으로 문자열 끝 \0 = null 생성/인식 X 
    printf("array_char_2 요소 크기: %d\n", sizeof(array_char_2[0]));         //  1 Byte
    printf("array_char_2 요소 갯수: %d\n", array_size / element_size);       // 10개


    array_size = sizeof(array_char_3);
    element_size = sizeof(array_char_3[0]);
    printf("array_char_3 배열 크기: %d\n", array_size);                      // 11 Bytes: "  " + 배열크기 선언 X → 자동으로 문자열 끝 \0 = null 생성/인식 O   ∵ abcdefghij = 문자열상수 O (문자열상수는 마지막 \0 = null 문자 생성/인식 O)   
    printf("array_char_3 요소 크기: %d\n", element_size);                    //  1 Byte
    printf("array_char_3 배열 크기: %d\n", sizeof(array_char_3));            // 11 Bytes: "  " + 배열크기 선언 X → 자동으로 문자열 끝 \0 = null 생성/인식 O   ∵ abcdefghij = 문자열상수 O (문자열상수는 마지막 \0 = null 문자 생성/인식 O)   
    printf("array_char_3 요소 크기: %d\n", sizeof(array_char_3[0]));         //  1 Byte
    printf("array_char_3 요소 갯수: %d\n", array_size / element_size);       // 11개

    array_size = sizeof(array_char_4);
    element_size = sizeof(array_char_4[0]);
    printf("array_char_4 배열 크기: %d\n", array_size);                      // 10 Bytes: {  } + 배열크기 선언 X → 자동으로 문자열 끝 \0 = null 생성/인식 X   ∵ abcdefghij = 문자열상수 X (문자열상수는 마지막 \0 = null 문자 생성/인식 O)     
    printf("array_char_4 요소 크기: %d\n", element_size);                    //  1 Byte
    printf("array_char_4 배열 크기: %d\n", sizeof(array_char_4));            // 10 Bytes: {  } + 배열크기 선언 X → 자동으로 문자열 끝 \0 = null 생성/인식 X   ∵ abcdefghij = 문자열상수 X (문자열상수는 마지막 \0 = null 문자 생성/인식 O)     
    printf("array_char_4 요소 크기: %d\n", sizeof(array_char_4[0]));         //  1 Byte
    printf("array_char_4 요소 갯수: %d\n", array_size / element_size);       // 10개

    return 0;
}
```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/6272ca53-b52a-4307-9505-958aa17d9004/image.png)
`char array_char[] = "abcdefghij"`
선언 동시 초기화
배열 크기 선언 X
요소 갯수 10개
"abcdefghij" = 문자열 상수 O → 문자열 마지막 \\0 = null 문자 존재/인식 O
∴ 배열 크기 = 11 → vscode에서 Mouse Overall시 char \[11\] 확인 가능 O

`char array_char[] = {'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j'};`
선언 동시 초기화
배열 크기 선언 X
요소 갯수 10개
'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j' = 문자열 상수 X → 문자열 마지막 \\0 = null 문자 존재/인식 X
∴ 배열 크기 = 10

### **Example) char-string\_2\_function**

#### **string**
'문자'열 자료형 O 정수/소수열 자료형 X
C++/Python Language 有 자료형 (C Language에는 無)
∴ 불편한점 발생 → 함수 라이브러리(.h 파일) 지원

함수 라이브러리 사용 전제

`\0 = null`
문자열 마지막 \\0 = null 문자 要
∵ 문자열 함수 \\0 = null 문자 전까지 인식/실행 O

**선언 후 초기화**
scanf %s: 문자열 마지막 \\0 = null 문자 생성 O
배열크기 >= 문자갯수 + 1

**선언 동시 초기화**
배열크기 선언 O
\[n\] + " ": 문자열 마지막 \\0 = null 문자 생성 O
배열크기 ≥ 문자갯수 + 1
문자열 마지막 \\0 = null Set-Up 要 X
\[n\] + { }: 문자열 마지막 \\0 = null 문자 생성 X
배열크기 ≥ 문자갯수 + 1
문자열 마지막 \\0 = null Set-Up 要 O
배열크기 선언 X
\[\] + " ": 문자열 마지막 \\0 = null 문자 생성 O
배열크기 ≥ 문자갯수 + 1
문자열 마지막 \\0 = null Set-Up 要 X
\[\] + { }: 문자열 마지막 \\0 = null 문자 생성 X
배열크기 ≥ 문자갯수 + 1
문자열 마지막 \\0 = null Set-Up 要 O

함수 종류

`strlen()`
\\0 = null 문자 제외 문자열 길이

`strcat(), strncat()`
문자열에 다른 문자열 이어 연결

`strcpy(), strncpy()`
문자열을 복사

`strcmp(), strncmp()`
2개의 문자열 비교

`toupper(), tolower()`
문자열 All 대문자 or All 소문자 변경

`atoi(), atol(), atoll(), atof()`
문자열 다른 자료형 변환

**※ 함수 비교**

| 문자열 함수 | 요소<br>변경 | 요소<br>초기화 | 출력 |
| ---| ---| ---| --- |
| 함수(stirng\_1);<br>함수(string\_1, string\_2); | 배열 자체<br>printf(%s, string\_1); | 함수 반환값(Return)<br>printf("% ", 함수(string\_1));<br>printf("% ", 함수(string\_1, string\_2)); |
| strlen | X | X | 문자열(%s) | 반환값 → 문자열 길이(%d) |
| strcmp | X | X | 문자열(%s) | 반환값 → 0, -1, 1(%d) |
| strcat, strncat | O string\_1 | O string\_1 | 변경 문자열(%s) | 반환값 → 주소값(%p, %d) |
| strcpy, strncpy | O string\_1 | O string\_1 | 변경 문자열(%s) | 반환값 → 복사된 문자열에 대한 포인터(%p, %d) |
|  |  |  |  | 위의 함수들의 반환값은 문자열 변경 X<br>∴ 반환값을 초기화할 필요 X<br>∴ 배열 출력 필요 O |
| toupper, tolower | O string\_1 | X | 변수에 초기화시<br>변경 문자열(%s) | 반환값 → 문자 1개(%c)<br><br>변경 문자열(%s)<br>∴ 출력값 無 (Segmentation Fault)<br>∴ 전체 초기화 필요 O<br>초기화 하지 않아도<br>변경문자 1개 출력가능 O(%c)<br>변경문자 1개 ASCII Code 변환정수 출력가능 O(%d) |

![](https://t9003081320.p.clickup-attachments.com/t9003081320/3f2c50ec-e48b-4361-b18d-1aab336aac41/Picture2.jpg)

`\0 = null`

**c\_one\_arr\_string\_1\_null\_a.c**

```cpp
#include <stdio.h>

int main()
{
    char array_char_1[100];                       // 선언  후  초기화
    char array_char_2[11] = "abcdefghij";         // 선언 동시 초기화 1
    char array_char_3[] = "klmnopqrst";           // 선언 동시 초기화 2

    scanf("%s", &array_char_1);                   // %s → 문자열 마지막 \0 = null 문자 생성
    printf("array_char_1:%s\n", array_char_1);    // \0 = null 문자 전까지 출력

    printf("문자열 상수  abcdefghij\n");           
    printf("문자열 상수  klmnopqrst\n");           
    printf("array_char_2 elements: %s\n", array_char_2);
    printf("array_char_3 elements: %s\n", array_char_3);
    printf("array_char_2 size:     %d\n", sizeof(array_char_2));
    printf("array_char_3 size:     %d\n", sizeof(array_char_3));

    return 0;
}
```

**c\_one\_arr\_string\_1\_null\_b.c**

```perl
#include <stdio.h>

int main()
{
    char array_char_1[100] = {0};                              // 선언  후 초기화
    char array_char_2[11] = "abcdefghij";                      // 선언 동시 초기화 1
    char array_char_3[] = "klmnopqrst";                        // 선언 동시 초기화 2

    array_char_2[3] = '\0';                                    // 문자열의 4번째 \0 = null 초기화
    printf("array_char_2: %s\n", array_char_2);                // \0 = null 문자 전까지 출력 
    for (int i = 0; i < 10; i++)
    {
        printf("array_char_2[%d]: %c\n", i, array_char_2[i]);  // 문자열의 4번째 이후 나머지 문자 유지 O
    }
    printf("\n");

    array_char_2[3] = 'd';                                     // 문자열 4번째 'd' 재 초기화
    printf("%s\n", array_char_2);                              // \0 = null 문자 전까지 출력    
    for (int i = 0; i < 10; i++)
    {
        printf("array_char_2[%d]: %c\n", i, array_char_2[i]);  // 문자열의 4번째 이후 나머지 문자 유지 O
    }
    printf("\n");

    return 0;
}
```

`strlen()`
\\0 = null 문자 전까지 문자열 길이 반환

| printf("%s", string\_1); | string\_1 문자열 출력 |
| ---| --- |
| printf("%d", strlen(string\_1)); | 반환값 = 문자열 길이<br>string\_1 문자열 길이 출력 |

**c\_one\_arr\_string\_2\_strlen.c**

```perl
#include <stdio.h>
#include <string.h>

int main()
{
    char array_char_1[100] = {0};                                              // 선언  후  초기화
    char array_char_2[11] = "abcdefghij";                                      // 선언 동시 초기화 1
    char array_char_3[] = "abcdefghij";                                        // 선언 동시 초기화 2
    char array_char_4[] = {'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j'};  // 선언 동시 초기화 3
              
    // array_char_1 'strlen 함수 반환값(Return)' = '문자열 길이' 출력
    printf("array_char_1 입력전 길이: %d\n", strlen(array_char_1));
    scanf("%s", array_char_1);
    printf("array_char_1 입력후 요소: %s\n", array_char_1);
    printf("array_char_1 입력후 길이: %d\n", strlen(array_char_1));
    printf("\n");

    // array_char_2 'strlen 함수 반환값(Return)' = '문자열 길이' 출력
    printf("array_char_2 길이: %d\n", strlen(array_char_2));
    printf("\n");

    // array_char_3 'strlen 함수 반환값(Return)' → int 자료형 메모리박스에 초기화 후 출력
    int array_char_3_length = strlen(array_char_3);
    printf("array_char_3 길이: %d\n", array_char_3_length);
    // array_char_3 문자열 4번째 \0 = null 문자 초기화
    array_char_3[3] = '\0';                                                   
    printf("문자열 4번째 null 문자 초기화 후 array_char_3 길이: %d\n", array_char_3_length);
    printf("\n");

    // array_char_1, 2, 3, 4
    int array_size, element_size;

    array_size = sizeof(array_char_2);
    element_size = sizeof(array_char_2[0]);   
    printf("array_char_2 배열 크기: %d\n", array_size);
    printf("array_char_2 요소 크기: %d\n", element_size);
    printf("array_char_2 배열 크기: %d\n", sizeof(array_char_2));
    printf("array_char_2 요소 크기: %d\n", sizeof(array_char_2[0]));               
    printf("array_char_2 요소 갯수: %d\n", array_size / element_size);
    printf("\n");    

    array_size = sizeof(array_char_3);
    element_size = sizeof(array_char_3[0]);  
    printf("array_char_3 배열 크기: %d\n", array_size);
    printf("array_char_3 요소 크기: %d\n", element_size);
    printf("array_char_3 배열 크기: %d\n", sizeof(array_char_3));
    printf("array_char_3 요소 크기: %d\n", sizeof(array_char_3[0]));                   
    printf("array_char_3 요소 갯수: %d\n", array_size / element_size);
    printf("\n"); 

    array_size = sizeof(array_char_4);
    element_size = sizeof(array_char_4[0]);  
    printf("array_char_4 배열 크기: %d\n", array_size);
    printf("array_char_4 요소 크기: %d\n", element_size);
    printf("array_char_4 배열 크기: %d\n", sizeof(array_char_4));
    printf("array_char_4 요소 크기: %d\n", sizeof(array_char_4[0]));                      
    printf("array_char_4 요소 갯수: %d\n", array_size / element_size);
    printf("\n"); 
    
    return 0;
}
```

`strcmp(), strncmp()`
2개의 문자열 비교

| 반환값<br> | string 1 & string2 | string 1 & string2 |
| ---| ---| --- |
| 길이 | 요소 |
| 0 | \= | \= |
| \-1 | <= | ≠ |
| 1 | \> | ≠ |

| printf("%s", string\_1); | string\_1 문자열 출력 |
| ---| --- |
| printf("%d", strcmp(string\_1, string\_2)); | 반환값 = string\_1 & string\_2 비교 판단값<br>string\_1 & string\_2 비교 판단값 출력(0, -1, 1) |

**c\_one\_arr\_string\_3\_strcmp.c**

```cpp
#include <stdio.h>
#include <string.h>

int main()
{
    char array_char_1[100] = "abcdefghij"; // 선언  후  초기화
    char array_char_2[30] = "abcdefghij";  // 선언 동시 초기화 1
    char array_char_3[] = "klmnopqrst";    // 선언 동시 초기화 2

    printf("array_char_1 길이: %d\n", strlen(array_char_1));
    printf("array_char_2 길이: %d\n", strlen(array_char_2));
    printf("array_char_3 길이: %d\n", strlen(array_char_3));
    printf("\n");    

    // strcmp 함수의 반환값(Return) = 0, -1, 1
    int strcmp_return_1 = strcmp(array_char_1, array_char_2);
    printf("strcmp(array_char_1, array_char_2): %d\n", strcmp_return_1);  // return = 0:  1) 길이 array_char_1 = array_char_2,  2) 요소 array_char_1 = array_char_2
    printf("strcmp(array_char_1, array_char_2): %d\n", strcmp(array_char_1, array_char_2));
    printf("\n");  

    array_char_2[3] = '\0';                                               // 문자열 4번째 요소 \0 = null 문자 초기화
    int strcmp_return_2 = strcmp(array_char_1, array_char_2);
    printf("strcmp(array_char_1, array_char_2): %d\n", strcmp_return_2);  // return = 1:  1) 길이 array_char_1 > array_char_2,  2) 요소 array_char_1 ≠ array_char_2
    printf("strcmp(array_char_1, array_char_2): %d\n", strcmp(array_char_1, array_char_2));
    printf("\n");  

    int strcmp_return_3 = strcmp(array_char_1, array_char_3);
    printf("strcmp(array_char_1, array_char_3): %d\n", strcmp_return_3);  // return = -1:  1) 길이 array_char_1 <= array_char_3,  2) 요소 array_char_1 ≠ array_char_3
    printf("strcmp(array_char_1, array_char_3): %d\n", strcmp(array_char_1, array_char_3)); 
    return 0;
}
```

**c\_one\_arr\_string\_3\_strncmp.c**

```perl
#include <stdio.h>
#include <string.h>

int main()
{
    char array_char_1[100] = "abcdefghij";  // 선언  후  초기화
    char array_char_2[30] = "abcdefghij";   // 선언 동시 초기화 1
    char array_char_3[] = "abcdefpqrst";    // 선언 동시 초기화 2
    
    printf("array_char_1 길이: %d\n", strlen(array_char_1));
    printf("array_char_1 길이: %d\n", strlen(array_char_2));
    printf("array_char_3 길이: %d\n", strlen(array_char_3));
    printf("\n");    

    // strcmp 함수의 반환값(Return) = 0, -1, 1
    int strncmp_ret_1 = strncmp(array_char_1, array_char_2, 10);
    int strncmp_ret_2 = strncmp(array_char_1, array_char_2, 5);
    printf("strncmp(array_char_1, array_char_2, 10): %d\n", strncmp_ret_1);  // return = 0:  1) 길이 array_char_1 = array_char_2,  2) 요소 array_char_1 = array_char_2
    printf("strncmp(array_char_1, array_char_2, 10): %d\n", strncmp(array_char_1, array_char_2, 10)); 
    printf("strncmp(array_char_1, array_char_2,  5): %d\n", strncmp_ret_2);  // return = 0:  1) 길이 array_char_1 = array_char_2,  2) 요소 array_char_1 = array_char_2
    printf("strncmp(array_char_1, array_char_2,  5): %d\n", strncmp(array_char_1, array_char_2, 5)); 
    printf("\n"); 

    array_char_2[3] = '\0';                                                  // 문자열 4번째 요소 \0 = null 문자 초기화
    int strncmp_ret_3 = strncmp(array_char_1, array_char_2, 10);
    int strncmp_ret_4 = strncmp(array_char_1, array_char_2, 5);
    printf("strncmp(array_char_1, array_char_2, 10): %d\n", strncmp_ret_3);  // return = 1:  1) 길이 array_char_1 > array_char_2,  2) 요소 array_char_1 ≠ array_char_2
    printf("strncmp(array_char_1, array_char_2, 10): %d\n", strncmp(array_char_1, array_char_2, 10)); 
    printf("strncmp(array_char_1, array_char_2,  5): %d\n", strncmp_ret_4);  // return = 1:  1) 길이 array_char_1 > array_char_2,  2) 요소 array_char_1 ≠ array_char_2
    printf("strncmp(array_char_1, array_char_2,  5): %d\n", strncmp(array_char_1, array_char_2, 5)); 
    printf("\n"); 

    int strncmp_ret_5 = strncmp(array_char_1, array_char_3, 10);
    int strncmp_ret_6 = strncmp(array_char_1, array_char_3, 5);
    printf("strncmp(array_char_1, array_char_3, 10): %d\n", strncmp_ret_5);  // return = -1:  1) 길이 array_char_1 <= array_char_3,  2) 요소 array_char_1 ≠ array_char_3
    printf("strncmp(array_char_1, array_char_3, 10): %d\n", strncmp(array_char_1, array_char_3, 10)); 
    printf("strncmp(array_char_1, array_char_3, 10): %d\n", strncmp_ret_6);  // return =  0:  1) 길이 array_char_1  = array_char_3,  2) 요소 array_char_1 = array_char_3
    printf("strncmp(array_char_1, array_char_3, 10): %d\n", strncmp(array_char_1, array_char_3, 5)); 

    return 0;
}
```

`strcat(), strncat()`
strcat: 문자열에 다른 문자열 이어 붙임
strncat: 문자열에 다른 문자열 n개 만큼만 이어 붙임
※ \\0 = null 문자 전까지 복사/붙임

| printf("%s", string\_1); | string\_1 변경후 문자열 출력 |
| ---| --- |
| printf("%d", strcat(string\_1, string\_2)); | 반환값 = 연결된 문자열 주소값 = 목적지 주소값<br>\= string\_1 주소값<br>string\_1 주소값 출력 |

**c\_one\_arr\_string\_4\_strcat.c**

```cpp
#include <stdio.h>
#include <string.h>

int main()
{
    char array_char_1[100];                // 선언  후  초기화
    char array_char_2[30] = "abcdefghij";  // 선언 동시 초기화 1
    char array_char_3[] = "klmnopqrst";    // 선언 동시 초기화 2

    // strcat 함수 처리시 array_char_1 배열 요소 변경 O → array_char_1 초기화 O
    scanf("%s", array_char_1);
    printf("array_char_1: %s\n", array_char_1);
    printf("\n");
    strcat(array_char_1, array_char_2);  // array_char_1 ← array_char_2
    printf("array_char_1 ← array_char_2: %s\n", array_char_1);
    printf("\n");
 
    // strcat 함수의 반환값(Return) = 연결된 문자열 전체(array_char_1 ← array_char_2) 주소값 = 목적지(array_char_1) 주소값 ≠ 변경된 배열(array_char_1) 요소    
    printf("array_char_1 주소: %d\n", &array_char_1);
    int strcat_return = strcat(array_char_1, array_char_2);        
    printf("strcat(array_char_1, array_char_2) 반환값(Return) = array_char_1 주소값(목적지 주소값): %d\n", strcat_return);
    printf("strcat(array_char_1, array_char_2) 반환값(Return) = array_char_1 주소값(목적지 주소값): %d\n", strcat(array_char_1, array_char_2));
    printf("\n");

    array_char_3[3] = '\0';              // 문자열 4번째 \0 = null 문자 초기화
    strcat(array_char_2, array_char_3);  // array_char_2 ← array_char_3
    printf("문자열 4번째 null 문자 초기화 후 array_char_2 ← array_char_3: %s\n", array_char_2);

    return 0;
}
```

**c\_one\_arr\_string\_4\_strncat.c**

```cpp
#include <stdio.h>
#include <string.h>

int main()
{
    char array_char_1[100];                 // 선언  후  초기화
    char array_char_2[30] = "abcdefghij";   // 선언 동시 초기화 1
    char array_char_3[] = "klmnopqrst";     // 선언 동시 초기화 2

    // strncat 함수 처리시 array_char_1 배열 요소 변경 O → array_char_1 초기화 O
    scanf("%s", array_char_1);
    printf("array_char_1: %s\n", array_char_1);
    printf("\n");
    strncat(array_char_1, array_char_2, 5);  // array_char_1 ← array_char_2(왼쪽부터 요소 5개)
    printf("array_char_1 ← array_char_2: %s\n", array_char_1);
    printf("\n");

    // strncat 함수의 반환값(Return) = 연결된 문자열 전체(array_char_1 ← array_char_2) 주소값 = 목적지(array_char_1) 주소값 ≠ 변경된 배열(array_char_1) 요소    
    printf("array_char_1 주소: %d\n", &array_char_1);
    int strncat_return = strncat(array_char_1, array_char_2, 5); 
    printf("strncat(array_char_1, array_char_2) 반환값(Return 값) = array_char_1 주소값(목적지의 주소값): %d\n", strncat_return);
    printf("strncat(array_char_1, array_char_2) 반환값(Return 값) = array_char_1 주소값(목적지의 주소값): %d\n", strncat(array_char_1, array_char_2, 5));
    printf("\n");
    
    array_char_3[3] = '\0';                 // 문자열 4번째 \0 = null 문자 초기화
    strcat(array_char_2, array_char_3);     // array_char_2 ← array_char_3:  array_char_3 문자열 4번째 \0 = null 문자 → 복사할 문자 갯수 5개 X  →  \0 = null 문자뒤 문자열은 복사/붙임 X
    printf("문자열 4번째 null 문자 초기화 후 array_char_2 ← array_char_3: %s\n", array_char_2);

    return 0;
}
```

`strcpy(), strncpy()`

**c\_one\_arr\_string\_5\_strcpy\_rule\_o.c**

**c\_one\_arr\_string\_5\_strcpy\_rule\_x.c**

**c\_one\_arr\_string\_5\_strncpy\_rule\_o.c**

**c\_one\_arr\_string\_5\_strncpy\_rule\_x.c**

`toupper(), tolower()`
문자열 All 대문자 or All 소문자 변경
배열 요소 변경 O → 배열 요소 초기화 X → 변수 = 함수(string\_1); 초기화 필요 O

| printf(%s, string\_1); | 변경전 문자열 출력(string\_1) |
| ---| --- |
| string\_2 = tolower(string\_1);<br>printf("%s", string\_2); | <br>변경후 문자열 출력(string\_2) |
| printf(%s, tolower(string\_1)); | 반환값(Return) = 변경후 문자1개(%c 지정)<br>출력값 無 (Segmentation fault) |
| printf(%c, tolower(string\_1\[n\])); | 반환값(Return) = 변경후 문자1개(%c 지정)<br>변경문자 1개 출력 |
| printf(%d, tolower(string\_1\[n\])); | 반환값(Return) = 변경후 문자1개(%c 지정)<br>변경문자 1개 ASCII Code 변환 정수 출력 |

**c\_one\_arr\_string\_6\_to\_ul\_1.c**

```cpp
#include <stdio.h>
#include <string.h>
// #include <ctype.h> // for Mac OS

int main()
{
    char array_current[100] = "ABCDEF ghijkl";   // 선언 동시 초기화: 자동 \0 = null 생성("ABCDEF ghijkl" = 문자열상수)
    char array_changed[100] = {0};
    printf("current_texts: %s\n", array_current);    
    printf("  upper_texts: %s\n", toupper(array_changed));
    printf("  lower_texts: %s\n", tolower(array_changed));
    printf("===========================\n");

    int i = 0; 
    while (array_current[i] != '\0')            // \0 = null 문자 아닐때 까지 반복 = \0 = null 문자 전까지 반복
    {
        array_changed[i] = toupper(array_current[i]);
        i += 1;
    }
    printf("array-upper_texts: %s\n", array_changed);

    i = 0;
    while (array_current[i] != '\0')             
    {
        array_changed[i] = tolower(array_current[i]);
        i += 1;   
    }
    printf("array-lower_texts: %s\n", array_changed);

    return 0;
}
```

**c\_one\_arr\_string\_6\_to\_ul\_2.c**

```cpp
#include <stdio.h>
#include <string.h>
// #include <ctype.h> // for Mac OS

int main()
{
    char array_current[100] = "ABCDEF ghijkl";   // 선언 동시 초기화: 자동 \0 = null 생성("Hello World!!" = 문자열상수)
    char array_changed[100] = {0};
    printf("current_texts: %s\n", array_current);    
    printf("  upper_texts: %s\n", toupper(array_changed));
    printf("  lower_texts: %s\n", tolower(array_changed));
    printf("===========================\n");

    printf("char-upper_texts: ");
    int i = 0;
    while (array_current[i] != '\0')             // \0 = null 문자 아닐때 까지 반복 = \0 = null 문자 전까지 반복
    {
        printf("%c", toupper(array_current[i]));
        i++;   
    }   

    printf("\n");

    printf("char-lower_texts: ");
    i = 0; 
    while (array_current[i] != '\0')
    {
        printf("%c", tolower(array_current[i]));
        i++; 
    }

    return 0;
}
```

`atoi(), atol(), atoll(), atof()`
문자열 다른 자료형 변환
atoi = char 문자 → int 정수
atol = char 문자 → long 정수
atoll = char 문자 → long long 정수
atof = char 문자 → double 실수

**c\_one\_arr\_string\_7\_ato.c**

```cpp
#include <stdio.h>
#include <string.h>
#include <stdlib.h> // atof함수 사용 시 필요

int main()
{
    char array_char_1[10] = "10";         
    char array_char_2[10] = "20.20";      

    int number_1 = atoi(array_char_1);
    int number_2 = atoi(array_char_2);
    printf("number_1: %d\n", number_1);
    printf("number_2: %d\n", number_2);

    long int number_3 = atol(array_char_1);
    long int number_4 = atol(array_char_2);
    printf("number_3: %ld\n", number_3);
    printf("number_4: %ld\n", number_4);

    long long int number_5 = atoll(array_char_1);
    long long int number_6 = atoll(array_char_2);
    printf("number_5: %lld\n", number_5);
    printf("number_6: %lld\n", number_6);

    double number_7 = atof(array_char_1);
    double number_8 = atof(array_char_2);
    printf("number_7: %lf\n", number_7);
    printf("number_8: %lf\n", number_8);

    return 0;
}
```
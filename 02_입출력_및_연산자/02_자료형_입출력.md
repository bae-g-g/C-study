# Int vs Float vs Char

# **int**

*   선언(메모리박스 할당)
자료형 변수명;
E.g)
`int A;`

*   초기화(입력/저장)

선언 '동시' 초기화: `=`

. 정수 (지정변수 O)

서식 X

E.g)

`int A = 97;`

→ 4 Bytes 크기 정수 1개(97)를 정수 자료형 4 Bytes 메모리박스(A)만큼 입력/저장

∵ A : 자료형 + 크기

. 문자(지정변수 X)

서식 ' '

E.g)

`int A = 'a';`

→ 1 Byte 크기 문자 1개(a)를 정수 자료형 4 Bytes 메모리박스(A)만큼 입력/저장

∵ A : 자료형 + 크기

a = 97 = 01100001 **00000000 00000000 00000000** (Little Endian)

a **만큼**

선언 '후' 초기화: `scanf` 함수 + `%d` 지정 입력서식, `&` 정수변수 (소수, 문자변수 X)
E.g)
int A;
scanf("%d", &A);
→ 4 Bytes 크기 정수 1개(%d)를 메모리박스(A)의 주소값(&)에 입력/저장
∵ `&A` : 주소값(메모리박스 주소)

*   출력
정수 출력: `printf`함수 + `%d` 지정 출력서식
→ 선언한 자료형 크기 만큼(에서) 정수(%d) 1개 형태(크기 + 형식) 10진수 출력
문자 출력: `printf`함수 + `%c` ASCII Code 변환
→ 선언한 자료형크기 만큼(에서) 문자(%c) 1개 형태(크기 + 형식) 출력

### **Example)**

**a\_int\_1.c**

```cpp
#include <stdio.h>

int main()
{
    // 선언 '동시' 초기화 (1)
    int X = 65;      // 정수 자료형 변수 X라는 이름으로 메모리박스 1개 선언 '동시' 변수값 정수 65 초기화: 정수자료형 65(4 Bytes) → 선언한 문자자료형 크기(4 Bytes) 만큼 '초기화'(입력/저장) 
    
    // 선언 '동시' 초기화 (2)
    int Y;      
    Y = 66;          // 정수 자료형 변수 Y라는 이름으로 메모리박스 1개 선언 '동시' 변수값 정수 66 초기화: 정수자료형 66(4 Bytes) → 선언한 문자자료형 크기(4 Bytes) 만큼 '초기화'(입력/저장) 

    // 선언 '후' 초기화
    int Z;      
    scanf("%d", &Z); // E.g.) %d 정수 자료형 67(4 Bytes)을 변수 Z의 주소값(&)에 '초기화'(입력/저장) 
                     // 정수 자료형 변수 Z라는 이름으로 메모리박스 1개 선언 '후' 변수 정수 67 '초기화'(입력/저장) [%d 정수자료형 변수값 67(4 Bytes)을 변수 Z 주소값(&)에 '초기화'(입력/저장)]
   
    printf("-------\n");

    printf("%d\n", X);
    printf("%d\n", Y);
    printf("%d\n", Z);

    printf("-------\n");

    printf("%c\n", X);
    printf("%c\n", Y);
    printf("%c\n", Z);

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/54915f7f-89c5-4440-9c4c-a17f1d34f145/1.png)

**a\_int\_2.c**

```cpp
#include <stdio.h>

int main()
{
    // 선언 '후' 초기화 → E.g.) 1234 '초기화'(입력/저장)
    //                         정수 자료형 변수 K라는 이름으로 메모리박스 1개 선언 '후' 변수값 정수 1234 초기화: %d 정수자료형 1234(4 Bytes) K 주소값(&)에 '초기화'('초기화'(입력/저장))
    int K;

    scanf("%d", &K);   // 입력서식(%d→정수) '초기화' 변수자료형(정수→1234) 매칭 O
                       // scanf 실행 성공:  정수 1개 1234 '초기화'(입력/저장)[%d 정수자료형 1234(4 Bytes) 변수 K의 주소값(&)에 '초기화'(입력/저장)]  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("%d\n", K); // %d → 선언한 자료형크기 만큼 정수 1개 1234 출력 
    printf("-------\n");

    scanf("%d", &K);   // scanf 실행:  버퍼 변수(문자→엔터) 삭제  →  입력서식(%d→정수) '초기화' 변수자료형(정수→1234) 매칭 O
                       // scanf 실행 성공:  정수 1개 1234 '초기화'(입력/저장)[%d 정수자료형 1234(4 Bytes) 변수 K의 주소값(&)에 '초기화'(입력/저장)]  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("%d\n", K); // %d → 선언한 자료형크기 만큼 정수 1개 1234 출력 
    printf("-------\n");

    scanf("%d", &K);   // scanf 실행:  버퍼 변수(문자→엔터) 삭제  →  입력서식(%d→정수) '초기화' 변수자료형(정수→1234) 매칭 O
                       // scanf 실행 성공:  정수 1개 1234 '초기화'(입력/저장)[%d 정수자료형 1234(4 Bytes) 변수 K의 주소값(&)에 '초기화'(입력/저장)]  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("%d\n", K); // %d → 선언한 자료형크기 만큼 정수 1개 1234 출력 
    printf("-------\n");

    scanf("%d", &K);   // scanf 실행:  버퍼 변수(문자→엔터) 삭제  →  입력서식(%d→정수) '초기화' 변수자료형(정수→1234) 매칭 O
                       // scanf 실행 성공:  정수 1개 1234 '초기화'(입력/저장)[%d 정수자료형 1234(4 Bytes) 변수 K의 주소값(&)에 '초기화'(입력/저장)]  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("%d\n", K); // %d → 선언한 자료형크기 만큼 정수 1개 1234 출력 
    printf("-------\n");

    scanf("%d", &K);   // scanf 실행:  버퍼 변수(문자→엔터) 삭제  →  입력서식(%d→정수) '초기화' 변수자료형(정수→1234) 매칭 O
                       // scanf 실행 성공:  정수 1개 1234 '초기화'(입력/저장)[%d 정수자료형 1234(4 Bytes) 변수 K의 주소값(&)에 '초기화'(입력/저장)]  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("%d\n", K); // %d → 선언한 자료형크기 만큼 정수 1개 1234 출력 
    printf("-------\n");

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/5031489f-b0d4-4d8a-adfa-831dff95f9ac/Picture1.png)

**a\_int\_3.c**

```cpp
// 입력서식 & '초기화'자료형 일치 X
// 예: 89 입력/저장
#include <stdio.h>

int main()
{
    int A;
    printf("---Input---\n");
    scanf("%d", &A);     // 입력서식(%d→정수) '초기화' 변수자료형(정수→89) 매칭 O
                         // scanf 실행 성공:  정수 1개 89 입력/저장[%d 정수자료형 89(4 Bytes) A 주소값(&)에 입력/저장]
    printf("---Output---\n");
    printf("<%d>\n", A); // %d → 선언한 자료형크기 만큼 정수 1개 89 출력

    int B;
    printf("---Input---\n");
    scanf("%d", &B);     // scanf 실행:  버퍼 변수(문자→엔터) 삭제  →  입력서식(%d→정수) '초기화' 변수자료형(정수→89) 매칭 O
                         // scanf 실행 성공:  정수 1개 89 입력/저장[%d 정수자료형 89(4 Bytes) B 주소값(&)에 입력/저장]  →  '초기화' 변수(문자→엔터) 버퍼 유지
    printf("---Output---\n");
    printf("<%c>\n", B); // %c → 선언한 자료형크기 만큼 정수 1개 89 ASCII Code 변환 문자 1개 Y 출력

    int C;
    printf("---Input---\n");
    scanf("%c", &C);     // scanf 실행:  입력서식(%c→문자) 버퍼 변수자료형(문자→엔터) 매칭 O
                         // scanf 실행 성공:  문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) C 주소값(&)에 입력/저장]
    printf("---Output---\n");
    printf("<%c>\n", C); // %c → 선언한 자료형크기 만큼 문자 1개 엔터 출력

    int D;
    printf("---Input---\n");
    scanf("%c", &D);     // 입력서식(%c→정수) '초기화' 변수자료형(%c: 정수→89 X 문자→89엔터 O 인식) 매칭 O
                         // scanf 실행 성공:  문자 1개 8 입력/저장[%c 문자자료형 8(1 Byte) D 주소값(&)에 입력/저장]  →  '초기화' 변수(문자→9, 엔터) 버퍼 유지
    printf("---Output---\n");
    printf("<%d>\n", D); // %d → int 자료형크기 4 Bytes: [(3 Bytes = 쓰레기값) + (1 Bytes = 문자 1개 8 ASCII Code 정수 변환 56)] 출력

    int E;
    printf("---Input---\n");
    scanf("%d", &E);     // scanf 실행:  입력서식(%d→정수) 버퍼 변수자료형(%d: 문자→9엔터 X 정수→9 O 인식) 매칭 O
                         // scanf 실행 성공:  정수 1개 9 입력/저장[%d 정수자료형 9(4 Bytes) E 주소값(&)에 입력/저장] → 버퍼 변수(문자→엔터) 유지
    printf("---Output---\n");
    printf("<%d>\n", E); // %d → 선언한 자료형크기 만큼 정수 1개 9 출력

    int F;
    printf("---Input---\n");
    scanf("%c", &F);     // scanf 실행:  입력서식(%c→문자) 버퍼 변수자료형(문자→엔터) 매칭 O
                         // scanf 실행 성공:  문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) C 주소값(&)에 입력/저장]
    printf("---Output---\n");
    printf("<%c>\n", F); // %d → 선언한 자료형크기 만큼 문자 1개 엔터 출력

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/0d0d6281-0731-4cf3-b535-5a5de1858096/Picture10.png)
int D;
![](https://t9003081320.p.clickup-attachments.com/t9003081320/778e01cd-abb3-4a8a-b73c-0f416309b856/Picture2.png)

**a\_int\_4.c**

```cpp
// 입력서식 & '초기화'자료형 일치 X
// a_int_3.c 부분 추출
// 예: 89 입력/저장

#include <stdio.h>

int main()
{
    // int A;
    // printf("---Input---\n");
    // scanf("%d", &A);     // 입력서식(%d→정수) '초기화' 변수자료형(정수→89) 매칭 O
    //                      // scanf 실행 성공:  정수 1개 89 입력/저장[%d 정수자료형 89(4 Bytes) A 주소값(&)에 입력/저장]
    // printf("---Output---\n");
    // printf("<%d>\n", A); // %d → 선언한 자료형크기 만큼 정수 1개 89 출력

    // int B;
    // printf("---Input---\n");
    // scanf("%d", &B);     // scanf 실행:  버퍼 변수(문자→엔터) 삭제  →  입력서식(%d→정수) '초기화' 변수자료형(정수→89) 매칭 O
    //                      // scanf 실행 성공:  정수 1개 89 입력/저장[%d 정수자료형 89(4 Bytes) A 주소값(&)에 입력/저장]  →  '초기화' 변수(문자→엔터) 버퍼 유지
    // printf("---Output---\n");
    // printf("<%c>\n", B); // %c → 선언한 자료형크기 만큼 정수 1개 89 ASCII Code 변환 문자 1개 Y 출력

    // int C;
    // printf("---Input---\n");
    // scanf("%c", &C);     // scanf 실행:  입력서식(%c→문자) 버퍼 변수자료형(문자→엔터) 매칭 O
    //                      // scanf 실행 성공:  문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) C 주소값(&)에 입력/저장]
    // printf("---Output---\n");
    // printf("<%c>\n", C); // %c → 선언한 자료형크기 만큼 문자 1개 엔터 출력

    int D;
    printf("---Input---\n");
    scanf("%c", &D);     // 입력서식(%c→정수) '초기화' 변수자료형(%c: 정수→89 X 문자→89엔터 O 인식) 매칭 O
                         // scanf 실행 성공:  문자 1개 8 입력/저장[%c 문자자료형 8(1 Byte) D 주소값(&)에 입력/저장]  →  '초기화' 변수(문자→9, 엔터) 버퍼 유지
    printf("---Output---\n");
    printf("<%d>\n", D); // %d → int 자료형크기 4 Bytes: [(3 Bytes = 쓰레기값) + (1 Bytes = 문자 1개 8 ASCII Code 정수 변환 56)] 출력

    int E;
    printf("---Input---\n");
    scanf("%d", &E); // scanf 실행:  입력서식(%d→정수) 버퍼 변수자료형(%d: 문자→9엔터 X 정수→9 O 인식) 매칭 O
                     // scanf 실행 성공:  정수 1개 9 입력/저장[%d 정수자료형 9(4 Bytes) E 주소값(&)에 입력/저장] → 버퍼 변수(문자→엔터) 유지
    printf("---Output---\n");
    printf("<%d>\n", E); // %d → 선언한 자료형크기 만큼 정수 1개 9 출력

    int F;
    printf("---Input---\n");
    scanf("%c", &F); // scanf 실행:  입력서식(%c→문자) 버퍼 변수자료형(문자→엔터) 매칭 O
                     // scanf 실행 성공:  문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) C 주소값(&)에 입력/저장]
    printf("---Output---\n");
    printf("<%c>\n", F); // %d → 선언한 자료형크기 만큼 문자 1개 엔터 출력

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/e75da7b7-6498-4293-854b-cfcea878c9d2/Picture6.png)
int D;
![](https://t9003081320.p.clickup-attachments.com/t9003081320/4278f2df-a4e6-4e77-9cfc-45be1215c997/Picture1.png)

**a\_int\_5.c**

```cpp
// 입력서식 & '초기화'자료형 일치 X
// 예: Y 입력/저장

#include <stdio.h>

int main()
{
    int A;
    printf("---Input---\n");
    scanf("%d", &A);     // 입력서식(%d→정수) '초기화' 변수자료형(문자→Y) 매칭 X
                         // scanf 실행 실패:  쓰레기값(예: 쓰레기값 0 = int 자료형크기 4 Bytes 정수값 0) → '초기화' 변수(Y, 엔터) 버퍼 유지
    printf("---Output---\n");
    printf("<%d>\n", A); // %d → 선언한 자료형크기 만큼 쓰레기값 정수 1개 출력(예: 정수 0)
    
    int B;
    printf("---Input---\n");
    scanf("%d", &B);     // scanf 실행:  입력서식(%d→정수) '버퍼 변수자료형(문자→Y) 매칭 X
                         // scanf 실행 실패: 쓰레기값(예: 쓰레기값 0 = int A 메모리박스 쓰레기값 관련 X = int 자료형크기 4 Bytes 정수 0) → '초기화' 변수(Y, 엔터) 버퍼 유지
    printf("---Output---\n");
    printf("<%c>\n", B); // %c → 선언한 자료형크기 만큼 쓰레기값 정수 ASCII Code 변환 문자 1개 출력(예: 정수 0 ASCII 변환 null)
    
    int C;
    printf("---Input---\n");
    scanf("%c", &C);     // scanf 실행:  입력서식(%c→문자) 버퍼 변수자료형(문자→Y) 매칭 O
                         // scanf 실행 성공:  버퍼 변수 문자 1개 Y 입력/저장[%c 문자자료형 Y(1 Byte) C 주소값(&)에 입력/저장] → 버퍼 변수 엔터 유지
    printf("---Output---\n");
    printf("<%c>\n", C); // %c → 선언한 자료형크기 만큼 문자 1개 Y 출력
    
    int D;
    printf("---Input---\n");
    scanf("%c", &D);     // scanf 실행:  입력서식(%c→문자) 버퍼 변수자료형(문자→엔터) 매칭 O
                         // scanf 실행 성공:  버퍼 변수 문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) C 주소값(&)에 입력/저장]
    printf("---Output---\n");
    printf("<%d>\n", D); // %d → int 자료형크기 4 Bytes:  [(3 Bytes = 쓰레기값) + (1 Bytes = 문자 엔터(LF-Line Feed) ASCII Code 변환 정수 1개 10)] 출력
    
    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/180a5839-1696-45df-8745-769eddc689c2/Picture12.png)
int C;
![](https://t9003081320.p.clickup-attachments.com/t9003081320/93802a2e-04cb-47b0-8585-93cbfc1280f6/Picture3.png)
int D;
![](https://t9003081320.p.clickup-attachments.com/t9003081320/cb01b462-e647-4927-bd0e-b6b8b348b4b4/Picture1.png)

* * *

# **float**

*   선언(메모리박스 할당)
자료형 변수명;
E.g)
`float B;`

*   초기화(입력/저장)

선언 '동시' 초기화: `=`

. 소수

서식 X

E.g)

`float B = 8.625;`

→ 4 Bytes 크기 소수 1개(8.625)를 소수 자료형 4 Bytes 메모리박스(B)만큼 입력/저장

∵ B : 자료형 + 크기

※ 8.625의 2진수 입력/저장 = 8.625의 부동소수점 환산 2진수 입력/저장

→ 8.625의 2진수 1000.101 입력/저장 X

→ 8.625의 부동소수점 환산 2진수 01000001000010100000000000000000 입력/저장 O

선언 '후' 초기화: `scanf` 함수 + `%f` 지정 입력서식, `&` 변수
E.g)
`float B;`
scanf("%f", &B);
→ 4 Bytes 크기 소수 1개(%f)를 메모리박스(B)의 주소값(&)에 입력/저장

*   출력
소수 출력: `printf`함수 + `%f` 지정 출력서식
→ 선언한 자료형크기 만큼(에서) 소수(%f) 1개 형태(크기 + 형식) 10진수 출력

### **Example)**

**b\_float\_1.c**

```cpp
#include <stdio.h>

int main()
{
    // 선언 '동시' 초기화 (1)
    float X = 0.5;   // 소수 자료형 X 메모리박스 1개 선언 '동시' 변수 소수 0.5 초기화: 소수자료형 0.5(4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 '초기화'(입력/저장) 
    
    // 선언 '동시' 초기화 (2)
    float Y;      
    Y = 0.25;        // 소수 자료형 Y 메모리박스 1개 선언 '동시' 변수 소수 0.25 초기화: 소수자료형 0.25(4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 '초기화'(입력/저장) 

    // 선언 '후' 초기화
    float Z;      
    scanf("%f", &Z); // 예: 0.625 '초기화'(입력/저장)
                     // 소수 자료형 Z 메모리박스 1개 선언 '후' 변수 소수 0.625 초기화[%d 정수자료형 0.625(4 Bytes) Z 주소값(&)에 '초기화'(입력/저장)] → '초기화' 변수(문자→엔터) 버퍼 유지

    printf("-------\n");

    printf("%f\n", X);
    printf("%f\n", Y);
    printf("%f\n", Z);

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/acdb33e0-575b-469e-aeae-d627d24a31c8/Picture22.png)

**b\_float\_2.c**

```cpp
#include <stdio.h>

int main()
{
    // 선언 '후' 초기화 → 예: 8.625 입력/저장
    //                   소수 자료형 K 메모리박스 1개 선언 '후' 변수 소수 8.625 초기화
    float K;

    scanf("%f", &K);   // 입력서식(%f→정수) '초기화' 변수자료형(소수→8.625) 매칭 O
                       // scanf 실행 성공:  소수 1개 8.625 입력/저장[%f 소수자료형 8.625(4 Bytes) K 주소값(&)에 입력/저장]  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("%f\n", K); // %f → 선언한 자료형크기 만큼 소수 1개 8.625 출력 

    scanf("%f", &K);   // scanf 실행:  버퍼 변수값(문자→엔터) 삭제  →  입력서식(%f→소수) '초기화' 변수자료형(소수→8.625) 매칭 O
                       // scanf 실행 성공:  소수 1개 8.625 입력/저장[%f 소수자료형 8.625(4 Bytes) K 주소값(&)에 입력/저장]  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("%f\n", K); // %f → 선언한 자료형크기 만큼 소수 1개 8.625 출력 

    scanf("%f", &K);   // scanf 실행:  버퍼 변수값(문자→엔터) 삭제  →  입력서식(%f→소수) '초기화' 변수자료형(소수→8.625) 매칭 O
                       // scanf 실행 성공:  소수 1개 8.625 입력/저장[%f 소수자료형 8.625(4 Bytes) K 주소값(&)에 입력/저장]  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("%f\n", K); // %f → 선언한 자료형크기 만큼 소수 1개 8.625 출력 

    scanf("%f", &K);   // scanf 실행:  버퍼 변수값(문자→엔터) 삭제  →  입력서식(%f→소수) '초기화' 변수자료형(소수→8.625) 매칭 O
                       // scanf 실행 성공:  소수 1개 8.625 입력/저장[%f 소수자료형 8.625(4 Bytes) K 주소값(&)에 입력/저장]  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("%f\n", K); // %f → 선언한 자료형크기 만큼 소수 1개 8.625 출력 

    scanf("%f", &K);   // scanf 실행:  버퍼 변수값(문자→엔터) 삭제  →  입력서식(%f→소수) '초기화' 변수자료형(소수→8.625) 매칭 O
                       // scanf 실행 성공:  소수 1개 8.625 입력/저장[%f 소수자료형 8.625(4 Bytes) K 주소값(&)에 입력/저장]  → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("%f\n", K); // %f → 선언한 자료형크기 만큼 소수 1개 8.625 출력 

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/9a428971-f98f-44cf-b876-59cd8cf34dee/Picture23.png)

* * *

# **char**

*   선언(메모리박스 할당)
자료형 변수명;
E.g)
`char C;`

*   초기화(입력/저장)

선언 '동시' 초기화: `=` & `' '`

. 문자(지정변수 O)

서식 ' '

E.g)

`char C = 'a';`

→ 1 Byte 크기 문자 1개(a)를 문자 자료형 1 Byte 메모리박스(C)만큼 입력/저장

∵ C : 자료형 + 크기

. 정수(지정변수 X)

서식 X

E.g)

`char C = 97;`

→ 4 Bytes 크기 정수 1개(97)를 문자 자료형 1 Byte 메모리박스(C)만큼 입력/저장

∵ C : 자료형 + 크기

97 = 01100001 **~~00000000 00000000 00000000~~** (Little Endian)

97 **~~만큼~~**

선언 '후' 초기화: `scanf` 함수 + `%c` 지정 입력서식, `&` 문자
E.g)
`char C;`
scanf("%c", &C);
→ 1 Byte 크기 문자 1개(%c)를 메모리박스(C)의 주소값(&)에 입력/저장
∵ &C : 주소값

*   출력
문자 출력: `printf`함수 + `%c` 지정 출력서식
→ 선언한 자료형크기 만큼(에서) 문자(%c) 1개 형태(크기 + 형식) 출력
정수 출력: `printf`함수 + `%d` ASCII Code 변환
→ 선언한 자료형크기 만큼(에서) 정수(%d) 1개 10진수 형태(크기 + 형식) 출력

int C; //  문자 a 입력/저장 
printf("%c", C);
→ 4 Bytes 만큼(에서) 문자(%c) 1개 출력 (4 Bytes 중 맨앞 1 Byte 출력)
선언한 자료형 크기만큼(에서) 문자 1개 형식(크기 + 형태) 출력
![](https://t9003081320.p.clickup-attachments.com/t9003081320/f0437eb9-6cf6-400c-bb19-30db60fb9436/Picture1.png)

printf("%d", C);
→ 4 Bytes 만큼(에서) 정수(%d) 1개 출력 (4 Bytes 만큼 출력)
선언한 자료형 크기만큼(에서) 정수 1개 형식(크기 + 형태) 출력
![](https://t9003081320.p.clickup-attachments.com/t9003081320/031ad83b-f65b-45bd-8504-c898cb1ffeca/Picture2.png)

### **Example)**

**c\_char\_1.c**

```cpp
#include <stdio.h>

int main()
{
    // 선언 '동시' 초기화 (1)
    char X = 'A'; // 문자 자료형 X 메모리박스 1개 선언 '후' 변수 문자 A 초기화: 문자자료형 A(1 Byte) → 선언 문자자료형 크기(1 Byte) 만큼 '초기화'(입력/저장) 
    
    // 선언 '동시' 초기화 (2)
    char Y;      
    Y = 'B'; // 문자 자료형 Y 메모리박스 1개 선언 '후' 변수 문자 B 초기화: 문자자료형 B(1 Byte) → 선언 문자자료형 크기(1 Byte) 만큼 '초기화'(입력/저장)  

    // 선언 '후' 초기화
    char Z;      
    scanf("%c", &Z); // 예: C 입력/저장
                     // 문자 자료형 Z 메모리박스 1개 선언 '후' 변수 문자 C 초기화[%c 문자자료형 C(1 Byte) Z 주소값(&)에 '초기화'(입력/저장)] → '초기화' 변수(문자→엔터) 버퍼 유지 

    printf("-------\n");

    printf("%c\n", X);
    printf("%c\n", Y);
    printf("%c\n", Z);

    printf("-------\n");

    printf("%d\n", X);
    printf("%d\n", Y);
    printf("%d\n", Z);

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/b5236227-79a1-46ee-86ff-833c4b1c01ff/a.png)

**c\_char\_2.c**

```cpp
#include <stdio.h>

int main()
{
    // 선언 '후' 초기화 → 예: A, B 입력/저장  /  1, 2 입력/저장
    //                       문자 자료형 K 메모리박스 1개 선언 '후' 변수 문자 A → B / 1 → 2 초기화
    char K;

    scanf("%c", &K);     // 입력서식(%c→문자) '초기화'자료형(문자→A/1, 엔터) 매칭 O
                         // scanf 실행 성공:  문자 1개 A/1 입력/저장[%c 문자자료형 A/1(1 Byte) K 주소값(&)에 입력/저장]  → '초기화' 변수(문자→엔터) 유지 
    printf("<%c>\n", K); // %c → 선언한 자료형크기 만큼 문자 1개 A/1 출력 

    scanf("%c", &K);     // scanf 실행:  입력서식(%c→문자) 버퍼 변수자료형(문자→엔터) 매칭 O
                         // scanf 실행 성공:  문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) K 주소값(&)에 입력/저장] 
    printf("<%c>\n", K); // %c → 선언한 자료형크기 만큼 문자 1개 엔터 출력

    scanf("%c", &K);     // scanf 실행:  입력서식(%c→문자) 버퍼 변수자료형(문자→B/2, 엔터) 매칭 O
                         // scanf 실행 성공:  문자 1개 B/2 입력/저장[%c 문자자료형 B/2(1 Byte) K 주소값(&)에 입력/저장]  →  버퍼 변수(문자→엔터) 유지 
    printf("<%c>\n", K); // %c → 선언한 자료형크기 만큼 문자 1개 B/2 출력 

    scanf("%c", &K);     // scanf 실행:  입력서식(%c→문자) 버퍼 변수자료형(문자→엔터) 매칭 O
                         // scanf 실행 성공:  문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) K 주소값(&)에 입력/저장] 
    printf("<%c>\n", K); // %c → 선언한 자료형크기 만큼 문자 1개 엔터 출력

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/4639c00c-73d8-470b-892e-53e55dcc062f/Picture6.png)

**c\_char\_3.c**

```cpp
#include <stdio.h>

int main()
{
    // 선언 '후' 초기화 → 예: ABCD 입력/저장  /  1234 입력/저장
    //                       문자 자료형 K 메모리박스 1개 선언 '후' 변수 문자 ABCD /  1234 초기화
    char K;

    scanf("%c", &K);   // 입력서식(%c→문자) '초기화'자료형(문자→A/1, 엔터) 매칭 O
                       // scanf 실행 성공:  문자 1개 A/1 입력/저장[%c 문자자료형 A/1(1 Byte) K 주소값(&)에 입력/저장]  → '초기화' 변수(문자→BCD/234, 엔터) 유지 
    printf("%c\n", K); // %c → 선언한 자료형크기 만큼 문자 1개 A/1 출력 

    scanf("%c", &K);   // scanf 실행:  입력서식(%c→문자) 버퍼 변수자료형(문자→BCD/234, 엔터) 매칭 O
                       // scanf 실행 성공:  문자 1개 B/2 입력/저장[%c 문자자료형 B/2(1 Byte) K 주소값(&)에 입력/저장]  →  버퍼 변수(문자→CD/34, 엔터) 유지 
    printf("%c\n", K); // %c → 선언한 자료형크기 만큼 문자 1개 B/2 출력 

    scanf("%c", &K);   // scanf 실행:  입력서식(%c→문자) 버퍼 변수자료형(문자→CD/34, 엔터) 매칭 O
                       // scanf 실행 성공:  문자 1개 C/3 입력/저장[%c 문자자료형 C/3(1 Byte) K 주소값(&)에 입력/저장]  →  버퍼 변수(문자→D/4, 엔터) 유지 
    printf("%c\n", K); // %c → 선언한 자료형크기 만큼 문자 1개 C/3 출력

    scanf("%c", &K);   // scanf 실행:  입력서식(%c→문자) 버퍼 변수자료형(문자→D/4, 엔터) 매칭 O
                       // scanf 실행 성공:  문자 1개 D/4 입력/저장[%c 문자자료형 D/4(1 Byte) K 주소값(&)에 입력/저장]  →  버퍼 변수(문자→엔터) 유지 
    printf("%c\n", K); // %c → 선언한 자료형크기 만큼 문자 1개 D/4 출력 

    scanf("%c", &K);   // scanf 실행:  입력서식(%c→문자) 버퍼 변수자료형(문자→엔터) 매칭 O
                       // scanf 실행 성공:  문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) K 주소값(&)에 입력/저장]
    printf("%c\n", K); // %c → 선언한 자료형크기 만큼 문자 1개 엔터 출력

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/65483ece-35ed-44c3-a5b3-65593f219bcb/b.png)

**c\_char\_4.c**

```cpp
// 입력서식 & '초기화'자료형 일치 O
// 예: Y 입력/저장 / 8 입력/저장

#include <stdio.h>

int main()
{
    char A;
    printf("---Input---\n"); 
    scanf("%c", &A);     // 입력서식(%c→문자)와 '초기화' 변수자료형(문자→Y엔터) 매칭 O
                         // scanf 실행 성공:  문자 Y 입력/저장[%c 문자자료형 Y(1 Byte) A 주소값(&)에 입력/저장]  →  '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("---Output---\n");
    printf("<%c>\n", A); // %c → 선언한 자료형크기 만큼 문자 1개 Y 출력 
    
    char B;
    printf("---Input---\n"); 
    scanf("%c", &B);     // scanf 실행:  입력서식(%c→문자) 버퍼 변수자료형(문자→엔터) 매칭 O
                         // scanf 실행 성공:  문자 1개 엔터(LF) 입력/저장[%c 문자자료형 엔터(1 Byte) B 주소값(&)에 입력/저장] 
    printf("---Output---\n");
    printf("<%d>\n", B); // %d → 선언한 자료형크기 만큼 문자 1개 엔터 ASCII Code 변환 정수 1개 10 출력 
    
    char C;
    printf("---Input---\n"); 
    scanf("%d", &C);     // scanf 실행:  입력서식(%d→정수) '초기화' 변수자료형(문자→Y) 매칭 X
                         // scanf 실행 실패:  쓰레기값[예: 쓰레기값 0 = char 자료형크기 1 Byte 만큼 정수 0 (1 Bytes = 8 Bits = 2진수 00000000 = 10진수 0)]  
                         //                   → '초기화' 변수(문자 → Y, 엔터) 버퍼 유지
    printf("---Output---\n");
    printf("<%d>\n", C); // %d → 선언한 자료형크기 만큼 정수 1개 쓰레기값 출력(예: 정수 1개 0)
    
    char D;
    printf("---Input---\n"); 
    scanf("%d", &D); // scanf 실행:  입력서식(%d→정수)와 버퍼 변수자료형(문자→Y)이 매칭 X
                     // scanf 실행 실패:  쓰레기값[예: 쓰레기값 0 = char C 메모리박스 쓰레기값 관련 X = char 자료형크기 1 Byte 정수값 0 출력(1 Bytes = 8 Bits = 2진수 00000000 = 10진수 0]) 
                     //                   → 버퍼 변수(문자 → Y, 엔터) 유지
    printf("---Output---\n"); 
    printf("<%c>\n", D); // %c → 선언한 자료형크기 만큼 문자 1개 쓰레기값 출력(예: 정수 1개 0 ASCII Code 변환 문자 1개 null)
    
    char E;
    printf("---Input---\n"); 
    scanf("%c", &E); // scanf 실행:  입력서식(%c→문자) 버퍼 변수자료형(문자→Y엔터) 매칭 O
                     // scanf 실행 성공:  문자 1개 Y 입력/저장[%c 문자자료형 Y(1 Byte) E 주소값(&)에 입력/저장]  →  버퍼 변수(문자→엔터) 유지
    printf("---Output---\n"); 
    printf("<%c>\n", E); // %c → 선언한 자료형크기 만큼 문자 1개 Y 출력 

    char F;
    printf("---Input---\n"); 
    scanf("%c", &F); // scanf 실행:  입력서식(%c→문자) 버퍼 변수자료형(문자→엔터) 매칭 O
                     // scanf 실행 성공:  문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) F 주소값(&)에 입력/저장]
    printf("---Output---\n"); 
    printf("<%c>\n", F); // %c → 선언한 자료형크기 만큼 문자 1개 엔터 출력 

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/8326b157-a696-445d-9463-6cfab73ff8ed/Picture3.png)

**c\_char\_5.c**

```cpp
// 입력서식 & '초기화'자료형 일치 O
// 예: 89 입력/저장

#include <stdio.h>

int main()
{
    char A;
    printf("---Input---\n");
    scanf("%c", &A); // 입력서식(%c→문자) '초기화' 변수자료형(문자→89엔터) 매칭 O
                     // scanf 실행 성공:  문자 1개 8 입력/저장[%c 문자자료형 8(1 Byte) A 주소값(&)에 입력/저장]  → '초기화' 변수(9, 엔터) 버퍼 유지
    printf("---Output---\n");
    printf("<%c>\n", A); // %c → 선언한 자료형크기 만큼 문자 1개 8 출력 
    
    char B;
    printf("---Input---\n");
    scanf("%c", &B); // 입력서식(%c→문자)와 '초기화' 변수자료형(문자→9엔터) 매칭 O
                     // scanf 실행 성공:  문자 1개 9 입력/저장[%c 문자자료형 9(1 Byte) A 주소값(&)에 입력/저장]  → 버퍼 변수(엔터) 유지
    printf("---Output---\n");
    printf("<%d>\n", B); // %c → 선언한 자료형크기 만큼 문자 1개 9 ASCII Code 변환 정수 1개 57출력 
    
    char C;
    printf("---Input---\n");
    scanf("%d", &C); // scanf 실행:  버퍼 변수(엔터) 삭제  →  입력서식(%d→문자) '초기화' 변수자료형(정수→89)이 매칭 O
                     // scanf 실행 성공:  정수 1개 89 입력/저장[%d 정수자료형 89(4 Bytes) C 주소값(&)에 입력/저장]  → '초기화' 변수(엔터) 버퍼 유지
    printf("---Output---\n");
    printf("<%d>\n", C); // %d → 선언한 자료형크기 만큼 정수 1개 89 출력 
    
    char D;
    printf("---Input---\n");
    scanf("%d", &D); // scanf 실행:  버퍼 변수(엔터) 삭제  →  입력서식(%d→문자) '초기화' 변수자료형(정수→89) 매칭 O
                     // scanf 실행 성공:  정수 1개 89 입력/저장[%d 정수자료형 89(4 Bytes) D 주소값(&)에 입력/저장]
    printf("---Output---\n");
    printf("<%c>\n", D); // %c →  선언한 자료형크기 만큼 정수 1개 89 ASCII Code 변환 문자 1개 Y 출력
    
    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/7d81f8e5-00b0-408a-bcc6-a48ed46c6610/Picture2.png)

**c\_char\_6.c**

```cpp
// 문자 2자리 이상 초기화
// 예 AB 입력/저장  (XYZ 입력/저장  /  123 입력저장)

#include <stdio.h>

int main()
{
    char X = 'AB';   // 뒷자리 문자 1개 입력/저장 → B 입력/저장 (XYZ: Z/ 123: 3)

    char Y;
    scanf("%c", &Y); // 앞자리 문자 1개 입력/저장 → A 입력/저장 (XYZ: X / 123: 1) → '초기화' 변수[문자→B(YZ/23), 엔터] 버퍼 유지

    printf("---선언 '동시' 초기화---\n");
    printf("<%c>\n", X); // %d → 문자 1개 B(Z/3) 출력
    printf("<%d>\n", X); // %d → 문자 1개 B(Z/3) ASCII Code 변환 66(90/) 정수 1개 출력
    
    printf("---선언   '후' 초기화---\n");
    printf("<%c>\n", Y); // %c → 문자 1개 A(X/1) 출력
    printf("<%d>\n", Y); // %c → 문자 1개 A(X/1) ASCII Code 변환값 65(88/) 정수 1개 출력

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/cd808153-4da5-46dd-aa06-ec8bc3babef3/Picture11.png)

**c\_char\_7.c**

```cpp
// 문자 2자리 이상 초기화
// 예 'AB' 입력/저장  (XYZ 입력/저장  /  123 입력저장)

#include <stdio.h>

int main()
{
    char X = 'AB';   // 뒷자리 문자 1개 입력/저장 → B 입력/저장 (XYZ: Z/ 123: 3)

    char Y;
    scanf("%c", &Y); // 앞자리 문자 1개 입력/저장 → A 입력/저장 (XYZ: X / 123: 1) → '초기화' 변수[문자→B(YZ/23), 엔터] 버퍼 유지

    printf("---선언 '동시' 초기화---\n");
    printf("<%c>\n", X); // %d → 문자 1개 B(Z/3) 출력
    printf("<%d>\n", X); // %d → 문자 1개 B(Z/3) ASCII Code 변환 정수 1개 66(90/) 출력
    
    printf("---선언   '후' 초기화---\n");
    printf("<%c>\n", Y); // %c → 문자 1개 A(X/1) 출력
    printf("<%d>\n", Y); // %c → 문자 1개 A(X/1) ASCII Code 변환 정수 1개 65(88/) 출력

    printf("---char Y 버퍼 변수 확인---\n");
    scanf("%c", &Y);     // 버퍼 변수[문자→B(Y/2)] 입력/저장
    printf("<%c>\n", Y); // %c → 문자 1개 B(Y/2) 출력

    scanf("%c", &Y);     // 버퍼 변수[문자→엔터(Z/3)] 입력/저장
    printf("<%c>\n", Y); // %c → 문자 1개 엔터(Z/3) 출력

    scanf("%c", &Y);     // scanf 실행:  입력서식(%c→문자) '초기화' 변수자료형(문자→A) 매칭 O 
    printf("<%c>\n", Y); // %c → 문자 1개 A(엔터/엔터) 출력 

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/a2a5286e-49c0-4d77-85a9-90e127209f15/Picture4.png)

* * *

# **int char**

### **Example)**

**d\_int\_char\_1.c**

```cpp
// 입력서식 & '초기화'자료형 일치 O
// 예:  126 입력/저장 → ~ 입력/저장

#include <stdio.h>

int main()
{
    int A;
    printf("---Input---\n");
    scanf("%d", &A); // 입력서식(%d→정수) '초기화' 변수자료형(정수→126) 매칭 O
                     // scanf 실행 성공:  정수 1개 126 입력/저장[%d 정수자료형 126(4 Bytes) A 주소값(&)에 입력/저장] → '초기화' 변수(문자→엔터) 버퍼 유지
    printf("---Output---\n");
    printf("<%d>\n", A); // %d → 선언한 자료형크기 만큼 정수 1개 126 출력
    printf("<%c>\n", A); // %c → 선언한 자료형크기 만큼 정수 1개 126 ASCII Code 변환 문자 1개 ~ 출력

    char B;
    printf("---Input---\n");
    scanf("%c", &B); // 입력서식(%c→문자) 버퍼 변수자료형(문자→엔터) 매칭 O
                     // scanf 실행 성공:  버퍼 문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) B 주소값(&)에 입력/저장]
    printf("---Output---\n");
    printf("<%c>\n", B); // %c → 선언한 자료형크기 만큼 문자 1개 엔터 출력
    printf("<%d>\n", B); // %d → 선언한 자료형크기 만큼 문자 1개 엔터 ASCII Code 변환 정수 1개 10 출력

    char C;
    printf("---Input---\n");
    scanf("%c", &C); // 입력서식(%c→문자)와 '초기화' 변수자료형(문자→~)이 매칭 O
                     // scanf 실행 성공:  문자 1개 ~ 입력/저장[%c 문자자료형 ~(1 Byte) C 주소값(&)에 입력/저장] → '초기화' 변수(문자→엔터) 버퍼 유지
    printf("---Output---\n");
    printf("<%c>\n", C); // %c → 선언한 자료형크기 만큼 문자 1개 ~ 출력
    printf("<%d>\n", C); // %d → 선언한 자료형크기 만큼 문자 1개 ~ ASCII Code 변환 정수 1개 126 출력

    char D;
    printf("---Input---\n");
    scanf("%c", &B); // 입력서식(%c→문자) 버퍼 변수자료형(문자→엔터) 매칭 O
                     // scanf 실행 성공:  버퍼 문자 2개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) B 주소값(&)에 입력/저장] 
    printf("---Output---\n");
    printf("<%c>\n", B); // %c → 선언한 자료형크기 만큼 문자 1개 엔터 출력
    printf("<%d>\n", B); // %d → 선언한 자료형크기 만큼 문자 1개 엔터 ASCII Code 변환 정수 1개 10 출력 → '초기화' 변수(문자→엔터) 버퍼 유지

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/2d92f4ac-508f-41a7-ae8e-f9f5faf49286/Picture3.png)

**d\_int\_char\_2.c**

```cpp
// 입력서식 & '초기화'자료형 일치 O
// 예: # 입력/저장 → 35 입력/저장 → 38 입력/저장

#include <stdio.h>

int main()
{
    char A;
    printf("---Input---\n");
    scanf("%c", &A); // 입력서식(%c→문자)와 '초기화' 변수자료형(문자→#엔터)이 매칭 O
                     // scanf 실행 성공:  문자 1개 # 입력/저장[%c 문자자료형 #(1 Byte) A 주소값(&)에 입력/저장] → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("---Output---\n");
    printf("<%c>\n", A); // %c → 선언한 자료형크기 만큼 문자 1개 # 출력
    printf("<%d>\n", A); // %d → 선언한 자료형크기 만큼 문자 1개 # ASCII Code 변환 정수 1개 35 출력

    char B;
    printf("---Input---\n");
    scanf("%c", &B); // 입력서식(%c→문자)와 버퍼 변수자료형(문자→엔터)이 매칭 O
                     // scanf 실행 성공:  문자 1개 # 입력/저장[%c 문자자료형 엔터(1 Byte) B 주소값(&)에 입력/저장]
    printf("---Output---\n");
    printf("<%c>\n", B); // %c → 선언한 자료형크기 만큼 문자 1개 엔터 출력
    printf("<%d>\n", B); // %d → 선언한 자료형크기 만큼 문자 1개 엔터 ASCII Code 변환 정수 1개 10 출력

    int C;
    printf("---Input---\n");
    scanf("%d", &C); // 입력서식(%d→정수)와 '초기화' 변수자료형(정수→35)이 매칭 O
                     // scanf 실행 성공: 정수 1개 35 입력/저장[%d 정수자료형 35(4 Bytes) C 주소값(&)에 입력/저장] → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("---Output---\n");
    printf("<%d>\n", C); // %d → 선언한 자료형크기 만큼 정수 1개 35 출력
    printf("<%c>\n", C); // %c → 선언한 자료형크기 만큼 정수 1개 35 ASCII Code 변환 문자 1개 # 출력

    int D;
    printf("---Input---\n");
    scanf("%d", &D); // scanf 실행:  버퍼 변수(문자→엔터) 삭제  →  입력서식(%d→정수) '초기화' 변수자료형(정수→38) 매칭 O
                     // scanf 실행 성공: 정수 1개 38 입력/저장[%d 정수자료형 38(4 Bytes) D 주소값(&)에 입력/저장] → '초기화' 변수(문자→엔터) 버퍼 유지 
    printf("---Output---\n");
    printf("<%d>\n", D); // %d → 선언한 자료형크기 만큼 정수 1개 38 출력
    printf("<%c>\n", D); // %c → 선언한 자료형크기 만큼 정수 1개 38 ASCII Code 변환 문자 1개 & 출력

    char E;
    printf("---Input---\n");
    scanf("%c", &E); // 입력서식(%c→문자)와 버퍼 변수자료형(문자→엔터)이 매칭 O
                     // scanf 실행 성공:  문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) B 주소값(&)에 입력/저장]
    printf("---Output---\n");
    printf("<%c>\n", E); // %c → 선언한 자료형크기 만큼 문자 1개 엔터 출력
    printf("<%d>\n", E); // %d → 선언한 자료형크기 만큼 문자 1개 엔터 ASCII Code 변환 정수 1개 10 출력
    
    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/befa261f-51bd-4977-a204-83224a7dac1f/Picture5.png)

**d\_int\_char\_3.c**

```cpp
// 입력서식 & '초기화'자료형 일치 X
// 예: Z 입력/저장

#include <stdio.h>

int main()
{
    int A;
    printf("---Input---\n");
    scanf("%d", &A); // 입력서식(%d→정수) '초기화' 변수자료형(문자→Z) 매칭 X
                     // scanf 실행 실패:  쓰레기값[예: 쓰레기값 0 = char 자료형크기 1 Byte 정수값 0 (1 Bytes = 8 Bits = 2진수 00000000 = 10진수 0)]  → '초기화' 변수(Z, 엔터) 버퍼 유지
    printf("---Output---\n");
    printf("<%d>\n", A); // %d → 선언한 자료형크기 만큼 쓰래기값 출력(예: 정수 1개 0)
    printf("<%c>\n", A); // %c → 선언한 자료형크기 만큼 쓰래기값 출력(예: 정수 1개 0 ASCII Code 변환 문자 1개 null)

    char B;
    printf("---Input---\n");
    scanf("%c", &B); // 입력서식(%c→문자) 버퍼 변수자료형(문자→Z엔터) 매칭 O
                     // scanf 실행 성공:  버퍼 문자 1개 Z 입력/저장[%c 문자자료형 Z(1 Byte) C 주소값(&)에 입력/저장] → 버퍼 변수(문자→엔터) 유지
    printf("---Output---\n");
    printf("<%c>\n", B); // %c → 선언한 자료형크기 만큼 문자 1개 Z 출력
    printf("<%d>\n", B); // %d → 선언한 자료형크기 만큼 문자 1개 Z ASCII Code 변환 정수 1개 90 출력

    char C;
    printf("---Input---\n");
    scanf("%c", &C); // 입력서식(%c→문자)와 버퍼 변수자료형(문자→엔터)이 매칭 O
                     // scanf 실행 성공:  버퍼 문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) C 주소값(&)에 입력/저장] 
    printf("---Output---\n");
    printf("<%c>\n", C); // %c → 선언한 자료형크기 만큼 문자 1개 엔터 출력
    printf("<%d>\n", C); // %d → 선언한 자료형크기 만큼 문자 1개 엔터 ASCII Code 변환 정수 1개 10 출력

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/e0efb84d-a9ba-43c1-8197-1514ac33e7a5/Picture8.png)

**d\_int\_char\_4.c**

```cpp
// 입력서식 & '초기화'자료형 일치 X
// 예: 90 입력/저장

#include <stdio.h>

int main()
{
    char A;
    printf("---Input---\n");
    scanf("%c", &A); // 입력서식(%c→문자)와 '초기화'변수 자료형(문자→90엔터)이 매칭 O
                     // scanf 실행 성공:  앞자리 문자 1개 입력/저장 → 9 입력/저장[%c 문자자료형 9(1 Byte) A 주소값(&)에 입력/저장] → '초기화' 변수(문자→0, 엔터) 버퍼 유지 
    printf("---Output---\n");
    printf("<%c>\n", A); // %c → 선언한 자료형크기 만큼 문자 1개 9 출력
    printf("<%d>\n", A); // %d → 선언한 자료형크기 만큼 문자 1개 9 ASCII Code 변환 정수 1개 57 출력

    int B;
    printf("---Input---\n");
    scanf("%d", &B); // 입력서식(%d→문자)와 버퍼 변수자료형(문자→0엔터 X 정수→0 O 인식) 매칭 O
                     // scanf 실행 성공:  버퍼 정수 1개 0 입력/저장[%d 정수자료형 0(4 Bytes) B 주소값(&)에 입력/저장] → 버퍼 변수(문자→엔터) 유지
    printf("---Output---\n");
    printf("<%d>\n", B); // %d → 선언한 자료형크기 만큼 정수 1개 0 출력
    printf("<%c>\n", B); // %c → 선언한 자료형크기 만큼 정수 1개 0 ASCII Code 변환 문자 1개 null 출력

    int C;
    printf("---Input---\n");
    scanf("%d", &C); // scanf 실행:  버퍼 변수(문자→엔터) 삭제  →  입력서식(%d→정수) '초기화' 변수자료형(정수→90) 매칭 O
                     // scanf 실행 성공: 정수 1개 90 입력/저장[%d 정수자료형 90(4 Bytes) A 주소값(&)에 입력/저장] → 버퍼 변수(문자→엔터) 유지
    printf("---Output---\n");
    printf("<%d>\n", C); // %d → 선언한 자료형크기 만큼 정수 1개 90 출력
    printf("<%c>\n", C); // %c → 선언한 자료형크기 만큼 정수 1개 90 ASCII Code 변환 문자 1개 Z 출력

    int D;
    printf("---Input---\n");
    scanf("%c", &D); // 입력서식(%c→문자)와 버퍼 변수자료형(문자→엔터) 매칭 O
                     // scanf 실행 성공: 문자 1개 엔터 입력/저장[%c 문자자료형 엔터(1 Byte) C 주소값(&)에 입력/저장]
    printf("---Output---\n");
    printf("<%c>\n", D); // %c → 선언한 자료형크기 만큼 문자 1개 엔터 출력
    printf("<%d>\n", D); // %d → int 자료형크기 4 Bytes:  [(3 Bytes = 쓰레기값) + (1 Bytes = 문자 엔터(LF-Line Feed) ASCII Code 변환 정수 1개 10)] 출력
    
    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/fad6b001-f4e5-487c-9e24-3b6e2f51cf5b/Picture4.png)
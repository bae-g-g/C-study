# Int vs Float vs Char

# **int**

*   정수(1개) 자료형

E.g.) 3, 0, -3

*   정수(1개) 자료형 크기: 4 Bytes = 32 Bits \* 1 Byte = 8 Bits

*   선언(메모리박스 할당)
자료형 변수명;
E.g.) `int A;`

*   초기화(입력/저장)

선언 '동시' 초기화: `=`

. 정수(지정변수값 O)

서식 X

E.g.) `int A = 97;`

. 문자(지정변수값 X)

서식 ' '

E.g.) `int A = 'a';`

선언 '후' 초기화: `scanf` 함수 + `%d` 지정 입력서식

*   출력

`int A = 5;`

정수 출력: `printf`함수 + `%d` 지정 출력서식
선언한 자료형크기(4 Bytes = 32 Bits) 만큼, 정수(`%d`) 1개 출력
∴ 4 Bytes 크기에서 정수 1개에 해당하는 전체 4 Bytes에 해당하는 2진수를 정수 출력
![](https://t9003081320.p.clickup-attachments.com/t9003081320/17c6817d-02e8-48d4-a8de-0a93948d2de1/Picture3.png)
↓
**ㅁ** 에 저장되어 있는 2진수를 10진수 정수로 출력

문자 출력: `printf`함수 + `%c` ASCII Code 변환
선언한 자료형크기(4 Bytes = 32 Bits) 만큼, 문자(`%c`) 1개 출력
∴ 4 Bytes 크기에서 문자 1개에 해당하는 가장 처음 1 Byte에 해당하는 2진수를 문자 출력
![](https://t9003081320.p.clickup-attachments.com/t9003081320/d52392e9-a2fb-46a0-a7a7-b34f61739e05/Picture2.png)
↓
**ㅁ** 저장되어 있는 2진수를 문자로 출력

### **Example)**

`int A = 5;`

\* 10진수 5 = 2진수 101 ➝ 00000000 00000000 00000000 00000**101** (32 Bits)

![](https://t9003081320.p.clickup-attachments.com/t9003081320/d03b1704-4708-4769-af68-750962a7e52a/Picture3.png)

**a\_int.c**

```cpp
#include <stdio.h> // 라이브러리 → 함수(e.g. scanf, printf, etc.) 실행 코드들의 저장소

void main() // 메인 함수
{ // 메인 함수 시작
    int A = 5; // int A:  정수의 자료형태로 변수 A라는 이름으로 '선언'(메모리박스 내에 A라는 이름으로 4 Bytes 크기의 입력/저장 공간 1개 할당)
               // = 5:  '동시에' 할당된 메모리박스 공간에 5라는 정수로 '초기화'(입력/저장)
               // → 정수형 메모리박스 1개 '할당'하여 변수 값(= 5) '초기화'(입력/저장)

    printf("%d\n", A);         // " "안의 '형태'로 출력해라(%d → 정수를 받아라, \n → 줄바꿈 해라):  %d 자리에 변수 A의 값을 받아 출력하고 줄바꿈 해라
    printf("%d\n", sizeof(A)); // " "안의 '형태'로 출력해라(%d → 정수를 받아라, \n → 줄바꿈 해라):  %d 자리에 변수 A의 자료형의 크기(=정수)를 받아 출력하고 줄바꿈 해라
    printf("%d\n", &A);        // " "안의 '형태'로 출력해라(%d → 정수를 받아라, \n → 줄바꿈 해라):  %d 자리에 A의 전체 주소값(= 정수)을 받아 출력하고 줄바꿈 해라
    // printf("%x\n", &A);        
    // printf("%X\n", &A);        
    // printf("%p\n", &A);        
} // 메인 함수 끝


```

*   자료형 크기: `%d` 정수 출력서식 + `sizeof` 함수
*   주소값: `%d` 정수 출력서식 + `&`
*   `\n`: 줄바꿈

* * *

# **float**

*   소수(1개) 자료형

E.g.) 9.7351....., 3.7, 2.0, -7.3

*   소수(1개) 자료형 크기: 4 Bytes = 32 Bits \* 1 Byte = 8 Bits

*   선언(메모리박스 할당)
자료형 변수명;
E.g.) `float B;`

*   초기화(입력/저장)

선언 '동시' 초기화: `=`

. 소수(지정변수값 O)

서식 X

E.g.) `float B = 0.25;`

선언 '후' 초기화: `scanf` 함수 + `%f` 지정 입력서식

*   출력

`float B = 8.625;`

소수 출력: `printf`함수 + `%f` 지정 출력서식
선언한 자료형크기(4 Bytes = 32 Bits) 만큼, 소수(`%f`) 1개 출력
∴ 4 Bytes 크기에서 소수 1개에 해당하는 전체 4 Bytes에 해당하는 2진수를 소수 출력
![](https://t9003081320.p.clickup-attachments.com/t9003081320/ac344a44-68a6-4f79-841a-4dff4746b6a0/Picture4.png)
↓
**ㅁ** 저장되어 있는 2진수를 소수 로 출력

### **Example)**

`float B = 8.625;`

\* 10진수 8.625 = 2진수 01000001 00001010 00000000 00000000

![](https://t9003081320.p.clickup-attachments.com/t9003081320/c9faa8f4-01e8-46b4-9eee-3a458ab70e1e/Picture4.png)

**b\_float.c**

```cpp
#include <stdio.h> // 라이브러리 → 함수(e.g. scanf, printf, etc.) 실행 코드들의 저장소

void main() // 메인 함수
{ // 메인 함수 시작
    float B = 8.625; // float B:  소수의 자료형태로 변수 B라는 이름으로 '선언'(메모리박스 내에 B라는 이름으로 4 Bytes 크기의 입력/저장 공간 1개 할당)
                     // = 8.625:  '동시에' 할당된 메모리박스 공간에 8.625라는 소수로 '초기화'(입력/저장)
                     // → 소수형 메모리박스 1개 '할당'하여 변수 값(= 8.625) '초기화'입력/저장

    printf("%f\n", B); // " "안의 '형태'로 출력해라(%f → 소수를 받아라, \n → 줄바꿈 해라):  %f 자리에 변수 B의 값을 받아 출력하고 줄바꿈 해라
    printf("%d\n", sizeof(B)); // " "안의 '형태'로 출력해라(%d → 정수를 받아라, \n → 줄바꿈 해라):  %d 자리에 변수 A의 자료형의 크기(=정수)를 받아 출력하고 줄바꿈 해라
    printf("%d\n", &B); //  " "안의 '형태'로 출력해라(%d → 정수를 받아라, \n → 줄바꿈 해라):  %d 자리에 A의 전체 주소값(= 정수)을 받아 출력하고 줄바꿈 해라

} // 메인 함수 끝


```

*   자료형 크기: `%d` 정수 출력서식 + `sizeof` 함수
*   주소값: `%d` 정수 출력서식 + `&`
*   `\n`: 줄바꿈

* * *

# **char**

*   문자(1개) 자료형
E.g.) 일반문자 'A', 'a', 'M', 'm'
특수문자 '%', '&', '\*', '@'
공백문자 '\\n' 엔터(줄바꿈), ' ' 스페이스(뛰어쓰기) 등

E.g.) '0', '1', '2', '3', '4', '5'

→ 문자로 인식 O

*   문자(1개) 자료형 크기: 1 Byte = 8 Bits \* 1 Byte = 8 Bits

*   선언(메모리박스 할당)
자료형 변수명;
E.g.) `char C;`

*   초기화(입력/저장)

선언 '동시' 초기화: `=` & `' '`

. 문자(지정변수값 O)

서식 ' '

E.g.) `char C = 'a';`

. 정수(지정변수값 X)

서식 X

E.g.) `char C = 97`;

선언 '후' 초기화: `scanf` 함수 + `%c` 지정 입력서식

*   출력

`char C = 'm';`

문자 출력: `printf`함수 + `%c` 지정 출력서식
선언한 자료형크기(1 Byte = 8 Bits) 만큼, 문자(`%c`) 1개 출력
∴ 1 Byte 크기에서 문자 1개에 해당하는 전체 1 Byte에 해당하는 2진수를 문자 출력
![](https://t9003081320.p.clickup-attachments.com/t9003081320/0c2b3b0a-82bd-4ee3-94e9-400c7cbd65a9/Picture7.png)
↓
**ㅁ** 에 저장되어 있는 2진수를 문자로 출력

정수 출력: `printf`함수 + `%d` ASCII Code 변환
선언한 자료형크기(1 Byte = 8 Bits) 만큼, 정수(`%d`) 1개 출력
∴ 1 Byte 크기에서 정수 1개 4 Bytes 크기 중
선언한 자료형의 크기인 1 Byte 만큼에만 해당하는 2진수를 정수 출력
![](https://t9003081320.p.clickup-attachments.com/t9003081320/02559a6d-8e99-4dd8-abf2-e23bb4a0d320/Picture9.png)
↓
**ㅁ** 저장되어 있는 2진수를 정수로 출력

※ ASCII Code: 10/16/8/2진수 ←→ 문자/기호 (컴퓨터처리 신호 변환/처리)

![](https://t9003081320.p.clickup-attachments.com/t9003081320/aa5ce56a-d3ae-45db-b68e-c81564db51bb/ASCII%20Code.jpg)

### **Example)**

**c\_char\_1.c**
`char C = 'm';`

```cpp
#include <stdio.h> // 라이브러리 → 함수(e.g. scanf, printf, etc.) 실행 코드들의 저장소

void main() // 메인 함수
{ // 메인 함수 시작
    char C = 'm'; // char C:  문자의 자료형태로 변수 C라는 이름으로 '선언'(메모리박스 내에 C라는 이름으로 1 Byte 크기의 입력/저장 공간 1개 할당)
                  // = 'm':  '동시에' 할당된 메모리박스 공간에 m라는 문자로 '초기화'(입력/저장)
                  // → 문자형 메모리박스 1개 '활성화'하여 변수 값(= m) '초기화'입력/저장

    printf("%c\n", C); // " "안의 '형태'로 출력해라(%c → 문자를 받아라, \n → 줄바꿈 해라):  %c 자리에 변수 C의 값을 받아 출력하고 줄바꿈 해라
    printf("%d\n", sizeof(C)); // " "안의 '형태'로 출력해라(%d → 정수를 받아라, \n → 줄바꿈 해라):  %d 자리에 변수 C의 자료형의 크기(=정수)를 받아 출력하고 줄바꿈 해라
    printf("%d\n", &C); //  " "안의 '형태'로 출력해라(%d → 정수를 받아라, \n → 줄바꿈 해라):  %d 자리에 C의 전체 주소값(= 정수)을 받아 출력하고 줄바꿈 해라
    
} // 메인 함수 끝


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/5be0c866-0c73-44cb-8c33-d6f2298a4d60/Picture1.png)
**초기화 과정**
`char C = 'm';`

❶ Past Compiler
① 문자 m (표면적) 초기화
↓
Complie Time: 2진수 변환 ➝ Hard Disk에 할당
① 문자 m →(ASCII Codes 변환)→ 정수 10진수 109
② 정수 10진수 109 = 2진수 **1101101** (7 Bits)
↓
(정수 크기 4 Bytes = 32 Bits Little Endian 나열 )
↓
0**1101101** 00000000 00000000 00000000
↓
(문자 크기 1 Byte = 8 Bits Little Endian 나열 유지 )
↓
Run Time: Memroy RAM에 할당
① 0**1101101** (1 Byte = 8 Bits) 할당

❷ Current Compiler
① 문자 m (표면적) 초기화
↓
Complie Time: 2진수 변환 내부 구현 ➝ Hard Disk에 할당
① 문자 m →(ASCII Codes 기반 내부구현)→ 10진수 109 = 문자 1 Bytes(8 Bits) 크기 2진수 0**1101101**
↓
Run Time: Memroy RAM에 할당
① 0**1101101** (1 Byte = 8 Bits) 할당

**출력 과정**
`printf` + `%c`
① 선언한 자료형크기(1 Byte = 8 Bits) 만큼 문자(`%c`) 1개 출력
② 2진수 0**1101101** (8 Bits) →(ASCII Codes 변환)→ 문자 m 출력
선언한 자료형크기(1 Byte = 8 Bits) 만큼, 문자(`%c`) 1개 출력
∴ 1 Byte 크기에서 문자 1개에 해당하는 전체 1 Byte에 해당하는 2진수를 문자 출력
![](https://t9003081320.p.clickup-attachments.com/t9003081320/c7c7260b-2864-4231-acbc-c51ddf58460b/image.png)
↓
**ㅁ** 에 저장되어 있는 2진수를 문자로 출력

**c\_char\_2.c**
`char C = 109;`

```cpp
#include <stdio.h> // 라이브러리 → 함수(e.g. scanf, printf, etc.) 실행 코드들의 저장소

void main() // 메인 함수
{ // 메인 함수 시작
    char C = 109; // char C:  문자의 자료형태로 변수 C라는 이름으로 '선언'(메모리박스 내에 C라는 이름으로 1 Byte 크기의 입력/저장 공간 1개 할당)
                  // = 109:  '동시에' 할당된 메모리박스 공간에 109라는 정수로 '초기화'(입력/저장)
                  // → 근데 '  '으로 초기화(입력/저장)하지 않아 할당된 메모리박스는 문자이기에 C 변수 내의 값을 정수를 문자형태로 '형변환' 초기화(입력/저장)

    printf("%c\n", C); // " "안의 '형태'로 출력해라(%c → 문자를 받아라, \n → 줄바꿈 해라):  %c 자리에 변수 C의 값을 받아 출력하고 줄바꿈 해라
                       // → C 변수 내의 값을 정수로 초기화(입력/저장)했기 때문에, ASCII Code에 의해 정수 109 = 문자 m 이므로, m 출력

    printf("%d\n", sizeof(C)); // " "안의 '형태'로 출력해라(%d → 정수를 받아라, \n → 줄바꿈 해라):  %d 자리에 변수 C의 자료형의 크기(=정수)를 받아 출력하고 줄바꿈 해라
    printf("%d\n", &C); //  " "안의 '형태'로 출력해라(%d → 정수를 받아라, \n → 줄바꿈 해라):  %d 자리에 C의 전체 주소값(= 정수)을 받아 출력하고 줄바꿈 해라

} // 메인 함수 끝


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/ff64cca6-dfd7-4278-a566-99cf6eed143a/Picture1.png)
**초기화 과정**
`char C = 109;`

❶ Past Compiler
① 정수 109 (표면적) 초기화
↓
Complie Time: 2진수 변환 ➝ Hard Disk에 할당
① 정수 10진수 109 = 2진수 **1101101** (7 Bits)
↓
(정수 크기 4 Bytes = 32 Bits Little Endian 나열 )
↓
0**1101101** 00000000 00000000 00000000
↓
(문자 크기 1 Bytes = 8 Bits Little Endian 나열 유지)
↓
Run Time: Memroy RAM에 할당
① 0**1101101** (1 Byte = 8 Bits) 할당

❷ Current Compiler
① 정수 109 (표면적) 초기화
↓
Complie Time: 2진수 변환 내부 구현 ➝ Hard Disk에 할당
① 10진수 109 = 문자 1 Bytes(8 Bits) 크기 2진수 0**1101101**
↓
Run Time: Memory RAM에 할당
① 0**1101101** (1 Byte = 8 Bits) 할당

**출력 과정**
`printf` + `%c`
① 선언한 자료형크기(1 Byte = 8 Bits) 만큼 문자(`%c`) 1개 출력
② 2진수 0**1101101** (8 Bits) →(ASCII Codes 변환)→ 문자 m 출력
선언한 자료형크기(1 Byte = 8 Bits) 만큼, 문자(`%c`) 1개 출력
∴ 1 Byte 크기에서 문자 1개에 해당하는 전체 1 Byte에 해당하는 2진수를 문자 출력
![](https://t9003081320.p.clickup-attachments.com/t9003081320/75b1443f-1bbd-4944-82c3-9a41afa7fdb2/image.png)
↓
**ㅁ** 에 저장되어 있는 2진수를 문자로 출력

**c\_char\_3.c**
`char C = 'm';`

```cpp
#include <stdio.h> // 라이브러리 → 함수(e.g. scanf, printf, etc.) 실행 코드들의 저장소

void main() // 메인 함수
{ // 메인 함수 시작
    char C = 'm'; // char C:  문자의 자료형태로 변수 C라는 이름으로 '선언'(메모리박스 내에 C라는 이름으로 1 Byte 크기의  입력/저장 공간 1개 할당)
                  // = 'm':  '동시에' 할당된 메모리박스 공간에 m라는 문자로 '초기화'(입력/저장)
                  // → 문자형 메모리박스 1개 '선언'하여 변수 값(= m) '초기화'입력/저장

    printf("%d\n", C); // " "안의 '형태'로 출력해라(%d → 정수를 받아라, \n → 줄바꿈 해라):  %d 자리에 변수 C의 값을 받아 출력하고 줄바꿈 해라
                       // → C 변수 내의 값을 문자로 초기화(입력/저장)했기 때문에, ASCII Code에 의해 문자 m = 정수 109 이므로, 109 출력

    printf("%d\n", sizeof(C)); // " "안의 '형태'로 출력해라(%d → 정수를 받아라, \n → 줄바꿈 해라):  %d 자리에 변수 C의 자료형의 크기(=정수)를 받아 출력하고 줄바꿈 해라
    printf("%d\n", &C); //  " "안의 '형태'로 출력해라(%d → 정수를 받아라, \n → 줄바꿈 해라):  %d 자리에 C의 주전체 주소값(= 정수)을 받아 출력하고 줄바꿈 해라

} // 메인 함수 끝


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/62d86853-6a76-4b28-8bbe-ab4de30c64bc/Picture1.png)
**초기화 과정**
`char C = 'm';`

❶ Past Compiler
① 문자 m (표면적) 초기화
↓
Complie Time: 2진수 변환 ➝ Hard Disk에 할당
① 문자 m →(ASCII Codes 변환)→ 정수 10진수 109
② 정수 10진수 109 = 2진수 **1101101** (7 Bits)
↓
(정수 크기 4 Bytes = 32 Bits Little Endian 나열 )
↓
0**1101101** 00000000 00000000 00000000
↓
(문자 크기 1 Bytes = 8 Bits Little Endian 나열 )
↓
Run Time: Memroy RAM에 할당
① 0**1101101** (1 Byte = 8 Bits) 할당

❷ Current Compiler
① 문자 m (표면적) 초기화
↓
Complie Time: 2진수 변환 내부 구현 ➝ Hard Disk에 할당
① 문자 m →(ASCII Codes 기반 내부구현)→ 10진수 109 = 문자 1 Bytes(8 Bits) 크기 2진수 0**1101101**
↓
Run Time: Memroy RAM에 할당
① 0**1101101** (1 Byte = 8 Bits) 할당

**출력 과정**
`printf` + `%d`
① 선언한 자료형크기(1 Byte = 8 Bits) 만큼 정수(%d) 1개 출력
② 2진수 0**1101101** (8 Bits) →(ASCII Codes 변환)→ 정수 109 출력
∴ 1 Byte 크기에서 정수 1개 4 Bytes 크기 중
선언한 자료형의 크기인 1 Byte 만큼에만 해당하는 2진수를 정수 출력
![](https://t9003081320.p.clickup-attachments.com/t9003081320/9a9e5ed5-6c09-4048-a582-6c5d3517e4ce/image.png)
↓
**ㅁ** 저장되어 있는 2진수를 정수로 출력

**c\_char\_4.c**

```cpp
#include <stdio.h> // 라이브러리 → 함수(e.g. scanf, printf, etc.) 실행 코드들의 저장소

void main() // 메인 함수
{ // 메인 함수 시작
    // 메인 함수 내에 여러 변수 '선언'(메모리할당) 및 '초기화'(입력/저장) 가능
    char I = 'A';
    // char J = A; // 문자는 '  '이용 '초기화'(입력/저장) 해야함
    char X = 77;
    char Y = '7';

    printf("%c %d\n", I, I); // " "안의 '형태'로 출력해라(%c → 문자를 받아라, %d → 정수를 받아라,\n → 줄바꿈 해라)
                              // ➝ 1) %c 자리에 변수 I의 값을 받아 출력하고 2) %d 자리에 변수 I의 값을 받아 출력(문자로 '초기화'입력/저장→ASCII Code 변환)하고 3) 줄바꿈 해라
    printf("%c %d\n", X, X); // " "안의 '형태'로 출력해라(%c → 문자를 받아라, %d → 정수를 받아라,\n → 줄바꿈 해라)
                              // ➝ 1) %c 자리에 변수 X의 값을 받아 출력(정수로 '초기화'입력/저장→ASCII Code 변환)하고 2) %d 자리에 변수 X의 값을 받아 출력하고 3) 줄바꿈 해라
    printf("%c %d\n", Y, Y); // " "안의 '형태'로 출력해라(%c → 문자를 받아라, %d → 정수를 받아라,\n → 줄바꿈 해라)
                              // ➝ 1) %c 자리에 변수 Y의 값을 받아 출력하고 2) %d 자리에 변수 Y의 값을 받아 출력(문자로 '초기화'입력/저장→ASCII Code 변환)하고 3) 줄바꿈 해라

    printf("%d %d %d\n", &I, &X, &Y);
} // 메인 함수 끝


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/1edee082-e0b0-46da-9326-55f30d004d1c/Picture12.png)

* * *
* * *

# **int char**

### **Example)**

**d\_int\_char.c**

```cpp
#include <stdio.h> // 라이브러리 → 함수(e.g. scanf, printf, etc.) 실행 코드들의 저장소

void main() // 메인 함수
{ // 메인 함수 시작

    // 메인 함수 내에 여러 자료형/변수 '선언'(메모리 할당) 및 '초기화'(입력/저장) 가능
    int number_1 = 65;
    int number_2 = 'A';

    char text_1 = 'X';
    char text_2 = 88;
    char text_3 = '8';

    printf("%d %c\n", number_1, number_1); // " "안의 '형태'로 출력해라(%d → 정수를 받아라, %c → 문자를 받아라,\n → 줄바꿈 해라)
                                           // ➝ 1) %d 자리에 변수 number_1의 값을 받아 출력하고 2) %c 자리에 변수 number_1의 값을 받아 출력(정수 →ASCII Code 변환→ 문자)하고 3) 줄바꿈 해라
    printf("%d %c\n", number_2, number_2); // " "안의 '형태'로 출력해라(%d → 정수를 받아라, %c → 문자를 받아라,\n → 줄바꿈 해라)
                                           // ➝ 1) %d 자리에 변수 number_2의 값을 받아 출력(문자 →ASCII Code 변환→ 정수)하고 2) %c 자리에 변수 number_2의 값을 받아 출력하고 3) 줄바꿈 해라
    
    printf("------------------------\n");

    printf("%c %d\n", text_1, text_1); // " "안의 '형태'로 출력해라(%c → 문자를 받아라, %d → 정수를 받아라,\n → 줄바꿈 해라)
                                       // ➝ 1) %c 자리에 변수 text_1의 값을 받아 출력하고 2) %d 자리에 변수 text_1의 값을 받아 출력(문자 →ASCII Code 변환→ 정수)하고 3) 줄바꿈 해라
    printf("%c %d\n", text_2, text_2); // " "안의 '형태'로 출력해라(%c → 문자를 받아라, %d → 정수를 받아라,\n → 줄바꿈 해라)
                                       // ➝ 1) %c 자리에 변수 text_2의 값을 받아 출력(정수 →ASCII Code 변환→ 문자)하고 2) %d 자리에 변수 text_2의 값을 받아 출력하고 3) 줄바꿈 해라
    printf("%c %d\n", text_3, text_3); // " "안의 '형태'로 출력해라(%c → 문자를 받아라, %d → 정수를 받아라,\n → 줄바꿈 해라)
                                       // ➝ 1) %c 자리에 변수 text_3의 값을 받아 출력하고 2) %d 자리에 변수 text_3의 값을 받아 출력(문자 →ASCII Code 변환→ 정수)하고 3) 줄바꿈 해라
    printf("%d %d %d %d %d\n", &number_1, &number_2, &text_1, &text_2, &text_3);
} // 메인 함수 끝


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/7156007d-1d9e-40fe-aa2a-77ff00d979e6/Picture8.png)
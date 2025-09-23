# [CH09L] Pointer (Lecture)

## **C Language Learning Road Map**

> 데이터 형식 종류 ➝ 데이터 입력/출력 방식/원리 ➝ 다양한 처리과정

![](https://t9003081320.p.clickup-attachments.com/t9003081320/9ffdfbf7-497a-4a5e-ac73-07ec85a51eea/Picture1.png)

# **Pointer 포인터**

컴퓨터가 해당언어(C Language)로 자료(Data)를 처리하는 방식

&, \*

#### **Ampersand Operator 주소/번지 연산자**
`&` 앰퍼샌드/앤드
*   변수값: 메모리박스(RAM)에 초기화된 데이터
*   주소값: 변수값(데이터) 초기화 위치
변수의 주소값 반환(Return)

![](https://t9003081320.p.clickup-attachments.com/t9003081320/6ad55784-91ae-4092-ad72-89a26f10716a/Pointer-Ptr_1.drawio%20(1).png)
변수값(데이터)의 주소값 = 해당 변수값(데이터)이 초기화된 메모리박스(RAM)의 "시작" 주소값

**a\_and.c**

```plain
#include <stdio.h>

int main()
{
    int A = 65;
    int B = 66;
    int C = 67;
    int D = 68;

    // 변수의 주소값을 다른 변수에 초기화
    int A_address = &A;
    int B_address = &B;
    int C_address = &C;
    int D_address = &D;

    // 주소값 10진수 출력  →  %d
    printf("%d\n", A_address); 
    printf("%d\n", B_address); 
    printf("%d\n", C_address); 
    printf("%d\n", D_address); 

    // 주소값 16진수 출력  →  %p
    printf("%p\n", A_address); 
    printf("%p\n", B_address); 
    printf("%p\n", C_address); 
    printf("%p\n", D_address); 

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/00932c8d-b037-4658-861f-d4736d200c7a/Pointer-Ptr_2.drawio%20(1).png)

#### **Asterisk Operator 참조 연산자**
`*` 에스터리스크/스타 → 포인터

포인터 변수 선언 및 초기화
포인터 변수는 주소값을 초기화하기 위해 선언한 변수
→ 포인터 변수는 주소값 초기화 역할
→ 포인터 변수는 주소값의 영향력 범위 지정 역할
\= 주소값이 가르키는값/변수의 자료형 종류/크기 지정 역할
포인터와 포인터 변수 사용
→ 포인터+포인터 변수는 포인터 변수에 초기화된 주소값이 가르키는/참조하는 값/변수
→ 포인터+포인터 변수의 반환값(Return 값) = 주소값이 가르키는/참조하는 값/변수
※ & 변수 = 주소값
※ 포인터 변수 = & 변수 = 주소값
※ 포인터+포인터 변수(\*포인터 변수) = 주소값이 가르키는/참조하는 값/변수
※ 포인터 변수(= 주소값)보다 \*포인터 변수(= 주소값이 가르키는/참조하는 값/변수)는 한차원 ↓
\= 변수의 주소값 아래에 변수값이 초기화
★ 포인터 변수가 가르키는 값 = 초기화된 값(주소값)이 가르키는 값
∴ 초기화된 값(주소값)이 동일 ➝ 가르키는/참조하는 값/변수도 동일

E.g)
int X = 5; ① //  X는 변수: X는 int 변수
X = 5;
int \*X\_ptr = &X; ② //  X\_ptr은 변수: X\_ptr은 포인터 변수 → X\_ptr은 int 포인터 변수
→ X\_ptr은 int \* 변수
X\_ptr = &X; ③
\*X\_ptr = 5 = X; ④ // \*X\_ptr은 포인터+변수: \*X\_ptr은 포인터+포인터 변수(\*포인터 변수)
//   X\_ptr (= &X)보다 \*X\_ptr (= X = 5)는 한차원 아래

| X | X\_ptr | \*X\_ptr |
| ---| ---| --- |
| 데이터 초기화<br><br>X = 5 | 주소값 초기화<br><br>&X | 초기화된 주소값이 가리키는 값<br>\= 데이터<br>X = 5 |
| 변수<br><br><br><br><br><br>int 변수<br>int형 변수<br>int자료형 변수<br><br>자료형: int | 변수<br><br>포인터 변수<br>포인터형 변수<br>포인터자료형 변수<br><br>int 포인터 변수<br>int 포인터형 변수<br>int 포인터자료형 변수<br><br>자료형: int 포인터<br>int \*<br>※ int<br>→ 주소값이 가리키는/참조하는<br>값/변수의 자료형 O<br>→ 주소값 자체의 자료형 X | 포인터+변수<br><br>포인터+포인터 변수<br>포인터+포인터형 변수<br>포인터+포인터자료형 변수<br><br>포인터+int 포인터 변수<br>포인터+int 포인터형 변수<br>포인터+int 포인터자료형 변수<br><br>※ `+` 名名: '붙인것' or '붙인것' 생략 |
| X\_ptr(= &X) 보다 \*X\_ptr (= X = 5) 한차원 ↓<br>\= 주소값 아래에 데이터(주소값이 가르키는/참조하는 값)이 초기화 |

* * *

Int Char Float ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-1878](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-1878))

Array (X vs &X\[0\]) ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-1898](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-1898))

Array (&X) ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-1918](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-1918))

Array (X vs &X\[0\] vs &X) ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-1938](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-1938))

Function #1 (Parameter) ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-1958](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-1958))

Void + Generic ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-1978](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-1978))

Usability ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-1998](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-1998))
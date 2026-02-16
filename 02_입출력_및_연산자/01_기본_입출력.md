# [CH02L] Input_Ouput (Lecture)

## **C Language Learning Road Map**

> 데이터 형식 종류 ➝ 데이터 입력/출력 방식/원리 ➝ 다양한 처리과정

![](https://t9003081320.p.clickup-attachments.com/t9003081320/73f5eb48-b88d-434a-b9f7-13418674c95a/Picture6.png)

# **Input & Output 입력과 출력**

컴퓨터가 해당언어(C Language)로 자료(Data)를 입력/저장 → 출력하는 방식

int, float, char, array

※ 선언시 변수 → 메모리박스 자료형+크기
※ 초기화시 &변수 → 메모리박스 주소값

※ 10진수 정수의 2진수 입력/저장 → 양수: 2진수 입력/저장, 음수: 2의 보수 2진수 입력/저장
→ `printf %d` 10진수 정수 출력
※ 10진수 소수의 2진수 입력/저장 → 부동소수점 환산 2진수 입력/저장
→ `printf %f` 10진수 소수 출력
※ 문자의 ASCII Code 변환 10진수의 2진수 입력/저장 → 2진수 입력/저장
→ `printf %c` 문자 출력

## **Input 입력**

'선언' = 메모리박스 '할당' = 메모리박스 '활성화'(자가 내집) & '생성'(확장 내집)

'초기화' = 변수값 '입력/저장'

*   선언 '동시' 초기화: `=`
집 할당받고 '동시'에 사람들어오고 문닫기
*   선언 '후' 초기화: `scanf` 함수 + 입력서식 `%d` `%f` `%c` `%s`
집 할당받고 문닫은 '후' 다시 문열고 사람들어오기

※ `scanf` 함수 + 입력서식 `%d` 정수 `%f` 소수 `%c` 문자 1개 `%s` 문자열
\= 출입허가 Key (정수 출입 가능, 소수 출입가능, 문자 1개 출입가능, 문자열 출입가능)

E.g.)
입력서식 `%d` `%f` & 초기화 자료형 일치 X
\= 출입허가 Key & 출입 자료형 일치 X
\= `scanf`함수 실행 X → 초기화 변수값은 버퍼 유지

. scanf("%d", X); → 문자 초기화 (e.g. A, B, C) `scanf`함수 실행 X
. scanf("%f", Y); → 문자 초기화 (e.g. A, B, C) `scanf`함수 실행 X

. scanf("%c", X); → 정수 초기화 (e.g. 1, 2, 3을 문자 '1', '2', '3'로 인식) `scanf`함수 실행 O
. scanf("%s", Y); → 문자1개 초기화 (e.g. A ➝ 문자열 1개) `scanf`함수 실행 O
. scanf("%c", Z); → 문자열 초기화 (e.g. ABCD, 1234) `scanf`함수 실행 O

※ `scanf` 작동원리

![](https://t9003081320.p.clickup-attachments.com/t9003081320/1eeeccb5-7ab3-4a30-8a98-f8a53b633b89/0_scanf_working_principle_1_upscaled.jpg)

## **Output 출력**

`printf`함수 + 출력서식 `%d` `%f` `%c` `%s`

* * *

### **Basic**

Int vs Float vs Char ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2538](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2538))

Array ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2558](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2558))

Char vs Array ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2578](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2578))

Int vs Float vs Char vs Array ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2598](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2598))

* * *

### **Advanced**

Hexadecimal Byte & Bit ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-4318](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-4318))

Input Advanced Concept ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-4338](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-4338))
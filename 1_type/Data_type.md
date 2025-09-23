# [CH01L] Data_Type (Lecture)

## **C Language Learning Road Map**

> 데이터 형식 종류 ➝ 데이터 입력/출력 방식/원리 ➝ 다양한 처리과정

![](https://t9003081320.p.clickup-attachments.com/t9003081320/c04916dc-66e8-457f-a0ed-8044d11f0f59/Picture3.png)

# **Data Type 자료형**

컴퓨터가 해당언어(C Language)로 어떤 자료(Data) 형식(Type)를 받아 들일지 결정

int, float, char, array, bool

## **Terminology 용어**

![](https://t9003081320.p.clickup-attachments.com/t9003081320/75ed7d4d-58db-4480-bd2f-51dc58909e8a/Picture2.png)
Computer (컴퓨터) = 아파트 단지
Memory Box\_Whole (메모리박스 전체) = 아파트동(여러집)
Memory Box\_Assinged (메모리박스 할당) = 내집
Byte/Bit (바이트/비트) = 방갯수/방을 파티션으로 나눈 갯수

주소값 = 집주소
\= 방주소 (집입구 첫번째 방 주소) = Bytes 내 0번째 Byte 주소값
≒ 전체 집주소 = Bytes 내 0번째 Byte 주소값(마지막 Byte 주소값까지의 범위를 포함한 의미)

*   서식문자 `%p`: 眞주소값 O

E.g.) 000000000061FE1C

*   서식문자 `%d`: 眞주소값 X
10진수 정수: 자리수 상이(8자리, 10자리 등)
E.g.) 6422044
*   서식문자 `%x`: 眞주소값 X
10진수 → 16진수 정수 + 소문자
E.g.) 61fe1c
*   서식문자 `%X`: 眞주소값 X
10진수 → 16진수 정수 + 대문자
E.g.) 61FE1C

**Overflow & Underflow 오버플로우 & 언더 플로우**
오버플로우: 양의 정수 범위 (약 +21억) 초과시 발생 + ➝ - (양수 ➝ 음수)
언더플로우: 음의 정수 범위 (약 - 21억) 초과시 발생 - ➝ + (음수 ➝ 양수)
E.g.) 오버워치게임에서 캐릭터가 공격받아 -1레벨이 되었는데 +최고 레벨업
![](https://t9003081320.p.clickup-attachments.com/t9003081320/94203847-6bd0-41ff-ad9c-01d9ddf81d90/Picture5.png)

* * *

## **Little & Big Endian 선언 및 초기화 방식**

'선언' = 메모리박스 '할당'

'초기화' = 변수값 '입력/저장'
Big Endian 방식: 일반적인 순서 입력/저장
Little Endian 방식: 역 순서 입력/저장

❶ **변수 선언 및 초기화**
변수
Little Endian 방식 (% New PC): 높은 주소값 → 낮은 주소값 = 오른쪽 → 왼쪽
E.g.)
int A = 5;
float B = 8.625;
char C = X;
![](https://t9003081320.p.clickup-attachments.com/t9003081320/781f0377-0cc5-4534-8cc7-bc24dd65c254/Picture1.png)

`Window OS`
![](https://t9003081320.p.clickup-attachments.com/t9003081320/781f0377-0cc5-4534-8cc7-bc24dd65c254/Picture1.png)
(대체적으로) 메모리박스 할당시 주소값 공백 없이 할당
∵ Window OS 처리 기반에서 처리 및 효율성 증가 고려
Pros) 개발자 입장에서 메모리박스 할당 위치 예측하여 Programming 가능 O
Cons) 개발자의 Programming 역량에 따라 의도한 메모리박스 할당위치에 해당 변수값 초기화 X
\= Overflow 초기화 가능성 증가

`Mac Os`
![](https://t9003081320.p.clickup-attachments.com/t9003081320/ad6f251d-4e5a-47b2-8bca-5e6ec49a1ca0/Picture1.png)
(대체적으로) 메모리박스 할당시 주소값 간의 공백을 두고 할당
∵ Mac OS 처리 기반에서 처리 및 효율성 증가 고려
Pros) 개발자의 Programming 역량과 관계없이
의도한 메모리박스 할당위치에 해당 변수값 초기화 O
\= Overflow 초기화 가능성 감소
Cons) 개발자 입장에서 메모리박스 할당 위치 예측하여 Programming 가능 X

배열
배열 요소 초기화
Big Endian 방식 (% Old PC): 낮은 주소값 → 높은 주소값 = 왼쪽 → 오른쪽
E.g.)
char D\[4\] = { 'I', 'J', 'K', '\\0'};
![](https://t9003081320.p.clickup-attachments.com/t9003081320/7a6f4ad9-7156-42c3-88d8-f0fc9efc0f7d/Picture6.png)

❷ **10진수 변수값의 2진수값 초기화**
E.g.)
10진수 2023 = 2진수 00000000 00000000 00000111 11100111 \* 4 Bytes = 32 Bits

Little Endian 방식 (% New PC): 앞 8 Bits 부터 높은 주소값 → 낮은 주소값 = 오른쪽 → 왼쪽
![](https://t9003081320.p.clickup-attachments.com/t9003081320/1cba7d09-154a-403a-b355-9be01dd5cba9/Picture1.png)

Big Endian 방식 (% Old PC): 앞 8 Bits 부터 낮은 주소값 → 높은 주소값 = 왼쪽 → 오른쪽
![](https://t9003081320.p.clickup-attachments.com/t9003081320/7b9b583d-e31b-42dd-89c4-997c65a87543/Picture2.png)

❸ **2진수값 8 Bits 내 초기화**
Big Endian 방식: 낮은 주소값 → 높은 주소값 = 왼쪽 → 오른쪽
E.g.)
2진수 = 11100111
![](https://t9003081320.p.clickup-attachments.com/t9003081320/b3a5b3e6-eb77-4c0d-80b5-dbeaeb568e37/Picture1.png)

#### ∵ Little Endian 방식 = Network에서 Data 전송시 송수신 입장에서 효율적
E.g.)
10진수 2023 = 2진수 00000000 00000000 00000111 11100111
*   Little Endian 송신 11100111 00000111 00000000 00000000
*   Big Endian 수신 00000000 00000000 00000111 11100111
![](https://t9003081320.p.clickup-attachments.com/t9003081320/4c84ad30-f24f-4760-a209-caeb5254a028/Picture3.png)
❶ 첫번째 송신(전달) ➝ 수신(받기)
❷ 두번째 송신(전달) ➝ 수신(받기)
❸ 세번째 송신(전달) ➝ 수신(받기)
❹ 네번째 송신(전달) ➝ 수신(받기)
i.e.)
❶ Data 값을 Little Endian 방식의 초기화 값에서 송신하면(전달하면)
❷ Big Endian 방식으로 수신하여(받아) 초기 초기화 하게되어
❸ 나열된 순서 그대로의 2진수 초기화값을 10진수 환산함에 용이
00000000 00000000 00000111 11100111 \= 2023

#### ∴ Data 송신 & 수신 입장에서 모두 용이

* * *
* * *

### **Basic**

Int vs Float vs Char ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2618](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2618))
Array ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2638](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2638))
Bool ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2658](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2658))

### **Advanced**

Two's Complement ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-4258](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-4258))
Int Negative Number ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-4278](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-4278))
Float Prime Number ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-4298](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-4298))
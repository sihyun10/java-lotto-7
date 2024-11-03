## 로또 발매기💸 기능 구현 목록

기능 목록 중에 가장 중요도가 높은 기능은 아래와 같다.

(중요도 ⭐⭐⭐⭐⭐) 로또 발매 기능   
(중요도 ⭐⭐⭐⭐) 당첨 내역 및 수익률 출력 기능

위 기능들은 테스트 코드를 작성해 확인하기!

------------------------------

### 사용자에게 입력받기 기능

- [ ] 로또 구입 금액 입력
    - [ ] `1,000원` 단위로 입력 받는다.
- [ ] 당첨 번호 입력
    - [ ] 중복되지 않는 6개의 당첨 번호
    - [ ] 쉼표(,)를 기준으로 구분한다.
- [ ] 보너스 번호 입력
    - [ ] 하나의 번호값만 입력받으며, 당첨 번호와는 중복되면 안된다.

### 로또 번호 (Lotto.class)

- [x] 6개의 숫자로만 이루어져 있어야 한다.
- [x] 중복이 없는 6개의 숫자로만 구성되어야 한다.
- [x] 숫자 범위는 1~45 까지이다.

### 로또 티켓 관리

- [x] 로또 티켓 한장 데이터를 저장하고 관리
- [x] 여러장의 로또 티켓들 관리

### 로또 발매 기능

- [ ] 구입 금액에 해당하는 만큼 로또 발행
    - [ ] 로또 발행 수 = 구입 금액 / 로또 1장 가격(`1,000원`)
- [x] 로또 1개 : 1 ~ 45 사이의 중복되지 않은 정수 6개 반환

```java
//camp.nextstep.edu.missionutils.Randoms의 pickUniqueNumbersInRange() 활용
Randoms.pickUniqueNumbersInRange(1,45,6);
```

### 발행한 로또 수량 및 번호 출력 기능

- [ ] 발행한 로또 수량 및 번호를 출력
    - [x] 로또 번호는 `오름차순`으로 정렬하여 보여주기

### 사용자 로또 당첨 상금 결정해주는 기능

- [x] 당첨번호, 보너스번호 관리
- [x] 사용자의 로또 번호와 비교하여 당첨 상금 결정

### 당첨 통계 출력 및 수익률 기능

사용자가 구매한 로또 번호와 당첨 번호를 비교하여 당첨 내역 및 수익률을 출력하고 로또 게임을 종료

- [x] 당첨 통계 출력  
  1등 ~ 5등까지 당첨 기준이 있다.  
  기준과 일치한다면 그에 맞게 개수 올려주기
- [x] 총 수익률 구하기
    - **총 수익률 = (당첨금액/구입금액) * 100**
    - [x] 소수점 둘째 자리에서 반올림 (ex. 100.0%, 51.5%, 1,000,000.0%)

```
당첨 통계
---
3개 일치 (5,000원) - 1개
4개 일치 (50,000원) - 0개
5개 일치 (1,500,000원) - 0개
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
6개 일치 (2,000,000,000원) - 0개
총 수익률은 62.5%입니다.
```

<br>

### 예외 처리 기능

- 사용자가 잘못된 값을 입력할 경우 `IllegalArgumentException`을 발생시키고, `[ERROR]`로 시작하는 에러 메시지를 출력 후 그 부분부터 입력을 다시 받는다.
    - `Exception`이 아닌 `IllegalArgumentException`, `IllegalStateException`등과 같은 명확한 유형을 처리한다.)

예외 상황 시 에러 문구를 출력해야 한다.  
단, 에러 문구는 "[ERROR]"로 시작해야 한다.

#### 예외 상황들

**0) 값을 입력할 경우 발생할 수 있는 공통 예외 상황들**

- [ ] 숫자가 아닌 값이 입력되는 경우
- [ ] Null 값, 빈값이 입력되는 경우
- [ ] 음수값 입력되는 경우
- [ ] 0이 입력되는 경우

**1) 로또 구입 금액 입력**

- [ ] `1,000원` 단위가 아닌 경우, 예외 처리
    - `구입금액 % 로또 1장 가격(1,000원) != 0`인 경우

```
[ERROR] 로또 구입 금액은 1,000원 단위로 입력해주어야 합니다.
```

**2) 당첨 번호 입력**

- [ ] 중복된 값이 있을 경우, 예외 처리

```
[ERROR] 당첨 번호는 중복된 값이 있을 수 없습니다.
```

- [ ] `,`(쉼표)를 기준으로 구분이 안될 경우, 예외 처리

```
[ERROR] 당첨 번호는 ,(쉼표)를 기준으로 작성해주어야 합니다.
```

- [ ] 1 ~ 45 사이의 숫자가 아니면 예외 처리

```
[ERROR] 당첨 번호는 1부터 45 사이의 숫자여야 합니다.
```

**3) 보너스 번호 입력**

- [ ] 당첨번호와 중복된 번호가 있을 경우, 예외 처리

```
[ERROR] 보너스 번호는 당첨번호와 중복된 숫자가 입력되면 안됩니다.
```

- [ ] 2개 이상의 보너스 번호을 입력하면 예외 처리

```
[ERROR] 보너스 번호는 하나의 숫자만 입력해주어야합니다.
```

- [ ] 1 ~ 45 사이의 숫자가 아니면 예외 처리

```
[ERROR] 보너스 번호는 1부터 45 사이의 숫자여야 합니다.
```

## 문자열(String ) 타입

> 자바에서 문자열은 String `객체`로 생성되어 String 변수에 객체의 번지가 대입된다.

### 문자열 비교

> String 객체를 문자열 리터럴로 생성하는지 new 연산자로 생성하는 지에 따라 비교 연산자의 결과가 달라질 수 있다.

#### 리터럴 직접 대입으로 String 객체 생성
 
> 자바는 문자열 리터럴이 동일하다면 String 객체를 공유한다.

```java
String name1 = "홍길동";
String name2 = "홍길동";
```

위 예제의 name1과 name2는 동일한 String 객체의 번지가 저장된다.

#### new 연산자로 String 객체 생성

> new 연산자로 직접 String 객체를 생성하고 대입하는 경우 각각 다른 번지를 가지게 된다.

```java
String name1 = new String("홍길동");
String name2 = new String("홍길동");
```

위 예제의 name1과 name2는 서로 다른 String  객체의 번지를 가지게 된다.

```java
String name1 = "홍길동";
String name2 = "홍길동";
String name3 = new String("홍길동");

name1 == name2    // true
name1 == name3    // false
```

위 예제처럼 name1과 name2는 동일한 객체를 참조하여 비교 연산자의 결과가 같지만, name3은 new 연산자로 String 객체를 별도로 생성했기 때문에 name1과 name3의 결과는 false이다.

#### String 내부 문자열만 비교시 equals()

> 동일한 String 객체인지 다른 객체인지 상관없이 내부 문자열만 비교할 경우 equals()를 사용한다.

`equals()`메소드는 내부 문자열이 같은지 검사하고 대소문자를 구분해서 비교한다. 앞에 느낌표(`!`)를 붙여 내부 문자열이 다른지 검사하는 것도 가능하다.

```java
boolean result = str1.equals(str2);  // 문자열이 같은지 검사
boolean result = !str1.equals(str2); // 문자열이 다른지 검사
```

String 변수에 빈 문자열(`""`)을 대입할 수 도 있다. 빈 문자열도 String 객체로 생성되기 때문에 변수가 빈 문자열을 참조하는지 조사하려면 equals() 메소드를 사용해야한다.

```java
String hobby = "";
if(hobby.equals("")){
	System.out.println("hobby는 빈 문자열");
}
```


### 문자 추출 - charAt()

> 특정 위치의 문자를 얻고 싶다면 `charAt()`메소드를 사용하면 된다.

| 자  | 바  |     | 프  | 로  | 그  | 래  | 밍  |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|  0  |  1  |  2  |  3  |  4  |  5  |  6  |  7  |

`자바 프로그래밍`이라는 문자열에서 charAt(3)은 3번 인덱스 위치에 있는 문자인 `프`가 해당된다.

### 문자열 길이 - length()

> 문자열에서 문자의 개수를 얻고 싶다면 `length()`메소드를 사용한다.

```java
String subject = "자바 프로그래밍";
int length = subject.length();  // 8
```

### 문자열 대체 - replace()

> 특정 문자열을 다른 문자열로 대체하고 싶다면 `replace()`메소드를 사용한다.

`replace()` 메소드는 기존 문자열은 그대로 두고, 대체한 새로운 문자열을 리턴한다.

```java
String oldStr = "자바 프로그래밍";
String newStr = oldStr.replacd("자바", "JAVA");
```

> String 객체의 문자열은 변경이 불가하다.

때문에 `replace()` 메소드가 리턴하는 문자열은 원래 문자열의 수정본이 아니라 완전히 새로운 문자열이다. 

![[5-1.png]]

### 문자열 잘라내기 - substring()

> 문자열에서 특정 위치의 문자열을 잘라내어 가져올 경우 `substring()`메소드를 사용한다.

| 메소드                                       | 설명                             |
| ----------------------------------------- | ------------------------------ |
| `substring(int beginindex)`               | beginIndex부터 끝까지 잘라내기          |
| `substring(int beginIndex, int endIndex)` | beginIndex부터 endIndex 앞까지 잘라내기 |

| 실제 값 |  1  |  2  |  3  |  4  |  5  |  6  |  -  |  7  |  8  |  9  |  1  |
| ---- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| 인덱스  |  0  |  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  | 10  |

```java
String ssn = "123456-7891";
String fistNum = ssn.substring(0,6);  // 123456
String secondNum = ssn.substring(7);  // 7891
```

### 문자열 찾기 - indexOf()( ps. contains())

> 특정 문자열의 위치를 찾고자 할 때에는 `indexOf()`메소드를 사용한다.

#### `indexOf()` 메소드는 주어진 문자열이 시작되는 인덱스를 리턴한다.

| 자   | 바   |     | 프   | 로   | 그   | 래   | 밍   |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   |

```java
String subject = "자바 프로그래밍";
int index = subject.indexOf("프로그래밍");   // 3
```

#### 주어진 문자열이 포함되어 있지 않다면 -1을 리턴한다.

```java
String subject = "자바 프로그래밍";
int index = subject.indexOf("JAVA");   // -1
```

#### 문자열 포함 여부 확인시 contains()

> 단순히 주어진 문자열이 포함되어 있는지 확일할 경우 contains()메소드를 사용한다.

원하는 문자열이 포함되어 있으면 `contains()`메소드는 true를 리턴하고, 그렇지 않으면 false를 리턴한다.

```java
String subject = "자바 프로그래밍";
boolean result = subject.contains("자바");    // true
boolean result = subject.contains("JAVA");   // false
```

### 문자열 분리 - split()

> 구분자를 사용해 문자열을 분리할 경우 split()메소드를 사용한다.

`split()` 메소드를 호출할 때 구분자를 제공하면 분리된 문자열로 구성 배열(array)를 리턴한다.

```java
String board = "번호, 제목, 내용, 글쓴이";
String[] arr = board.split(", ");
```

| arr[0] | arr[1] | arr[2] | arr[3] |
| :----: | :----: | :----: | :----: |
|   번호   | 제목     | 내용     | 글쓴이    |

<br>

---
## 배열

> 연속된 공간에 값을 나열시키고, 각 값에 인덱스를 부여해 놓은 자료구조

### 배열의 특징
- 배열은 같은 타입의 값만 관리한다.
- 배열의 길이는 늘리거나 줄일 수 없다.

### 배열 변수 선언

배열을 사용하기 위해서는 배열 변수를 선언해야 한다. 

- 선언방법

| 타입[] 변수;              | 타입 변수[];              |
| --------------------- | --------------------- |
| int[] intArray;       | int intArray[];       |
| double[] doubleArray; | double doubleArray[]; |
| String[] strArray;    | String strArray[];    |

배열 변수는 참조 변수이다. 참조할 배열이 없다면 `null`로 초기화할 수 있다.

```java
타입[] 변수 = null;
```

배열 변수가 null 값을 가진 상태에서 변수[인덱스]로 값을 읽거나 저장하게 되면 `NullPointException`에러가 발생한다.

#### 값 목록으로 배열 생성

> 타입[] 변수 = {값0, 값1, 값2, 값3, ... };

```java
String[] season = {"Spring", "Summer", "Fall", "Winter"};
season[1] = "여름";
```

중괄호(`{}`)로 감싼 값 목록을 변수에 대입할 경우 미리 선언한 변수에 값 목록을 대입할 수는 없다.

String[] season;
~~season = {"Spring", "Summer", "Fall", "Winter"};~~     //  Error

배열 변수를 선언한 시점과 값 목록이 대입되는 시점이 다르다면 `new 타입[]`을 중괄호 앞에 붙여주면 된다.

```java
타입[] 변수;
변수 = new 타입[] {값0, 값1, 값2, 값3, ... };

String[] names = null;
names = new String[] {"김자바", "박자바", "국자바"};
```

메소드의 매개변수가 배열 타입일 경우에도 마찬가지이다.

```java
// 메소드 선언
void printItem(int[] scores){ ... }

// 잘못된 메소드 호출
printItem( {98, 85, 90});   // Error

// 올바른 메소드 호출
printItem( new int[] {98, 85, 90});
```


### new 연산자로 배열 생성

> 타입[] 변수 = new 타입[길이];

new 연산자는 해당 길이의 배열을 생성하고 배열의 번지를 리턴하기 때문에 배열 변수에 대입할 수 있다.

```java
타입[] 변수 = null
변수 = new 타입[길이];

int[] intArray = new int[5];
```

`intArray` 변수는 길이가 5인 int[] 배열을 생성하고 배열 번지를 intArray 변수에 대입한다.

| intArray[0] | intArray[1] | intArray[2] | intArray[3] | intArray[4] |
| :---------: | :---------: | :---------: | :---------: | :---------: |
|      0      |      0      |      0      |      0      |      0      |
값 목록 설정 없이 new 연산자로 배열을 처음 생성하면 배열 항목은 기본값으로 초기화된다.(값이 비어있지 않음.) 타입별로 배열의 초기값은 다르다

| 데이터 타입 | 정수  | 실수  | 논리    | 참조   |
| :---: | :---: | :---: | :---: | :---: |
| 초기값    | 0   | 0.0 | false | null |

String[] names = new String[5];
- names의 초기값

| names[0] | names[1] | names[2] | names[3] | names[4] |
| :---------: | :---------: | :---------: | :---------: | :---------: |
|      null      |      null      |      null      |      null      |      null      |

### 배열 생성 후 특정 인덱스 항목의 값을 변경하는 방법

> 변수[인덱스] = 값;

```java
double[] arr1 = new double[3];

for(int i=0;i<3;i++){
	System.out.print("arr1[" + i + "] : " + arr2[i] + ", ");
}
System.out.println();
arr1[0] = 0.1;
arr1[2] = 0.2;
arr1[3] = 0.3;
for(int i=0;i<3;i++){
	System.out.print("arr1[" + i + "] : " + arr2[i] + ", ");
}
// arr1[0] : 0, arr1[1] : 0, arr1[2] : 0,
// arr1[0] : 0.1, arr1[1] : 0.2, arr1[2] : 0.3,
```

### 배열 길이 - length

> 배열 길이랑 배열을 저장할 수 있는 항목의 수를 말하며 length로 확인할 수 있다.

배열의 특징 중 하나인 배열의 길이는 늘리거나 줄일 수 없으므로 `length`필드는 읽기만 가능하고 값은 변경할 수 없다.

~~intArray.length = 10~~     // Error

`length`는 for문에서 많이 사용된다.

```java
int[] scores = {84, 90, 96};
int sum = 0;

for(int i=0; i<scores.length ; i++){
	sum += scores[i];
}

System.out.println
("ArrayIndexOutOfBoundsException 에러발생 : " + scores[scores.length] );   // Error
```

위 예제의 마지막 줄처럼 배열의 인덱스를 초과해서 사용하면 `ArrayIndexOutOfBoundsException`가 발생한다.

<br>

---
## 다차원 배열

> 배열 항목에 또 다른 배열이 대입된 형태이다.

#그림

위 그림처럼 값1, 값3, 값4을 읽는 방법은 다음과 같다.

```java
변수[0][0][0]   // 값1
변수[0][1][0]   // 값3
변수[1][0][1]   // 값6
```

### 값 목록으로 다차원 배열 생성

> 다차원 배열 변수 선언 시 타입 뒤에 대괄호 []를 차원의 수만큼 붙이고 값 목록도 차원의 수만큼 중괄호를 중첩시킨다.

```java
타입[][] 변수 = {
	{값1, 값2, ...},   // 1차원 배열의 0 인덱스
	{값3, 값4, ...},   // 1차원 배열의 1 인덱스
}

```
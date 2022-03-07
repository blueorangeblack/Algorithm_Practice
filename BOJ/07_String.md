## #01 [11654 아스키 코드](https://www.acmicpc.net/problem/11654)

### 문제
알파벳 소문자, 대문자, 숫자 0-9중 하나가 주어졌을 때, 주어진 글자의 아스키 코드값을 출력하는 프로그램을 작성하시오.

### 입력
알파벳 소문자, 대문자, 숫자 0-9 중 하나가 첫째 줄에 주어진다.

### 출력
입력으로 주어진 글자의 아스키 코드 값을 출력한다.

### 제출
~~~ swift
print(Character(readLine()!).asciiValue!)
~~~

<br>

## #02 [11720 숫자의 합](https://www.acmicpc.net/problem/11720)

### 문제
N개의 숫자가 공백 없이 쓰여있다. 이 숫자를 모두 합해서 출력하는 프로그램을 작성하시오.

### 입력
첫째 줄에 숫자의 개수 N (1 ≤ N ≤ 100)이 주어진다. 둘째 줄에 숫자 N개가 공백없이 주어진다.

### 출력
입력으로 주어진 숫자 N개의 합을 출력한다.

### 제출
~~~ swift
_ = Int(readLine()!)!
print(readLine()!.map { Int(String($0))! }.reduce(0, +))
~~~

### 메모
Character 타입 (String.Element)은 바로 Int 타입으로 변환할 수 없고 String으로 먼저 변환 후 Int로 변환해야 함
~~~ swift
//let a = "12345".map { Int($0)! }

// => Cannot convert value of type 'String.Element' (aka 'Character') to expected argument type 'String'

let aa = "12345".map { Int(String($0))! }
~~~
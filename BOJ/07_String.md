## #01 [11654 아스키 코드](https://www.acmicpc.net/problem/11654)
* 문제

    알파벳 소문자, 대문자, 숫자 0-9중 하나가 주어졌을 때, 주어진 글자의 아스키 코드값을 출력하는 프로그램을 작성하시오.

* 입력

    알파벳 소문자, 대문자, 숫자 0-9 중 하나가 첫째 줄에 주어진다.

* 출력

    입력으로 주어진 글자의 아스키 코드 값을 출력한다.

* 제출
    ~~~ swift
    print(Character(readLine()!).asciiValue!)
    ~~~

<br>

## #02 [11720 숫자의 합](https://www.acmicpc.net/problem/11720)
* 문제

    N개의 숫자가 공백 없이 쓰여있다. 이 숫자를 모두 합해서 출력하는 프로그램을 작성하시오.

* 입력

    첫째 줄에 숫자의 개수 N (1 ≤ N ≤ 100)이 주어진다. 둘째 줄에 숫자 N개가 공백없이 주어진다.

* 출력

    입력으로 주어진 숫자 N개의 합을 출력한다.

* 제출
    ~~~ swift
    _ = Int(readLine()!)!
    print(readLine()!.map { Int(String($0))! }.reduce(0, +))
    ~~~

* 메모

    Character 타입 (String.Element)은 바로 Int 타입으로 변환할 수 없고 String으로 먼저 변환 후 Int로 변환해야 함
    ~~~ swift
    //let a = "12345".map { Int($0)! }

    // => Cannot convert value of type 'String.Element' (aka 'Character') to expected argument type 'String'

    let aa = "12345".map { Int(String($0))! }
    ~~~

<br>

## #03 [10809 알파벳 찾기](https://www.acmicpc.net/problem/10809)
* 문제

    알파벳 소문자로만 이루어진 단어 S가 주어진다. 각각의 알파벳에 대해서, 단어에 포함되어 있는 경우에는 처음 등장하는 위치를, 포함되어 있지 않은 경우에는 -1을 출력하는 프로그램을 작성하시오.

* 입력

    첫째 줄에 단어 S가 주어진다. 단어의 길이는 100을 넘지 않으며, 알파벳 소문자로만 이루어져 있다.

* 출력

    각각의 알파벳에 대해서, a가 처음 등장하는 위치, b가 처음 등장하는 위치, ... z가 처음 등장하는 위치를 공백으로 구분해서 출력한다.

    만약, 어떤 알파벳이 단어에 포함되어 있지 않다면 -1을 출력한다. 단어의 첫 번째 글자는 0번째 위치이고, 두 번째 글자는 1번째 위치이다.

* 제출
    ~~~ swift
    let s = readLine()!.map { String($0) }
    let alphabet = Array(97...122).map { String(UnicodeScalar($0)) }
    var result = [String]()

    for i in 0..<alphabet.count {
        if let index = s.firstIndex(of: alphabet[i]) {
            result.append(String(index))
        } else {
            result.append("-1")
        }
    }

    print(result.joined(separator: " "))
    ~~~

* 다른 사람
    ~~~ swift
    if let s = readLine() {
        let alphabet = "abcdefghijklmnopqrstuvwxyz"
        var result = [Int]()
        alphabet.forEach {
            result.append(s.map { $0 }.firstIndex(of: $0) ?? -1)
        }
        print(result.map { String($0) }.joined(separator: " "))
    }
    ~~~
    if let else 대신 ?? 사용하여 result.append 중복코드 제거하고 한줄로 간단하게 함

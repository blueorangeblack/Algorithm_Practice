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

<br>

## #04 [2675 문자열 반복](https://www.acmicpc.net/problem/2675)
* 문제
    
    문자열 S를 입력받은 후에, 각 문자를 R번 반복해 새 문자열 P를 만든 후 출력하는 프로그램을 작성하시오. 즉, 첫 번째 문자를 R번 반복하고, 두 번째 문자를 R번 반복하는 식으로 P를 만들면 된다. S에는 QR Code "alphanumeric" 문자만 들어있다.

    QR Code "alphanumeric" 문자는 0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ\$%*+-./: 이다.

* 입력

    첫째 줄에 테스트 케이스의 개수 T(1 ≤ T ≤ 1,000)가 주어진다. 각 테스트 케이스는 반복 횟수 R(1 ≤ R ≤ 8), 문자열 S가 공백으로 구분되어 주어진다. S의 길이는 적어도 1이며, 20글자를 넘지 않는다. 

* 출력

    각 테스트 케이스에 대해 P를 출력한다.

* 제출
    ~~~swift
    let t = Int(readLine()!)!

    for _ in 1...t {
        let input = readLine()!.split(separator: " ").map { String($0) }
        let r = Int(input[0])!
        let s = input[1].map { String($0) }
        var result = ""

        s.forEach {
            for _ in 1...r {
                result.append($0)
            }
        }
        print(result)
    }
    ~~~

* 다른 사람
    ~~~swift
    for _ in 0..<Int(readLine()!)! {
        let input = readLine()!.split(separator: " ").map { String($0) }
        let r = Int(input[0])!, str = input[1].map { String($0) }
        for s in str {
            print(String(repeating: s, count: r), terminator: "")
        }
        print()    
    }
    ~~~
    => repeating 사용함. terminator: ""로 해서 줄바꿈 안되고 한줄에 출력할 수 있고, print()를 해줘서 줄바꿈함.
    ~~~swift
    for s in "ABC" {
        print(String(repeating: s, count: 3), terminator: "")
    }
    // => 
    //AAABBBCCC

    for s in "ABC" {
        print(s)
    }
    // =>
    //A
    //B
    //C

    ~~~

<br>

## #05 [1157 단어 공부](https://www.acmicpc.net/problem/1157)
* 문제

    알파벳 대소문자로 된 단어가 주어지면, 이 단어에서 가장 많이 사용된 알파벳이 무엇인지 알아내는 프로그램을 작성하시오. 단, 대문자와 소문자를 구분하지 않는다.

* 입력

    첫째 줄에 알파벳 대소문자로 이루어진 단어가 주어진다. 주어지는 단어의 길이는 1,000,000을 넘지 않는다.

* 출력

    첫째 줄에 이 단어에서 가장 많이 사용된 알파벳을 대문자로 출력한다. 단, 가장 많이 사용된 알파벳이 여러 개 존재하는 경우에는 ?를 출력한다.

* 제출
    ~~~swift
    let s = readLine()!.map { $0.uppercased() }
    var dict = [String: Int]()

    s.forEach {
        if dict[$0] == nil {
            dict[$0] = 1
        } else {
            dict[$0]! += 1
        }
    }

    var alphabet = ""
    var max = 0
    var same = false
    dict.forEach {
        if $0.value == max {
            same = true
        } else if $0.value > max {
            alphabet = $0.key
            max = $0.value
            same = false
        }
    }

    if same {
        print("?")
    } else {
        print(alphabet)
    }
    ~~~

* 다른 사람
    ~~~swift
    var result = [String]()

    for key in dict.keys {
        if dict[key] == dict.values.max() {
            result.append(key)
        }
    }

    print(result.count > 1 ? "?" : result[0])
    ~~~
    => 두번째 단계에서 `dict.values.max()`로 가장 큰 수를 알아내고 각각을 비교해서 String array로 만들고 count가 1이 아니면 ?를 출력하도록 함. 코드도 더 간단하고 속도도 조금 더 빠름.

<br>

## #06 [1152 단어의 개수](https://www.acmicpc.net/problem/1152)
* 문제

    영어 대소문자와 공백으로 이루어진 문자열이 주어진다. 이 문자열에는 몇 개의 단어가 있을까? 이를 구하는 프로그램을 작성하시오. 단, 한 단어가 여러 번 등장하면 등장한 횟수만큼 모두 세어야 한다.

* 입력

    첫 줄에 영어 대소문자와 공백으로 이루어진 문자열이 주어진다. 이 문자열의 길이는 1,000,000을 넘지 않는다. 단어는 공백 한 개로 구분되며, 공백이 연속해서 나오는 경우는 없다. 또한 문자열은 공백으로 시작하거나 끝날 수 있다.

* 출력

    첫째 줄에 단어의 개수를 출력한다.

* 제출
    ~~~swift
    let s = readLine()!
    var count = 1
    s.forEach {
        if $0 == " " {
            count += 1
        }
    }
    if s.first == " " {
        count -= 1
    }
    if s.last == " " {
        count -= 1
    }
    print(count)
    ~~~

* 다른 사람
    ~~~swift
    print(readLine()!.split(separator: " ").count)
    ~~~
    => 코드는 훨씬 간단하지만 메모리와 시간이 더 소요됨

<br>

## #07 [2908 상수](https://www.acmicpc.net/problem/2908)
* 문제

    상근이의 동생 상수는 수학을 정말 못한다. 상수는 숫자를 읽는데 문제가 있다. 이렇게 수학을 못하는 상수를 위해서 상근이는 수의 크기를 비교하는 문제를 내주었다. 상근이는 세 자리 수 두 개를 칠판에 써주었다. 그 다음에 크기가 큰 수를 말해보라고 했다.

    상수는 수를 다른 사람과 다르게 거꾸로 읽는다. 예를 들어, 734와 893을 칠판에 적었다면, 상수는 이 수를 437과 398로 읽는다. 따라서, 상수는 두 수중 큰 수인 437을 큰 수라고 말할 것이다.

    두 수가 주어졌을 때, 상수의 대답을 출력하는 프로그램을 작성하시오.

* 입력

    첫째 줄에 상근이가 칠판에 적은 두 수 A와 B가 주어진다. 두 수는 같지 않은 세 자리 수이며, 0이 포함되어 있지 않다.

* 출력

    첫째 줄에 상수의 대답을 출력한다.

* 제출
    ~~~swift
    let input = readLine()!
    var nums = ""
    for c in input.reversed() {
        nums.append(c)
    }
    print(nums.split(separator: " ").compactMap { Int($0) }.max()!)
    ~~~

* 다른 풀이
    ~~~swift
    print(readLine()!.split{$0==" "}.map{Int(String($0.reversed()))!}.max()!)
    ~~~
    => $0.reversed()로 접근하면 위에 for문에서 input.reversed()한 것과 마찬가지로 역순으로 들어옴. 메모리와 시간은 같음.

<br>

## #08 [5622 다이얼](https://www.acmicpc.net/problem/5622)
* 문제

    상근이의 할머니는 아래 그림과 같이 오래된 다이얼 전화기를 사용한다.

    전화를 걸고 싶은 번호가 있다면, 숫자를 하나를 누른 다음에 금속 핀이 있는 곳 까지 시계방향으로 돌려야 한다. 숫자를 하나 누르면 다이얼이 처음 위치로 돌아가고, 다음 숫자를 누르려면 다이얼을 처음 위치에서 다시 돌려야 한다.

    숫자 1을 걸려면 총 2초가 필요하다. 1보다 큰 수를 거는데 걸리는 시간은 이보다 더 걸리며, 한 칸 옆에 있는 숫자를 걸기 위해선 1초씩 더 걸린다.

    상근이의 할머니는 전화 번호를 각 숫자에 해당하는 문자로 외운다. 즉, 어떤 단어를 걸 때, 각 알파벳에 해당하는 숫자를 걸면 된다. 예를 들어, UNUCIC는 868242와 같다.

    할머니가 외운 단어가 주어졌을 때, 이 전화를 걸기 위해서 필요한 최소 시간을 구하는 프로그램을 작성하시오.

* 입력

    첫째 줄에 알파벳 대문자로 이루어진 단어가 주어진다. 단어의 길이는 2보다 크거나 같고, 15보다 작거나 같다.

* 출력

    첫째 줄에 다이얼을 걸기 위해서 필요한 최소 시간을 출력한다.

* 제출
    ~~~swift
    let input = readLine()!
    let alphabet: [Int: Set<String>] = [ 2: ["A", "B", "C"],
                                        3: ["D", "E", "F"],
                                        4: ["G", "H", "I"],
                                        5: ["J", "K", "L"],
                                        6: ["M" ,"N", "O"],
                                        7: ["P", "Q", "R", "S"],
                                        8: ["T", "U", "V"],
                                        9: ["W", "X", "Y", "Z"] ]

    var result = Int()

    for c in input {
        for a in alphabet {
            if a.value.contains(String(c)) {
                result += a.key + 1
            }
        }
    }

    print(result)
    ~~~

* 다른 풀이
    ~~~swift
    func getCallTime(word: String) -> Int {
        var callTime: Int = 0
        for character in word {
            switch character {
            case "A", "B", "C":
                callTime += 3
            case "D", "E", "F":
                callTime += 4
            case "G", "H", "I":
                callTime += 5
            case "J", "K", "L":
                callTime += 6
            case "M", "N", "O":
                callTime += 7
            case "P", "Q", "R", "S":
                callTime += 8
            case "T", "U", "V":
                callTime += 9
            case "W", "X", "Y", "Z":
                callTime += 10
            default:
                break
            }
        }
        return callTime
    }

    let word = readLine()!
    print(getCallTime(word: word))
    ~~~
    => switch 사용
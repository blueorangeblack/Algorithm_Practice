## #09 [2438 별 찍기 - 1](https://www.acmicpc.net/problem/2438)
* 문제

    첫째 줄에는 별 1개, 둘째 줄에는 별 2개, N번째 줄에는 별 N개를 찍는 문제

* 입력

    첫째 줄에 N(1 ≤ N ≤ 100)이 주어진다.

* 출력

    첫째 줄부터 N번째 줄까지 차례대로 별을 출력한다.

* 제출
    ~~~ swift
    let n = Int(readLine()!)!
    for i in 1...n {
        print(String(repeating: "*", count: i))
    }
    ~~~

<br>

## #10 [2439 별 찍기 - 2](https://www.acmicpc.net/problem/2439)
* 문제

    첫째 줄에는 별 1개, 둘째 줄에는 별 2개, N번째 줄에는 별 N개를 찍는 문제

    하지만, 오른쪽을 기준으로 정렬한 별(예제 참고)을 출력하시오.

* 입력

    첫째 줄에 N(1 ≤ N ≤ 100)이 주어진다.

* 출력

    첫째 줄부터 N번째 줄까지 차례대로 별을 출력한다.

* 제출
    ~~~ swift
    let n = Int(readLine()!)!
    var star = ""
    for i in 1...n {
        star = String(repeating: " ", count: n-i)
        star += String(repeating: "*", count: i)
        print(star)
    }
    ~~~
* 다른 사람 1
    ~~~ swift
    let n = Int(readLine()!)!

    for i in 1...n {
        print("\(String(repeating: " ", count: n-i))\(String(repeating: "*", count: i))")
    }
    ~~~
    => 이렇게 위에 문제 별 찍기 1처럼 바로 print해도 됨. 메모리와 시간은 같지만 더 간단하다.
* 다른 사람 2
    ~~~ swift
    let input = Int(readLine()!)!

    for i in 1...input {
        let space = [Character].init(repeating: " ", count: input-i)
        let star = [Character].init(repeating: "*", count: i)
        print(String(space+star))
    }
    ~~~
    => 바로 String으로 만들지 않고 [Character]로 만든 후 String으로 변환함. 메모리는 같지만 시간이 빠르다.

<br>

## #11 [10871 X보다 작은 수](https://www.acmicpc.net/problem/10871)
* 문제

    정수 N개로 이루어진 수열 A와 정수 X가 주어진다. 이때, A에서 X보다 작은 수를 모두 출력하는 프로그램을 작성하시오.

* 입력

    첫째 줄에 N과 X가 주어진다. (1 ≤ N, X ≤ 10,000)

    둘째 줄에 수열 A를 이루는 정수 N개가 주어진다. 주어지는 정수는 모두 1보다 크거나 같고, 10,000보다 작거나 같은 정수이다.

* 출력

    X보다 작은 수를 입력받은 순서대로 공백으로 구분해 출력한다. X보다 작은 수는 적어도 하나 존재한다.

* 제출
    ~~~swift
    let input = readLine()!.split(separator: " ").map { Int(String($0))! }
    let a = readLine()!.split(separator: " ").map { Int(String($0))! }
    var result = [String]()
    a.forEach {
        if $0 < input[1] {
            result.append(String($0))
        }
    }
    print(result.joined(separator: " "))
    ~~~

* 다른 사람
    ~~~swift
    print(a.filter { $0 < input[1] }
        .map { "\($0)" }
        .joined(separator: " ")
    )
    ~~~
    => for, forEach를 사용하지 않고 filter 사용. 시간은 같고 메모리 조금 더 필요.
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
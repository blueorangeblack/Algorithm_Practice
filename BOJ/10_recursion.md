## #01 [10872 팩토리얼](https://www.acmicpc.net/problem/10872)
* 문제

    0보다 크거나 같은 정수 N이 주어진다. 이때, N!을 출력하는 프로그램을 작성하시오.
* 입력

    첫째 줄에 정수 N(0 ≤ N ≤ 12)이 주어진다.
* 출력

    첫째 줄에 N!을 출력한다.
* 풀이
    ~~~swift
    // 방법 1) reduce
    // 메모리 69100KB, 시간 12ms
    let n = Int(readLine()!)!
    if n == 0 {
        print("1")
    } else {
        print((1...n).reduce(1, *))
    }

    // 방법 2) 재귀함수
    // 메모리 69100KB, 시간 8ms
    func factorial(n: Int) -> Int {
        if n == 0 { return 1 }
        return n * factorial(n: n - 1)
    }
    print(factorial(n: Int(readLine()!)!))

    // 방법 3) for
    // 메모리 69100KB, 시간 8ms
    let n = Int(readLine()!)!
    var total = 1
    if n != 0 {
        for i in 1...n {
            total *= i
        }
    }
    print(total)
    ~~~
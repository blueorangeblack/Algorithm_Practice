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

## #02 [10870 피보나치 수 5](https://www.acmicpc.net/problem/10870)
* 문제

    피보나치 수는 0과 1로 시작한다. 0번째 피보나치 수는 0이고, 1번째 피보나치 수는 1이다. 그 다음 2번째 부터는 바로 앞 두 피보나치 수의 합이 된다.

    이를 식으로 써보면 Fn = Fn-1 + Fn-2 (n ≥ 2)가 된다.

    n=17일때 까지 피보나치 수를 써보면 다음과 같다.

    0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987, 1597

    n이 주어졌을 때, n번째 피보나치 수를 구하는 프로그램을 작성하시오.

* 입력

    첫째 줄에 n이 주어진다. n은 20보다 작거나 같은 자연수 또는 0이다.

* 출력

    첫째 줄에 n번째 피보나치 수를 출력한다.

* 제출
    ~~~swift
    let n = Int(readLine()!)!
    var index = 0
    var fibArr = [Int]()
    func fibonacci() -> Int {
        if index < 2 {
            fibArr.append(index)
        } else {
            fibArr.append(fibArr[index - 1] + fibArr[index - 2])
        }

        if n == index {
            return fibArr.last ?? 0
        } else {
            index += 1
            return fibonacci()
        }
    }
    print(fibonacci())
    ~~~

* 다른 사람
    ~~~swift
    let line = Int(readLine()!)!
        
    func f(x: Int) -> Int {
        if x == 0 || x == 1 {
            return x
        } else {
            return f(x:x - 1) + f(x:x - 2)
        }
        
    }
    print(f(x: line))
    ~~~
    => 간단하지만 시간 더 소요됨
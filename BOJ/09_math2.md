## #01 [1978 소수 찾기](https://www.acmicpc.net/problem/1978)
* 문제

    주어진 수 N개 중에서 소수가 몇 개인지 찾아서 출력하는 프로그램을 작성하시오.

* 입력

    첫 줄에 수의 개수 N이 주어진다. N은 100이하이다. 다음으로 N개의 수가 주어지는데 수는 1,000 이하의 자연수이다.

* 출력

    주어진 수들 중 소수의 개수를 출력한다.

* 제출
    ~~~swift
    _ = readLine()!
    let input = readLine()!.split(separator: " ").map { Int($0)! }
    var result = 0
    for i in input {
        var count = 0
        for j in 1...i {
            if i % j == 0 {
                count += 1
            }
            if count > 2 {
                break
            }
        }
        if count == 2 {
            result += 1
        }
    }
    print(result)
    ~~~

## #02 [2581 소수 찾기](https://www.acmicpc.net/problem/2581)
* 문제

    자연수 M과 N이 주어질 때 M이상 N이하의 자연수 중 소수인 것을 모두 골라 이들 소수의 합과 최솟값을 찾는 프로그램을 작성하시오.

    예를 들어 M=60, N=100인 경우 60이상 100이하의 자연수 중 소수는 61, 67, 71, 73, 79, 83, 89, 97 총 8개가 있으므로, 이들 소수의 합은 620이고, 최솟값은 61이 된다.

* 입력

    입력의 첫째 줄에 M이, 둘째 줄에 N이 주어진다.

    M과 N은 10,000이하의 자연수이며, M은 N보다 작거나 같다.

* 출력

    M이상 N이하의 자연수 중 소수인 것을 모두 찾아 첫째 줄에 그 합을, 둘째 줄에 그 중 최솟값을 출력한다. 

    단, M이상 N이하의 자연수 중 소수가 없을 경우는 첫째 줄에 -1을 출력한다.

* 제출
    ~~~swift
    let m = Int(readLine()!)!
    let n = Int(readLine()!)!

    var primeNumber = [Int]()
    for i in m...n {
        var count = 0
        for j in 1...i {
            if i % j == 0 {
                count += 1
            }
            if count > 2 {
                break
            }
        }
        if count == 2 {
            primeNumber.append(i)
        }
    }

    if primeNumber.isEmpty {
        print("-1")
    } else {
        print(primeNumber.reduce(0, +))
        print(primeNumber[0])
    }
    ~~~

* 다른 사람
    ~~~swift
    import Foundation

    func isPrime(num : Int) -> Bool {
        var result = true
        if num == 1 {
            return false
        }
        
        if num == 2 || num == 3 {
            return true
        }
        
        for i in 2...Int(sqrt(Double(num))) {
            if num % i == 0 {
                result = false
                break
            }
        }
        
        return result
    }

    let a = Int(readLine()!)!
    let b = Int(readLine()!)!
    var minValues = -1
    var sum = 0

    for i in a...b {
        if isPrime(num: i) {
            sum += i
            if minValues == -1 {
                minValues = i
            }
        }
    }

    if minValues != -1 {
        print(sum)
        print(minValues)
    } else {
        print(-1)
    }
    ~~~
    => sqrt()사용해서 소수인지 확인하는 isPrime 함수를 만들고, for사용해서 sum을 구함.
    메모리는 더 크지만 빠름.

## #03 [11653 소인수분해](https://www.acmicpc.net/problem/11653)
* 문제

    정수 N이 주어졌을 때, 소인수분해하는 프로그램을 작성하시오.

* 입력

    첫째 줄에 정수 N (1 ≤ N ≤ 10,000,000)이 주어진다.

* 출력

    N의 소인수분해 결과를 한 줄에 하나씩 오름차순으로 출력한다. N이 1인 경우 아무것도 출력하지 않는다.

* 제출
    ~~~swift
    var n = Int(readLine()!)!
    var d = 2

    while d <= n {
        if n % d != 0 {
            d += 1
        } else {
            print(d)
            n /= d
        }
    }
    ~~~
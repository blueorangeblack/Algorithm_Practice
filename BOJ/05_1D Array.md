## #06 [8958 OX퀴즈](https://www.acmicpc.net/problem/8958)
* 문제

    "OOXXOXXOOO"와 같은 OX퀴즈의 결과가 있다. O는 문제를 맞은 것이고, X는 문제를 틀린 것이다. 문제를 맞은 경우 그 문제의 점수는 그 문제까지 연속된 O의 개수가 된다. 예를 들어, 10번 문제의 점수는 3이 된다.

    "OOXXOXXOOO"의 점수는 1+2+0+0+1+0+0+1+2+3 = 10점이다.

    OX퀴즈의 결과가 주어졌을 때, 점수를 구하는 프로그램을 작성하시오.

* 입력

    첫째 줄에 테스트 케이스의 개수가 주어진다. 각 테스트 케이스는 한 줄로 이루어져 있고, 길이가 0보다 크고 80보다 작은 문자열이 주어진다. 문자열은 O와 X만으로 이루어져 있다.

* 출력

    각 테스트 케이스마다 점수를 출력한다.

* 제출
    ~~~ swift
    let n = Int(readLine()!)!
    for _ in 0..<n {
        let result = readLine()!.map { String($0) }
        var p = 0
        var total = 0
        for i in 0..<result.count {
            if result[i] == "O" {
                p += 1
                total += p
            } else {
                p = 0
            }
        }
        print(total)
    }
    ~~~

<br>

## #07 [4344 단어 공부](https://www.acmicpc.net/problem/4344)
* 문제

    대학생 새내기들의 90%는 자신이 반에서 평균은 넘는다고 생각한다. 당신은 그들에게 슬픈 진실을 알려줘야 한다.

* 입력

    첫째 줄에는 테스트 케이스의 개수 C가 주어진다.

    둘째 줄부터 각 테스트 케이스마다 학생의 수 N(1 ≤ N ≤ 1000, N은 정수)이 첫 수로 주어지고, 이어서 N명의 점수가 주어진다. 점수는 0보다 크거나 같고, 100보다 작거나 같은 정수이다.

* 출력

    각 케이스마다 한 줄씩 평균을 넘는 학생들의 비율을 반올림하여 소수점 셋째 자리까지 출력한다.

* 제출
    ~~~swift
    import Foundation // String(format: ,)을 사용하기 위해 import

    let c = Int(readLine()!)!

    for _ in 0..<c {
        var input = readLine()!.split(separator: " ").compactMap { Double($0) }
        let n = input.removeFirst()
        let avg = (input.reduce(0, +)) / n

        var count = 0.0
        input.forEach {
            if $0 > avg {
                count += 1
            }
        }
        
        let result = String(format: "%.3f", count / n * 100)
        print("\(result)%")
    }
    ~~~
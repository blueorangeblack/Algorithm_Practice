## #02 [2292 벌집](https://www.acmicpc.net/problem/2292)
* 문제

    위의 그림과 같이 육각형으로 이루어진 벌집이 있다. 그림에서 보는 바와 같이 중앙의 방 1부터 시작해서 이웃하는 방에 돌아가면서 1씩 증가하는 번호를 주소로 매길 수 있다. 숫자 N이 주어졌을 때, 벌집의 중앙 1에서 N번 방까지 최소 개수의 방을 지나서 갈 때 몇 개의 방을 지나가는지(시작과 끝을 포함하여)를 계산하는 프로그램을 작성하시오. 예를 들면, 13까지는 3개, 58까지는 5개를 지난다.

* 입력

    첫째 줄에 N(1 ≤ N ≤ 1,000,000,000)이 주어진다.

* 출력

    입력으로 주어진 방까지 최소 개수의 방을 지나서 갈 때 몇 개의 방을 지나는지 출력한다.

* 제출
    ~~~ swift
    let n = Int(readLine()!)!
    var count = 1
    var max = 1
    while n > max {
        max += count * 6
        count += 1
    }
    print(count)
    ~~~

<br>

## #03 [1193 분수찾기](https://www.acmicpc.net/problem/1193)
* 문제

    무한히 큰 배열에 다음과 같이 분수들이 적혀있다.

    1/1	1/2	1/3	1/4	1/5	…

    2/1	2/2	2/3	2/4	…	…

    3/1	3/2	3/3	…	…	…

    4/1	4/2	…	…	…	…

    5/1	…	…	…	…	…

    …	…	…	…	…	…

    이와 같이 나열된 분수들을 1/1 → 1/2 → 2/1 → 3/1 → 2/2 → … 과 같은 지그재그 순서로 차례대로 1번, 2번, 3번, 4번, 5번, … 분수라고 하자.

    X가 주어졌을 때, X번째 분수를 구하는 프로그램을 작성하시오.

* 입력

    첫째 줄에 X(1 ≤ X ≤ 10,000,000)가 주어진다.

* 출력

    첫째 줄에 분수를 출력한다.

* 제출
    ~~~swift
    let x = Int(readLine()!)!
    var line = 1 //몇 번째 라인인지?
    var max = 1 //그 라인의 max가 뭔지?
    while x > max {
        line += 1
        max += line
    }

    let move = x - (max - line) //이전 max (max - line)
    if line % 2 == 0 {
        print("\(move)/\(line - move + 1)")
    } else {
        print("\(line - move + 1)/\(move)")
    }
    ~~~

<br>

## #04 [2869 달팽이는 올라가고 싶다](https://www.acmicpc.net/problem/2869)

* 문제

    땅 위에 달팽이가 있다. 이 달팽이는 높이가 V미터인 나무 막대를 올라갈 것이다.

    달팽이는 낮에 A미터 올라갈 수 있다. 하지만, 밤에 잠을 자는 동안 B미터 미끄러진다. 또, 정상에 올라간 후에는 미끄러지지 않는다.

    달팽이가 나무 막대를 모두 올라가려면, 며칠이 걸리는지 구하는 프로그램을 작성하시오.

* 입력

    첫째 줄에 세 정수 A, B, V가 공백으로 구분되어서 주어진다. (1 ≤ B < A ≤ V ≤ 1,000,000,000)

* 출력

    첫째 줄에 달팽이가 나무 막대를 모두 올라가는데 며칠이 걸리는지 출력한다.

* 제출
    ~~~swift
    import Foundation
    let input = readLine()!.split(separator: " ").map { Double($0)! }
    let a = input[0]
    let b = input[1]
    let v = input[2]
    print(Int(ceil((v-b) / (a-b))))
    ~~~

* 메모
    * ceil을 사용하기 위해 `import Foundation`
    * 나눗셈 후 소수점까지 사용하기 위해 input을 `Double`로 받음
    * v / (a-b) => 이렇게 하면 저녁에 최초로 닿은 날인데 낮에 이미 다 올라갔으면 더이상 올라가지 않으니까 낮을 기준으로 계산해야 해서 `(v-b) / (a-b)`가 됨
    * `Int(ceil((v-b) / (a-b)))` => 소수점이 있다는 건 하루가 더 지나야 올라갈 수 있는 거라 올림한 후 Int로 출력
    * while문으로 하면 시간 오래 걸려서 안됨
        ~~~swift
        let input = readLine()!.split(separator: " ").map { Int($0)! }
        let a = input[0]
        let b = input[1]
        let v = input[2]

        var day = 0
        var m = 0

        while m <= v {
            day += 1
            m += a
            if m >= v {
                break
            }
            m -= b
        }
        print(day)
        ~~~
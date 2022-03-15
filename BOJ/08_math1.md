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
    
<br>

## #05 [10250 ACM 호텔](https://www.acmicpc.net/problem/10250)
* 문제

    ACM 호텔 매니저 지우는 손님이 도착하는 대로 빈 방을 배정하고 있다. 고객 설문조사에 따르면 손님들은 호텔 정문으로부터 걸어서 가장 짧은 거리에 있는 방을 선호한다고 한다. 여러분은 지우를 도와 줄 프로그램을 작성하고자 한다. 즉 설문조사 결과 대로 호텔 정문으로부터 걷는 거리가 가장 짧도록 방을 배정하는 프로그램을 작성하고자 한다.

    문제를 단순화하기 위해서 호텔은 직사각형 모양이라고 가정하자. 각 층에 W 개의 방이 있는 H 층 건물이라고 가정하자 (1 ≤ H, W ≤ 99). 그리고 엘리베이터는 가장 왼쪽에 있다고 가정하자(그림 1 참고). 이런 형태의 호텔을 H × W 형태 호텔이라고 부른다. 호텔 정문은 일층 엘리베이터 바로 앞에 있는데, 정문에서 엘리베이터까지의 거리는 무시한다. 또 모든 인접한 두 방 사이의 거리는 같은 거리(거리 1)라고 가정하고 호텔의 정면 쪽에만 방이 있다고 가정한다.

    방 번호는 YXX 나 YYXX 형태인데 여기서 Y 나 YY 는 층 수를 나타내고 XX 는 엘리베이터에서부터 세었을 때의 번호를 나타낸다. 즉, 그림 1 에서 빗금으로 표시한 방은 305 호가 된다.

    손님은 엘리베이터를 타고 이동하는 거리는 신경 쓰지 않는다. 다만 걷는 거리가 같을 때에는 아래층의 방을 더 선호한다. 예를 들면 102 호 방보다는 301 호 방을 더 선호하는데, 102 호는 거리 2 만큼 걸어야 하지만 301 호는 거리 1 만큼만 걸으면 되기 때문이다. 같은 이유로 102 호보다 2101 호를 더 선호한다.

    여러분이 작성할 프로그램은 초기에 모든 방이 비어있다고 가정하에 이 정책에 따라 N 번째로 도착한 손님에게 배정될 방 번호를 계산하는 프로그램이다. 첫 번째 손님은 101 호, 두 번째 손님은 201 호 등과 같이 배정한다. 그림 1 의 경우를 예로 들면, H = 6이므로 10 번째 손님은 402 호에 배정해야 한다.

* 입력

    프로그램은 표준 입력에서 입력 데이터를 받는다. 프로그램의 입력은 T 개의 테스트 데이터로 이루어져 있는데 T 는 입력의 맨 첫 줄에 주어진다. 각 테스트 데이터는 한 행으로서 H, W, N, 세 정수를 포함하고 있으며 각각 호텔의 층 수, 각 층의 방 수, 몇 번째 손님인지를 나타낸다(1 ≤ H, W ≤ 99, 1 ≤ N ≤ H × W). 

* 출력

    프로그램은 표준 출력에 출력한다. 각 테스트 데이터마다 정확히 한 행을 출력하는데, 내용은 N 번째 손님에게 배정되어야 하는 방 번호를 출력한다.

* 제출
    ~~~swift
    let t = Int(readLine()!)!

    for _ in 0..<t {
        let input = readLine()!.split(separator: " ").compactMap { Int($0) }
        let h = input[0]
        _ = input[1]
        let n = input[2]
        
        var y = n % h
        if y == 0 {
            y = h
        }
        var x = n / h
        if h * x != n {
            x += 1
        }
        
        x > 9 ? print("\(y)\(x)") : print("\(y)0\(x)")
    }
    ~~~

* 다른 사람
    ~~~swift
    import Foundation
    for _ in 0..<Int(readLine()!)! {
        let input = readLine()!.split(separator: " ").map { Int($0)! }
        let h = input[0], w = input[1], n = input[2]
        let floor = n % h == 0 ? h : n % h
        let room = n % h == 0 ? n / h : n / h + 1
        print("\(floor)\(String(format: "%02d", room))")
    }
    ~~~
    => if 대신 삼항연산자를 사용하고 String format을 사용하여 코드가 짧아졌지만 메모리가 조금 더 필요하고 시간도 4초 더 걸린다.
        
<br>

## #06 [2775 부녀회장이 될테야](https://www.acmicpc.net/problem/2775)
* 문제
    평소 반상회에 참석하는 것을 좋아하는 주희는 이번 기회에 부녀회장이 되고 싶어 각 층의 사람들을 불러 모아 반상회를 주최하려고 한다.

    이 아파트에 거주를 하려면 조건이 있는데, “a층의 b호에 살려면 자신의 아래(a-1)층의 1호부터 b호까지 사람들의 수의 합만큼 사람들을 데려와 살아야 한다” 는 계약 조항을 꼭 지키고 들어와야 한다.

    아파트에 비어있는 집은 없고 모든 거주민들이 이 계약 조건을 지키고 왔다고 가정했을 때, 주어지는 양의 정수 k와 n에 대해 k층에 n호에는 몇 명이 살고 있는지 출력하라. 단, 아파트에는 0층부터 있고 각층에는 1호부터 있으며, 0층의 i호에는 i명이 산다.

* 입력

    첫 번째 줄에 Test case의 수 T가 주어진다. 그리고 각각의 케이스마다 입력으로 첫 번째 줄에 정수 k, 두 번째 줄에 정수 n이 주어진다

* 출력

    각각의 Test case에 대해서 해당 집에 거주민 수를 출력하라.

* 제한

    1 ≤ k, n ≤ 14

* 제출
    ~~~swift
    let t = Int(readLine()!)!

    for _ in 0..<t {
        let k = Int(readLine()!)!
        let n = Int(readLine()!)!
        
        //필요한 만큼의 2차원 배열을 초기화. 일단은 모두 0으로
        var array = Array(repeating: Array(repeating: 0, count: n+1), count: k+1)

        for i in 0...k {
            for j in 1...n {
                if j == 1 {
                    array[i][1] = 1
                } else if j == 2 {
                    array[i][2] = i + 2
                } else if i == 0 {
                    array[0][j] = j
                } else if j > 2 && i > 0 {
                    array[i][j] = array[i-1][j] + array[i][j-1]
                }
            }
        }
        print(array[k][n])
    }
    ~~~
  
<br>

## #07 [2839 설탕 배달](https://www.acmicpc.net/problem/2839)
* 문제

    상근이는 요즘 설탕공장에서 설탕을 배달하고 있다. 상근이는 지금 사탕가게에 설탕을 정확하게 N킬로그램을 배달해야 한다. 설탕공장에서 만드는 설탕은 봉지에 담겨져 있다. 봉지는 3킬로그램 봉지와 5킬로그램 봉지가 있다.

    상근이는 귀찮기 때문에, 최대한 적은 봉지를 들고 가려고 한다. 예를 들어, 18킬로그램 설탕을 배달해야 할 때, 3킬로그램 봉지 6개를 가져가도 되지만, 5킬로그램 3개와 3킬로그램 1개를 배달하면, 더 적은 개수의 봉지를 배달할 수 있다.

    상근이가 설탕을 정확하게 N킬로그램 배달해야 할 때, 봉지 몇 개를 가져가면 되는지 그 수를 구하는 프로그램을 작성하시오.

* 입력

    첫째 줄에 N이 주어진다. (3 ≤ N ≤ 5000)

* 출력

    상근이가 배달하는 봉지의 최소 개수를 출력한다. 만약, 정확하게 N킬로그램을 만들 수 없다면 -1을 출력한다.

* 제출
    ~~~swift
    let n = Int(readLine()!)!

    var numberOfFive = n / 5
    var numberOfThree = n % 5 / 3

    for _ in 0...numberOfFive {
        if n != numberOfFive * 5 + numberOfThree * 3 {
            if numberOfFive == 0 {
                print("-1")
            }
            numberOfFive -= 1
            numberOfThree = (n - numberOfFive * 5) / 3
        } else {
            print(numberOfFive + numberOfThree)
            break
        }
    }
    ~~~

* 다른 사람
    ~~~swift
    var data_2 = Int(readLine()!)!
    var total = 0

    while true {
        if data_2 % 5 == 0 {
            total += data_2 / 5
            print(total)
            break
        }
        
        data_2 -= 3
        total += 1
        
        if data_2 < 0 {
            total = -1
            print(total)
            break
        }
    }
    ~~~
    => 먼저 5로 나누어 떨어지는지 확인 후 3씩 줄여가면서 total을 계산. 메모리와 시간은 같음.
# TSP-Genetic-Algorithm
유전 알고리즘은 자연에서 얻은 진화과정에 기초한 계산 모델로서 존 홀랜드(John Holland)에 의해서 1975년에 개발된 전역 최적화 기법으로, 최적화 문제를 해결하는 기법의 하나이다. 생물의 진화를 모방한 진화 연산의 대표적인 기법으로, 실제 진화의 과정에서 많은 부분을 차용하였으며, 변이(돌연변이), 교배 연산 등이 존재한다. 또한 세대, 인구 등의 용어도 문제 풀이 과정에서 사용된다. 


TSP(Travelling Salesman Problem, 외판원 문제)는 조합 최적화(Combinatorial Optimization) 문제로 전산학에서 연구된 가장 유명한 문제 중 하나이다. 문제의 요구 사항은 다음과 같다.

“도시의 개수와 각 도시 쌍 간의 거리들이 주어질 때, 모든 도시를 한 번씩 방문하고 여행을 시작한 원래 도시로 돌아올 수 있는 최단 거리 경로(Shortest distance Path)를 구하라.”


유전자 알고리즘은 개체의 진화를 통해 일정 데이터를 최적화할 수 있는 방법이기에, TSP문제에서 경로를 최적화를 위해 응용될 수 있다. 유전자 알고리즘은 보통 다음과 같은 연산을 거친다. 

1. 초기, 염색체 모델(경로)을 생성하여 적합성을 판단 
2. 선택 연산을 통해서 부모 모집단을 선택 후, 한 세대에서 다음 세대로 전해지는 해의 후보가 되는 해들을 선택
3. 교차 연산을 부모 해의 유전자들을 서로 교차시켜서 자식해를 생성
4. 변이 연산을 통해 돌연변이 유전자를 생성하여, 유전의 다양성 확보 
5. 각 염색체의 적합성을 판단 
6. 적합하지 않으면, 2 – 5 연산을 반복 || 적합하면 종료하는 과정 

본 연구는 이러한 유전자 알고리즘을 TSP 문제에 적용하기 위하여, 문제에 가장 적합하게 각 단계의 연산에 맞는 최적의 방법을 찾고자 하였다.

# Selection_선택연산
선택(Selection) 연산이란, 교차(Crossover) 연산에 쓰일 2개의 부모해를 고르기 위한 연산을 의미한다. 선택 연산의 방법으로는 Roulette wheel selection, Tournament selection, Rank selection 등 다양한 방법이 있으나, 공통적으로 적용되는 원칙은 우수한 해가 선택될 확률이 높아야 한다는 것이다.

## Roulette wheel selection
Roulette wheel selection 은 적합도가 높을수록 부모해로 선택될 확률을 높게 부여해주는 선택 연산 방법으로, 가장 대표적인 선택 연산 방법 중 하나이다. 

## Tournament selection
Tournament selection은 염색체를 임의의 개수로 선택하여 Tournament 방식으로 부모해를 선택하는 방법이다.

# Crossover_교차연산
교차 연산은 유전 알고리즘의 대표 연산이다. 연산 중 가장 다양한 대안이 존재한다. 생명체가 세대 내에서의 교배를 통해 다음 세대를 생성하듯, 유전 알고리즘도 교차 연산을 통해 선택된 두 개의 해들을 교배하여 다음 세대의 해들을 생성한다. 여기서 교차란, 염색체가 재조합되는 과정에서 부모 염색체의 일부분이 특정 위치를 기준으로 서로 바뀌어 결합되는 경우를 말한다. 우리 연구에서는 다양한 교차 방식을 사용했다.

## One Point Crossover

## Multi-Point Crossover

## Uniform Crossover

## Order Crossover
Order Crossover 방식은 염색체가 순열로 표시되는 경우을 위하여 고안된 교차 연산자이다. 먼저 임의로 두 개의 자름선을 정한 다음 두 자름선 사이에 있는 첫 번째 부모의 염색체 부분을 복사한다. 나머지 위치는 두 번째 부모의 염색체 부분에서 두 번째 자름선 바로 다음 위치부터 사용되지 않은 유전자들을 순서대로 복사한다. 
![alt text](https://www.researchgate.net/profile/Shuihua-Wang/publication/282998951/figure/fig4/AS:433588496801795@1480386961920/An-example-of-order-crossover.png)

## Partially Matched Crossover(PMX)
PMX 방식은 Goldberg & Lingle이 고안한 교차 연산자이다. 두 부모해의 임의로 두 개의 자름선을 정한 다음 두 자름선 사이에 있는 부분을 첫번째 부모해로부터 복사한다. 나머지 위치는 두번째 부모해로부터 복사하되 만일 해당 값이 사용되었으면 같은 값을 가진 첫번째 부모해의 위치를 찾아 같은 위치의 두번째 부모해로부터 복사한다. 이 값은 사용되지 않을 수도, 사용되었을 수도 있는데, 마지막 과정에서 이미 사용되어 중복이 일어난 유전자를 고쳐준다. 
Order Crossover 방식은 염색체가 순열로 표시되는 경우을 위하여 고안된 교차 연산자이다. 먼저 임의로 두 개의 자름선을 정한 다음 두 자름선 사이에 있는 첫 번째 부모의 염색체 부분을 복사한다. 나머지 위치는 두 번째 부모의 염색체 부분에서 두 번째 자름선 바로 다음 위치부터 사용되지 않은 유전자들을 순서대로 복사한다. 
![alt text](https://i.stack.imgur.com/ArNsG.png)

최종적으로 Crossover에서 우리가 채택한 교차 연산자는 Order Crossover(순서 교차)였다. 일점 교차와 다점 교차, 균등 교차 연산은 중복 방문 도시 혹은 미방문 도시가 자식해에서 발생해서 채택할 수가 없었다. 반면 Order Crossover(순서 교차)와 PMX 교차 연산 중에서 Average Fitness 값은 Order Crossover가 더 적게 나왔다. 따라서 Order Crossover 방식이 다른 연산자의 비해 자식해의 값이 최적화가 더 잘 되어 있는 것을 알 수 있었다. 

# Mutation 변이 연산
Mutation연산은 다음 세대에게 이전 세대와는 다른 유전적 다양성을 부여하여 더 나은 해답을 찾기 위한 연산이다. Mutation연산을 통해 유전자배열의 일부를 의도적으로 변화시켜 세대를 거쳐 생성되는 여러 개체들 간의 유사성을 조절할 수 있다. 이 때, 너무 많은 값/비율의 변화는 무작위검색과의 차별성을 둘 수 없고, 적은 값의 변화는 이전 세대와의 차이가 적어져 개체 간 다양성을 확보하지 못하므로, 문제에 맞는 적절한 Mutation방법과 횟수 설정이 필요하였다. 

## Swap Mutation
Swap 연산은 유전자 배열 중 랜덤하게 뽑힌 일부 유전자 값을 대치하여 바꿔주는 과정을 일정하게 지정한 Mutation 횟수만큼 반복하였다. Scramble 연산은 랜덤으로 지정한 일부 구간의 값들을 셔플하여 순서를 바꿔주는 과정을 지정한 Mutation횟수만큼 반복하였다. 

## Scramble Mutation
Scramble 연산은 랜덤으로 지정한 일부 구간의 값들을 셔플하여 순서를 바꿔주는 과정을 지정한 Mutation 횟수만큼 반복하였다.

## Inversion Mutation
Inversion 연산은 Scramble과 마찬가지로 랜덤으로 일부 구간을 지정하지만, 규칙없이 섞는 것이 아니라, 순서를 반전시켜주는 과정을 하였다. 마찬가지로 Mutation 횟수는 일정하게 설정하였다. 


Swap Mutation은 PMX Cross Over에서, Inversion Mutation은 Order Cross Over에서 각각 앞서는 성능을 보이는 것을 확인할 수 있었다. 그러나 이 프로젝트에서는 Order Cross Over가 더 높은 성능을 보이는 것을 확인하였으므로, Inversion Mutation을 선택하는 것을 임의로 결정하였다. 이에 따라 추가적인 확인을 진행하였다. Order CrossOver를 선택한 뒤, Population Size를 15로 늘려 실험하였다.

# Other Variable Adjustment
TSP 문제를 풀기 위한 유전 알고리즘에서는 핵심적인 연산자를 설정하는 것 외에도 다양한 변수의 값을 조정함으로써 최적의 적합도를 찾아나가는 과정이 필요하다. 본 연구는 임계점을 나타내는 THRESHOLD, 모집단의 크기를 나타내는 population_size, Generation의 수를 나타내는 Generation_Count 이 세 가지 변수를 각각 실험군으로 설정하여 적합도를 판단하는 실험을 진행하였다.


# Discussion and Conclusion

결론적으로 임계값은 35000~50000의 범위에서 1000 단위로 값을 달리하여 실험을 진행한 결과, 임계값이 낮을수록 적합도가 더 좋게 나타났으나, 임계값을 너무 낮게 설정하면 모집단의 다양성이 떨어지고 시간이 오래 걸린다는 단점이 있기 때문에 우리 연구에서는 36000으로 설정하였다. 또한 Population Size는 실행시간이 크게 달라지는 데 비해 적합도를 발전시키는 데 유의미한 영향을 끼치지 못했기 때문에 간단히 15로 설정하였고, Generation Count 역시 비슷하나 Population Size보다는 적합도에 더 도움을 주었다고 판단되어 최종적으로 3000으로 설정하였다.

선택 연산에서는 Roulette wheel selection 과 Tournament Selection을 비교한 결과, 후자의 방법이 더 나은 적합도를 찾아내는 것으로 나타났고, 실험 결과 Tournament에 참석하는 염색체 수가 많을수록 최적해에 더 가까워졌기 때문에 우리 연구에서는 최종적으로 염색체 15개를 선택하여 Tournament를 진행하기로 했다.

교차 연산에서는 One Point Crossover, Multi-Point Crossover, Uniform Crossover, Order Crossover, Partially Matched Crossover 이 5가지 연산을 수행한 결과, 앞의 3가지 방법은 미방문 도시와 중복 도시가 발생하여 TSP 문제에는 적합하지 않다는 결론이 도출되었다. TSP 문제에 비교적 적합하다고 생각되는 Order Crossover 과 Partially Matched Crossover을 비교 · 분석한 결과, Order Crossover가 더 최적해에 가까운 결과를 보였으므로, 우리 연구에서는 최종적으로 Order Crossover 연산을 선택하였다.

변이 연산에서는 Swap Mutation, Scramble Mutation, Inversion Mutation 이 3가지 연산을 수행한 결과, 우리가 선택한 교차 연산인 Order Crossover와 더 좋은 성능을 보인 연산은 Inversion Mutation이었으므로, 우리 연구에서는 최종적으로 Inversion Mutation 연산을 선택하였다.


최종적으로 선택한 연산 방법과 변수 값들을 적용하였을 때, Total Best Fitness는 약 32407.21, 실행 시간은 약 1721.51초로 나타났다.


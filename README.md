Download Link :https://programming.engineering/product/cse3081-hw-1-%ed%9a%a8%ec%9c%a8%ec%a0%81%ec%9d%b8-%ec%a0%95%eb%a0%ac-%eb%b0%a9%eb%b2%95%ec%9d%98-%ea%b5%ac%ed%98%84cse3081-hw-1-%ed%9a%a8%ec%9c%a8%ec%a0%81%ec%9d%b8-%ec%a0%95%eb%a0%ac-%eb%b0%a9/


# CSE3081-HW-1-CSE3081-HW-1-
CSE3081 HW 1: 효율적인 정렬 방법의 구현CSE3081 HW 1: 효율적인 정렬 방법의 구현
마감: 10월 19일 수요일 오후 8시 정각

제출물, 제출방법, LATE 처리 방법 등: 조교가과목게시판에 공고할 예정임.

목표: 이번 숙제에서는 수업 시간에 배운몇가지 정렬(sorting) 방법을 구현하여 이론적으로배운 내용과 실제 로구현한 결과를 비교하여 본다. 특히 교과서적인 quick sort 방법의 속도향상을위하여 속도최적화기법을 적용한 후분석하여봄으로써고급 소프트웨어 개발능력을 배양토록 한다.

본숙제에서 다룰배열 데이터의 각원소는다음과같이 32바이트의 레코드 구조로구성되어 있으며,

선택 또는 정렬을해야할 기준이 되는 key 값은 아래와같이 ELEMENT 타입의 배열 원소의 주소 x에 대한매크로함수를사용하여 접근할 수 있다. 해당 내용은 본숙제에서 제공하는 my types.h 파일에 정의되어 있다.

typedef struct {

unsigned int key; float score; double other; char name[16];

} ELEMENT;

#define ELEMENT KEY(x) ((x)->key)

정렬방법 구현 시 원소 값을이동할 때 전체 구조를이동하며, 이때 아래의함수를사용하라.

#include <string.h>

void *memcpy(void *dest, const void *src, size t n);

구현 요구사항

본 숙제에서 여러분이 구현하는 각 함수들은 각각 동일한 이름을 가지는 네 개 의 파일 insertion sort.cpp, heap sort.cpp, quick sort.cpp, 그리고 quick sort opt.cpp에 저장하라. (주의:조교는 숙제 채점 시 자신의 Visual Studio 프로젝 트에 위 네개의 파일을 복사한 후자신의 주 함수에서 각함수를 차례대로호출하며구현내용과 수행 결과를 확인할 예정임. ← 본 숙제에서 제공하는 예제 프로그램참고). 특히 각 함수들은 정상 적으로원하는 계산이 완료되었으면 0 값을 아니면 그 외의 값을리턴해주어야 한다(비정상적으로 종료할 경우 에러 형태에 따른 번호를리턴해주면 되나, 본 숙제에서는 적절한 error code의사용은 채점의 대상이 아님).

다음과 같은 프로토타입을 가지는 정렬 방법을 구현하라. 이 함수들은 data[left]부터 data[right]까지 n (= right-left+1)개의 원소들을 key 값에 대하여 non-decreasing order

로정렬해주어야 함.

Insertion sort: 전형적인 insertion sort 방법을 구현함.

int INSERTION SORT(ELEMENT data[], int left, int right);

Heap sort: 전형적인 heap sort 방법을 구현함.

서강대학교 공과대학 컴퓨터공학과

(2/3)

int HEAP SORT(ELEMENT data[], int left, int right);

Quick sort: 자신만의 효과적인 pivot strategy를사용하여 pivot 원소를 선택하는 재귀적인 방식 의전형적인 quick sort 방법을구현함. Pivot 원소선택은가장보편적인방식대로배열 데이터 제일 앞 (인덱스 left), 가운데 (인덱스 (left+right)/2), 제일 뒤 (인덱스 right)에 있 는세 원소들 중앙값을가지는원소를 pivot 원소로 사용하여도 좋고, 더 적절한방법이있으면 자신이원하는방식을사용하여도 됨.

int QUICK SORT(ELEMENT data[], unsigned int left, int right);

Optimized quick sort: 바로 위에서 구현한 방법을 확장하여 최적화된 quick sort 방법을 구현하 라. 최적화기법으로는 기본적으로 수업시간에설명한 insertion sort와결합하는 방법과길이가 짧은 쪽에 대해서만 recursion을 적용하는 방법 등을 고려할 수있으며, 그외에의 기법을 적용 하여도무방함. 여기서최적화란속도 향상을의미함. (주의: 이숙제에서는이함수는재귀적인 함수를사용하여야 하며, 함수 전체에 대하여 반복(iteration)을사용하면 인정 안함.)

int QUICKSORT OPT(ELEMENT data[], unsigned int left,

int right);

(실험) 각 구현방법의 성능을 평가하기 위하여 n = 1024, 4096, 16384, 65536, 262144, 1048576, · · · (또

는메모리가 허용하는범위내에서 최대 크기까지) 각 구현방법의시간측정에 적합한적절한크기들을 선택하여아래에 기술하는 세가지 특성을 가지는입력데이터들을생성한 후 실험하라. 본 숙제에서는 입력데이터는 binary format으로 파일에 저장하야 하며, 그 형식은먼저 첫 네바이트에는배열 데이터의 원소의 개수 n이 int 형식으로저장하고, 이후 sizeof(ELEMENT) 바이트씩 n개의 원소의 내용이 순서대로 저장되도록 하라. (← 본 숙제에서 제공하는샘플 데이터 참고)

Entirely random: 배열 원소의 key 값으로 적절한 범위의 random number를 n개 생성하여 만든 데이터. (← 본숙제에서 제공하는 데이터생성 프로그램참조)

Descending: 배열 원소의 key 값이 n−1, n−2, n−3, ··· , 1, 0와같이 정반대로 정렬되어 있는 배열 데이터.

Few swaps: 배열 원소의 key 값이 0, 1, 2, ··· , n − 1과같이 정렬된 상태에서 int(√n)개의 random number pair (i, j)를생성하여 i번째 원소와 j번째 원소를 서로 교환함 (이때 |i − j| < √n의 조건을 만족하도록 할것).

(보고서기술) 다음의 내용을 포함하여 본인의 구현 내용특이사항, 실험 방법, 성능측정 결과, 그리고 분석 내용등을 보고서에 명료하게기술하라.

• 다음의 예처럼 실험에 사용한 CPU의 속도및메인 메모리의 용량 등의 실험 환경을 기술하라 (프로 그램 수행에 충분한 크기의 메모리를장착한컴퓨터를사용할 것).

OS: Windows 10 Education

CPU: Intel(R) Core(TM) i9-10910 @ 3.60GHz 3.60GHz

RAM: 32.00GB

Compiler: Visual Studio 2022 Release Mode

• 자신이 선정한 실헙 데이터의 각각에 대하여 각 구현 함수의 수행 시간을측정한 후 이를 적절한 형태의 테이블에 그 결과를 요약하라. 시간측정은 본수업에서 제시한 방법을사용하며, 실험은 각 상황에 대하여 최소 다섯 번 이상실험을한후 적절히 평균시간을취할것.

• 과연 수행 시간과 이 방법들의이론적인 시간복잡도간에 깊은 연관성을 발견할 수 있는가?

• 이때 서로 다른 종류의 데이터에 대하여 수행 시간에차이가 있는가? 있다면 그 이유는 무엇으로 추정되는가?

• 과연 quick sort 방법은 그 이름이의미하는 바와같이 정말 빠른가?

• 과연어떤부류의 데이터에 대해 insertion sort 방법의 수행 시간이 heap sort 또는 quick sort 방법 에비해 빠르거나그리느리지 않은가? 과연 insertion sort 방법이 거의 선형적인 시간에작동하는 경우를 발견하였는가?

– [CS3081(2반): 알고리즘 설계와분석] HW1 (2022년 10월 6일) –

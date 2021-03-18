# std-tie-and-tuple

1. std::tie를 이용해 tuple object를 unpacking 한다.

```
std::tuple<int, string> example_tu(2, "Halley");

int id;
// tuple 내 특정 데이터와 묶을 필요가 없으면 std::ignore
std::tie(id, std::ignore) = example_tu;
cout << "tied id = " << id << endl;
```

    swap처리에 응용

```
//보통의 swap 처리
int a = 3, z = 4;
int temp = a;
a = z;
z = temp;

//std::tie를 사용한 swap 처리
a = 3, z = 4;
std::tie(z, a) = std::make_tuple(a, z);
```

2. sort의 기준이 여러 개일때

```
struct ArrayNums
{
    int num[3];
}array_nums[] =
{
    {1000, 2000, 3000},
    {1001, 2002, 3003},
    {1001, 2001, 3001},
    {1001, 2002, 3002},
};

//오름차순 sorting에 사용할 lambda func
auto array_less = [](ArrayNums& a, ArrayNums& b) -> bool
{
    return (tie(a.num[0], a.num[1], a.num[2]) < tie(b.num[0], b.num[1], b.num[2]));
};
```

- 참고: https://codedreamer.tistory.com/entry/stdtuple-사용하기 [code = (smart & simple) | elaborate;]

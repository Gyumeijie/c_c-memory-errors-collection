
#### 内存分配大小类型不匹配

```cpp
struct Test {
    uint64_t first; 
    uint64_t second;
    uint64_t third;
};

int main()
{
    Test* test = (Test*)malloc(sizeof(void*));
    std::cout << test << std::endl;
    std::cout <<&test->second << std::endl;
    std::cout <<&test->third << std::endl;
    test->first = 100;
    test->second = 200;
    test->third = 300;
    uint64_t* i = (uint64_t*)malloc(sizeof(void*));
    std::cout << i << std::endl;
    std::cout << *i << std::endl;
}
```
```
0x7fe08d402b60
0x7fe08d402b68
0x7fe08d402b70
0x7fe08d402b70
300

```

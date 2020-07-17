
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

#### 未初始话内存访问

```cpp
char *pStr = (char*) malloc(512);
char c = pStr[0]; // the contents of pStr were not initialized
void func()
{ 
    int a; 
    int b = a * 4; // uninitialized read of variable a 
}
```


#### 内存泄露

> 特别是异常分支，容易忘记释放

```cpp
char *pStr = (char*) malloc(512);
return;
```


#### 不匹配内存分配释放函数

```cpp
char *s = (char*) malloc(5); 
delete s;
```




# C++ 語言
## Array 陣列
- Array是相同類型的物件序列，佔用連續記憶體區域。
- 在 C style語言中， Array是許多bug來源，因此不建議使用，建議使用std::vector或 std::array，因為這兩種library都會將其元素儲存為連續記憶體區塊contiguous block of memory，提供更大的型別安全性 type safety，並保證指向序列內有效位置的iterator。    

https://learn.microsoft.com/zh-tw/cpp/cpp/arrays-cpp?view=msvc-170    
https://learn.microsoft.com/en-us/cpp/cpp/arrays-cpp?view=msvc-170


## namespace 命名空間

- 命名空間是一種功能，允許將相關名稱的(例如變量、函數、類、其他實體)，分組到命名範圍中。
- 命名空間以模塊化和分層化方式組織代碼，用於防止命名衝突。
- 在處理大型的codebase或需要合併有自己名稱的外部的library時非常有用。


```C++
// Declaration of a namespace
namespace MyNamespace {
    int myFunction(int x) {
        return x * 2;
    }
}

// Usage of the namespace
int main() {
    int result = MyNamespace::myFunction(5);
    // ...
    return 0;
}
```
在這個例子中，聲明了一個命名空間MyNamespace並在其中定義了一個函數myFunction。   
要使用該函數，需要在函數名稱前指定指定命名空間前綴MyNamespace::。   


創建分層命名空間：
```C++
namespace Outer {
    namespace Inner {
        void myFunction() {
            // ...
        }
    }
}
```
在這個例子中，Inner 命名空間嵌套在Outter命名空間中，所以我們可以使用 Outer::Inner::myFunction()訪問函數myFunction。

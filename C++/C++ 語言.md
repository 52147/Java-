# C++ 語言
## Array 陣列
- Array是相同類型的物件序列，佔用連續記憶體區域。
- 在 C style語言中， Array是許多bug來源，因此不建議使用，建議使用std::vector或 std::array，因為這兩種library都會將其元素儲存為連續記憶體區塊contiguous block of memory，提供更大的型別安全性 type safety，並保證指向序列內有效位置的iterator。    

https://learn.microsoft.com/zh-tw/cpp/cpp/arrays-cpp?view=msvc-170    
https://learn.microsoft.com/en-us/cpp/cpp/arrays-cpp?view=msvc-170

# Java 基礎語法
## 動態儲存區: 棧、堆 vs 靜態儲存區: 樹據段、代碼段
https://blog.csdn.net/chen1083376511/article/details/54930191     
https://www.cnblogs.com/yanxiaoge/p/10658154.html
## Java 變量類型: 類變量、實例變量、局部變量
1. 類變量(靜態變量static): 
   - 方法之外的變量，用static修飾。
   - 靜態變量除了被聲明為常量外，很少使用。ex: public static final String DEPARTMENT = "數學系"; 。靜態變量被初始化後不可改變。
   - 靜態變量儲存在靜態儲存區。
   - 在第一次訪問時被創建，在程序結束時銷毀。
   - 有默認值。數字默認為0，boolean默認為false，引用類型默認為null。
   - 可以通過ClassName.VariableName的方式訪問。ex: Employee.DEPARTMENT
   - 類變量被聲明為 public static final時，變量名稱一般使用大寫字母。
3. 實例變量: 
   - 方法之外的變量，沒有用static修飾。
   - 當對象被實例化後，實例變量的值也跟著確定。
   - 儲存在堆(heap)中
   - 可以用訪問修飾符(modifer)修飾。ex: public, private。
     - public : 這個實例變量僅對子類可見
     - private : 這個實例變量僅對該類可見
4. 局部變量: 
   - 方法中的變量。
   - 變量名及值存在方法棧(stack)中。
   - 沒有默認值，所以局部變量被聲明後，必須經過初始化initizlized(賦初始值)，才可以使用。 ex: int a = 10;
   - 每當程序調用方法時，系統都會建立一個方法棧，在方法中聲明的變量將放在方法棧中，當方法結束時，系統會銷毀方法棧，在該方法中的變量也會被銷毀，因此局部變量只能在方法中有效的原因。



延伸: 實例變量與遞歸函數     
https://www.runoob.com/java/java-variable-types.html     
https://developer.aliyun.com/article/947126
## Java 有全域變量嗎



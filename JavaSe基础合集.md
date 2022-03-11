[toc]

### 从入门到精通

* * *

#### 1.5 Java语言的环境搭建
##### 什么是JDK，JRE？
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201105101251.png)
##### JDK，JRE，JVM的关系
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201105101425.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201105101526.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201105103012.png)
#### 3.4数组涉及到的常见算法
**1.数组元素的赋值（杨辉三角，回行数等）**

* **杨辉三角**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201105173320.png)
```java
* 1.使用二维数组打印一个10 行杨辉三角 
* 【提示】
* 1.第一行有 1 个元素，第n行有n个元素 
* 2.每一行的第一个元素和最后一个元素都是1
* 3.从第三行开始，对于非第一个元素和最后一个元素的元素。即：
* yanghui[i][j] = yanghui[i-1][j-1] + yanghui[i-1][j]; 
public class 杨辉三角 {    
public static void main(String[] args) {       
//1.声明并初始化二维数组   
int[][] yanghui = new int[10][];   
//2.给数组的元素赋值    
for (int i = 0; i < yanghui.length ; i++) {     
yanghui[i] = new int[i+1];     
//2.1给首末元素赋值      
yanghui[i][0] = 1;      
yanghui[i][i] = 1;     
//2.2给每行的非首末元素赋值       
if (i >= 2){       
for (int j = 1; j < yanghui[i].length - 1 ; j++) {           
yanghui[i][j] = yanghui[i-1][j-1] + yanghui[i-1][j];               
}            }        }          
//3.遍历二维数组    
for (int i = 0; i < yanghui.length ; i++) {        
    for (int j = 0; j < yanghui[i].length; j++) {        
    System.out.print(yanghui[i][j] + " ");            }    
    System.out.println( );        }    }
    }
```

**扩展之笔试题**
         
    创建一个长度为6的int型数组，要求数组元素的值都在1-30之间，且是随机赋值，同时要求元素的值各不同
```java
public void test(){   
int[] arr = new int[6];  
for (int i = 0; i < arr.length ; i++) {    
int number = (int) (30 * Math.random());   
int j = 0;     
while (j <= i){     
if (arr[j] == number){        
number = (int) (30 * Math.random());    j = -1;            }   
j++;        }     
arr[i] = number;   
System.out.println(arr[i]);    }
```
**数组的反转**
```java
较差的算法：
n为元素的个数
for(int  i= 0; i < n ; i++){
b[i] = a[n - i - 1];
}
for(int i = 0 ; i < n; i++){
a[i] = a[i];
}
算法优化一：
for(int i = 0;i< n / 2; i++){
temp = a[i];
a[i] = a[n - i - 1];
a[n - i - 1] = temp;
}
算法优化二：
for(int i = 0; j = n - 1;i < j; i++; j--){
temp = a[i];
a[i] = a[j];
a[j] = temp;
}
```
#### 数组中涉及到的常见算法
**二分查找法**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201105210515.png)
```java
public  void test1(){    
二分法查找前提是,所查找的数组元素是有序的  
int[] arr = new int[]{1,2,3,4,5,6,7,8,9};  
int n = 2;  
int end = arr.length - 1;初始的末索引  
int head = 0; 初始的首索引  
boolean isFlag = true; 
while (head <= end){  
int midIndex = (end +head) / 2;    
if (n == arr[midIndex]){   
System.out.println("找到了指定元素，位置为：" + midIndex);     
isFlag = false;        
break;      
}else if (n < arr[midIndex]){       
end = midIndex - 1;    
}else if (n > arr[midIndex]){     
head = midIndex + 1; } } 
if (isFlag){ System.out.println("很遗憾，没有找到的啦！");  }}
```
**排序算法**

    衡量排序算法的优劣：
    1. 时间复杂度：分析关键字的比较次数和记录的移动次数
    2. 空间复杂度：分析排序算法中需要多少辅助内存
    3. 稳定性：若两个记录A和B的关键字相等，但排序后A，B的先后次序保持不变，则称这种排       序算法是稳定的
**排序算法分类**

    内部排序：整个排序过程不需要借助于外部存储器（如磁盘等），所有排序操作都在内存中完成
    外部排序：参与排序的数据非常多，数据量非常大，计算机无法把整个排序过程放在内存中完成，必须借助于外部存储器（如磁盘）。外部排序最常见的是多路归并排序。可以认为外部排序是由多次内部排序组成

**冒泡排序**
```java
public class BubbleSortTest {  
public static void main(String[] args) {    
int[] nums = new int[]{2,3,6,8,7,4,1};  
//外轮全部要排序几次
for (int i = 0; i < nums.length -1 ; i++) {
//每一趟排序要排几次 
for (int j = 0; j < nums.length - 1  - i ; j++) {      
if (nums[j] > nums[j+1]){          
int temp = nums[j];         
nums[j] = nums[j+1];         
nums[j+1] = temp;       
}}}     
System.out.println(Arrays.toString(nums));}}
```
##### 冒泡排序解析
* **冒泡排序原理：**
    * **如果有n个数据进行排序，总共需要比较n-1次**
    * **每一次比较完毕，下一次的比较就会少一个数据参与**

**代码如下：**
```java
@Test
    public void testBubbleSort(){
        int[] arr = {24,98,65,45,23};
        System.out.println("排序前：" + Arrays.toString(arr));

        //第一次比较
        for (int i = 0; i < arr.length - 1 - 0 ; i++) {
            if (arr[i] > arr[i+1]){
                int temp = arr[i];
                arr[i] = arr[i+1];
                arr[i+1] = temp;
            }
        }
        System.out.println("第一次排序：" + Arrays.toString(arr));

        //第二次比较
        for (int i = 0; i < arr.length - 1 - 1 ; i++) {
            if (arr[i] > arr[i+1]){
                int temp = arr[i];
                arr[i] = arr[i+1];
                arr[i+1] = temp;
            }
        }
        System.out.println("第二次排序：" + Arrays.toString(arr));
        //第三次比较
        for (int i = 0; i < arr.length - 1 - 2 ; i++) {
            if (arr[i] > arr[i+1]){
                int temp = arr[i];
                arr[i] = arr[i+1];
                arr[i+1] = temp;
            }
        }
        System.out.println("第三次排序：" + Arrays.toString(arr));
        //第四次比较
        for (int i = 0; i < arr.length - 1 - 3 ; i++) {
            if (arr[i] > arr[i+1]){
                int temp = arr[i];
                arr[i] = arr[i+1];
                arr[i+1] = temp;
            }
        }
        System.out.println("第四次排序：" + Arrays.toString(arr));

        //代码合并，优化
        for (int i = 0; i < arr.length - 1; i++) { //一共比较n-1次
            for (int j = 0; j < arr.length - 1 - i ; j++) {// 每比较一次,少一个元素参与
                if (arr[i] > arr[i+1]){
                    int temp = arr[i];
                    arr[i] = arr[i+1];
                    arr[i+1] = temp;
                }
            }
        }
        System.out.println("优化排序后的结果：" + Arrays.toString(arr));

    }
```
**快速排序**

    介绍：
    快速排序通常明显比同为O(nlogn)的其他算法更快，因此常被采用，而且快排采用了分治法的思想，所以在很多笔试面试中能经常看到快排的影子，可见掌握快排的重要性。
    快速排序(Quick Sort)由图灵奖获得者Tony Hoare发明：被列为“20世纪十大算法之一”，是迄今为止所有内排序算法中速度最快的一种。冒泡排序的升级版，交换排序的一种。
    快速排序的时间复杂度为：O(nlogn).

**十大内部排序算法**        
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201106211936.png)
**排序算法性能对比**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201106212202.png)
**排序算法的选择**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201106212927.png)

### 对象
##### 对象的创建和使用：内存解析
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201107153350.png)
##### 理解变量的赋值

    关于变量的赋值：
    如果变量是基本数据类型，此时赋值的是变量所保存的数据值。
    如果变量是引用数据类型，此时赋值的是变量所保存的数据的地址值。

##### 方法的形参的传递机制：值传递 
* **方法，必须由其所在类或对象调用才有意义。若方法含有参数：**    
     **形参：方法定义时，声明的小括号内的参数**
     **实参：方法调用时，实际传递给形参的数据**   
##### Java的实参值如何传入方法呢？

```java
Java里方法的参数传递方式只有一种：值传递。 即将实际参数值的副本（复制品）传入方法内，而参数本身不受影响。 
形参是基本数据类型：将实参基本数据类型变量的“数据值”传递给形参
形参是引用数据类型：将实参引用数据类型变量的“地址值”传递给形参
```
* **值传递机制：**

```java
如果参数是"基本数据类型"，此时实参赋给形参的是实参真实储存的"数据值"。
如果变量是"引用数据类型"，此时实参赋给形参的是实参存储数据的"地址值"。
基本类型参数传递："不改变值"
```
#### 方法的参数传递
##### 基本数据类型的参数传递
 ![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201217195140.png)   
##### 引用数据类型的参数传递
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201217195315.png)
* **内存解析**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201217195406.png)

* * *
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201217195509.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201217195602.png)
* * *
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201217195836.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201108160604.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201217195943.png)

>**画内存结构图思想：**

    1.内存结构：栈（局部变量），堆（new出来的结构：对象(非static成员变量)，数组）
    2.变量：成员变量 VS 局部变量（方法内，方法形参，构造器内，构造器形参，代码块内）

>**从java内存模型出发考虑：画内存图，swap(int a,int b)方法执行完，弹出栈，方法体里面的变量也跟着弹出栈**
>![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201108161639.png)

**引用类型参数传递：改变值**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201108160701.png)

**内存结构图**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201108163410.png)

![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201108165516.png)
**内存结构图**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201108165418.png)


* **貌似是考查方法的参数传递**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201217200138.png)

* **扩展**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201217200413.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201217200530.png)

#### 可变参数
```java

```

#### Java JVM 中 堆，栈，方法区 详解
>链接博客：https://blog.csdn.net/zhangqiluGrubby/article/details/59110906

##### 递归
**1.定义：**
**递归方法：一个方法体内调用它自身。**

**2.如何理解递归方法？**
> 方法递归包含了一种隐式的循环，它会重复执行某段代码，但这种重复执行无须循环控制。

> 递归一定要向已知方向递归，否则这种递归就变成了无穷递归，类似于死循环。

**3.举例：**
```java
// 例1：计算1-n之间所自然数的和
     public int getSum(int n) {// 3
          if (n == 1) {
              return 1;
          } else {
              return n + getSum(n - 1);
          }
     }
     // 例2：计算1-n之间所自然数的乘积:n!
     public int getSum1(int n) {
          if (n == 1) {
              return 1;
          } else {
              return n * getSum1(n - 1);
          }
     }
     //例3：已知一个数列：f(0) = 1,f(1) = 4,f(n+2)=2*f(n+1) + f(n),
     //其中n是大于0的整数，求f(10)的值。
     public int f(int n){
          if(n == 0){
              return 1;
          }else if(n == 1){
              return 4;
          }else{
//            return f(n + 2) - 2 * f(n + 1);
              return 2*f(n - 1) + f(n - 2);
          }
     }
     //例4：斐波那契数列

     //例5：汉诺塔问题

     //例6：快排

```
**扩展：
Ryan，我今天去字节面试，遇到一个一个双重递归调用的问题，我琢磨了一下，完全不知道为什么。打断点了，也还是没看懂为什么程序会那样走。您有空可以看一下，求指教**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201108190447.png)

**该题递归分析图**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201108190528.png)

##### MVC设计模式
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201109164842.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201109164920.png)

##### 基于MVC设计模式项目练习
###### 客户信息管理软件

* **软件设计结构**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201111172930.png)
* **目录展示**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201111165337.png)

* **Customer类**
```java
package 客户信息管理软件.dao;

/**
 * @author 布丁熊.菲特尼斯
 * @create 2020-11-10 19:07
 */
public class Customer {
    private String name;
    private char sex;
    private int age;
    private String number;
    private String email;

    public Customer(){ }
    public Customer(String name, char sex, int age, String number, String email) {
        this.name = name;
        this.sex = sex;
        this.age = age;
        this.number = number;
        this.email = email;
    }
/*------------------------get方法-------------------------------------*/
    public String getName() {
        return name;
    }

    public char getSex() {
        return sex;
    }

    public int getAge() {
        return age;
    }

    public String getNumber() {
        return number;
    }

    public String getEmail() {
        return email;
    }

    /*--------------------------set方法------------------------------*/

    public void setName(String name) {
        this.name = name;
    }

    public void setSex(char sex) {
        this.sex = sex;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public void setNumber(String number) {
        this.number = number;
    }

    public void setEmail(String email) {
        this.email = email;
    }

    @Override
    public String toString() {
        return "Customer{" +
                ", name='" + name + '\'' +
                ", sex='" + sex + '\'' +
                ", age=" + age +
                ", number='" + number + '\'' +
                ", email='" + email + '\'' +
                '}';
    }

    /*-----------------测试主函数-----------------------------*/
    public static void main(String[] args) {
      }
}

```
* **CustomerList类**
```java
package 客户信息管理软件.service;

import 客户信息管理软件.dao.Customer;

/**
 * @author 布丁熊.菲特尼斯
 * @create 2020-11-10 19:07
 */
public class CustomerList {
    private Customer[] customers;
    private int total;//记录已保存客户对象的数量

    //调用构造器初始化数组
    /*
     * @Description:
     * @Param: [totalCustomer]：指定数组长度
     * @Return: 
     */
    public CustomerList(int totalCustomer){
        customers = new Customer[totalCustomer];
    }

    //将参数customer添加到数组中最后一个客户对象记录之后
    public boolean addCustomer(Customer customer){
            rangeCheckForAdd(total);
            customers[total++] = customer;
            return true;
    }

    //用参数customer替换数组中由index指定的对象
    public boolean replaceCustomer(int index,Customer customer){
        rangeCheck(index);
        customers[index] = customer;
        return true;
    }

    //从数组中删除参数index指定索引位置的客户对象记录
    public boolean deleteCustomer(int index){
        rangeCheck(index);
        //元素前移
        for (int i = index + 1; i < total; i++) {
            customers[i - 1] = customers[i];
        }
        //要是集合存放的是对象,那么数组中的最后一个内存地址，和数组倒数第二个内存地址存放的对象引用相同
        customers[--total] = null;
        return true;
    }

    //返回数组中记录的所有客户对象
    public Customer[] getAllCustomers(){
        Customer[] custs = new Customer[total];
        for (int i = 0; i < total ; i++) {
            custs[i] = customers[i];
        }
        return custs;
        /*return customers;*/
    }

    //返回参数index指定索引位置的客户对象记录
    public Customer getCustomer(int index){
        rangeCheck(index);
        return customers[index];
    }
    public int getTotal(){
        return total;
    }
    /** 设计数组下标异常 */
    private void outOfBounds(int index){
        throw new IndexOutOfBoundsException("Index:" + index +", total:" + total);
    }
    private void maxSizeCapacity(int total){
        throw new IndexOutOfBoundsException("total:" + total +",已经到达最大容量了!");
    }
    /**判断elements数组下标index*/
    private void rangeCheck(int index){
        if (index < 0 || index >= total){
            outOfBounds(index);
        }
    }
    private void rangeCheckForAdd(int total){
        if (total == customers.length ){
            outOfBounds(total);
        }
    }
}

```
* CustomerView类
```java
package 客户信息管理软件.ui;

import 客户信息管理软件.dao.Customer;
import 客户信息管理软件.service.CustomerList;
import 客户信息管理软件.utils.CMUtility;


/**
 * @author 布丁熊.菲特尼斯
 * @create 2020-11-10 19:07
 */

public class CustomerView {
    private final static int DEFAULT_CAPATICY = 10;//默认最大容量
    private CustomerList cust = new CustomerList(DEFAULT_CAPATICY);;

    public CustomerView(){
        Customer customer = new Customer("布丁熊.菲特尼斯",'男',18,"10086","wt@gmail.com");
        cust.addCustomer(customer);
    }
    //显示主菜单，响应用户输入，根据用户操作分别调用其他相应的成员方法（如addNewCustomer），以完成客户信息处理。
    public void enterMainMenu(){
        boolean isFlag = true;
        while (isFlag){
            System.out.println("\n----------------客户信息管理软件----------------");
            System.out.println("                   1 添 加 客 户");
            System.out.println("                   2 修 改 客 户");
            System.out.println("                   3 删 除 客 户");
            System.out.println("                   4 客 户 列 表");
            System.out.println("                   5  退    出\n");
            System.out.print("   请 选 择(1-5): ");

            //用户选择输入
            char menu = CMUtility.readMenuSelection();
            switch (menu){
                case '1':
                    addNewCustomer();
                    break;
                case '2':
                    modifyCustomer();
                    break;
                case '3':
                    deleteCustomer();
                    break;
                case '4':
                    listAllCustomers();
                    break;
                case '5':
                    System.out.print("确认是否退出(Y/N): ");
                    char isExit = CMUtility.readConfirmSelection();
                    if (isExit == 'Y'){
                        isFlag = false;
                    }
            }

            /*isFlag = false;*/
        }
    }
    //增加用户的操作
    private void addNewCustomer(){
        //System.out.println("添加客户客户的操作");
        System.out.println("--------------------------添加客户------------------------");
        System.out.println("姓名：");
        String name = CMUtility.readString(10);

        System.out.println("性别：");
        char gender = CMUtility.readChar();

        System.out.println("年龄：");
        int age = CMUtility.readInt();

        System.out.println("电话：");
        String phone = CMUtility.readString(13);

        System.out.println("邮箱：");
        String email = CMUtility.readString(30);

        //将上述数据封装到对象中
        Customer customer = new Customer(name,gender,age,phone,email);
        //添加操作
        boolean isSuccess = cust.addCustomer(customer);
        if (isSuccess){
            System.out.println("--------------------------添加完成------------------------");
        }else {
            System.out.println("--------------------------用户目录已满,添加失败------------------------");
        }
    }

    //修改用户的操作
    private void modifyCustomer(){
        //System.out.println("修改用户的操作");
        System.out.println("--------------------------修改客户------------------------");
        Customer customer = null;
        int number;
        for (;;){
            System.out.print("请选择待修改的客户编号(-1退出)：");
            number = CMUtility.readInt();
            if (number == -1){
                return;
            }
             customer = cust.getCustomer(number - 1);
            if (customer == null){
                System.out.println("无法找到指定用户！");
            }else { //找到相应的客户
                break;
            }
        }
        //找到相应客户,修改客户信息
        System.out.println("姓名(" + customer.getName() + "):");
        String name = CMUtility.readString(10, customer.getName());

        System.out.println("姓别(" + customer.getSex() + "):");
        char gender = CMUtility.readChar(customer.getSex());
        
        System.out.println("年龄(" + customer.getAge() + "):");
        int age = CMUtility.readInt(customer.getAge());

        System.out.println("电话(" + customer.getNumber() + "):");
        String phone = CMUtility.readString(13,customer.getNumber());
        
        System.out.println("邮箱(" + customer.getEmail() + "):");
        String email = CMUtility.readString(30, customer.getEmail());

        //创建用户
        Customer newCust = new Customer(name,gender,age,phone,email);
        boolean isReplaced = cust.replaceCustomer(number - 1, newCust);
        if (isReplaced){
            System.out.println("--------------------------修改完成------------------------");
        }else {
            System.out.println("--------------------------修改失败------------------------");
        }
    }

    //删除用户的操作
    private void deleteCustomer(){
        //System.out.println("删除用户的操作");
        System.out.println("--------------------------删除用户------------------------");

        int number;
        for (;;){ //for死循环,假如用户输入数字不正确，循环再次输入
            System.out.print("请选择待删除客户编号(-1退出)：");
            number = CMUtility.readInt();
            if (number == -1){
                return;
            }
            //获取你要删除的用户
            Customer customer = cust.getCustomer(number - 1);
            if (customer == null){
                System.out.println("无法找到指定用户！");
            }else {
                break;//退出for循环
            }
        }

        //退出循环，意味着找到指定用户
        System.out.println("确认是否删除(Y/N)：");
        char isDelete = CMUtility.readConfirmSelection();
        if (isDelete == 'Y'){
            boolean deleteCustomer = cust.deleteCustomer(number - 1);
            if (deleteCustomer){
                System.out.println("--------------------------删除完成------------------------");
            }else {
                System.out.println("--------------------------删除失败------------------------");
            }
        }else {
            return;
        }
    }

    //展示用户列表操作
    private void listAllCustomers(){
        System.out.println("展示用户列表操作");
        System.out.println("--------------------------客户列表------------------------");
        int total = cust.getTotal();
        if (total == 0){
            System.out.println("没有用户记录!");
        }else {
            System.out.println("编号\t\t姓名\t\t\t性别\t\t\t年龄\t\t\t电话\t\t\t邮箱");
            Customer[] allCusts = cust.getAllCustomers();
            for (int i = 0; i < allCusts.length ; i++) {
                Customer customer = allCusts[i];
                System.out.println((i + 1) + "\t" + customer.getName()+ "\t"
                        +customer.getSex()+ "\t\t\t" +customer.getAge()+ "\t\t\t"
                        +customer.getNumber()+ "\t" +customer.getEmail()+ "\t" );
            }
        }
        System.out.println("--------------------------客户列表加载完成------------------------");
    }

    public static void main(String[] args) {
        CustomerView cv = new CustomerView();
        cv.enterMainMenu();
    }
}
```
* **CMUtility类**
```java
package 客户信息管理软件.utils;


import java.util.*;
/**
CMUtility工具类：
将不同的功能封装为方法，就是可以直接通过调用方法使用它的功能，而无需考虑具体的功能实现细节。
*/
public class CMUtility {
    private static Scanner scanner = new Scanner(System.in);
    /**
	用于界面菜单的选择。该方法读取键盘，如果用户键入’1’-’5’中的任意字符，则方法返回。返回值为用户键入字符。
	*/
	public static char readMenuSelection() {
        char c;
        for (; ; ) {
            String str = readKeyBoard(1, false);
            c = str.charAt(0);
            if (c != '1' && c != '2' && 
                c != '3' && c != '4' && c != '5') {
                System.out.print("选择错误，请重新输入：");
            } else break;
        }
        return c;
    }
	/**
	从键盘读取一个字符，并将其作为方法的返回值。
	*/
    public static char readChar() {
        String str = readKeyBoard(1, false);
        return str.charAt(0);
    }
	/**
	从键盘读取一个字符，并将其作为方法的返回值。
	如果用户不输入字符而直接回车，方法将以defaultValue 作为返回值。
	*/
    public static char readChar(char defaultValue) {
        String str = readKeyBoard(1, true);
        return (str.length() == 0) ? defaultValue : str.charAt(0);
    }
	/**
	从键盘读取一个长度不超过2位的整数，并将其作为方法的返回值。
	*/
    public static int readInt() {
        int n;
        for (; ; ) {
            String str = readKeyBoard(2, false);
            try {
                n = Integer.parseInt(str);
                break;
            } catch (NumberFormatException e) {
                System.out.print("数字输入错误，请重新输入：");
            }
        }
        return n;
    }
	/**
	从键盘读取一个长度不超过2位的整数，并将其作为方法的返回值。
	如果用户不输入字符而直接回车，方法将以defaultValue 作为返回值。
	*/
    public static int readInt(int defaultValue) {
        int n;
        for (; ; ) {
            String str = readKeyBoard(2, true);
            if (str.equals("")) {
                return defaultValue;
            }

            try {
                n = Integer.parseInt(str);
                break;
            } catch (NumberFormatException e) {
                System.out.print("数字输入错误，请重新输入：");
            }
        }
        return n;
    }
	/**
	从键盘读取一个长度不超过limit的字符串，并将其作为方法的返回值。
	*/
    public static String readString(int limit) {
        return readKeyBoard(limit, false);
    }
	/**
	从键盘读取一个长度不超过limit的字符串，并将其作为方法的返回值。
	如果用户不输入字符而直接回车，方法将以defaultValue 作为返回值。
	*/
    public static String readString(int limit, String defaultValue) {
        String str = readKeyBoard(limit, true);
        return str.equals("")? defaultValue : str;
    }
	/**
	用于确认选择的输入。该方法从键盘读取‘Y’或’N’，并将其作为方法的返回值。
	*/
    public static char readConfirmSelection() {
        char c;
        for (; ; ) {
            String str = readKeyBoard(1, false).toUpperCase();
            c = str.charAt(0);
            if (c == 'Y' || c == 'N') {
                break;
            } else {
                System.out.print("选择错误，请重新输入：");
            }
        }
        return c;
    }

    private static String readKeyBoard(int limit, boolean blankReturn) {
        String line = "";

        while (scanner.hasNextLine()) {
            line = scanner.nextLine();
            if (line.length() == 0) {
                if (blankReturn) return line;
                else continue;
            }

            if (line.length() < 1 || line.length() > limit) {
                System.out.print("输入长度（不大于" + limit + "）错误，请重新输入：");
                continue;
            }
            break;
        }

        return line;
    }
}

```
### 面向对象特征之二：继承
#### 一. 继承性的好处
* **减少代码的冗余，提高代码的复用性**
* **便于功能的扩展**
* **为之后多态性的使用，提供前提**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201112094347.png)
#### 二. 继承的格式

* **格式：class A extends B{}**
* **A：子类，派生类，subclass**
* **B：父类，超类，基类，superclass**
>**2.1 体现：一旦子类A继承父类B以后，子类A中就获取了父类B中声明的所有的 属性，方法**
>**特别的，父类中声明为private的属性和方法，子类继承父类以后，仍然认为获取了父类中私有的结构。**

>**只是因为封装性的影响，使得子类不能直接调用父类的结构而已**
>**2.2 子类继承父类以后，还可以声明自己特有的属性或方法，实现功能的扩展。**
>**父类的功能比子类的功能更单一  extends：延展，扩展**

#### java中关于继承性的规定

* **一个类可以被多个子类继承**
* **java中类的单继承性：一个类只能有一个父类**
* **子父类是相对的概念**
* **子类直接继承的父类，称为：直接父类。间接继承的父类称为：间接父类**
* **子类j继承父类以后，就获取了直接父类以及所有间接父类中声明的属性和方法**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201112094253.png)
#### 项目规范
**1.至少独立完成一遍以上的项目代码**
**2.积累完成项目的过程中常见的bug的调试
方式一：“硬”看，必要时，添加输出语句。
方式二：Debug
3.捋顺思路,强化逻辑
4.对象、数组等内存结构的解析**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201112093448.png)
**注：项目二**

**5.遵守编码的规范,标识符的命名规范等
int i1 = 10;
int total = 0;
6.在类前,方法前,方法内具体逻辑的实现步骤等添加必要的注释.
类前、方法前、属性前：文档注释。
逻辑步骤：单行、多行注释。**

### 方法的重写(override / overwrite)

**1. 重写：子类继承父类以后，可以对父类中同名同参数的方法，进行覆盖操作**

**2. 应用：重写以后，当创建子类对象以后，通过子类对象调用子父类中的同名同参数的方法时，实际执行的是子类重写父类的方法**

**3. 重写的规定：**

    方法的声明：权限修饰符 返回值类型 方法名(形参列表){
       //方法体    
    } 
    约定俗成：子类中的叫重写的方法，父类中的叫被重写的方法
    
    1. 子类重写的方法的 方法名 和 形参列表 与父类被重写的方法的 方法名 和 形参列表 相同
    
    2. 子类重写的方法的权限修饰符不小于父类被重写的方法的权限修饰符
        >特殊情况：子类不能重写父类中声明为private权限的方法
        
    3. 返回值类型
        >父类被重写的方法的返回值类型是void，则子类重写的方法的返回值类型只能是void
        >父类被重写的方法的返回值类型是A类型，则子类重写的方法的返回值类型可以是A类或A的子类
        >父类被重写的方法的返回值类型是基本数据类型(比如：double)，则子类重写的方法的返回值类型必须是相同的基本数据类型(也必须是double)
     
    4. 子类重写的方法抛出的异常类型不大于父类被重写的方法抛出的异常类型
    
    5. 子类和父类中同名同参数的方法要么都声明为非static的(考虑重写)，要么都声明为static的(不是重写)
####  四种访问修饰符
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201112150512.png)

#### 关键字：super
super关键字的使用

**1. super理解为：父类的
2. super可以用来调用：属性，方法，构造器
3. super的使用：调用属性和方法
 3.1 我们可以在子类的方法或构造器中，通过使用“super.属性”或“super.方法”的方式，显示地调用父类中声明的属性和方法。但是，通常情况下，我们习惯省略“super.”**

   **3.2 特殊情况：当子类和父类中定义了同名的属性时，我们要想在子类中调用父类中声明的属性，则必须显示地使用“super.属性”的方式，表明调用的是父类中声明的属性**
   
   **3.3 特殊情况：当子类重写了父类中的方法以后，我们要想在子类的方法中调用父类中被重写的方法时，则必须显示地使用“super.方法”的方式，表明调用的是父类中被重写的方法**
   

**4. super调用构造器   
  4.1 我们可以在子类的构造器中显示地使用“super(形参列表)”的方式，调用父类中声明的指定构造器
  4.2 “super(形参列表)”的使用，必须声明在子类构造器的首行！
  4.3 我们在类的构造器中，针对于“this(形参列表)”或“   super(形参列表)”只能二选一，不能同时出现
  4.4 在构造器的首行，没有显示的声明“this(形参列表)”或“super(形参列表)”，则默认调用的是父类中空参的构造器：super( )
  4.5 在类的多个构造器中，至少有一个类的构造器中使用了“super(形参列表)”，调用父类的构造器**

#### 子类对象实例化的过程
**1. 从结果上来看：(继承性)
   子类继承父类以后，就获取了父类中声明的属性和方法
   创建子类的对象，在堆空间中，就会加载所有父类中声明的属性**

**2. 从过程上来看：
   当我们通过子类的构造器创建对象时，我们一定会直接或间接调用其父类的构造器，进而调用父类的父类的构造器，直到调用了java.lang.Object类中空参的构造器为止。正因为加载过所有的父类的结构，所以才可以看到内存中有父类中的结构，子类对象才可以考虑进行调用。**

   **明确：虽然创建子类对象时，调用了父类的构造器，但是自始自终就创建过一个对象，即为new的子类对象。**

#### 面向对象特征之三：多态性
1.理解多态性：可以理解为一个事物的多种形态

2.何为多态性：
  对象的多态性：父类的引用指向子类的对象(或子类的对象赋值父类的引用)
  >可以直接应用在抽象类和接口上

3.多态性的使用：虚拟方法调用
 有了对象的多态性以后，我们在编译期，只能调用父类中声明的方法，但是在运行期，我们实际执行的是子类重写父类的方法

4.Java引用变量有两个类型：**编译时类型**和**运行时类型**。编译时类型由声明该变量时使用的类型决定，运行时类型由实际赋给该变量的对象决定。
简称：编译时，看左边；运行时，看右边
        >若编译时类型和运行时类型不一致，就出现了对象的多态性(Polymorphism)
        >多态情况下，“看左边”：看的时父类的引用(父类中不具备子类特有的方法)
                          “看右边”：看的是子类的对象(实际运行的是子类重写父类的方法)

>**总结多态性：编译看左边，运行看右边**

```java
 正常的方法调用

Person e = new Person();

e.getInfo();

Student e = new Student();

e.getInfo();

 虚拟方法调用 (多态情况下) 

子类中定义了与父类同名同参数的方法，在多态情况下，将此时父类的方法称为虚拟方法，父

类根据赋给它的不同子类对象，动态调用属于子类的该方法。这样的方法调用在编译期是无法确定的。

Person e = new Student();

e.getInfo();

//调用Student类的getInfo()方法

 编译时类型和运行时类型

编译时e为Person类型，而方法的调用是在运行时确定的，所以调用的是Student类 

的getInfo()方法。——动态绑定
```

4.多态性使用的前提：

*   类的继承关系
*   方法的重写

#### 小结：方法的重载和重写

1. 二者的定义细节：略
2. 从编译和运行的角度看：
重载，是指允许存在多个同名方法，而这些方法的参数不同。编译器根据方法不
同的参数表，对同名方法的名称做修饰。对于编译器而言，这些同名方法就成了
不同的方法。它们的调用地址在编译期就绑定了。Java的重载是可以包括父类
和子类的，即子类可以重载父类的同名不同参数的方法。
所以：对于重载而言，在方法调用之前，编译器就已经确定了所要调用的方法，
这称为“早绑定”或“静态绑定”；
而对于多态，只有等到方法调用的那一刻，解释运行器才会确定所要调用的具体
方法，这称为“晚绑定”或“动态绑定”。
引用一句Bruce Eckel的话：“不要犯傻，如果它不是晚绑定，它就不是多态。”

##### 面试题

1.什么是方法的重写(override 或 overwrite)？
子类继承父类以后，可以对父类中同名同参数的方法，进行覆盖操作.

2. 应用：
重写以后，当创建子类对象以后，通过子类对象调用子父类中的同名同参数的方法时，实际执行的是子类重写父类的方法。

3.举例：
```java
class Circle{
public double findArea(){}//求面积
}
class Cylinder extends Circle{
public double findArea(){}//求表面积
}

class Account{
public boolean withdraw(double amt){}
}
class CheckAccount extends Account{
public boolean withdraw(double amt){}
}
```

***************

4.重写的规则：
```java
 方法的声明： 权限修饰符  返回值类型  方法名(形参列表) throws 异常的类型{

 *                              //方法体

 *                         }

 *         约定俗称：子类中的叫重写的方法，父类中的叫被重写的方法

 *         ① 子类重写的方法的方法名和形参列表与父类被重写的方法的方法名和形参列表相同

 *         ② 子类重写的方法的权限修饰符不小于父类被重写的方法的权限修饰符

 *         >特殊情况：子类不能重写父类中声明为private权限的方法

 *         ③ 返回值类型：

 *         >父类被重写的方法的返回值类型是void，则子类重写的方法的返回值类型只能是void

 *         >父类被重写的方法的返回值类型是A类型，则子类重写的方法的返回值类型可以是A类或A类的子类

 *         >父类被重写的方法的返回值类型是基本数据类型(比如：double)，则子类重写的方法的返回值类型必须是相同的基本数据类型(必须也是double)

 *         ④ 子类重写的方法抛出的异常类型不大于父类被重写的方法抛出的异常类型（具体放到异常处理时候讲）

 *   **********************************************************************

 *    子类和父类中的同名同参数的方法要么都声明为非static的（考虑重写，要么都声明为static的（不是重写)，static不能被子类重写。  
```

5.面试题：区分方法的重写和重载？
```java
答：
① 二者的概念：
② 重载和重写的具体规则
③ 重载：不表现为多态性。
重写：表现为多态性。
重载，是指允许存在多个同名方法，而这些方法的参数不同。编译器根据方法不同的参数表，对同名方法的名称做修饰。对于编译器而言，这些同名方法就成了不同的方法。它们的调用地址在编译期就绑定了。Java的重载是可以包括父类和子类的，即子类可以重载父类的同名不同参数的方法。
所以：对于重载而言，在方法调用之前，编译器就已经确定了所要调用的方法，这称为“早绑定”或“静态绑定”；
而对于多态，只等到方法调用的那一刻，解释运行器才会确定所要调用的具体方法，这称为“晚绑定”或“动态绑定”。 
引用一句Bruce Eckel的话：“不要犯傻，如果它不是晚绑定，它就不是多态。”

```

#### 关键字super
1.super 关键字可以理解为：父类的
2.可以用来调用的结构：属性、方法、构造器
3.super调用属性、方法：

3.1 我们可以在子类的方法或构造器中。通过使用"super.属性"或"super.方法"的方式，显式的调用父类中声明的属性或方法。但是，通常情况下，我们习惯省略"super."

3.2 特殊情况：当子类和父类中定义了同名的属性时，我们要想在子类中调用父类中声明的属性，则必须显式的使用"super.属性"的方式，表明调用的是父类中声明的属性。

3.3 特殊情况：当子类重写了父类中的方法以后，我们想在子类的方法中调用父类中被重写的方法时，则必须显式的使用"super.方法"的方式，表明调用的是父类中被重写的方法。

4.super调用构造器：
4.1  我们可以在子类的构造器中显式的使用"super(形参列表)"的方式，调用父类中声明的指定的构造器

4.2 "super(形参列表)"的使用，必须声明在子类构造器的首行！

4.3 我们在类的构造器中，针对于"this(形参列表)"或"super(形参列表)"只能二一，不能同时出现

4.4 在构造器的首行，没显式的声明"this(形参列表)"或"super(形参列表)"，则默认调用的是父类中空参的构造器：super()

4.5 在类的多个构造器中，至少一个类的构造器中使用了"super(形参列表)"，调用父类中的构造器

**思考：**
1).为什么super(…)和this(…)调用语句不能同时在一个构造器中出现？
因为super()和this()都只能出现在首行
2).为什么super(…)或this(…)调用语句只能作为构造器中的第一句出现？
无论通过哪个构造器创建子类对象，需要保证先初始化父类
目的：当子类继承父类后，“继承”父类中所有的属性和方法，因此子类有必要知道父类如何为对象进行初始化

####  子类对象实例化全过程
理解即可。
1.从结果上看：继承性
> 子类继承父类以后，就获取了父类中声明的属性或方法。

> 创建子类的对象，在堆空间中，就会加载所父类中声明的属性。

2.从过程上看：
当我们通过子类的构造器创建子类对象时，我们一定会直接或间接的调用其父类的构造器，进而调用父类的父类的构造器，...直到调用了java.lang.Object类中空参的构造器为止。正因为加载过所的父类的结构，所以才可以看到内存中父类中的结构，子类对象才可以考虑进行调用。
图示：
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201114160202.png)
3.强调说明：
虽然创建子类对象时，调用了父类的构造器，但是自始至终就创建过一个对象，即为new的子类对象。
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201114160242.png)

#### 面向对象的特征三：多态性
1.多态性的理解：可以理解为一个事物的多种形态。
2.何为多态性：
对象的多态性：父类的引用指向子类的对象（或子类的对象赋给父类的引用）
举例：
Person p = new Man();
Object obj = new Date();
3.多态性的使用：虚拟方法调用
> 有了对象的多态性以后，我们在编译期，只能调用父类中声明的方法，但在运行期，我们实际执行的是子类重写父类的方法。
> 总结：编译，看左边；运行，看右边。
> 4.多态性的使用前提：
> ① 类的继承关系  ② 方法的重写
```java
5.多态性的应用举例：
举例一：
	public void func(Animal animal){//Animal animal = new Dog();
		animal.eat();
		animal.shout();
	}
举例二：
public void method(Object obj){ }
举例三：
class Driver{
	
	public void doData(Connection conn){//conn = new MySQlConnection(); / conn = new OracleConnection();
		//规范的步骤去操作数据
	conn.method1();
	conn.method2();
	conn.method3();
	}
}
```
6.多态性使用的注意点：
对象的多态性，只适用于方法，不适用于属性（编译和运行都看左边）

************************************************************
#### 关于向上转型与向下转型：
7.1 向上转型：多态
7.2 向下转型：
7.2.1 为什么使用向下转型：
有了对象的多态性以后，内存中实际上是加载了子类特有的属性和方法的，但是由于变量声明为父类类型，导致编译时，只能调用父类中声明的属性和方法。子类特有的属性和方法不能调用。如何才能调用子类特的属性和方法？使用向下转型。
7.2.2 如何实现向下转型：
使用强制类型转换符：()
7.2.3 使用时的注意点：
① 使用强转时，可能出现ClassCastException的异常。
② 为了避免在向下转型时出现ClassCastException的异常，我们在向下转型之前，先进行instanceof的判断，一旦返回true，就进行向下转型。如果返回false，不进行向下转型。
**7.2.4 instanceof的使用：**
① a instanceof A:判断对象a是否是类A的实例。如果是，返回true；如果不是，返回false。
② 如果 a instanceof A返回true,则 a instanceof B也返回true.其中，类B是类A的父类。
③ 要求a所属的类与类A必须是子类和父类的关系，否则编译错误。
7.2.5 图示：
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201114161629.png)

#### 面试题：
8.1 谈谈你对多态性的理解？
① 实现代码的通用性。
② Object类中定义的public boolean equals(Object obj){  }
  JDBC:使用java程序操作(获取数据库连接、CRUD)数据库(MySQL、Oracle、DB2、SQL Server)
③ 抽象类、接口的使用肯定体现了多态性。（抽象类、接口不能实例化）
8.2 多态是编译时行为还是运行时行为？

#### 练习思考
1.若子类重写了父类的方法，就意味着子类里定义的方法彻底覆盖了父类里的同名方法，系统将不可能把父类里的方法转移到子类中：编译看左边，运行看右边

2.对于实例变量则不存在这样的现象，即使子类里定义了与父类完全相同的实例变量，这个实例变量依然不可能覆盖父类中定义的实例变量：编译运行都看左边

### Object类结构剖析

###### 面试题：== 和 equals( )区别

1. 回顾 == 的使用：== （运算符）
1). 可以使用在基本数据类型变量和引用数据类型变量中
2). 如果比较的是基本数据类型变量：
    比较两个变量保存的数据值是否相等.(不一定类型要相同)
    如果比较的是引用数据类型变量：比较两个对象的地址值是否相同，即两个引用是否指向同一个对象实体

2. equals( )方法的使用
 1). 是一个方法，非运算符
     2). 只能适用于引用数据类型
     3). Object类中equals( )的定义：
    
```java
public boolean equals(Object obj) {   return (this == obj);  } 
```
说明：Object类中定义的equals( ) 和 ==的作用是相同的：比较两个对象的地址是否相同，即两个引用是否指向同一块内存空间或(同一个内存地址)。

4. 像String，Date，File，包装类等都重写了Object类中的equals( )方法。重写以后，比较的不是两个引用的地址是否相同，而是比较两个对象的“属性内容”是否相同

5.补充：==符号使用时，必须保证符号左右两边的变量类型一致 

* String底层equals( )方法重写代码
```java
public boolean equals(Object anObject) {
        if (this == anObject) {
            return true;
        }
        if (anObject instanceof String) {
            String anotherString = (String)anObject;
            int n = value.length;
            if (n == anotherString.value.length) {
                char v1[] = value;
                char v2[] = anotherString.value;
                int i = 0;
                while (n-- != 0) {
                    if (v1[i] != v2[i])
                        return false;
                    i++;
                }
                return true;
            }
        }
        return false;
    }
```

* 自己重写Customer类的equals( )方法
```java
public boolean equals(Object obj){
if(this == obj) return true;
if(obj instanceof Customer){
Customer cust = (Customer)obj;
return this.age == cust.age && this.name.equals(cust.name);
}else{ return false;}}
```

* 面试题：== 和 equals的区别
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201116194110.png)

* 重写equals( )方法的原则
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201116194612.png)
练习题
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201116194947.png)

##### Object类中toString()的使用

* 当我们输出一个对象的引用时，实际就是调用当前对象的toString()方法
```java
public void println(Object x) {
        String s = String.valueOf(x);
        synchronized (this) {
            print(s);
            newLine();
        }
    }
public static String valueOf(Object obj) {
        return (obj == null) ? "null" : obj.toString();
    }
```
* Object类中toString( )定义
```java
public String toString() {
        return getClass().getName() + "@" + Integer.toHexString(hashCode());
    }
```

* 像String，Date，File，包装类等都重写了Object类中的toString( )方法， 使得在调用对象的toString()时，返回“实体内容”信息
* 自定义类也可以重写toString( )方法，当调用此方法时，返回对象的“实体内容”

**总结：基本类型，包装类与String类间的相互转换**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201117103155.png)

##### 关键字：static
>某些特定的数据在内存区域只存在一份

* static：静态的
* static可以用来修饰：属性，方法，代码块，内部类
* 使用static修饰属性：静态变量
    * 属性，按是否使用static修饰，又分为：静态属性  VS  非静态属性(实例变量)
    * 实例变量：我们创建了类的多个对象，每个对象都独立的拥有一套类中的非静态属性。当修改其中一个对象中的非静态属性时，不会导致其它对象中同样的属性值修改
    * 静态变量：我们创建了类的多个对象，多个对象共享同一个静态变量。当通过某一个对象修改静态变量时，会导致其它的对象调用此静态变量时，是修改过了的

* static修饰属性的其他说明：
    * 静态变量随着类的加载而加载，可以通过”类.静态变量“的方式进行调用
    * 静态变量的加载要早于对象的创建
    * 由于类只会加载一次，则静态变量在内存中y也只会存在一份：存在方法区中的静态域中
* 使用static修饰方法：静态方法
    * 随着类的加载而加载，可以通过”类.静态方法“的方式进行调用
    * 静态方法中，只能调用静态的方法或属性  （从生命周期角度出发）
    * 非静态方法中，既可以调用非静态的方法或属性，也可以调用静态的方法或属性
* static 注意点：
    * 在静态的方法内，不能使用this关键字，super关键字
    * 关于静态属性和静态方法的使用，大家都从生命周期的角度去理解
*  开发中，如何确定一个属性是否要声明为static？
    *  属性是可以被多个对象所共享的，不会随着对象的不同而不同的
    *  类中的常量也常常声明为static
*  开发中，如何确定一个方法是否要声明为static？
    *  操作静态属性的方法，通常设置为static的
    *  工具类中的方法，习惯上声明为static的。比如：Math，Arrays，Collections
    
* 单例（Singleton）设计模式

        所谓类的单例设计模式，就是采取一定的方法保证在整个的软件系统中，对 
        某个类只能存在一个对象实例，并且该类只提供一个取得其对象实例的方法。 
        如果我们要让类在一个虚拟机中只能产生一个对象，我们首先必须将类的构 
        造器的访问权限设置为private，这样，就不能用new操作符在类的外部产生 
        类的对象了，但在类内部仍可以产生该类的对象。因为在类的外部开始还无 
        法得到类的对象，只能调用该类的某个静态方法以返回类内部创建的对象， 
        静态方法只能访问类中的静态成员变量，所以，指向类内部产生的该类对象 
        的变量也必须定义成静态的。

* 饿汉式单例模式
```java
class Singleton{
//1. 私有构造器
private Singleton(){}

//2. 内部提供一个当前类的实例
//4.此实例也必须静态化
private static Singleton single = new Singleton();

//3.提供公共的静态方法，返回当前类的对象
public static Singleton getInstance(){
return single;}
}
```

* 懒汉式 (该单例线程不安全)
```java
class Singleton{
//1.私有化构造器
private Singleton(){}
//2. 内部提供一个当前类的实例
//4. 此实例也必须是静态化的
private static Singleton single;
//3. 提供公共的静态方法，返回当前类的对象
public static Singleton getInstance(){
if(single == null){ single = new Singleton(); }
return single;
}
}
```

* 区分饿汉式和懒汉式
    * 饿汉式：
        * 坏处：对象加载时间长
        * 好处：饿汉式是线程安全的
    * 懒汉式
        * 好处：延迟对象的创建
        * 坏处：线程不安全(多线程内容时，不安全性可以消除)
* 单例设计模式的优点
  
        由于单例模式只生成一个实例，减少了系统性能开销，当一个对象的
        产生需要比较多的资源时，如读取配置、产生其他依赖对象时，则可
        以通过在应用启动时直接产生一个单例对象，然后永久驻留内存的方
        式来解决。

*   单例(Singleton)设计模式--应用场景
* 网站的计数器，一般也是单例模式实现，否则难以同步。 
* 应用程序的日志应用，一般都使用单例模式实现，这一般是由于共享的日志 
文件一直处于打开状态，因为只能有一个实例去操作，否则内容不好追加。 
*  数据库连接池的设计一般也是采用单例模式，因为数据库连接是一种数据库 
资源。 
* 项目中，读取配置文件的类，一般也只有一个对象。没有必要每次使用配置 
文件数据，都生成一个对象去读取。 
* Application 也是单例的典型应用 
* Windows的Task Manager (任务管理器)就是很典型的单例模式 
* Windows的Recycle Bin (回收站)也是典型的单例应用。在整个系统运行过程 
中，回收站一直维护着仅有的一个实例。

##### 浅析Java中static修饰符
>https://www.cnblogs.com/zoe15/p/5370108.html
```java
1、概述

　　static关键字的中文意思是静态的，该修饰符可以修饰字段、方法、内部类。使用该关键字修饰的内容，在面向对象中static修饰的内容是隶属于类，而不是直接隶属于对象的，所以static修饰的成员变量一般称作类成员变量，而static修饰的方法一般称作类方法。

2、static修饰符的特点

　　1)static修饰的成员(字段/方法),随着所在类的加载而加载。当JVM把字节码加载斤JVM的时候,static修饰的成员已经在内存中存在了

　　2)优先于对象的存在，对象是我们手动通过new关键字创建出来的。

　　3)satic修饰的成员被该类型的所有对象所共享。根据该类创建出来的任何对象，都可以访问static成员。 分析:表面上通过对象去访问static成员,其本质依然使用类名访问,和对象没有任何关系(通过反编译可以看到)。

　　4)直接使用类名访问static成员 ，因为static修饰的成员直接属于类，不属于对象，所以可以直接使用类名访问static成员。

3、类成员和实例成员的访问

　　1)类成员：使用static修饰的成员，直接属于类，可以通过类来访问static字段和static方法

　　2)实例成员：没有使用static修饰的成员，只属于对象，通过对象来访问非static字段和非static方法(对象其实可以访问类成员，但是底层依然使用类名访问的)

　　3)static方法中：只能调用static成员

　　4)非static方法：可以访问静态成员，也可以访问实例成员

4、什么时候定义成static的字段和方法

　　如果这个一个状态或行为属于整个事物(类)，就直接使用static修饰，被所有对象所共享。 在开发中，往往把工具方法使用static修饰。如果不使用static修饰,则这些方法属于该类的对象，我们得先创建对象再调用方法，在开发中工具对象只需要一份即可，可能创建N个对象，此时我们往往把该类设计为单例的，但还是有点麻烦。所以，一般在开发中设计工具方法，为了调用简单，我们使用static修饰。

5、类成员的使用

　　1)利处：对对象的共享数据进行单独空间的存储，节省空间，没有必要每一个对象中都存储一份，可以直接被类名调用。

　　2)弊端：生命周期过长。
```
##### Java中static的含义和用法
>https://www.cnblogs.com/liuguoguo/p/8525220.html
```java
Java中static的含义和用法
static:静态的，用于修饰成员(成员变量，成员方法);

1.被static所修饰的变量或者方法会储存在数据共享区;

2.被static修饰后的成员变量只有一份！

3.当成员被static修饰之后，就多了一种访问方式，除了可以被对象调用之外，还可以直接

被类名调用，(类名.静态成员);

4.static的特点：

1.随着类的加载而被加载;

2.优先于对象存在;

3.被所有对象共享;

5.被static修饰的变量成为静态变量(类变量)或者实例变量;

6.存放位置

1.类变量随着类的加载而存在于date内存区;

2.实例变量随着对象的建立而存在于堆内存;

7.生命周期：

1.类变量周期生命最长，随着类的消失而消失;

2.实例变量生命周期比类变量短，它是随着对象的消失而消失;

8.方法注意事项：

1.静态的方法只能访问静态的成员;

2.非静态得方法即能访问静态得成员(成员变量，成员方法)又能访问非静态得成员;

3.局部变量不能被static修饰;

4.静态得方法中是不可以定义this、super关键字的，因为静态优先于对象存在，所以静态方法不可以出this;

9.什么时候使用static修成员：

当属于同一个类的所有对象出现共享数据时,就需要将存储这个共享数据的成员用static修饰;

10.什么时候使用static修饰方法：

当功能内部没有访问到非静态的成员时（对象特有的数据）那么该功能可以定义成静态的;
Example:
class Examples{
　　String name;
　　//当属于同一个类的所有对象出现共享数据时,就需要将存储这个共享数据的成员用static修饰;
　　static String country;
//当功能内部没有访问到非静态的成员时（对象特有的数据）那么该功能可以定义成静态的;
　　static void print(){
　　　　System.out.println("你好"+country);
　　}
//当功能内部有访问到非静态的成员时（对象特有的数据）那么该功能就不可以定义成静态的;
　　void print1(){
　　System.out.println("你好"+name);
　　}
}
public class Test{
　　public static void main(String[] args){
　　　　Examples One = new Examples();
　　　　Examples Tow = new Examples();
　　　　Examples.country = "中国";
　　　　One.name = "小明";
　　　　//One.country = "中国";
　　　　Tow .name = "小花";
　　　　//Tow .country = "中国";
　　　　//类名.静态方法名
　　　　Examples.print();
　　　　One.print1();
　　}
}
```
### 类的成员之四：代码块(或初始化块)
1. 代码块的作用：用来初始化类，对象
2. 代码块如果有修饰的话，只能使用static

#### 分类：静态代码块 VS 非静态代码块

* 静态代码块
    * 内部可以有输出语句
    * 随着类的加载而执行，而且只执行一次
    * 作用：初始化类的信息
    * 如果一个类中定义了多个静态代码块，则按照声明的先后顺序执行
    * 静态代码块的执行要优先于非静态的代码块执行
    * 静态代码块内只能调用静态的属性，静态的方法，不能调用非静态的结构


* 非静态代码块
    * 内部可以有输出语句
    * 随着对象的创建而执行
    * 每创建一个对象，就执行一次非静态代码块
    * 作用：可以在创建对象时，对对象的属性等进行初始化
    * 如果一个类定义了多个非静态代码块，则按照声明的先后顺序执行
    * 非静态代码块内可以调用静态的属性，静态的方法，或非静态的属性，非静态的方法


* 对属性可以赋值的位置
    * 默认初始化
    * 显示初始化
    * 构造器中初始化
    * 有了对象以后，可以通过“对象.属性”或“对象.方法”的方式进行赋值
    * 在代码块中赋值   
* 属性执行顺序
    * 1.  默认初始化
    * 2. 显示初始化  / 3. 代码块中赋值
    * 3. 构造器中初始化
    * 4. 有了对象以后，可以通过“对象.属性”或“对象.方法”的方式进行赋值
* java变量的初始化顺序
    * (静态变量、静态初始化块) >（变量、初始化块）> 构造器   

### 关键字:final
final：最终的

* final 可以用来修饰的结构：类，方法，变量
* final 用来修饰一个类：此类不能被其它类所继承
    * 比如：String类，System类，StringBuffer类
* final 用来修饰方法：表明此方法不能被重写
    * 比如：Object类中的getClass（）方法    
* final 用来修饰变量：此时的"变量"就称为是一个常量
    * final 修饰属性：可以考虑赋值的位置有：显示初始化，代码块中初始化，构造器中初始化
    * final修饰局部变量：
        * 尤其是使用final修饰形参时，表明此形参是一个常量。当我们调用此方法时，给常量形参赋值一个实参，一旦赋值以后，就只能在方法体内使用此形参，但不能进行重新赋值
* static final 用来修饰属性：全局常量

### abstract关键字的使用

* abstract：抽象的
* abstract可以用来修饰的结构：类，方法
* abstract修饰类：抽象类
    * 此类不能实例化
    * 抽象类中一定有构造器，便于子类实例化时调用(涉及：子类对象实例化的全过程)
    * 开发中，都会提供抽象类的子类，让子类对象实例化，完成相关操作
    
* abstract修饰方法：抽象方法
    * 抽象方法只有方法的声明，没有方法体
    * 包含抽象方法的类，一定是一个抽象类，反之，抽象类中可以没有抽象方法的
    * 若子类重写了父类中的所有抽象方法后，此子类方可实例化
    * 若子类没有重写父类中所有的抽象方法，此子类也是一个抽象类，需要使用abstract修饰   

### 接口的使用

* 接口使用interface来定义
* Java中，接口和类是并列的两个结构
* 如何定义接口：定义接口中的成员
    * JDK7及以前：只能定义全局常量和抽象方法
        * 全局常量：public static final的，但是书写时，可以省略不写
        * 抽象方法：public abstract
    * JDK8.0：除了定义全局常量和抽象方法之外，还可以定义静态方法，默认方法         
* 接口中不能定义构造器，意味着j接口不可以实例化
* Java中，接口通过类的实现(implements)的方式来使用
    * 如果实现类覆盖了接口中所有的抽象方法，则此实现类就可以实例化
    * 如果实现类没有覆盖接口中所有的抽象方法，则此实现类仍为一个抽象类
* Java类可以实现多个接口  --->   弥补了Java单继承性的局限性
    * 格式：class AA extends BB implements CC，DD，EE
* 接口与接口之间可以继承，而且可以多继承 
* 接口的具体使用，体现多态性
* 接口，实际上可以看做成是一种规范    

### java中final，finally，finalize的区别与用法
>相关博客链接：https://www.cnblogs.com/smart-hwt/p/8257330.html

### 成员内部类的理解
>有关内部类博客链接(超A的)：https://blog.51cto.com/android/384844
>CSDN博客链接：https://blog.csdn.net/WuchangI/article/details/79182850                                         


* 作为外部类的成员：
    * 可以调用外部类的结构
    * 可以被static修饰
    * 可以被4种不同的权限修饰符修饰
* 作为一个类：
    * 类内可以定义属性，方法，构造器等
    * 可以被final修饰，表示此类不能被继承(言外之意，不使用final，就可以被继承)
    * 可以被abstract修饰

**如何实例化成员内部类的对象**
* 在Person类中创建Dog类的实例(静态成员内部类)
```java
Person.Dog dog = new Person.Dog();
dog.show();
```
* 在Person类中创建Dog类的实例(非静态的成员内部类)
```java
Person p = new Person();
Person.Bird bird = p.new Bird();
```
注意：

* 接口中定义的静态方法，只能通过接口来调用
* 通过实现类的对象，可以调用接口中的默认方法
* 如果实现类重写了接口中默认方法，调用时，仍然调用的是重写以后的方法
* 如果子类(或实现类)继承的父类和实现的接口中声明了同名同参数的默认方法，那么子类在没有重写此方法的情况下，默认调用的是父类中同名同参数的方法 -----> 类优先原则
* 如果实现类实现了多个接口，而这多个接口中定义了同名同参数的默认方法，这就需要我们必须在实现类中重写此方法
* 如何在子类(或实现类)的方法中调用父类，接口中被重写的方法
* super.父类的方法名：调用的是父类声明的
* 接口类.super.方法名：调用的是接口中被重写的方法


        Java中用static修饰符修饰的方法被称为静态方法，本文我们来看看Java中static静态方法的用法特点。Java的static静态方法是属于整个类的类方法。不用static修饰符限定的方法，是属于某个具体类对象的方法。static方法使用特点如下：（
        1）引用这个方法时，可以使用对象名做前缀，也可以使用类名做前缀；
        （2）static方法不能被覆盖，也就是说，这个类的子类，不能有相同名、相同参数的方法；
        （3）static方法只能访问static方法，不能访问非static方法，但非static方法可以访问static方法；
        （4）static方法只能访问static数据成员，不能访问非static数据成员，但非static方法可以访问static数据成员；
        （5）main方法是静态方法。在Java的每个Application程序中，都必须有且只能有一个main方法，它是Application程序运行的入口点。
        （6）static方法是属于整个类的，它在内存中的代码段将随着类的定义而分配和装载。而非static的方法是属于某个对象的方法，在这个对象创建时，在对象的内存中拥有这个方法的专用代码段； 

### Java异常处理的抓抛模型
* ”抛“：程序在正常执行的过程中，一旦出现异常，就会在异常代码处生成一个对应的异常类对象，并将此对象抛出
    * 一旦抛出对象后，其后的代码就不再执行
    * 关于异常对象的产生：
        * 系统自动生成的异常对象
        * 手动的生成一个异常对象，并抛出（throw）
* ”抓“：可以理解为异常的处理方式：
    * try-catch-finally
    * throws
* 异常处理方式
    * try-catch-finally
* 使用说明：
```java
try{
 *      //可能出现异常的代码
 *}catch(异常类型1 变量名1){
 *      //处理异常的方式1
 * }catch(异常类型2 变量名2){
 *      //处理异常的方式2
 * }catch(异常类型3 变量名3){
 *      //处理异常的方式3
 * }
 * ....
 * finally{
 *      //一定会执行的代码
 * }
```
* 说明    
  
     * 1. finally是可的。

     * 2. 使用try将可能出现异常代码包装起来，在执行过程中，一旦出现异常，就会生成一个对应异常类的对象，根据此对象的类型，去catch中进行匹配

     * 3. 一旦try中的异常对象匹配到某一个catch时，就进入catch中进行异常的处理。一旦处理完成，就跳出当前的try-catch结构（在没写finally的情况。继续执行其后的代码

     * 4. catch中的异常类型如果没子父类关系，则谁声明在上，谁声明在下无所谓。

     *    catch中的异常类型如果满足子父类关系，则要求子类一定声明在父类的上面。否则，报错

     * 5. 常用的异常对象处理的方式： ① String  getMessage()    
    ② printStackTrace()

     * 6. 在try结构中声明的变量，再出了try结构以后，就不能再被调用

     * 7. try-catch-finally结构可以嵌套
    
* 总结：如何看待代码中的编译时异常和运行时异常？
   * 体会1：使用try-catch-finally处理编译时异常，是得程序在编译时就不再报错，但是运行时仍可能报错。相当于我们使用try-catch-finally将一个编译时可能出现的异常，延迟到运行时出现。

   * 体会2：开发中，由于运行时异常比较常见，所以我们通常就不针对运行时异常编写try-catch-finally了。针对于编译时异常，我们说一定要考虑异常的处理。

2.2：finally的再说明：
 * 1.finally是可的

 * 2.finally中声明的是一定会被执行的代码。即使catch中又出现异常了，try中return语句，catch中return语句等情况。

 * 3.像数据库连接、输入输出流、网络编程Socket等资源，JVM是不能自动的回收的，我们需要自己手动的进行资源的释放。此时的资源释放，就需要声明在finally中。



### 如何自定义异常类

* 继承于现有的异常结构：RuntimeException，Exception
* 提供全局常量：serialVersionUID
* 提供重载的构造器
```java
public class MyException extends Exception {  
static final long serialVersionUID = -3387516993124229947L; 
public MyException(){ }
public MyException(String msg){   super(msg);    }}
```
#### 比较throw和throws的区别
    throw:生成一个异常对象，并抛出 在使用方法的内部 <----> 自动抛出异常对象
    throws:处理异常的方式，使用在方法声明处的末尾 <----> try-catch-finally
        总结："上游排污，下游治污"

### 多线程
#### 基本概念：程序，进程，线程
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201128174633.png)
* 程序(program)是为完成特定任务、用某种语言编写的一组指令的集合。即指一
段静态的代码，静态对象。
* 进程(process)是程序的一次执行过程，或是正在运行的一个程序。是一个动态
  的过程：有它自身的产生、存在和消亡的过程。——生命周期
    * 如：运行中的QQ，运行中的MP3播放器
    * 程序是静态的，进程是动态的
    * 进程作为资源分配的单位，系统在运行时会为每个进程分配不同的内存区域
* 线程(thread)，进程可进一步细化为线程，是一个程序内部的一条执行路径。
    * 若一个进程同一时间并行执行多个线程，就是支持多线程的
    * 线程作为调度和执行的单位，每个线程拥有独立的运行栈和程序计数器(pc)，线程切换的开
    销小 
* 一个进程中的多个线程共享相同的内存单元/内存地址空间(堆和方法区) ->它们从同一堆中分配对象，可以访问相同的变量和对象。这就使得线程间通信更简便、高效。但多个线程操作共享的系统资源可能就会带来安全的隐患。
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201128184140.png)
* 内存结构
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201128184227.png)
进程可以细化为多个线程。
每个线程，拥有自己独立的：栈、程序计数器
多个线程，共享同一个进程中的结构：方法区、堆

#### 单核CPU和多核CPU的理解 
*  单核CPU，其实是一种假的多线程，因为在一个时间单元内，也只能执行一个线程 
的任务。例如：虽然有多车道，但是收费站只有一个工作人员在收费，只有收了费 
才能通过，那么CPU就好比收费人员。如果有某个人不想交钱，那么收费人员可以 
把他“挂起”（晾着他，等他想通了，准备好了钱，再去收费）。但是因为CPU时 
间单元特别短，因此感觉不出来。 
*  如果是多核的话，才能更好的发挥多线程的效率。（现在的服务器都是多核的） 
*  一个Java应用程序java.exe，其实至少有三个线程：main()主线程，gc() 
垃圾回收线程，异常处理线程。当然如果发生异常，会影响主线程。 
#### 并行与并发 
*  并行：多个CPU同时执行多个任务。比如：多个人同时做不同的事。 
*  并发：一个CPU(采用时间片)同时执行多个任务。比如：秒杀、多个人做同一件事。

#### 使用多线程的优点
> 背景：以单核CPU为例，只使用单个线程先后完成多个任务（调用多个方法），肯定比用多个线程来完成用的时间更短，为何仍需多线程呢？ 

* 多线程程序的优点： 
    1. 提高应用程序的响应。对图形化界面更有意义，可增强用户体验。 
    2. 提高计算机系统CPU的利用率 
    3. 改善程序结构。将既长又复杂的进程分为多个线程，独立运行，利于理解和修改

* 何时需要多线程
    * 程序需要同时执行两个或多个任务。 
    * 程序需要实现一些需要等待的任务时，如用户输入、文件读写 操作、网络操作、搜索等。 
    * 需要一些后台运行的程序时。
#### 线程的创建和使用
* Java语言的JVM允许程序运行多个线程，它通过java.lang.Thread类来体现。
* Thread类的特性：
    * 每个线程都是通过某个特定Thread对象的run()方法来完成操作的，经常把run()方法的主体称为线程体
    * 通过该Thread对象的start()方法来启动这个线程，而非直接调用run()

#### 测试Thread中的常用方法

* start()：启动当前线程，调用当前线程的run()；
* run()：通常需要重写Thread类中的此方法，将创建的线程要执行的操作声明在此方法中
* currntThread()：静态方法，返回执行当前代码的线程
* getName()：获取当前线程的名字
* setName()：设置当前线程的名字
* yield()：释放当前cup的执行权，线程让步
    * 暂停当前正在执行的线程，把执行机会让给优先级相同或更高的线程
    * 若队列中没有同优先级的线程，忽略此方法

网上说法：
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201201190557.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201201190355.png)

![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201201190830.png)
* join()：在线程a中调用线程b的join()，此时线程a进入阻塞状态，直到线程b完全执行完以后，线程a才结束阻塞状态
>join博客链接：https://blog.csdn.net/frankarmstrong/article/details/55504161?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-2.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-2.control
* * *
* sleep(long millitime)：让当前线程“睡眠”指定的millitime毫秒，在指定的millitime毫秒时间内，当前线程是阻塞状态
    * 令当前活动线程在指定时间段内放弃对CPU控制,使其他线程有机会被执行,时间到后重排队。
    * 抛出InterruptedException异常

* isAlive()：判断当前线程是否存活
#### 线程的调度
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201128154433.png)
#### 线程的优先级

* 线程的优先级等级
    * MAX_PRIORITY：10
    * MIN_PRIORITY：1
    * NORM_PRIORITY：5   --> 默认优先级
* 如何获取和设置当前线程的优先级：
    * getPriority() ：返回线程优先值
    * setPriority(int newPriority) ：改变线程的优先级
* 说明：
    * 高优先级的线程要抢占d低优先级线程cpu的执行权，但是只是从概率上讲，高优先级的线程高概率的情况下被执行，并不意味着只有当高优先级的线程执行完以后，低优先级的线程才执行

#### 比较创建线程的两种方式
* 开发中，优先选择：实现Runnable接口的方式
* 原因：
    * 实现的方式没有类的单继承性的局限性
    * 实现的方式更适合来处理多个线程有共享数据的情况

    * 联系: public class Thread implements Runnable
    * 相同点：两种方式都要重写run()方法，将线程要执行的逻辑声明在run()方法中  

#### 线程的生命周期
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201128193902.png)

#### 线程的同步
* 问题的提出
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201128194512.png)
#### "非线程安全"术语
    非线程安全：主要是指多个线程对同一个对象中的同一个实例变量进行操作时会出现值被更改，值不同步的情况，进而影响程序的执行流程

#### 线程的同步

* 问题的提出
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201129174038.png)

* 例题（模拟火车站售票程序，开启三个窗口售票）

```java
class Ticket implements Runnable {
private int tick = 100;
public void run() {
while (true) {
if (tick > 0) {
System.out.println(Thread.currentThread().getName() + "售出车票，tick号为：" + tick--);
} else
break; } } }
class TicketDemo {
public static void main(String[] args) {
Ticket t = new Ticket();
Thread t1 = new Thread(t);
Thread t2 = new Thread(t);
Thread t3 = new Thread(t);
t1.setName("t1窗口");
t2.setName("t2窗口");
t3.setName("t3窗口");
t1.start();
t2.start();
t3.start();
} }
```
**理想状态**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201129174333.png)
**极端状态**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201129174411.png)
共享代码增加个sleep()，执行效果更明显
```java
private int tick = 100;
public void run(){
while(true){
if(tick>0){
try{
Thread.sleep(10);
}catch(InterruptedException e){ e.printStackTrace();}
System.out.println(Thread.currentThread().getName()+“售出车票，tick号为：
"+tick--);
} } }

```
#### 多线程出现了安全问题
1. 问题的原因：
当多条语句在操作同一个线程共享数据时，一个线程对多条语句只执行了一部分，还没有执行完，另一个线程参与进来执行。导致共享数据的错误。
2. 解决办法：
对多条操作共享数据的语句，只能让一个线程都执行完，在执行过程中，其他线程不可以参与执行

**例子：创建三个窗口卖票，总票数为100张，使用实现Runnable接口的方式**
1. 问题：卖票过程中，出现了重票，错票  ---->   出现了线程安全问题
2. 问题出现的原因：当某个线程操作车票过程中，尚未完成时，其它线程也参与进来，也操作车票
3. 如何解决：
   * 当一个线程a在操作ticket的时候，其他线程不能参与进来，直到线程a操作完ticket时，其它线程才可以操作ticket，这种情况下即使线程a出现了阻塞，也不能被改变
4. 在java中，我们通过同步机制，来解决线程的安全问题  

* 同步分析原理
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201129193131.png)
* 方式一：同步代码块
```java
synchronized(同步监视器){
//需要被同步的代码
}
```
**说明：**
1. 操作共享数据的代码，即为需要被同步的代码
2. 共享数据：多个线程共同操作的变量，比如：ticket就是共享数据
3. 同步监视器，俗称：锁，任何一个类的对象都可以充当锁
    要求：多个线程必须共用同一把锁
   补充：在实现Runnable接口创建多线程的方式中，我们可以考虑使用this充当同步监视器
   说明：在继承Thread类创建多线程的方式中，慎用this充当同步监视器，可以考虑当前类(类.class)来充当同步监视器
   

 **避免雷区**

        synchronized后面括号里是类，如果线程进入，则线程在该类中所有操作不能进行，包括静态变量和静态方法，对于含有静态方法和静态变量的代码块的同步，通常使用这种方式

* 方式二：同步方法

```java
synchronized还可以放在方法声明中，表示整个方法为同步方法。
例如：
public synchronized void show (String name){ 
….
}
```
* 如果操作共享数据的代码完整的声明在一个方法中，我们不妨将此方法声明为同步的

5. **使用锁机制的好处**
* 同步的方式，解决了线程的安全问题
  **使用锁机制的弊端**
* 操作同步代码时，只有一个线程参与，其它线程等待，相当于是一个单线程的过程，效率低下

* * *


#### 同步机制中的锁
l. 同步锁机制： 同步机制中的锁
在《Thinking in Java》中，是这么说的：对于并发工作，你需要某种方式来防止两个任务访问相同的资源（其实就是共享资源竞争）。 防止这种冲突的方法
就是当资源被一个任务使用时，在其上加锁。第一个访问某项资源的任务必须锁定这项资源，使其他任务在其被解锁之前，就无法访问它了，而在其被解锁之时，另一个任务就可以锁定并使用它了。 
    2. synchronized的锁是什么？ 
Ø 任意对象都可以作为同步锁。所有对象都自动含有单一的锁（监视器）。
Ø 同步方法的锁：静态方法（类名.class）、非静态方法（this）
Ø 同步代码块：自己指定，很多时候也是指定为this或类名.class
3 注意：
Ø 必须确保使用同一个资源的多个线程共用一把锁，这个非常重要，否则就无法保证共享资源的安全
Ø 一个线程类中的所有静态方法共用同一把锁（类名.class），所有非静态方
法共用同一把锁（this），同步代码块（指定需谨慎）    

#### 同步范围

1、如何找问题，即代码是否存在线程安全？**（非常重要）**
（1）明确哪些代码是多线程运行的代码
（2）明确多个线程是否有共享数据
（3）明确多线程运行代码中是否有多条语句操作共享数据
2、如何解决呢？**（非常重要）**
对多条操作共享数据的语句，只能让一个线程都执行完，在执行过程中，其他线程不可以参与执行。即所有操作共享数据的这些语句都要放在同步范围中
3、切记：
1). 范围太小：没锁住所有有安全问题的代码
2). 范围太大：没发挥多线程的功能

#### 释放锁的操作
     当前线程的同步方法、同步代码块执行结束。
     当前线程在同步代码块、同步方法中遇到break、return终止了该代码块、
    该方法的继续执行。
     当前线程在同步代码块、同步方法中出现了未处理的Error或Exception，导
    致异常结束。
     当前线程在同步代码块、同步方法中执行了线程对象的wait()方法，当前线
    程暂停，并释放锁

 #### 不会释放锁的操作   

    线程执行同步代码块或同步方法时，程序调用Thread.sleep()、
    Thread.yield()方法暂停当前线程的执行
    线程执行同步代码块时，其他线程调用了该线程的suspend()方法将该线程
    挂起，该线程不会释放锁（同步监视器）。
    应尽量避免使用suspend()和resume()来控制线程

* 使用同步方法解决实现Runnable接口的线程安全问题
    * 关于同步方法的总结
    * 同步方法仍然涉及到同步监视器，只是不需要我们显示的声明
    * 非静态的同步方法，同步监视器是：this
    * 静态的同步方法，同步监视器是：当前类本身  
##### 谈谈你对同步代码块中同步监视器和共享数据的理解及各自要求
* 同步监视器：俗称锁
1）任何一个类的对象都可以充当锁
2）多个线程共用一把锁

* 共享数据
1）多个线程共同操作的数据，即为共享数据
2）需要使用同步机制将操作共享数据的代码包起来，不能包多了，也不能包少了
####  线程安全的单例模式之懒汉式
```java
效率较差
class Singleton {
private static Singleton instance = null;
private Singleton(){}
public static Singleton getInstance(){
//同步代码块
synchronized(Singleton.class){
if(instance == null){
instance=new Singleton();}}}
return instance;}
public class SingletonTest{
public static void main(String[] args){
Singleton s1=Singleton.getInstance();
Singleton s2=Singleton.getInstance();
System.out.println(s1==s2);
}}
```
```java
class Singleton {
private static Singleton instance = null;
private Singleton(){}
//同步方法
public static synchronized Singleton getInstance(){
if(instance == null){
instance=new Singleton();}}
return instance;}
public class SingletonTest{
public static void main(String[] args){
Singleton s1=Singleton.getInstance();
Singleton s2=Singleton.getInstance();
System.out.println(s1==s2);
```
```java

单例设计模式之懒汉式(线程安全)---效率高
class Singleton {
private static Singleton instance = null;
private Singleton(){}
public static Singleton getInstance(){
if(instance==null){
synchronized(Singleton.class){
if(instance == null){
instance=new Singleton();}
}
}
return instance;
}
}
public class SingletonTest{
public static void main(String[] args){
Singleton s1=Singleton.getInstance();
Singleton s2=Singleton.getInstance();
System.out.println(s1==s2);
}}

```
#### 线程的死锁问题
* 死锁
    * 不同的线程分别占用对方需要的同步资源不放弃，都在等待对方放弃自己需要的同步资源，就形成了线程的死锁
    * 出现死锁后，不会出现异常，不会出现提示，只是所有的线程都处于阻塞状态，无法继续
* 解决方法
    * 专门的算法、原则
    * 尽量减少同步资源的定义
    * 尽量避免嵌套同步

* 死锁demo-one

```java
package com.atguigu.线程.死锁;

/**
 * @author 布丁熊.菲特尼斯
 * @create 2020-11-30 10:18
 */
public class LockThread {
    public static void main(String[] args) {
        StringBuffer s1 = new StringBuffer();//线程安全
        StringBuffer s2 = new StringBuffer();

        //匿名内部类
        new Thread(){
            @Override
            public void run() {
                super.run();
                synchronized (s1){
                    s1.append("a");
                    s2.append("1");
                    try {
                        sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
                synchronized (s2){
                    s1.append("b");
                    s2.append("2");
                    System.out.println(s1);
                    System.out.println(s2);
                }
            }
        }.start();

        new Thread(new Runnable() {
            @Override
            public void run() {
                synchronized (s2){
                    s1.append("c");
                    s2.append("3");
                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
                synchronized (s1){
                    s1.append("d");
                    s2.append("4");
                    System.out.println(s1);
                    System.out.println(s2);
                }
            }
        }).start();
    }
}


```

* 死锁demo-two

```java
package com.atguigu.java;

class A {
	public synchronized void foo(B b) {
		System.out.println("当前线程名: " + Thread.currentThread().getName()
				+ " 进入了A实例的foo方法"); // ①
		try {
			Thread.sleep(200);
		} catch (InterruptedException ex) {
			ex.printStackTrace();
		}
		System.out.println("当前线程名: " + Thread.currentThread().getName()
				+ " 企图调用B实例的last方法"); // ③
		b.last();
	}

	public synchronized void last() {
		System.out.println("进入了A类的last方法内部");
	}
}

class B {
	public synchronized void bar(A a) {
		System.out.println("当前线程名: " + Thread.currentThread().getName()
				+ " 进入了B实例的bar方法"); // ②
		try {
			Thread.sleep(200);
		} catch (InterruptedException ex) {
			ex.printStackTrace();
		}
		System.out.println("当前线程名: " + Thread.currentThread().getName()
				+ " 企图调用A实例的last方法"); // ④
		a.last();
	}

	public synchronized void last() {
		System.out.println("进入了B类的last方法内部");
	}
}

public class DeadLock implements Runnable {
	A a = new A();
	B b = new B();

	public void init() {
		Thread.currentThread().setName("主线程");
		// 调用a对象的foo方法
		a.foo(b);
		System.out.println("进入了主线程之后");
	}

	public void run() {
		Thread.currentThread().setName("副线程");
		// 调用b对象的bar方法
		b.bar(a);
		System.out.println("进入了副线程之后");
	}

	public static void main(String[] args) {
		DeadLock dl = new DeadLock();
		new Thread(dl).start();
		dl.init();
	}
}

```
### Lock锁

3. Lock(锁)
```java
class A{
private final ReentrantLock lock = new ReenTrantLock();
public void m(){
lock.lock();
try{
//保证线程安全的代码;
}
finally{
lock.unlock();
}
}
}
```
**注意：如果同步代码有异常，要将unlock()写入finally语句块**


#### synchronized 与 Lock 的对比

1. Lock是显式锁（手动开启和关闭锁，别忘记关闭锁），synchronized是隐式锁，出了作用域自动释放
2. Lock只有代码块锁，synchronized有代码块锁和方法锁
3. 使用Lock锁，JVM将花费较少的时间来调度线程，性能更好。并且具有更好的扩展性（提供更多的子类）
4. 优先使用顺序：
Lock ---> 同步代码块（已经进入了方法体，分配了相应资源） --->  同步方法（在方法体之外）

解决线程安全问题的方式三：Lock锁   ---  JDK5.0新增
    
    面试题：synchronized 与 Lock的异同？
    相同点：二者都可以解决线程安全问题，实现多线程之间的同步
    不同点：synchronized机制在执行完相应的同步代码以后，自动的释放同步监视器
               Lock需要手动的启动同步(lock())，同时结束同步也需要手动的实现(unLock())


```java
package com.atguigu.线程.线程同步;

import java.util.concurrent.locks.ReentrantLock;

/**
 * @author 布丁熊.菲特尼斯
 * @create 2020-11-30 11:03
 */
public class Window implements Runnable {
    private int ticket = 100;//票数
    //1.实例化ReentrantLock
    private ReentrantLock lock = new ReentrantLock();
    @Override
    public void run() {
        while (true){
            try {
                //2. 调用锁定方法lock()
                lock.lock();
                if (ticket > 0){
                    Thread.sleep(100);
                    System.out.println(Thread.currentThread().getName() + ": 售票,票数: "+ticket);
                    ticket--;
                }else {
                    break;
                }
            } catch (InterruptedException e) {
                e.printStackTrace();
            } finally {
                //3.调用解锁方法：unlock()
                lock.unlock();
            }
        }
    }

    public static void main(String[] args) {
        Window w = new Window();
        Thread t1 = new Thread(w);
        Thread t2 = new Thread(w);
        Thread t3 = new Thread(w);
        t1.setName("窗口1");
        t2.setName("窗口2");
        t3.setName("窗口3");
        t1.start();
        t2.start();
        t3.start();
    }
}

```
#### 线程通信中涉及到的三个方法

* wait()：一旦执行此方法，当前线程进入阻塞状态，并释放同步锁
* notify()：一旦执行此方法，就会唤醒被wait的一个线程，如果有多个线程被wait，就唤醒优先级高的那个线程
* notifyAll()：一旦执行此方法，就会唤醒所有被wait的线程

说明：
1. wait()，notify()，notifyAll()三个方法必须使用在同步代码块或同步方法中
2. wait()，notify()，notifyAll()三个方法的调用者必须是同步代码块或同步方法中的同步监视器
   否则会出现“java.lang.IllegalMonitorStateException”异常
3. wait()，notify()，notifyAll()三个方法是定义在java.Lang.Object类中    

##### 多线程中wait方法和sleep方法的区别

* * *
一、共同点： 
1. 他们都是在多线程的环境下，都可以在程序的调用处阻塞指定的毫秒数，并返回。 
2. wait()和sleep()都可以通过interrupt()方法 打断线程的暂停状态 ，从而使线程立刻抛出InterruptedException。 
        如果线程A希望立即结束线程B，则可以对线程B对应的Thread实例调用interrupt方法。如果此刻线程B正在wait()、sleep ()、join()，则线程B会立刻抛出InterruptedException，在catch() {} 中直接return即可安全地结束线程。 
       需要注意的是，InterruptedException是线程自己从内部抛出的，并不是interrupt()方法抛出的。对某一线程调用 interrupt()时，如果该线程正在执行普通的代码，那么该线程根本就不会抛出InterruptedException。但是，一旦该线程进入到 wait()、sleep()、join()后，就会立刻抛出InterruptedException 。

二、不同点： 
      1. Thread类的方法：sleep(),yield()等 
           Object的方法：wait()和notify()等 
       2. 每个对象都有一个锁来控制同步访问。Synchronized关键字可以和对象的锁交互，来实现线程的同步。 sleep方法没有释放锁，而wait方法释放了锁，使得其他线程可以使用同步控制块或者方法。 
       3. wait，notify和notifyAll只能在同步控制方法或者同步控制块里面使用，而sleep可以在任何地方使用 
       4. sleep必须捕获异常，而wait()，notify()和notifyAll()不需要捕获异常
sleep()和wait()方法的最大区别是：
　　　　sleep()睡眠时，保持对象锁，仍然占有该锁；
　　　　而wait()睡眠时，释放对象锁。
　　      但是wait()和sleep()都可以通过interrupt()方法打断线程的暂停状态，从而使线程立刻抛出InterruptedException（但不建议使用该方法）。
sleep（）方法
      sleep()使当前线程进入停滞状态（阻塞当前线程），让出CUP的使用、目的是不让当前线程独自霸占该进程所获的CPU资源，以留一定时间给其他线程执行的机会;
　　 sleep()是Thread类的Static(静态)的方法；因此他不能改变对象的机锁，所以当在一个Synchronized块中调用Sleep()方法是，线程虽然休眠了，但是对象的机锁并木有被释放，其他线程无法访问这个对象（即使睡着也持有对象锁）。
　　在sleep()休眠时间期满后，该线程不一定会立即执行，这是因为其它线程可能正在运行而且没有被调度为放弃执行，除非此线程具有更高的优先级。 
wait（）方法
       wait()方法是Object类里的方法；当一个线程执行到wait()方法时，它就进入到一个和该对象相关的等待池中，同时失去（释放）了对象的机锁（暂时失去机锁，wait(long timeout)超时时间到后还需要返还对象锁）；其他线程可以访问；
　　wait()使用notify或者notifyAlll或者指定睡眠时间来唤醒当前等待池中的线程。
　　wiat()必须放在synchronized block中，否则会在program runtime时扔出”java.lang.IllegalMonitorStateException“异常。

**额外补充：**
sleep和yield，虽然暂停了，但占着锁不释放；       
ii. 调用该线程的suspend挂起，同样不释放同步锁；
* * *
#### 经典例题：生产者/消费者问题

    生产者(Productor)将产品交给店员(Clerk)，而消费者(Customer)从店员处
    取走产品，店员一次只能持有固定数量的产品(比如:20），如果生产者试图
    生产更多的产品，店员会叫生产者停一下，如果店中有空位放产品了再通
    知生产者继续生产；如果店中没有产品了，店员会告诉消费者等一下，如
    果店中有产品了再通知消费者来取走产品。
    这里可能出现两个问题：
    生产者比消费者快时，消费者会漏掉一些数据没有取到。
    消费者比生产者快时，消费者会取相同的数据。

代码分析：
1. 是否是多线程问题？是，生产者线程，消费者线程
2. 是否有共享数据？是，店员（或产品）
3. 如何解决线程安全问题？同步机制，有三种方法
4. 是否涉及到线程通信？是

截图代码
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201130203104.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201130203128.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201130203148.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201130203202.png)
```java
package com.atguigu.线程.生产者和消费者demo;

/**
 * @author 布丁熊.菲特尼斯
 * @create 2020-11-30 19:03
 */

//代码逻辑点：货物和店员都是共享数据

//店员
class Clerk{
private static int goodsCount = 0;//共享的数据
    public void productGoods() {
            synchronized (this) {
                if (goodsCount < 20){
                    goodsCount++;
                    System.out.println(Thread.currentThread().getName() +":开始生产第"+ goodsCount+"个产品");
                    notify();//只要生产了一个产品,就唤醒消费者消费
                }else {
                    try {
                        wait();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
            }
    }

    public void consumeGoods() {
            synchronized (this) {
                if (goodsCount > 0){
                    System.out.println(Thread.currentThread().getName() + ":开始消费第" + goodsCount + "个产品");
                    goodsCount--;
                    notify();//只要消费了一个产品,就唤生产者生产
                }else {
                    try {
                        wait();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
            }

    }
}
//生产者
class Productor extends Thread{
    private Clerk clerk;
    public Productor(Clerk clerk){
        this.clerk = clerk;
    }
    @Override
    public void run() {
        System.out.println(getName() + ": 通知生产者开始生产...");
        while (true){
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            clerk.productGoods();
        }

    }
}
//消费者
class Consumer extends Thread{
        private Clerk clerk;
        public Consumer(Clerk clerk){
            this.clerk = clerk;
        }
    @Override
    public void run() {
        super.run();
        System.out.println(getName() + ": 通知消费者开始消费...");
        while (true){
            try {
                Thread.sleep(2000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            clerk.consumeGoods();
        }
    }
}

public class ProductTest {
    public static void main(String[] args) {
        Clerk clerk = new Clerk();
        Productor p = new Productor(clerk);
        Consumer c = new Consumer(clerk);
        p.setName("生产者1");
        c.setName("消费者1");
        p.start();
        c.start();
    }
}

```
#### JDK5.0新增线程创建方式
##### 实现Callable接口

自定义实现Callable接口时，必须指定泛型类，该泛型为返回值的类型。同时，每次创建线程都需要创建一个新的Callable接口的实现类
创建一个实现了Callable接口的类
重写类中call()方法
创建一个 FutureTask 对象，传入 Callable 类型的参数
以FutureTask实例为参数创建Thread对象
通过futureTask.get()方法可以获得返回值

* 与使用Runnable相比， Callable功能更强大些 
    * 相比run()方法，可以有返回值 
    * 方法可以抛出异常 
    * 支持泛型的返回值 
    * 需要借助FutureTask类，比如获取返回结果

```java
package com.atguigu.线程.实现Callable接口创建线程;

import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.FutureTask;

/**
 * @author 布丁熊.菲特尼斯
 * @create 2020-12-01 9:16
 * 创建线程的方式三: 实现Callable接口  ---- JDK 5.0新增
 */
//1.创建一个实现Callable接口的实现类
class mythread implements Callable<Integer>{

    //2.实现call方法，将此线程需要执行的操作声明在call()中
    @Override
    public Integer call() throws Exception {
         int sum = 0;
        for (int i = 1; i < 100 ; i++) {
            if (i % 2 == 0){
                System.out.println(i);
                sum += i;
            }
        }
        return sum;
    }
}


public class myThreadTest {
    public static void main(String[] args) {
        //3. 创建Callable接口实现类的对象
        mythread mythread = new mythread();
        //4. 将此Callable接口实现类的对象作为参数传递到FutureTask构造器中，创建FutureTask的对象
        FutureTask<Integer> fu =  new FutureTask<>(mythread);
        //5.将此FutureTask的对象作为参数传递到Thread类的构造器中，创建Thread对象，并调用start(),启动线程
        new Thread(fu).start();
        try {
            //6. 获取Callable中call()方法的返回值
            //get()返回值即为FutureTask构造器函数Callable实现类重写的call()的返回值
            Integer sum = fu.get();
            System.out.println("总和为: " + sum);
        } catch (InterruptedException e) {
            e.printStackTrace();
        } catch (ExecutionException e) {
            e.printStackTrace();
        }
    }
}
```
**从底层源码理解线程的创建和启动**
```java
        //3. 创建Callable接口实现类的对象
        mythread mythread = new mythread();
        //4. 将此Callable接口实现类的对象作为参数传递到FutureTask构造器中，创建FutureTask的对象
        FutureTask fu =  new FutureTask(mythread);  
        //5.将此FutureTask的对象作为参数传递到Thread类的构造器中，创建Thread对象，并调用start(),启动线程
        new Thread(fu).start();

源代码
/**
     * Allocates a new {@code Thread} object. This constructor has the same
     * effect as {@linkplain #Thread(ThreadGroup,Runnable,String) Thread}
     * {@code (null, null, gname)}, where {@code gname} is a newly generated
     * name. Automatically generated names are of the form
     * {@code "Thread-"+}<i>n</i>, where <i>n</i> is an integer.
     */
    public Thread() {
        init(null, null, "Thread-" + nextThreadNum(), 0);
    }

    /**
     * Allocates a new {@code Thread} object. This constructor has the same
     * effect as {@linkplain #Thread(ThreadGroup,Runnable,String) Thread}
     * {@code (null, target, gname)}, where {@code gname} is a newly generated
     * name. Automatically generated names are of the form
     * {@code "Thread-"+}<i>n</i>, where <i>n</i> is an integer.
     *
     * @param  target
     *         the object whose {@code run} method is invoked when this thread
     *         is started. If {@code null}, this classes {@code run} method does
     *         nothing.
     */
    public Thread(Runnable target) {
        init(null, target, "Thread-" + nextThreadNum(), 0);
    }
   
   当我们创建一个线程时，new Thread()或者new Thread(Runnable target)有参或者无参时，系统会默认为这个线程设置线程名--"Thread-nextThreadNum()",nextThreadNum()方法默认返回的初始值为“0”
   
  以上述代码FutureTask类为例， 当我们new thread(fu).start()；开始启动线程时，源代码分析如下
  
  /**
     * Causes this thread to begin execution; the Java Virtual Machine
     * calls the <code>run</code> method of this thread.
     * <p>
     * The result is that two threads are running concurrently: the
     * current thread (which returns from the call to the
     * <code>start</code> method) and the other thread (which executes its
     * <code>run</code> method).
     * <p>
     * It is never legal to start a thread more than once.
     * In particular, a thread may not be restarted once it has completed
     * execution.
     *
     * @exception  IllegalThreadStateException  if the thread was already
     *               started.
     * @see        #run()
     * @see        #stop()
     */
    public synchronized void start() {
        /**
         * This method is not invoked for the main method thread or "system"
         * group threads created/set up by the VM. Any new functionality added
         * to this method in the future may have to also be added to the VM.
         *
         * A zero status value corresponds to state "NEW".
         */
        if (threadStatus != 0)
            throw new IllegalThreadStateException();

        /* Notify the group that this thread is about to be started
         * so that it can be added to the group's list of threads
         * and the group's unstarted count can be decremented. */
        group.add(this);

        boolean started = false;
        try {
            start0();
            started = true;
        } finally {
            try {
                if (!started) {
                    group.threadStartFailed(this);
                }
            } catch (Throwable ignore) {
                /* do nothing. If start0 threw a Throwable then
                  it will be passed up the call stack */
            }
        }
    }
    
    虽然这个new thread(fu).start()是在main方法调用的，也就是在主线程 main启动的，但是这个run()方法是不为主线程main或者系统system调用的，它是由“he Java Virtual Machine calls the run method of this thread.”底层虚拟机VM调用的
    
   线程中run()方法源代码
   
     /**
     * If this thread was constructed using a separate
     * <code>Runnable</code> run object, then that
     * <code>Runnable</code> object's <code>run</code> method is called;
     * otherwise, this method does nothing and returns.
     * <p>
     * Subclasses of <code>Thread</code> should override this method.
     *
     * @see     #start()
     * @see     #stop()
     * @see     #Thread(ThreadGroup, Runnable, String)
     */
    @Override
    public void run() {
        if (target != null) {
            target.run();
        }
    }
    
    public class FutureTask<V> implements RunnableFuture<V> 
    
    public interface RunnableFuture<V> extends Runnable, Future<V> {
    /**
     * Sets this Future to the result of its computation
     * unless it has been cancelled.
     */
    void run();
}

因为FutureTask类实现了RunnableFuture接口
public class FutureTask<V> implements RunnableFuture<V> 
而RunnableFuture接口继承了Runnable, Future<V>接口（接口可以多继承）,FutureTask类也就实现了run()方法
        mythread mythread = new mythread();
        FutureTask fu =  new FutureTask(mythread);
        new Thread(fu).start();
而new new Thread(fu).start()线程启动，此时调用的方法是FutureTask类中重写的run()方法

FutureTask类中的run()方法源代码如下

 public void run() {
        if (state != NEW ||
            !UNSAFE.compareAndSwapObject(this, runnerOffset,
                                         null, Thread.currentThread()))
            return;
        try {
            Callable<V> c = callable;
            if (c != null && state == NEW) {
                V result;
                boolean ran;
                try {
                    result = c.call();
                    ran = true;
                } catch (Throwable ex) {
                    result = null;
                    ran = false;
                    setException(ex);
                }
                if (ran)
                    set(result);
            }
        } finally {
            // runner must be non-null until state is settled to
            // prevent concurrent calls to run()
            runner = null;
            // state must be re-read after nulling runner to prevent
            // leaked interrupts
            int s = state;
            if (s >= INTERRUPTING)
                handlePossibleCancellationInterrupt(s);
        }
    }
 源代码中：
  Callable<V> c = callable;  result = c.call();
  在执行run()方法中会调用 Callable接口中的抽象call()方法,该抽象方法可以向外抛异常，又因为 mythread mythread = new mythread();
  
  mythread类实现了Callable接口，由于java的多态性，c.call()执行的是Callable接口的实现类mythread类中的call()方法，并可以接收返回值result
  
 FutureTask类中run()方法源代码中：if (ran)   set(result);
 如果这个线程启动，已经调用了call()方法，就把这个返回值result保存起来，
 
 FutureTask中set()方法源代码如下
 /**
     * Sets the result of this future to the given value unless
     * this future has already been set or has been cancelled.
     *
     * <p>This method is invoked internally by the {@link #run} method
     * upon successful completion of the computation.
     *
     * @param v the value
     */
     
/** The result to return or exception to throw from get() */
    private Object outcome; // non-volatile, protected by state reads/writes
    protected void set(V v) {
        if (UNSAFE.compareAndSwapInt(this, stateOffset, NEW, COMPLETING)) {
            outcome = v;
            UNSAFE.putOrderedInt(this, stateOffset, NORMAL); // final state
            finishCompletion();
        }
    }
  因为c.call()是在FutureTask类中的run()方法调用的，所以这个返回值result是从FutureTask类中获取到的，即 object obj = fu.get();
  mythread mythread = new mythread();
  FutureTask fu =  new FutureTask(mythread);
  
  FutureTask类中的get()方法源代码如下：
  
  /**
     * @throws CancellationException {@inheritDoc}
     */
    public V get() throws InterruptedException, ExecutionException {
        int s = state;
        if (s <= COMPLETING)
            s = awaitDone(false, 0L);
        return report(s);
    }
  call()方法的结果值为 report(s)方法的返回值
  report(s)方法中的s参数为state，每当我们创建一个FutureTask类时，在构造器中state自动会赋值为NEW，即为 this.state = NEW
  FutureTask类中相关代码
  /**
     * The run state of this task, initially NEW.  The run state
     * transitions to a terminal state only in methods set,
     * setException, and cancel.  During completion, state may take on
     * transient values of COMPLETING (while outcome is being set) or
     * INTERRUPTING (only while interrupting the runner to satisfy a
     * cancel(true)). Transitions from these intermediate to final
     * states use cheaper ordered/lazy writes because values are unique
     * and cannot be further modified.
     *
     * Possible state transitions:
     * NEW -> COMPLETING -> NORMAL
     * NEW -> COMPLETING -> EXCEPTIONAL
     * NEW -> CANCELLED
     * NEW -> INTERRUPTING -> INTERRUPTED
     */
    private volatile int state;
    private static final int NEW          = 0;
    private static final int COMPLETING   = 1;
    private static final int NORMAL       = 2;
    private static final int EXCEPTIONAL  = 3;
    private static final int CANCELLED    = 4;
    private static final int INTERRUPTING = 5;
    private static final int INTERRUPTED  = 6;

/**
     * Creates a {@code FutureTask} that will, upon running, execute the
     * given {@code Callable}.
     *
     * @param  callable the callable task
     * @throws NullPointerException if the callable is null
     */
    public FutureTask(Callable<V> callable) {
        if (callable == null)
            throw new NullPointerException();
        this.callable = callable;
        this.state = NEW;       // ensure visibility of callable
    }

    /**
     * Creates a {@code FutureTask} that will, upon running, execute the
     * given {@code Runnable}, and arrange that {@code get} will return the
     * given result on successful completion.
     *
     * @param runnable the runnable task
     * @param result the result to return on successful completion. If
     * you don't need a particular result, consider using
     * constructions of the form:
     * {@code Future<?> f = new FutureTask<Void>(runnable, null)}
     * @throws NullPointerException if the runnable is null
     */
    public FutureTask(Runnable runnable, V result) {
        this.callable = Executors.callable(runnable, result);
        this.state = NEW;       // ensure visibility of callable
    }
    
   FutureTask类中report(s)方法源代码如下
        /**
     * Returns result or throws exception for completed task.
     *
     * @param s completed state value
     */
    @SuppressWarnings("unchecked")
    private V report(int s) throws ExecutionException {
        Object x = outcome;
        if (s == NORMAL)
            return (V)x;
        if (s >= CANCELLED)
            throw new CancellationException();
        throw new ExecutionException((Throwable)x);
    }
    将outcome值赋值给Object x，再将其返回，得到返回值的数据

```
##### Callable接口与Runnable接口的比较

    首先，Runnable和Callable都是接口
    Callable接口和Runnable接口的区别就是：
    Callable接口需要实现call方法，Runnable接口需要实现run方法；
    与此同时call方法还可以返回任何对象（因为在Callable接口中可以使用泛型），若不指定，JVM都会当作Object对象来处理，这样在代码中需要相应的类型转换。若指定了泛型的类型，则就不需要了
    
    Callable接口和Runnable接口的不同点有：
    ①.Runnable是自从java1.1就有了，而Callable是1.5之后才加上去的
    ②.Callable可以返回一个泛型类型V，而Runnable不能做到
    ③.Callable和Runnable都可以和Executors类（见下边）使用。然而Thread类只能使用Runnable
    ④.Callable可以抛出checked exception,而Runnable没有。
    
    用Executors来构建线程池步骤：
    1).可以调用Executors类中的静态方法newCachedThreadPool(必要时创建新线程，空闲线程会被保留60秒)来创建线程池也可以调用newFixedThreadPool方法创建固定数量的线程池等，返回一个实现了ExecutorService接口的ThreadPoolExecutor类或者是一个实现了ScheduledExecutorServiece接口的类对象。
    2).调用submit方法或者execute方法提交Runnable或Callable对象，返回一个Future（见下边）接口
    3).当不再需要线程池时，可以通过shutdown方法销毁 
    
    Future接口：常用与提取Callable执行的状态。主要方法有：
    ①get()，获得Callable的返回值
    ②cancel()，取消Callable的执行
    ③isDone()，判断是否已经完成
    ④isCanceled()，判断是否已经取消


​    

* * *
* 举例
    * **1. 实现Runnable接口例子**
```java
public class Demo1 {
 
    public static void main(String[] args) {
 
        //创建含有5个线程的线程池
        ExecutorService pool = Executors.newFixedThreadPool(5);
        
        //可以通过execute方法或者submit方法来提交任务
        pool.execute(new Task1());
        pool.submit(new Task2());
        
        //销毁
        pool.shutdown();
    }
}
 
//实现Runnable接口
class Task1 implements Runnable{
 
    @Override
    public void run() {
        //业务逻辑略
        System.out.println("Runnable-----Task1");
    }
}
 
class Task2 implements Runnable{
 
    @Override
    public void run() {
        //业务逻辑略
        System.out.println("Runnable-----Task2");
    }
}
```
    * **2. 实现Callable接口例子**

```java
public class Demo2 {
 
    public static void main(String[] args) {
 
        ExecutorService e=Executors.newFixedThreadPool(5);
        //调用submit方法提交任务
        //用Future接口接收
        Future f1=e.submit(new MyCallable());
        Future f2=e.submit(new MyCallable());
 
        try {
            //通过get方法来获取call返回的值
            System.out.println(f1.get());
            System.out.println(f2.get());
        } catch (InterruptedException e1) {
            e1.printStackTrace();
        } catch (ExecutionException e1) {
            e1.printStackTrace();
        }
 
        //销毁
        e.shutdown();
 
    }
}
 
class MyCallable implements Callable<String>{
 
    @Override
    public String call() throws Exception {
        //简单的返回一个字符串
        return "aaaaa";
    }
}
```

会很容易的发现，在实现Runnable接口的run方法中没有返回值，而实现Callable接口的call方法中又返回值而且可以通过get方法获取到

* * *
#### 线程池
    背景：经常创建和销毁、使用量特别大的资源，比如并发情况下的线程对性能影响很大。 
    1 思路：提前创建好多个线程，放入线程池中，使用时直接获取，使用完放回池中。可以避免              频繁创建销毁、实现重复利用。类似生活中的公共交通工具。
    2 好处：
    Ø 提高响应速度（减少了创建新线程的时间）
    Ø 降低资源消耗（重复利用线程池中线程，不需要每次都创建）
    Ø 便于线程管理
      corePoolSize：核心池的大小
      maximumPoolSize：最大线程数 
      keepAliveTime：线程没有任务时最多保持多长时间后会终止
      …


* * *
 ![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201202112706.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201202112820.png)
* * *



```java
class NumberThread implements Runnable{

    @Override
    public void run() {
        for(int i = 0;i <= 100;i++){
            if(i % 2 == 0){
                System.out.println(Thread.currentThread().getName() + ": " + i);
            }
        }
    }
}

class NumberThread1 implements Runnable{

    @Override
    public void run() {
        for(int i = 0;i <= 100;i++){
            if(i % 2 != 0){
                System.out.println(Thread.currentThread().getName() + ": " + i);
            }
        }
    }
}

public class ThreadPool {

    public static void main(String[] args) {
        //1. 提供指定线程数量的线程池
        ExecutorService service = Executors.newFixedThreadPool(10);
        ThreadPoolExecutor service1 = (ThreadPoolExecutor) service;
        //设置线程池的属性
//        System.out.println(service.getClass());
//        service1.setCorePoolSize(15);
//        service1.setKeepAliveTime();


        //2.执行指定的线程的操作。需要提供实现Runnable接口或Callable接口实现类的对象
        service.execute(new NumberThread());//适合适用于Runnable
        service.execute(new NumberThread1());//适合适用于Runnable

//        service.submit(Callable callable);//适合使用于Callable
        //3.关闭连接池
        service.shutdown();
    }

}
```

#### 线程池相关API     
>http://zchengb.xyz/2020/09/17/Thread%20in%20Java/

#### 有关线程同步：同步监视器、同步方法、同步锁、死锁博客
>https://blog.csdn.net/Lirx_Tech/article/details/50913520
>https://www.cnblogs.com/aspirant/p/8876670.html

#### 有关线程笔试题
1. 画图说明线程的生命周期，以及各状态切换使用到的方法等
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201128193902.png)
**2. 同步代码块中涉及到的同步监视器和共享数据，谈谈你对同步监视器和共享数据的理解，以及注意点**

* * *

* 同步监视器理解：监视器是控制对象并发访问的机制
* 监视器是一种概念/机制，不仅限于Java语言
    * “在并发编程中，监视器是一个旨在由多个线程安全使用的对象或模块”;
        正如每个读者都知道的那样，Java中的每个对象都是java.lang.Object的子类。 
        java人员以这样的方式创建了java.lang.Object，它具有使Java程序员能够将任何对象用         作监视器的特性和特性。

* 同步代码块的同步监视器监视器
                
        synchronized(同步监视器){
        //操作共享数据的代码   （不能包括多了，也不能包括少了）
        }
    
 * 同步方法的同步监视器
    * 同步非静态方法的同步监视器
        * 当前对象 this       
    * 同步静态方法的同步监视器
        * 当前类  类.class    
    
* 共享数据
    * 多个线程共同共享并操作的资源，也称临界资源      
    例如，每个对象都有一个等待队列，一个重新进入队列以及等待和通知方法，使其成为监视器;
    文章链接：
>https://www.itranslater.com/qa/details/2325744537852969984

* * *
3. sleep()和wait()区别
* 相同点：sleep()和wait()方法都是可以让线程进入阻塞状态，切换cup运行资源
* 不同点：
    * sleep(long millis)可以限定时间参数，在该时间过后，该线程又可以去争取cup资源；而wait（）则需要notify或者notifyAll方法对其唤醒，将其放入就绪等待队列，等待获取cup的控制权
    * sleep()方法是属于Java.lang.Thread类中的一个方法，而wait()方法是Object类下的方法
    * sleep()方法执行时，线程进入阻塞队列，释放cup资源但不释放锁资源，而wait()方法既释放锁资源又释放cup资源
    * wait()方法不属于线程，必须要放在同步代码块或者同步方法中才有效，通常与notify/notifyAll方法配套使用
    * 通常sleep()方法通常要与try-catch配套使用
    * wait用于锁机制，sleep不是，这就是为啥sleep不释放锁，wait释放锁的原因，sleep是线程的方法，跟锁没半毛钱关系，wait，notify,notifyall 都是Object对象的方法，是一起使用的，用于锁机制

4. 写一个线程安全的懒汉式
```java
public class Singleton{
private static Singleton instance = null;
private Singleton(){}
public static Singleton getInstance(){
if(instance == null){
synchronized(Singleton.class){
if(instance == null){
instance = new Singleton();
}
}
}
return instance;
}}
```

5. 创建多线程有哪几种方式  4种
* 继承Thread类
* 实现Runnable接口
* 实现Callable接口
* 利用线程池（响应速度提高了，提高了资源利用率，便于管理）

### 常用类
#### 理解String的不可变性
* String的特性
    * String类：代表字符串。Java 程序中的所有字符串字面值（如 "abc" ）都作 为此类的实例实现。 
    * String是一个final类，代表不可变的字符序列。 
    * 字符串是常量，用双引号引起来表示。它们的值在创建之后不能更改。 
    * String对象的字符内容是存储在一个字符数组value[]中的。

```java
public final class String
    implements java.io.Serializable, Comparable<String>, CharSequence {
    * The value is used for character storage. 
    private final char value[];

    * Cache the hash code for the string
    private int hash; // Default to 0

    * use serialVersionUID from JDK 1.0.2 for interoperability 
    private static final long serialVersionUID = -6849794470754667710L;
```

* * *

这个 char 类型的变量也是被 final 关键字修饰，而数组变量属于引用类型，它的值其实就是数组的地址，也就是说 value 数组在初始化之后就不能再指向另外的对象，这也保证了 String 类的不可变性

但是这里有一点需要额外提到的就是，虽然 value 数组在初始化之后就不能再指向另外的对象，但是它原本指向的地址的内容是可以改变的（利用反射原理）。

* * *
```java
 final char[] str = {'1','2','3'};
// 直接赋值将 str 数组的内容修改为{'1','2','4'}
str[2] = '4';
// 通过反射将 str 数组的内容修改为{'1','2','5'}
java.lang.reflect.Array.set(str, 2, '5');

第一个方式是直接对 str 数组变量中元素进行赋值，第二个方式是通过反射修改数组内容。所以，要记得的是：被 final 修饰的引用类型变量只是引用地址不能改变。而为了保证 String 对象的内容，也就是 value 数组的元素不被修改，源码中也没有提供任何修改 value 数组的方法，这也是保证 String 类的不可变性的一种方式。
```
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201202161335.png)
```java
package com.atguigu.String类;

import org.junit.Test;

/**
 * @author 布丁熊.菲特尼斯
 * @create 2020-12-02 11:45
 */
public class StringTest {
    /*
     * String:字符串，用一对""引起来表示
     * String声明为finald的，是不可被继承的
     * String实现了Serializable接口:表示字符串是支持序列化的
     *       实现了Comparable接口:表示String可以比较大小
     * String内部定义了final char[] value用于存储字符串数据
     * String:代表不可变的字符序列。简称:不可变性
     * 体现：1.当对字符串重新赋值时，需要重写指定内存区域赋值，不能使用原有的value进行赋值
     *      2.当对现有的字符串进行连接操作时，也需要指定内存区域赋值，不能使用原有的value进行赋值
     *      3.当调用String的replace()方法修改指定字符或字符串时，也需要指定内存区域赋值，不能使用原有的value进行赋值
     * 通过字面量的方式(区别于new)给一个字符串赋值,此时的字符串值声明在字符串常量池中
     * 字符串常量池中是不会存储相同内容的字符串的
     *
     */
    @Test
    public void test1(){
        String s1 = "abc";
        String s2 = "abc";
        System.out.println(s1 == s2);//比较是s1和s2的地址值
        s1 = "hello";
        System.out.println(s1);//hello
        System.out.println("***********************");

        String s3 = "abc";
        s3 += "def";  //为s3有重新在字符串常量池创建了一个"abcedf"的字符串
                      //而原有的"abc"字符串还在常量池并未改变
        System.out.println(s3);//abcdef
        System.out.println(s2);//abc
        System.out.println("************************");

        String s4 = "abc";
        String s5 = s4.replace('a', 'c');
        System.out.println(s4);//abc
        System.out.println(s5);//cbc
    }
}

```
运行结果
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201202163151.png)

#### String对象的创建
```java
String str = "hello";
//本质上this.value = new char[0];
String s1 = new String(); 
//this.value = original.value;
String s2 = new String(String original); 
//this.value = Arrays.copyOf(value, value.length);
String s3 = new String(char[] a); 
String s4 = new String(char[] a,int startIndex,int count);
```

* * *
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201202180009.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201202180046.png)
* * *

#### 字符串对象是如何储存的
```java
/*
     * String的实例化方式
     * 方式一：通过字面量定义的方式
     * 方式二：通过new + 构造器的方式
     *  
     */
    @Test
    public void test2(){
        //通过字面量定义的方式:此时的s1和说s2的数据javaEE声明在方法区中的字符常量池中
        String s0 = "javaEEhadoop"
        String s1 = "javaEE";
        String s2 = "javaEE";
        //通过new + 构造器的方式:此时s3和s4保存的地址值,是数据在堆空间中开辟空间以后对应的地址值
        String s3 = new String("javaEE");
        String s4 = new String("javaEE");
        final String s5 = "javaEE";//final修饰后，s5就是常量
        String s6 = s5 + "hadoop"; //s5:常量
        System.out.println(s0 == s6);//true
        System.out.println(s1 == s2);//true
        System.out.println(s1 == s3);//false
        System.out.println(s1 == s4);//false
        System.out.println(s3 == s4);//false
    }
```
结论：
**常量与常量的拼接结果在常量池，且常量池不会存在相同内容的常量
只要其中参与运算的有一个是变量，结果就在堆中
如果拼接的结果调用intern()方法，返回值就在常量池中**
* * *

![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201202173704.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201202173723.png)

* * *
##### String对象创建个数的面试题
>博客链接：https://www.mdeditor.tw/pl/pI9Q
>**概念：
>如果有了解过JVM的同学会知道，虚拟机中有一个地方叫常量池，它会存储字符串常量，在JDK1.7之后常量池位于Java堆中。在程序中创建的对象实例，也会被存放在Java堆中，但与常量池存放的位置是不一样的。还有就是，对象的引用变量，会被存放在虚拟机栈中**

    String s = new String("abc");方式创建对象,在内存中创建了几个对象？
    两个或者一个：一个是堆空间中new的一块内存区域，String对象；
            一个是String类底层char[ ] value对象，对应常量池中的数据：“abc”
            
    若该字符串数据“abc”在常量池中已存在，则 String s = new String("abc")创建了一个对象，String对象，因为常量池不会放两个相同的“abc”，直接用现有的   


​    
    而对于使用new关键词来创建一个String对象，首先虚拟机会在Java堆中创建一个String对象，然后再去常量池中寻找abc字符串是否存在，如果不存在会在常量池中创建一个abc字符串，然后把Java堆中的对象引用的值指向在常量池中创建的abc字符串；若常量池中已存在abc字符串，不会创建该字符串，也不会改变Java堆中对象的引用值。综上所述，String str = new String("abc")这个语句，会创建1个或2个对象，若常量池中没有abc字符串，那么会创建2个对象，否则只会在Java堆中创建一个对象
    
    String s = “abc”创建了几个对象？
    而直接赋值语句会创建0个或1个对象，若常量池中没有abc字符串，会创建1个对象，否则不会创建对象，只需将引用指向常量池中的"abc"字符串

示例代码
```java
public static void main(String[] args) {
String a = new String("abc"); 
String b = "abc"; System.out.println(a==b);//false
}
```
我们画一张图来描述一下示例代码中对象之间的关系。
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201203095439.png)

    第一行代码中使用new String("abc")创建了一个对象，所以会在堆中创建一个value[]对象，而此时常量池不存在abc字符串，所以会在常量池中创建此字符串，并将value[]对象的引用值指向常量池中的abc字符串，但是这两个值的地址是不一样的。第二行代码中使用直接赋值的方式，由于常量池中abc字符串已经存在，所以b这个引用变量会直接指向常量池中的abc字符串。最后，由于value[]对象的地址与常量池中abc字符串的地址是不一样的，所以a与b是不相等的。


* * *



* 练习    
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201202184917.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201202184942.png)

* * *

* * *

##### 字符串的特性
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201202190038.png)
>一个初始时为空的字符串池，它由类String私有地维护
>当调用intern()方法时，如果池子已经包含一个等于此String对象的字符串(该对象由equals(Object)方法确定)，则返回池中的字符串

结论
1.常量与常量的拼接结果在常量池，且常量池中不会存在相同内容的常量
2.只要参与字符串拼接的，有一个变量结果就在堆中
3.如果拼接的结果调用intern()方法，返回值就在常量池中
* * *
#### String使用陷阱
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201202212036.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201202212200.png)

* * *
面试题
```java
class StringTest1{
    String str = new String("good");
    char[] ch = { 't', 'e', 's', 't' };
    public void change(String str, char ch[]) {
        str = "test ok";
        ch[0] = 'b'; }
    public static void main(String[] args) {
        StringTest1 ex = new StringTest1();
        ex.change(ex.str, ex.ch);
        System.out.print(ex.str + " and ");
        System.out.println(ex.ch);
        //结果输出 good and best
    } }

```
#### 为什么说String是不可变的
>博客链接：https://zhuanlan.zhihu.com/p/36799480

##### 1.什么是不可变对象

    如果一个对象在创建之后就不能再改变它的状态，那么这个对象是不可变的（Immutable）。不能改变状态的意思是，不能改变对象内的成员变量，包括基本数据类型变量的值不能改变，引用类型的变量不能指向其他的对象，引用类型指向的对象的状态也不能改变。

##### 2.final关键字的作用

如果要创建一个不可变对象，关键一步就是要将所有的成员变量声明为final类型。所以下面简单回顾一下final关键字的作用：
* final修饰类，表示该类不能被继承，俗称断子绝孙类，该类的所有方法自动地成为final方法
* final修饰方法，表示子类不可重写该方法
* final修饰变量时，又分为两种情况：
    * final修饰基本数据类型变量，表示该变量为常量，值不能再修改
    * final修饰引用类型变量，表示该引用在构造对象之后不能指向其他的对象，但该引用指向的       对象的状态可以改变
    
##### 3.String类不可变性的分析
```java
String s = "abc";    //(1)
System.out.println("s = " + s);

s = "123";    //(2)
System.out.println("s = " + s);

打印结果为：
s = abc
s = 123
```
```java
  看到这里，你可能对String是不可变对象产生了疑惑，因为从打印结果可以看出，s的值的确改变了。其实不然，因为s只是一个String对象的引用，并不是String对象本身,所谓的不可变性是指String类底层char数组value的引用以及内容都不可变（反射可以改变），若（replace()方法）改变了String类里的char数组里面字符内容，其实是在内存空间重新创建了一个字符串
```

 当执行(1)处这行代码之后，会先在方法区的运行时常量池创建一个String对象"abc"，然后在Java栈中创建一个String对象的引用s，并让s指向"abc"，如下图所示：
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201203084621.png)

当执行完(2)处这行代码之后，会在方法区的运行时常量池创建一个新的String对象"123"，然后让引用s重新指向这个新的对象，而原来的对象"abc"还在内存中，并没有改变，如下图所示：
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201203084654.png)

* * *

##### 4.String类不可变性的原理

要理解String类的不可变性，首先看一下String类中都有哪些成员变量。在JDK1.8中，String的成员变量主要有以下几个：
```java
public final class String
    implements java.io.Serializable, Comparable<String>, CharSequence {
    // The value is used for character storage. 
    private final char value[];

    // Cache the hash code for the string 
    private int hash; // Default to 0

    //use serialVersionUID from JDK 1.0.2 for interoperability 
    private static final long serialVersionUID = -6849794470754667710L;

    
     * Class String is special cased within the Serialization Stream Protocol.
     * A String instance is written into an ObjectOutputStream according to
     * <a href="{@docRoot}/../platform/serialization/spec/output.html">
     * Object Serialization Specification, Section 6.2, "Stream Elements"</a>
     
    private static final ObjectStreamField[] serialPersistentFields =
        new ObjectStreamField[0];
        }
```
```java
首先可以看到，String类使用了final修饰符，表明String类是不可继承的。然后，我们主要关注String类的成员变量value,value是char[]类型，因此String对象实际上是用这个字符数组进行封装的。再看value的修饰符，使用了private，也没有提供setter方法，所以在String类的外部不能修改value，同时value也使用了final进行修饰，那么在String类的内部也不能修改value，但是上面final修饰引用类型变量的内容提到，这只能保证value不能指向其他的对象，但value指向的对象的状态是可以改变的。通过查看String类源码可以发现，String类不可变，关键是因为SUN公司的工程师，在后面所有String的方法里都很小心的没有去动字符数组里的元素。所以String类不可变的关键都在底层的实现，而不仅仅是一个final。
```


##### 5.String对象真的不可变嘛？

上面提到，value虽然使用了final进行修饰，但是只能保证vaue不能指向其他的对象，但value指向的对象的状态是可以改变的，也就是说，可以修改value指向的字符数组里面的元素。因为value是private类型的，所以只能使用反射来获取String对象的value属性，再去修改value指向的字符数组里面的元素。通过下面的代码进行验证：
```java
    public void testChangeString() throws Exception {
        String s = "Flamingo";
        //1.获取String类中的value属性
        Field field = String.class.getDeclaredField("value");
        //2.改变value属性的访问权限
        field.setAccessible(true);
        //3.获取s对象上的value属性的值
        char[] value = (char[])field.get(s);
        System.out.println("value= " + Arrays.toString(value));
        //4.改变value所引用的数组种第8个字符
        value[7] = 's';
        System.out.println("value= " + Arrays.toString(value));
        System.out.println("s= " + s);
        System.out.println("***********************************");

        String s1 = "iridescent";
        String s2 = s1.replace('s', 't');
        System.out.println("s2= " + s2);//在常量池中重新创建了一个字符串s2
        System.out.println("s1= " +s1);//原字符串s1没有改变
    }
  
```
运行结果：

    value= [F, l, a, m, i, n, g, o]
    value= [F, l, a, m, i, n, g, s]
    s= Flamings
    ***********************************
    s2= iridetcent
    s1= iridescent

在上述代码中，s始终指向同一个String对象，但是在反射操作之后，这个String对象的内容发生了变化。也就是说，通过反射是可以修改String这种不可变对象的。

* * *
#### 6.String设计成不可变的原因
* 高效性
    * 拿常量池来说，只有变量是不可修改的，才能被缓存起来，从而实现常量池功能 
* 安全性
    * Java 之父 James Gosling 解释过，迫使 String 类设计成不可变的另一个原因是安全，当你在调用其他方法时，比如调用一些系统级操作指令之前，可能会有一系列校验，如果是可变类的话，可能在你校验过后，它的内部的值又被改变了，这样有可能会引起严重的系统崩溃问题。 

* * *

#### 重新回顾String字符串
##### 问题：String 是如何实现的？它有哪些重要的方法？
* 典型回答
    * 以主流的 JDK 版本 1.8 来说，String 内部实际存储结构为 char 数组，源码如下：
    
```java
   public final class String
    implements java.io.Serializable, Comparable<String>, CharSequence {
    // 用于存储字符串的值
    private final char value[];
    // 缓存字符串的 hash code
    private int hash; // Default to 0
    // ......其他内容
}
```
##### String源码中包含下面几个重要的方法
* 1. 多构造方法
 String 字符串有以下 4 个重要的构造方法：
```java
// String 为参数的构造方法

     * Initializes a newly created {@code String} object so that it represents
     * the same sequence of characters as the argument; in other words, the
     * newly created string is a copy of the argument string. Unless an
     * explicit copy of {@code original} is needed, use of this constructor is
     * unnecessary since Strings are immutable.
     
     * @param  original
     * A {@code String}
public String(String original) {
    this.value = original.value;
    this.hash = original.hash;
}
// char[] 为参数构造方法

     * Allocates a new {@code String} so that it represents the sequence of
     * characters currently contained in the character array argument. The
     * contents of the character array are copied; subsequent modification of
     * the character array does not affect the newly created string.
     * @param  value
     * The initial value of the string
     
public String(char value[]) {
    this.value = Arrays.copyOf(value, value.length);
}

public static char[] copyOf(char[] original, int newLength) {
        char[] copy = new char[newLength];
        System.arraycopy(original, 0, copy, 0,
                         Math.min(original.length, newLength));
        return copy;
    }
    
// StringBuffer 为参数的构造方法
public String(StringBuffer buffer) {
    synchronized(buffer) {
        this.value = Arrays.copyOf(buffer.getValue(), buffer.length());
    }
}
// StringBuilder 为参数的构造方法
public String(StringBuilder builder) {
    this.value = Arrays.copyOf(builder.getValue(), builder.length());
}

其中，比较容易被我们忽略的是以 StringBuffer 和 StringBuilder 为参数的构造函数，因为这三种数据类型，我们通常都是单独使用的，所以这个小细节我们需要特别留意一下。
```
* 2. equals()比较两个字符串是否相等
      源码如下：
  
```java
public boolean equals(Object anObject) {
    // 对象引用相同直接返回 true
    if (this == anObject) {
        return true;
    }
    // 判断需要对比的值是否为 String 类型，如果不是则直接返回 false
    if (anObject instanceof String) {
        String anotherString = (String)anObject;
        int n = value.length;
        if (n == anotherString.value.length) {
            // 把两个字符串都转换为 char 数组对比
            char v1[] = value;
            char v2[] = anotherString.value;
            int i = 0;
            // 循环比对两个字符串的每一个字符
            while (n-- != 0) {
                // 如果其中有一个字符不相等就 true false，否则继续对比
                if (v1[i] != v2[i])
                    return false;
                i++;
            }
            return true;
        }
    }
    return false;
}
```
String 类型重写了 Object 中的 equals() 方法，equals() 方法需要传递一个 Object 类型的参数值，在比较时会先通过 instanceof 判断是否为 String 类型，如果不是则会直接返回 false，instanceof 的使用如下：
```java
Object oString = "123";
Object oInt = 123;
System.out.println(oString instanceof String); // 返回 true
System.out.println(oInt instanceof String); // 返回 false
```
当判断参数为 String 类型之后，会循环对比两个字符串中的每一个字符，当所有字符都相等时返回 true，否则则返回 false。还有一个和 equals() 比较类似的方法 equalsIgnoreCase()，它是用于忽略字符串的大小写之后进行字符串对比。
##### 3. compareTo( )比较两字符串
compareTo()方法用于比较两字符串，返回的结果为int类型的值，源码如下：
```java
public int compareTo(String anotherString) {
    int len1 = value.length;
    int len2 = anotherString.value.length;
    // 获取到两个字符串长度最短的那个 int 值
    int lim = Math.min(len1, len2);
    char v1[] = value;
    char v2[] = anotherString.value;
    int k = 0;
    // 对比每一个字符
    while (k < lim) {
        char c1 = v1[k];
        char c2 = v2[k];
        if (c1 != c2) {
            // 有字符不相等就返回差值
            return c1 - c2;
        }
        k++;
    }
    return len1 - len2;
}

```

    从源码中可以看出，compareTo() 方法会循环对比所有的字符，当两个字符串中有任意一个字符不相同时，则 return char1-char2。比如，两个字符串分别存储的是 1 和 2，返回的值是 -1；如果存储的是 1 和 1，则返回的值是 0 ，如果存储的是 2 和 1，则返回的值是 1。还有一个和 compareTo() 比较类似的方法 compareToIgnoreCase()，用于忽略大小写后比较两个字符串。可以看出 compareTo() 方法和 equals() 方法都是用于比较两个字符串的，
    但它们有两点不同：    
         equals() 可以接收一个 Object 类型的参数，而 compareTo() 只能接收一个 String 类型的参数；equals() 返回值为 Boolean，而 compareTo() 的返回值则为 int。         
        它们都可以用于两个字符串的比较，当 equals() 方法返回 true 时，是 compareTo() 方法返回 0 时，则表示两个字符串完全相同。

##### 其它重要方法
* indexOf()：查询字符串首次出现的下标位置
* lastIndexOf()：查询字符串最后出现的下标位置
* contains()：查询字符串中是否包含另一个字符串
* toLowerCase()：把字符串全部转换成小写
* toUpperCase()：把字符串全部转换成大写
* length()：查询字符串的长度
* trim()：去掉字符串首尾空格
* replace()：替换字符串中的某些字符
* split()：把字符串分割并返回字符串数组
* join()：把字符串数组转为字符串

* * *

##### String面试还会关联以下问题
* 为什么String类型要用final修饰？
* ==和equals的区别是什么？
* String和StringBuilder，StringBuffer  有什么区别？
* String的intern()方法有什么含义？
* String类型在JVM(Java虚拟机)中是如何存储的？编译器对String做了哪些优化？

* * *
##### 知识扩展

1. == 和 equals的区别

>" ==" 对于基本数据类型来说，用于比较 ”值“是否相等；而对于引用类型来说，是用于比较引用地址是否相同的

查看源码我们可以知道 Object 中也有 equals()  方法，源码如下：
```java
public boolean equals(Object obj) {
    return (this == obj);//比较的是地址
}
```
可以看出，Object 中的 equals() 方法其实就是 ==，而 String 重写了 equals() 方法把它修改成比较两个字符串的值是否相等。
源码如下：
```java
public boolean equals(Object anObject) {
    // 对象引用相同直接返回 true
    if (this == anObject) {
        return true;
    }
    // 判断需要对比的值是否为 String 类型，如果不是则直接返回 false
    if (anObject instanceof String) {
        String anotherString = (String)anObject;
        int n = value.length;
        if (n == anotherString.value.length) {
            // 把两个字符串都转换为 char 数组对比
            char v1[] = value;
            char v2[] = anotherString.value;
            int i = 0;
            // 循环比对两个字符串的每一个字符
            while (n-- != 0) {
                // 如果其中有一个字符不相等就 true false，否则继续对比
                if (v1[i] != v2[i])
                    return false;
                i++;
            }
            return true;
        }
    }
    return false;
}

```

2. final修饰的好处

从 String 类的源码我们可以看出 String 是被 final 修饰的不可继承类，源码如下： 
```
public final class String 
	implements java.io.Serializable, Comparable<String>, CharSequence { //...... }
```
那这样设计有什么好处呢？    

    Java 语言之父 James Gosling 的回答是，他会更倾向于使用 final，因为它能够缓存结果，当你在传参时不需要考虑谁会修改它的值；如果是可变类的话，则有可能需要重新拷贝出来一个新值进行传参，这样在性能上就会有一定的损失。
    
    James Gosling 还说迫使 String 类设计成不可变的另一个原因是安全，当你在调用其他方法时，比如调用一些系统级操作指令之前，可能会有一系列校验，如果是可变类的话，可能在你校验过后，它的内部的值又被改变了，这样有可能会引起严重的系统崩溃问题，这是迫使 String 类设计成不可变类的一个重要原因。

重点优势：1、可以利用不可变性实现字符串常量池；2、非常适合做 HashMap 的 key（因为不变）；3、天生线程安全。   
总结来说，使用 final 修饰的第一个好处是安全；第二个好处是高效，以 JVM 中的字符串常量池来举例，如下两个变量：
```java
String s1 = "java";
String s2 = "java";
```
只有字符串是不可变时，我们才能实现字符串常量池，字符串常量池可以为我们缓存字符串，提高程序的运行效率，如下图所示：
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201203160420.png)

试想一下如果 String 是可变的，那当 s1 的值修改之后，s2 的值也跟着改变了，这样就和我们预期的结果不相符了，因此也就没有办法实现字符串常量池的功能了

3. String的intern()方法的含义

String#intern 是一个 native 方法，注释写的很详细，“如果常量池中存在当前字符串, 就会直接返回当前字符串. 如果常量池中没有此字符串, 会将此字符串放入常量池中后, 再返回”

4. String 和 StringBuilder、StringBuffer 的区别

因为 String 类型是不可变的，所以在字符串拼接的时候如果使用 String 的话性能会很低，因此我们就需要使用另一个数据类型 StringBuffer，它提供了 append 和 insert 方法可用于字符串的拼接，它使用 synchronized 来保证线程安全，如下源码所示：
```java
@Override
public synchronized StringBuffer append(Object obj) {
    toStringCache = null;
    super.append(String.valueOf(obj));
    return this;
}
@Override
public synchronized StringBuffer append(String str) {
    toStringCache = null;
    super.append(str);
    return this;
}

```

因为它使用了 synchronized 来保证线程安全，所以性能不是很高，于是在 JDK 1.5 就有了 StringBuilder，它同样提供了 append 和 insert 的拼接方法，但它没有使用 synchronized 来修饰，因此在性能上要优于 StringBuffer，所以在非并发操作的环境下可使用 StringBuilder 来进行字符串拼接。

5.String 和 JVM
>根据 JVM 规范，JVM 内存共分为虚拟机栈、堆、方法区、程序计数器、本地方法栈五个部分。

![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201203170757.png)

String 常见的创建方式有两种，new String() 的方式和直接赋值的方式，直接赋值的方式会先去字符串常量池中查找是否已经有此值，如果有则把引用地址直接指向此值，否则会先在常量池中创建，然后再把引用指向此值；而 new String() 的方式一定会先在堆上创建一个字符串对象，然后再去常量池中查询此字符串的值是否已经存在，如果不存在会先在常量池中创建此字符串，然后把引用的值指向此字符串，如下代码所示：
```java
String s1 = new String("Java");
String s2 = s1.intern();
String s3 = "Java";
System.out.println(s1 == s2); // false
System.out.println(s2 == s3); // true

```

它们在 JVM 存储的位置，如下图所示：
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201203161937.png)

>小贴士：JDK 1.8 把永生代换成的元空间，JDK1.7 把字符串常量池从方法区移到了 Java 堆上。除此之外编译器还会对 String 字符串做一些优化，例如以下代码：

```java
String s1 = "Ja" + "va";
String s2 = "Java";
System.out.println(s1 == s2);
```
常量池不会有 “ja”、“va”，代码在编译器阶段被优化成了"Java"
虽然 s1 拼接了多个字符串，但对比的结果却是 true，我们使用反编译工具，看到的结果如下：
```javaCompiled from "StringExample.java"
public class com.lagou.interview.StringExample {
  public com.lagou.interview.StringExample();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return
    LineNumberTable:
      line 3: 0
  public static void main(java.lang.String[]);
    Code:
       0: ldc           #2                  // String Java
       2: astore_1
       3: ldc           #2                  // String Java
       5: astore_2
       6: getstatic     #3                  // Field java/lang/System.out:Ljava/io/PrintStream;
       9: aload_1
      10: aload_2
      11: if_acmpne     18
      14: iconst_1
      15: goto          19
      18: iconst_0
      19: invokevirtual #4                  // Method java/io/PrintStream.println:(Z)V
      22: return
    LineNumberTable:
      line 5: 0
      line 6: 3
      line 7: 6
      line 8: 22
}
```
从编译代码 #2 可以看出，代码 "Ja"+"va" 被直接编译成了 "Java" ，因此 s1==s2 的结果才是 true，这就是编译器对字符串优化的结果。

* * *
##### 字符串相关的类：String常用方法1
int length()：返回字符串的长度： return value.length
 char charAt(int index)： 返回某索引处的字符return value[index]
 boolean isEmpty()：判断是否是空字符串：return value.length == 0
 String toLowerCase()：使用默认语言环境，将 String 中的所有字符转换为小写
 String toUpperCase()：使用默认语言环境，将 String 中的所有字符转换为大写
 String trim()：返回字符串的副本，忽略前导空白和尾部空白
 boolean equals(Object obj)：比较字符串的内容是否相同
 boolean equalsIgnoreCase(String anotherString)：与equals方法类似，忽略大小写
 String concat(String str)：将指定字符串连接到此字符串的结尾。 等价于用“+” 
 int compareTo(String anotherString)：比较两个字符串的大小
 String substring(int beginIndex)：返回一个新的字符串，它是此字符串的从beginIndex开始截取到最后的一个子字符串。
 String substring(int beginIndex, int endIndex) ：返回一个新字符串，它是此字符串从beginIndex开始截取到endIndex(不包含)的一个子字符串。

 boolean endsWith(String suffix)：测试此字符串是否以指定的后缀结束
 boolean startsWith(String prefix)：测试此字符串是否以指定的前缀开始
 boolean startsWith(String prefix, int toffset)：测试此字符串从指定索引开始的子字符串是否以指定前缀开始
 boolean contains(CharSequence s)：当且仅当此字符串包含指定的 char 值序列时，返回 true
 int indexOf(String str)：返回指定子字符串在此字符串中第一次出现处的索引
 int indexOf(String str, int fromIndex)：返回指定子字符串在此字符串中第一次出
现处的索引，从指定的索引开始
 int lastIndexOf(String str)：返回指定子字符串在此字符串中最右边出现处的索引
 int lastIndexOf(String str, int fromIndex)：返回指定子字符串在此字符串中最后一次出现处的索引，从指定的索引开始反向搜索
注：indexOf和lastIndexOf方法如果未找到都是返回-1

String replace(char oldChar, char newChar)：返回一个新的字符串，它是通过用 newChar 替换此字符串中出现的所有 oldChar 得到的。 
 String replace(CharSequence target, CharSequence replacement)：使用指定的字面值替换序列替换此字符串所有匹配字面值目标序列的子字符串。
 String replaceAll(String regex, String replacement) ： 使 用 给 定 的replacement 替换此字符串所有匹配给定的正则表达式的子字符串。
 String replaceFirst(String regex, String replacement) ： 使 用 给 定 的replacement 替换此字符串匹配给定的正则表达式的第一个子字符串。
 boolean matches(String regex)：告知此字符串是否匹配给定的正则表达式。
 String[] split(String regex)：根据给定正则表达式的匹配拆分此字符串。
 String[] split(String regex, int limit)：根据匹配给定的正则表达式来拆分此字符串，最多不超过limit个，如果超过了，剩下的全部都放到最后一个元素中。

* * *
##### String与基本数据类型转换
* 字符串 ---> 基本数据类型，包装类（parseXxx（str））
    * Integer包装类的public static int parseInt(String s)：可以将由“数字”字符组成的字符串转换为整型。
    * 类似地,使用java.lang包中的Byte、Short、Long、Float、Double类调相应的类方法可以将由“数字”字符组成的字符串，转化为相应的基本数据类型

* 基本数据类型，包装类 --->  字符串（valueOf（xxx））
    * 调用String类的public String valueOf(int n)可将int型转换为字符串
    * 相应的valueOf(byte b)、valueOf(long l)、valueOf(float f)、valueOf(doubled)、valueOf(boolean b)可由参数的相应类型到字符串的转换

##### String与字符数组转换

* 字符数组 ---> 字符串（调用String构造器）
    * String 类的构造器：String(char[]) 和 String(char[]，int offset，intlength) 分别用字符数组中的全部字符和部分字符创建字符串对象。 

* 字符串 ---> 字符数组(调用String的toCharArray( ))
    * public char[] toCharArray()：将字符串中的全部字符存放在一个字符数组中的方法。
    * public void getChars(int srcBegin, int srcEnd, char[] dst,int dstBegin)：提供了将指定索引范围内的字符串存放到数组中的方法。

##### String与字节数组转换
* * *
* 字节数组 ---> 字符串（调用String的构造器）
    * String(byte[])：通过使用平台的默认字符集解码指定的 byte 数组，构造一个新的String。
    * String(byte[]，int offset，int length) ：用指定的字节数组的一部分，即从数组起始位置offset开始取length个字节构造一个字符串对象。

* 字符串 -- 字节数组 （调用String的getBytes()）
* public byte[] getBytes() ：使用平台的默认字符集将此 String 编码为byte 序列，并将结果存储到一个新的 byte 数组中。
* public byte[] getBytes(String charsetName) ：使用指定的字符集将此 String 编码到 byte 序列，并将结果存储到新的 byte 数组。

* * *
编码：String  ---> byte[]：调用String的getBytes()
解码：byte[]  ---> String: 调用String的构造器
编码：字符串  ---> 字节(看的懂 ---> 看不懂的二进制数据)
解码：编码的逆过程，字节 ---> 字符串(看不懂的二进制数据 ---> 看得懂)
说明：解码时，要求解码使用的字符集必须与编码时使用的字符集一致，否则会出现乱码
* * *

##### StringBuffer类
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201204134522.png)

* * *

![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201204134555.png)

##### String,StringBuffer,StringBuilder三者的异同？

* String：不可变的字符序列；底层使用cha[]存储
* StringBuffer：可变的字符序列；线程安全的，效率低，底层使用char[]储存
* StringBuilder：可变的字符序列；jdk5.0新增的，线程不安全的，效率高；底层使用char[]存储

源码分析：
```java

     * Initializes a newly created {@code String} object so that it represents
     * an empty character sequence.  Note that use of this constructor is
     * unnecessary since Strings are immutable.
     
    public String() {
        this.value = "".value;
    }
String str = new String(); //char[] value = new char[0];


     * Initializes a newly created {@code String} object so that it represents
     * the same sequence of characters as the argument; in other words, the
     * newly created string is a copy of the argument string. Unless an
     * explicit copy of {@code original} is needed, use of this constructor is
     * unnecessary since Strings are immutable.
     *
     * @param  original
     *         A {@code String}
     
char[] value;
public String(String original) {
        this.value = original.value;
        this.hash = original.hash;
    }
String str1 = new String("abc");//char[] value = new char[]{'a','b','c'};


     * Constructs a string buffer with no characters in it and an
     * initial capacity of 16 characters.
     
    public StringBuffer() {
        super(16);
    }
	//super()调用StringBuffer父类的构造器
    char[] value;
    AbstractStringBuilder(int capacity) {
        value = new char[capacity];
    }


     * Returns the length (character count).
     
     * @return  the length of the sequence of characters currently
     *          represented by this object
     
    @Override
    public int length() {
        return count;//char[]数组的元素个数
    }
StringBuffer sb1 = new StringBuffer(); //char[] value = new char[16];底层创建了一个长度为16的字符数组
System.out.println(sb1.length());//0
sb1.append('a');//value[0]='a';
sb1.append('b');//value[1]='b';


     * Constructs a string buffer initialized to the contents of the
     * specified string. The initial capacity of the string buffer is
     * {@code 16} plus the length of the string argument.
     *
     * @param   str   the initial contents of the buffer.
     
public StringBuffer(String str) {
        super(str.length() + 16);
        append(str);
    }
StringBuffer sb2 = new StringBuffer("abc");//char[] value = new char["abc".length() + 16];

//问题1. System.out.println(sb2.length());//3
//问题2. 扩容问题: 如果要添加的数据底层char[]数组内存空间不够，那就需要对char[]数组扩容
//默认情况下，扩容为原来的容量的2倍 + 2，同时将原有数组中的元素复制到新的数组中

    /**
     * A cache of the last value returned by toString. Cleared
     * whenever the StringBuffer is modified.
     */
    private transient char[] toStringCache;

@Override
    public synchronized StringBuffer append(String str) {
        toStringCache = null;
        super.append(str);
        return this;
    }
//父类AbstractStringBuilder的方法
public AbstractStringBuilder append(String str) {
        if (str == null)
            return appendNull();
        int len = str.length();
        ensureCapacityInternal(count + len);
        str.getChars(0, len, value, count);
        count += len;
        return this;//直接返回StringBuffer对象(说明append方法可以连续使用)
    }
private void ensureCapacityInternal(int minimumCapacity) {//minimumCapacity = count + len
        // overflow-conscious code
        if (minimumCapacity - value.length > 0) {
            value = Arrays.copyOf(value,
                    newCapacity(minimumCapacity));
        }
    }
private int newCapacity(int minCapacity) {
        // overflow-conscious code
        int newCapacity = (value.length << 1) + 2;//char[]数组扩容2倍 + 2
        if (newCapacity - minCapacity < 0) {//若扩容后的char数组长度还是小于所需要的最小数组长度
            newCapacity = minCapacity;//直接将所需要的最小数组长度赋值给newCapacity
        }
        return (newCapacity <= 0 || MAX_ARRAY_SIZE - newCapacity < 0)
            ? hugeCapacity(minCapacity)
            : newCapacity;
    }
//直到意义：开发中建议大家使用：StringBuffer(int capacity) 或 StringBuilder(int capacity)

     * Constructs a string buffer with no characters in it and
     * the specified initial capacity.
     *
     * @param      capacity  the initial capacity.
     * @exception  NegativeArraySizeException  if the {@code capacity}
     *               argument is less than {@code 0}.
     
    public StringBuffer(int capacity) {
        super(capacity);
    }
//若开发中使用的场景要求线程安全，就使用StringBuffer，否则使用StringBuilder
```
##### StringBuffer类的常用方法
* StringBuffer append(xxx)：提供了很多的append()方法，用于进行字符串拼接 
* StringBuffer delete(int start,int end)：删除指定位置的内容 
* StringBuffer replace(int start, int end, String str)：把[start,end)位置替换为str 
* StringBuffer insert(int offset, xxx)：在指定位置插入xxx 
* StringBuffer reverse() ：把当前字符序列逆转 
* 当append和insert时，如果原来value数组长度不够，可扩容。
* 如上这些方法支持方法链操作。
* 方法链的原理：
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201204135011.png)

* * *
总结：
* 增：append(xxx)
* 删：delete(int start,int end)
* 改：setCharAt(int n,char ch),replace(int start,int end,String str)
* 查：charAt(int n)
* 长度：length();
* 遍历：for + charAt()
* * *
##### String,StringBuffer,StringBuilder三者的效率
```java
   /*
    对比String,StringBuffer,StringBuilder三者的效率:
    从高到底排序:StringBuilder > StringBuffer > String
   */
    @Test
    public void testQuickly(){
        //初始设置
        long startTime = 0L;
        long endTime = 0L;
        String text = "";
        StringBuffer buffer = new StringBuffer("");
        StringBuilder builder = new StringBuilder("");
       //开始对比
        startTime = System.currentTimeMillis();
        for (int i = 0; i < 20000; i++) {
            buffer.append(String.valueOf(i));
        }
        endTime = System.currentTimeMillis();
        System.out.println("StringBuffer的执行时间：" + (endTime - startTime));
        startTime = System.currentTimeMillis();
        for (int i = 0; i < 20000; i++) {
            builder.append(String.valueOf(i));
        }
        endTime = System.currentTimeMillis();
        System.out.println("StringBuilder的执行时间：" + (endTime - startTime));
        startTime = System.currentTimeMillis();
        for (int i = 0; i < 20000; i++) {
            text = text + i; }
        endTime = System.currentTimeMillis();
        System.out.println("String的执行时间：" + (endTime - startTime));
    }
    
```
##### String与StringBuffer、StringBuilder之间的转换
    String --> StringBuffer、StringBuilder:调用StringBuffer、StringBuilder构造器
    StringBuffer、StringBuilder --> String:
    ①调用String构造器；
    ②StringBuffer、StringBuilder的toString()
##### JVM中字符串常量池存放位置说明
    jdk 1.6 (jdk 6.0 ,java 6.0):字符串常量池存储在方法区（永久区）
    jdk 1.7:字符串常量池存储在堆空间
    jdk 1.8:字符串常量池存储在方法区（元空间）


* * *
##### 面试题（程序输出）

* Instance_One

```java
public void testStringBuffer(){
        String str = null;
        StringBuffer sb = new StringBuffer();
        sb.append(str);
        System.out.println(sb.length());//4
        System.out.println(sb);//"null"
        StringBuffer sb1 = new StringBuffer(str);//抛异常NullPointerException
        System.out.println(sb1);
    }
```
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201204174648.png)

* * *

源码解析：
```java
//String str = null;
//StringBuffer sb = new StringBuffer();分析
public StringBuffer() {
        super(16);
    }
//super调用的是父类AbstractStringBuilder的构造方法
AbstractStringBuilder(int capacity) {
        value = new char[capacity];
    }
//sb.append(str)分析
@Override
    public synchronized StringBuffer append(String str) {
        toStringCache = null;
        super.append(str);
        return this;
    }
public AbstractStringBuilder append(String str) {
        if (str == null)
            return appendNull();
        int len = str.length();
        ensureCapacityInternal(count + len);
        str.getChars(0, len, value, count);
        count += len;
        return this;
    }

private AbstractStringBuilder appendNull() {
        int c = count;
        ensureCapacityInternal(c + 4);
        final char[] value = this.value;
        value[c++] = 'n';
        value[c++] = 'u';
        value[c++] = 'l';
        value[c++] = 'l';
        count = c;
        return this;
    }
private void ensureCapacityInternal(int minimumCapacity) {
        // overflow-conscious code
        if (minimumCapacity - value.length > 0) {
            value = Arrays.copyOf(value,
                    newCapacity(minimumCapacity));
        }
    }
    private int newCapacity(int minCapacity) {
        // overflow-conscious code
        int newCapacity = (value.length << 1) + 2;
        if (newCapacity - minCapacity < 0) {
            newCapacity = minCapacity;
        }
        return (newCapacity <= 0 || MAX_ARRAY_SIZE - newCapacity < 0)
            ? hugeCapacity(minCapacity)
            : newCapacity;
    }
//Object obj = new Object();
//最终System.out.println(obj)输出 ---> obj为非String类的对象
//System.out.println(sb)
底层源码:
 
     * Prints an Object and then terminate the line.  This method calls
     * at first String.valueOf(x) to get the printed object's string value,
     * then behaves as
     * though it invokes <code>{@link #print(String)}</code> and then
     * <code>{@link #println()}</code>.
     *
     * @param x  The <code>Object</code> to be printed.
     
//System.out.println(sb)分析;//null
public void println(Object x) {
        String s = String.valueOf(x);
        synchronized (this) {
            print(s);
            newLine();
        }
    }
//obj.toString(),这里的obj为sb对象，调用的是StringBuffer类的toString()方法
public static String valueOf(Object obj) {
        return (obj == null) ? "null" : obj.toString();
    }

//toStringCache 解释代码如下

     * A cache of the last value returned by toString. Cleared
     * whenever the StringBuffer is modified.
     
    private transient char[] toStringCache;

//System.out.println(sb2)该方法调用的是StringBuffer类中的toString()方法
源码如下：
@Override
    public synchronized String toString() {
        if (toStringCache == null) {
            toStringCache = Arrays.copyOfRange(value, 0, count);
        }
    //第二次再次相同打印输出，直接返回缓存的char数组toStringCache里的字符
        return new String(toStringCache, true);
    }

    * Package private constructor which shares value array for speed.
    * this constructor is always expected to be called with share==true.
    * a separate constructor is needed because we already have a public
    * String(char[]) constructor that makes a copy of the given char[].
    
    String(char[] value, boolean share) {
        // assert share : "unshared not supported";
        this.value = value;
    }

//StringBuffer sb1 = new StringBuffer(str)分析；其中String str=null
public StringBuffer(String str) {
        super(str.length() + 16);
        append(str);
    }
//此时str.length()会报NullPointerException空指针异常，运行结束

```

* Instance_Two
```java
@Test
    public void testString(){
        String a = "123";
        String b ="123";
        String c = new String("123");
        String d = new String("123");
        System.out.println(a.equals(b));//true
        System.out.println(a == b);//true
        System.out.println(c.equals(d));//true
        System.out.println(c == d);//false
        System.out.println(a.equals(c));//true
        System.out.println(a == c);//false
    }
```
* * *


##### String常见算法题目的考察    

1. 模拟一个trim方法，去除字符串两端的空格。
```java
@Test
    public void testTrim(){
        String s = " abc ";
        String s1 = s.trim();
        System.out.println(s1);
    }
```
2. 将一个字符串进行反转。将字符串中指定部分进行反转。比如“abcdefg”反
转为”abfedcg”
```java
public String testreverse(String str,int startIndex,int endIndex){
        //方法一
        if (str!=null){
            //起始字符位置
            String substr = str.substring(0, startIndex);
            //要反转的字符位置
            for (int i = endIndex; i>=startIndex ; i--) {
                substr += str.charAt(i);
            }
            //后段字符位置
            substr  += str.substring(endIndex+1);
            return substr;
        }
        return null;
    }
    public String reverse(String str,int startIndex,int endIndex){
         //方法二
        if (str != null){
            char[] arr = str.toCharArray();
            for (int i = startIndex,end = endIndex; i < end ; i++,end--) {
                char temp = arr[i];
                arr[i] = arr[end];
                arr[end] = temp;
            }
            return new String(arr);
        }
        return null;
    }
    //方式三:使用StringBuffer/StringBuilder替换String
    public String bfReverse(String str,int startIndex,int endIndex){
        if (str!=null){
            StringBuffer buffer = new StringBuffer(str.length());
            //第1部分
            buffer.append(str.substring(0,startIndex));
            //第2部分
            for (int i = endIndex; i >= startIndex ; i--) {
                buffer.append(str.charAt(i));
            }
            //第3部分
            //若endIndex为字符串的最后一个字符下标位置,str.substring(endIndex+1) == null
            buffer.append(str.substring(endIndex+1));
            return buffer.toString();
        }
        return null;
    }
@Test
    public void testReverse(){
        String s = "abcdefg";
        String str = reverse(s, 2, 6);
        System.out.println("方法1："+str);
        String str1 = testreverse(s, 2, 5);
        System.out.println("方法2：" + str1);
        String s1 = bfReverse(s, 2, 6);
        System.out.println("bf拼接："+s1);
        StringBuffer buffer = new StringBuffer("abcdefg");
        String substring = buffer.substring(2);
        StringBuffer reverse = new StringBuffer(substring).reverse();
        StringBuffer replace = buffer.replace(2, 7, reverse.toString());
        System.out.println(buffer.toString());
    }
```
3. 获取一个字符串在另一个字符串中出现的次数。
比如：获取“ ab”在 “abkkcadkabkebfkabkskab” 中出现的次数
```java
/*
     * @Description: 获取subStr在mainStr中出现的次数
     * @Param: [mainStr, subStr]
     * @Return: int
     */
    public int getCount(String mainStr,String subStr){
        int mainLength = mainStr.length();
        int subStrLength = subStr.length();
        int count = 0;
        int index = 0 ;
        if (subStrLength <= mainLength){
            //第一种方法(字符串底层大量拼接,性能不好)
            while ((index = mainStr.indexOf(subStr))!=-1){
                count++;
                //mainStr = "abcdefab",subStr = "ab"
                // 若找到subStr,第一次index=0,则接着从"cdefab"找
                mainStr = mainStr.substring(index + subStr.length());
            }
            //第二种方法(代码优化,无需字符串重复拼接)
            while ((index =  mainStr.indexOf(subStr,index))!= -1){
                count++;
                index = index + subStrLength;
            }
        }
        return count;
    }

    @Test
    public void testStringCount(){
        String s = "abkkcadkabkebfkabkskab";
        String s1 = "ab";
        //第一种方法
        int count = getCount(s, s1);
        System.out.println(count);

        //第二种方法
        String[] abs = s.split(s1);
        System.out.println(abs.length);
        System.out.println(Arrays.toString(abs));
    }
```
4. 获取两个字符串中最大相同子串。比如：
str1 = "abcwerthelloyuiodef“;str2 = "cvhellobnm"
提示：将短的那个串进行长度依次递减的子串与较长的串比较。（难度教大）
>题目资源：尚硅谷 day21_常用类_07视频
```java
// 第4题
	// 如果只存在一个最大长度的相同子串
	public String getMaxSameSubString(String str1, String str2) {
		if (str1 != null && str2 != null) {
			String maxStr = (str1.length() > str2.length()) ? str1 : str2;
			String minStr = (str1.length() > str2.length()) ? str2 : str1;

			int len = minStr.length();

			for (int i = 0; i < len; i++) {// 0 1 2 3 4 此层循环决定要去几个字符

				for (int x = 0, y = len - i; y <= len; x++, y++) {

					if (maxStr.contains(minStr.substring(x, y))) {

						return minStr.substring(x, y);
					}

				}

			}
		}
		return null;
	}

	// 如果存在多个长度相同的最大相同子串
	// 此时先返回String[]，后面可以用集合中的ArrayList替换，较方便
	public String[] getMaxSameSubString1(String str1, String str2) {
		if (str1 != null && str2 != null) {
			StringBuffer sBuffer = new StringBuffer();
			String maxString = (str1.length() > str2.length()) ? str1 : str2;
			String minString = (str1.length() > str2.length()) ? str2 : str1;

			int len = minString.length();
			for (int i = 0; i < len; i++) {
				for (int x = 0, y = len - i; y <= len; x++, y++) {
					String subString = minString.substring(x, y);
					if (maxString.contains(subString)) {
						sBuffer.append(subString + ",");
					}
				}
				System.out.println(sBuffer);
                //若找到最大的相同字串，终止循环查找
				if (sBuffer.length() != 0) {
					break;
				}
			}
            //replaceAll(",$", "")切换掉结尾的逗号
			String[] split = sBuffer.toString().replaceAll(",$", "").split("\\,");
			return split;
		}

		return null;
	}
	// 如果存在多个长度相同的最大相同子串：使用ArrayList
	public List<String> getMaxSameSubString1(String str1, String str2) {
		if (str1 != null && str2 != null) {
			List<String> list = new ArrayList<String>();
			String maxString = (str1.length() > str2.length()) ? str1 : str2;
			String minString = (str1.length() > str2.length()) ? str2 : str1;

			int len = minString.length();
			for (int i = 0; i < len; i++) {
				for (int x = 0, y = len - i; y <= len; x++, y++) {
					String subString = minString.substring(x, y);
					if (maxString.contains(subString)) {
						list.add(subString);
					}
				}
               //若找到最大的相同字串，终止循环查找
				if (list.size() != 0) {
					break;
				}
			}
			return list;
		}
		return null;
	}
```
5. 对字符串中字符进行自然顺序排序。
提示：
1）字符串变成字符数组。
2）对数组排序，选择，冒泡，Arrays.sort();
3）将排序后的数组变成字符串。
```java
@Test
    //冒泡排序
    public void testBubbleSort(){
        int[] arr = {24,98,65,45,23};
        System.out.println("排序前：" + Arrays.toString(arr));

        //第一次比较
        for (int i = 0; i < arr.length - 1 - 0 ; i++) {
            if (arr[i] > arr[i+1]){
                int temp = arr[i];
                arr[i] = arr[i+1];
                arr[i+1] = temp;
            }
        }
        System.out.println("第一次排序：" + Arrays.toString(arr));

        //第二次比较
        for (int i = 0; i < arr.length - 1 - 1 ; i++) {
            if (arr[i] > arr[i+1]){
                int temp = arr[i];
                arr[i] = arr[i+1];
                arr[i+1] = temp;
            }
        }
        System.out.println("第二次排序：" + Arrays.toString(arr));
        //第三次比较
        for (int i = 0; i < arr.length - 1 - 2 ; i++) {
            if (arr[i] > arr[i+1]){
                int temp = arr[i];
                arr[i] = arr[i+1];
                arr[i+1] = temp;
            }
        }
        System.out.println("第三次排序：" + Arrays.toString(arr));
        //第四次比较
        for (int i = 0; i < arr.length - 1 - 3 ; i++) {
            if (arr[i] > arr[i+1]){
                int temp = arr[i];
                arr[i] = arr[i+1];
                arr[i+1] = temp;
            }
        }
        System.out.println("第四次排序：" + Arrays.toString(arr));

        //代码合并，优化
        for (int i = 0; i < arr.length - 1; i++) { //一共比较n-1次
            for (int j = 0; j < arr.length - 1 - i ; j++) {// 每比较一次,少一个元素参与
                if (arr[i] > arr[i+1]){
                    int temp = arr[i];
                    arr[i] = arr[i+1];
                    arr[i+1] = temp;
                }
            }
        }
        System.out.println("优化排序后的结果：" + Arrays.toString(arr));

    }
    @Test
    public void testSortString(){
        String s = "owvbcna";
        char[] chars = s.toCharArray();
        String s1 = new String(chars);
        for (int i = 0; i < chars.length - 1; i++) {
            for (int j = 0; j < chars.length - 1 - i ; j++) {
                if (chars[j] > chars[j+1]){
                    char c = chars[j+1];
                    chars[j+1] = chars[j];
                    chars[j] = c;
                }
            }
        }
        System.out.println(Arrays.toString(chars));

    }
```
#### JDK8之前日期时间API
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201204192510.png)

1. java.lang.System类
System类提供的public static long currentTimeMillis()用来返回当前时
间与1970年1月1日0时0分0秒之间以毫秒为单位的时间差。**(此方法适于计算时间差)**

* 计算世界时间的主要标准有：
UTC(Coordinated Universal Time)
GMT(Greenwich Mean Time)
CST(Central Standard Time)


2. java.util.Date类
表示特定的瞬间，精确到毫秒

构造器：
 Date()：使用无参构造器创建的对象可以获取本地当前时间。
 Date(long date)
 常用方法
 getTime():返回自 1970 年 1 月 1 日 00:00:00 GMT 以来此 Date 对象
表示的毫秒数。
 toString():把此 Date 对象转换为以下形式的 String： dow mon ddhh:mm:ss zzz yyyy 其中： dow 是一周中的某一天 (Sun, Mon, Tue,Wed, Thu, Fri, Sat)，zzz是时间标准。
 其它很多方法都过时了

```java
/*java.util.Date类
         |---java.sql.Date类
    1. 两个构造器的使用
         >构造器一:Date():创建一个对应当前时间的Date对象
         >构造器二:创建指定毫秒数的Date对象
    2. 两个方法的使用
       >toString():显示当前的年,月,日,时,分,秒
       >getTime():获取当前Date对象对应的毫秒数(时间戳)
    3. java.sql.Date对应着数据库中的日期类型的变量
       >如何实例化
       >如何将sql.Date ---> 转化为util.Date对象(多态)
       >如何将util.Date对象转换为sql.Date对象
       */
    @Test
    public void testDate(){
        //构造器一:Date():创建一个对应当前时间的Date对象
        Date date = new Date();
        System.out.println(date.toString());//Fri Dec 04 19:41:46 CST 2020
        System.out.println(date.getTime());//1607082214568

        //构造器二:创建指定毫秒数的Date对象
        Date date1 = new Date(1607082214568L);
        System.out.println(date1);
        System.out.println(date1.toString());

        //创建java.sql.Date对象
        java.sql.Date date2 = new java.sql.Date(1607082666267L);
        System.out.println(date2);//2020-12-04

        //将util.Date对象转换为sql.Date对象
        //情况一
        Date date3 = new java.sql.Date(1607082666287L);
        System.out.println(date3);
        java.sql.Date date4 = (java.sql.Date)date3;
        System.out.println(date4);

        //情况二
        Date date5 = new Date();
        System.out.println(date5.getTime());
        java.sql.Date date6 = new java.sql.Date(date5.getTime());

    }
```

##### java.text.SimpleDateFormat类

Date类的API不易于国际化，大部分被废弃了，java.text.SimpleDateFormat
类是一个不与语言环境有关的方式来格式化和解析日期的具体类。
 它允许进行格式化：日期 --->文本、解析：文本 --->日期
 格式化：
 SimpleDateFormat() ：默认的模式和语言环境创建对象
 public SimpleDateFormat(String pattern)：该构造方法可以用参数pattern
指定的格式创建一个对象，该对象调用：
 public String format(Date date)：方法格式化时间对象date
 解析：
 public Date parse(String source)：从给定字符串的开始解析文本，以生成
一个日期。

1. 两个操作：
1.1 格式化：日期 ---> 字符串
1.2 解析：格式化的逆过程，字符串 ---> 日期
```java
2.SimpleDateFormat的实例化
    @Test
    public void testSimpleDateFormat() throws ParseException {
        //实例化SimpleDateFormat:使用默认的构造器 
        SimpleDateFormat sdf = new SimpleDateFormat();

        //格式化：日期 ---> 字符串
        Date date = new Date();
        System.out.println(date);//Fri Dec 04 21:47:47 CST 2020

        String format = sdf.format(date);
        System.out.println(format);//20-12-4 下午9:47(默认格式化)

        //解析:格式化的逆过程,字符串 ---> 日期
        String str = "19-12-18 上午11:45";
        Date date2 = sdf.parse(str);
        System.out.println(date2);//Wed Dec 18 11:45:00 CST 2019

        System.out.println("*****指定的方式格式化和解析:调用带参的构造器******");
        //SimpleDateFormat sdf1 = new SimpleDateFormat("yyyyy.MMMMM.dd GGG hh:mm aaa");
        SimpleDateFormat sdf1 = new SimpleDateFormat("yyyy-MM-dd hh:mm:ss");
        String format1 = sdf1.format(date);
        System.out.println(format1);//2020-12-04 09:47:47

        //解析:要求字符串必须是符合SimpleDateFormat识别的格式(通过构造器参数体现)
        //否则,抛异常
        Date date1 = sdf1.parse("2020-12-04 09:41:27");
        System.out.println(date1);//Fri Dec 04 09:41:27 CST 2020
    }
```
##### Date小试牛刀
* 字符串"2020-09-08"转换为java.sql.Date
```java
//字符串"2020-09-08"转换为java.sql.Date
    @Test
    public void testDateWork() throws ParseException {
        String birth = "2020-09-08";
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
        Date parse = sdf.parse(birth);
        System.out.println(parse);//Tue Sep 08 00:00:00 CST 2020
        System.out.println(parse.getTime());//1599494400000
        java.sql.Date birthDate = new java.sql.Date(parse.getTime());
        System.out.println(birthDate);//2020-09-08

        SimpleDateFormat sdf1 = new SimpleDateFormat("yyyy-MM-dd hh:mm:ss");
        String format1 = sdf1.format(date);
        System.out.println(format1);
    }
```
* "三天打鱼两天晒网"   1990-01-01   xxxx-xx-xx(时间段) 打鱼？晒网？
```java
//"三天打鱼两天晒网"   1990-01-01   xxxx-xx-xx(时间段) 打鱼？晒网？
    //举例:2020-09-08 ？总天数

    //总天数 % 5 == 1,2,3 : 打鱼
    //总天数 % 5 == 4,0 : 晒网
    @Test
    public void testFishDay() throws ParseException {
        String date = "1990-01-01";
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
        Date startDate = sdf.parse(date);
        Date LocalDate = sdf.parse("2020-09-08");
        long startTime = startDate.getTime();
        long localTime = LocalDate.getTime();
        long time = localTime-startTime;
        long day = time/(1000*60*60*24) + 1;;
        System.out.println(startTime);
        System.out.println(localTime);
        System.out.println(day);
        long num = day % 5;
         if (num == 1 || num == 2 || num == 3){
             System.out.println("该天晒网");
         }else if (num == 4 || num == 0){
             System.out.println("该天打鱼");
         }
        System.out.println(9/5);
    }
```
##### 日期时间格式化类：DateTimeFormatter
* 说明
① 格式化或解析日期、时间
② 类似于SimpleDateFormat

* 常用方法
① 实例化方式：

预定义的标准格式。如：ISO_LOCAL_DATE_TIME;ISO_LOCAL_DATE;ISO_LOCAL_TIME
本地化相关的格式。如：ofLocalizedDateTime(FormatStyle.LONG)
自定义的格式。如：ofPattern(“yyyy-MM-dd hh:mm:ss”)

② 常用方法：
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201206165736.png)
```java
特别的：自定义的格式。如：ofPattern(“yyyy-MM-dd hh:mm:ss”)
//  重点：自定义的格式。如：ofPattern(“yyyy-MM-dd hh:mm:ss”)
DateTimeFormatter formatter3 = DateTimeFormatter.ofPattern("yyyy-MM-dd hh:mm:ss");
//格式化
String str4 = formatter3.format(LocalDateTime.now());
System.out.println(str4);//2019-02-18 03:52:09

//解析
TemporalAccessor accessor = formatter3.parse("2019-02-18 03:52:09");
//{MinuteOfHour=52, HourOfAmPm=3, MilliOfSecond=0, MicroOfSecond=0, NanoOfSecond=0, SecondOfMinute=9},ISO resolved to 2019-02-18
System.out.println(accessor);
```
#### java比较器
在Java中经常会涉及到对象数组的排序问题，那么就涉及到对象之间的比较问题。
* Java实现对象排序的方式有两种：
    * 自然排序：java.lang.Comparable
    * 定制排序：java.util.Comparator
    
##### 自然排序：java.lang.Comparable

* Comparable接口强行对实现它的每个类的对象进行整体排序。这种排序被称为类的自然排序。
* 实现 Comparable 的类必须实现 compareTo(Object obj) 方法，两个对象即通过 compareTo(Object obj) 方法的返回值来比较大小。如果当前对象this大于形参对象obj，则返回正整数，如果当前对象this小于形参对象obj，则返回负整数，如果当前对象this等于形参对象obj，则返回零。
* 实现Comparable接口的对象列表（和数组）可以通过 Collections.sort 或Arrays.sort进行自动排序。实现此接口的对象可以用作有序映射中的键或有序集合中的元素，无需指定比较器。
* 对于类 C 的每一个 e1 和 e2 来说，当且仅当 e1.compareTo(e2) == 0 与e1.equals(e2) 具有相同的 boolean 值时，类 C 的自然排序才叫做与 equals一致。建议（虽然不是必需的）最好使自然排序与 equals 一致。


* Comparable 的典型实现：(默认都是从小到大排列的)
    * String：按照字符串中字符的Unicode值进行比较
    * Character：按照字符的Unicode值来进行比较
    * 数值类型对应的包装类以及BigInteger、BigDecimal：按照它们对应的数值大小进行比较
    * Boolean：true 对应的包装类实例大于 false 对应的包装类实例
    * Date、Time等：后面的日期时间比前面的日期时间大

```java
*Comparable接口的使用举例:自然排序
        * 1.像String,包装类等实现了Comparable接口,重写了compareTo(obj)方法,给出了两个对象比较器
        * 2.像String,包装类重写了compareTo()方法以后,进行了从小到大的排列
        * 3.重写compareTo(obj)的规则:
        *   如果当前对象this大于形参对象obj,则返回正数
        *   如果当前对象this小于形参对象obj,则返回负数
        *   如果当前对象this等于形参对象obj,则返回0
        * 4.对于自定义来说,如果需要排序,我们可以让自定义类实现Comparable接口,重写compareTo()方法
        *   在compareTo(obj)方法中指明如何排序
        * 
```
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201206153009.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201206153037.png)

##### 定制排序：java.util.Comparator
* 当元素的类型没有实现java.lang.Comparable接口而又不方便修改代码，或者实现了java.lang.Comparable接口的排序规则不适合当前的操作，那么可以考虑使用 Comparator 的对象来排序，强行对多个对象进行整体排序的比较。
* 重写compare(Object o1,Object o2)方法，比较o1和o2的大小：如果方法返回正整数，则表示o1大于o2；如果返回0，表示相等；返回负整数，表示o1小于o2。
* 可以将 Comparator 传递给 sort 方法（如 Collections.sort 或 Arrays.sort），从而允许在排序顺序上实现精确控制。
* 还可以使用 Comparator 来控制某些数据结构（如有序 set或有序映射）的顺序，或者为那些没有自然顺序的对象 collection 提供排序。
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201206161223.png)
### 枚举类的使用
主要内容：
* 如何自定义枚举类
* 如何使用关键字enum定义枚举类
* Enum类的主要方法
* 实现接口的枚举类

* * *
     类的对象只有有限个，确定的。举例如下：
     星期：Monday(星期一)、......、Sunday(星期天)
     性别：Man(男)、Woman(女)
     季节：Spring(春节)......Winter(冬天)
     支付方式：Cash（现金）、WeChatPay（微信）、Alipay(支付宝)、BankCard(银行卡)、CreditCard(信用卡)
     就职状态：Busy、Free、Vocation、Dimission
     订单状态：Nonpayment（未付款）、Paid（已付款）、Delivered（已发货）Return（退货）、Checked（已确认）Fulfilled（已配货）、
     线程状态：创建、就绪、运行、阻塞、死亡
     当需要定义一组常量时，强烈建议使用枚举类
* * *
* 枚举类的实现

* * *
    JDK1.5之前需要自定义枚举类
    JDK 1.5 新增的 enum 关键字用于定义枚举类
    若枚举只有一个对象, 则可以作为一种单例模式的实现方式。
     枚举类的属性
    枚举类对象的属性不应允许被改动, 所以应该使用 private final 修饰
    枚举类的使用 private final 修饰的属性应该在构造器中为其赋值
    若枚举类显式的定义了带参数的构造器, 则在列出枚举值时也必须对应的
    传入参数
* * *
##### 自定义枚举类
1. 私有化类的构造器，保证不能在类的外部创建其对象
2. 在类的内部创建枚举类的实例。声明为：public static final
3. 对象如果有实例变量，应该声明为private final，并在构造器中初始化
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201206202626.png)
```java
package com.atguigu.枚举类;


 * @author 布丁熊.菲特尼斯
 * @create 2020-12-06 17:34
 

* 1.枚举类的使用
* 1).枚举类的理解:类的对象只有有限个,确定的.我们称此类为枚举类
* 2).当需要定义一组常量时,强烈建议使用枚举类
* 3).如果枚举类中只有一个对象,则可以作为单例模式的实现方式
*
* 2.如何定义枚举类
* 方式一:jdk5.0之前,自定义枚举类
* 方式二:jdk5.0,可以使用enum关键字定义枚举类
* 

public class ModifyEnum {
    public static void main(String[] args) {
        Season season = Season.AUTUMN;
        System.out.println(season);
    }
}
//自定义枚举类
class Season{
    //1.声明Season对象的属性:private final修饰
    private final String seasonName;//季节的名称
    private final String seaonDesc;//季节的描述
    //2.私有化类的构造器,并给对象属性赋值
    private Season(String seasonName,String seaonDesc){
        this.seasonName = seasonName;
        this.seaonDesc = seaonDesc;
    }

    //3.提供当前枚举类的多个对象:public static final
    public static final Season SPRING = new Season("春天","春回大地");
    public static final Season SUMMER = new Season("夏天","夏日炎炎");
    public static final Season AUTUMN = new Season("秋天","秋高气爽");
    public static final Season WINTER = new Season("冬天","寒风冷冽");

    //4.获取枚举类对象的属性
    public String getSeasonName() {
        return seasonName;
    }

    public String getSeaonDesc() {
        return seaonDesc;
    }
    //5.重写toString方法

    @Override
    public String toString() {
        return "Season{" +
                "seasonName='" + seasonName + '\'' +
                ", seaonDesc='" + seaonDesc + '\'' +
                '}';
    }
}
```
* 使用enum定义枚举类

* 使用说明
    * 使用 enum 定义的枚举类默认继承了 java.lang.Enum类，因此不能再继承其他类
    * 枚举类的构造器只能使用 private 权限修饰符
    * 枚举类的所有实例必须在枚举类中显式列出(, 分隔; 结尾)。列出的实例系统会自动添加           public static final 修饰
    * **必须在枚举类的第一行声明枚举类对象**
    * JDK 1.5 中可以在 switch 表达式中使用Enum定义的枚举类的对象作为表达式, case 子句       可以直接使用枚举值的名字, 无需添加枚举类作为限定
    ![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201206202711.png)    
```java
package com.atguigu.枚举类;


 * @author 布丁熊.菲特尼斯
 * @create 2020-12-06 19:15
 

 * 使用enum关键字定义枚举类
 * 说明:定义的枚举类默认继承于class java.lang.Enum
 *
public class SeasonsTest {
    public static void main(String[] args) {
        Seasons seasons = Seasons.SUMMER;
        System.out.println(seasons);//SUMMER
        System.out.println(seasons.getClass().getSuperclass());//class java.lang.Enum
    }
}
//使用enum关键字枚举类
enum Seasons{

    //1.提供当前枚举类的对象,多个对象之间用","隔开,末尾对象";"结束
    SPRING("春天","春回大地"),
    SUMMER("夏天","夏日炎炎"),
    AUTUMN("秋天","秋高气爽"),
    WINTER("冬天","寒风冷冽");

    //2.声明Season对象的属性:private final修饰
    private final String seasonName;
    private final String seaonDesc;
    //3.私有化类的构造器,并给对象属性赋值
    private Seasons(String seasonName,String seaonDesc){
        this.seasonName = seasonName;
        this.seaonDesc = seaonDesc;
    }
    //5.获取枚举类对象的属性
    public String getSeasonName() {
        return seasonName;
    }

    public String getSeaonDesc() {
        return seaonDesc;
    }
    //6.重写toString方法

    @Override
    public String toString() {
        return "Season{" +
                "seasonName='" + seasonName + '\'' +
                ", seaonDesc='" + seaonDesc + '\'' +
                '}';
    }
    }

```
* Enum类的主要方法
    * values()方法：返回枚举类型的对象数组。该方法可以很方便地遍历所有的枚举值。
    * valueOf(String str)：可以把一个字符串转为对应的枚举类对象。要求字符串必须是枚举类      对象的“名字”。如不是，会有运行时异常：IllegalArgumentException。
    * toString()：返回当前枚举类对象常量的名称
    ![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201206203701.png)

* 实现接口的枚举类
>和普通 Java 类一样，枚举类可以实现一个或多个接口

* 若每个枚举值在调用实现的接口方法呈现相同的行为方式，则只要统一实现该方法即可。
* 若需要每个枚举值在调用实现的接口方法呈现出不同的行为方式,则可以让每个枚举值分别来实现该方法
```java
interface info{
    void show();
}
//使用enum关键字枚举类
enum Seasons implements info{

    //1.提供当前枚举类的对象,多个对象之间用","隔开,末尾对象";"结束
    SPRING("春天","春回大地"){
        @Override
        public void show() {

        }
    },
    SUMMER("夏天","夏日炎炎"){
        @Override
        public void show() {

        }
    },
    AUTUMN("秋天","秋高气爽"){
        @Override
        public void show() {

        }
    },
    WINTER("冬天","寒风冷冽"){
        @Override
        public void show() {
            
        }
    };

    //2.声明Season对象的属性:private final修饰
    private final String seasonName;
    private final String seaonDesc;
    //3.私有化类的构造器,并给对象属性赋值
    private Seasons(String seasonName,String seaonDesc){
        this.seasonName = seasonName;
        this.seaonDesc = seaonDesc;
    }
    //5.获取枚举类对象的属性
    public String getSeasonName() {
        return seasonName;
    }

    public String getSeaonDesc() {
        return seaonDesc;
    }
    //6.重写toString方法
    }

```
### 注解(Annotation) 
主要内容:

* 注解(Annotation)概述
 常见的Annotation示例
 自定义Annotation
 JDK中的元注解
 利用反射获取注解信息（在反射部分涉及）
 JDK 8中注解的新特性

* 注解的概述

* * *

    从 JDK 5.0 开始, Java 增加了对元数据(MetaData) 的支持, 也就是Annotation(注解)       
     Annotation 其实就是代码里的特殊标记, 这些标记可以在编译, 类加载, 运行时被读取, 并   执行相应的处理。通过使用 Annotation, 程序员可以在不改变原有逻辑的情况下, 在源文件      中嵌入一些补充信息。
    代码分析工具、开发工具和部署工具可以通过这些补充信息进行验证或者进行部署。
    Annotation 可以像修饰符一样被使用, 可用于修饰包,类, 构造器, 方 法, 成员变量, 参数,局    部变量的声明, 这些信息被保存在 Annotation  的 “name=value” 中

* * *

    在JavaSE中，注解的使用目的比较简单，例如标记过时的功能，忽略警告等。JavaEE/Android中注解占据了更重要的角色，例如用来配置应用程序的任何切面，代替JavaEE旧版中所遗留的繁冗代码和XML配置等。
    未来的开发模式都是基于注解的，JPA是基于注解的，Spring2.5以上都是基于注解的，Hibernate3.x以后也是基于注解的，现在的Struts2有一部分也是基于注解的了，注解是一种趋势，一定程度上可以说：框架 = 注解 + 反射 + 设计模式。

* 常见的Annotation示例
* 示例一：生成文档相关的注解
```java
@author 标明开发该类模块的作者，多个作者之间使用,分割
@version 标明该类模块的版本
@see 参考转向，也就是相关主题
@since 从哪个版本开始增加的
@param 对方法中某参数的说明，如果没有参数就不能写
@return 对方法返回值的说明，如果方法的返回值类型是void就不能写
@exception 对方法可能抛出的异常进行说明 ，如果方法没有用throws显式抛出的异常就不能写
其中
@param @return 和 @exception 这三个标记都是只用于方法的。
@param的格式要求：@param 形参名 形参类型 形参说明
@return 的格式要求：@return 返回值类型 返回值说明
@exception的格式要求：@exception 异常类型 异常说明
@param和@exception可以并列多个
```
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201207101042.png)

* 示例二：在编译时进行格式检查(JDK内置的三个基本注解)
```java
@Override: 限定重写父类方法, 该注解只能用于方法
@Deprecated: 用于表示所修饰的元素(类, 方法等)已过时。通常是因为所修饰的结构危险或存在更好的选择
@SuppressWarnings: 抑制编译器警告
```
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201207101207.png)

* 示例三：跟踪代码依赖性，实现替代配置文件功能
* Servlet3.0提供了注解(annotation),使得不再需要在web.xml文件中进行Servlet的部署。
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201207101342.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201207101411.png)

* spring框架中关于“事务”的管理
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201207101721.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201207101745.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201207101953.png)
#### 自定义Annotation
* 定义新的 Annotation 类型使用 @interface 关键字
* 自定义注解自动继承了java.lang.annotation.Annotation接口
* Annotation 的成员变量在 Annotation 定义中以无参数方法的形式来声明。其方法名和返回值定义了该成员的名字和类型。我们称为配置参数。类型只能是八种基本数据类型、String类型、Class类型、enum类型、Annotation类型、以上所有类型的数组。
* 可以在定义 Annotation 的成员变量时为其指定初始值, 指定成员变量的初始值可使用 default 关键字
* 如果只有一个参数成员，建议使用参数名为value
* 如果定义的注解含有配置参数，那么使用时必须指定参数值，除非它有默认值。格式是“参数名 = 参数值”，如果只有一个参数成员，且名称为value，可以省略“value=”
* 没有成员定义的 Annotation 称为标记; 包含成员变量的 Annotation 称为元数据Annotation
注意：自定义注解必须配上注解的信息处理流程（使用反射）才有意义

>如果自定义注解没有成员，表明只是一个标识作用
>如果注解有成员，在使用注解时，需要指明成员的值

```java
@MyAnnotation(value="尚硅谷")
public class MyAnnotationTest {
public static void main(String[] args) {
Class clazz = MyAnnotationTest.class;
Annotation a = clazz.getAnnotation(MyAnnotation.class);
MyAnnotation m = (MyAnnotation) a;
String info = m.value();
System.out.println(info);
} }
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.TYPE)
@interface MyAnnotation{
String value() default "auguigu"; }
```

#### JDK 中的元注解
* JDK 的元 (注解)Annotation 用于修饰其他 Annotation 定义
* JDK5.0提供了4个标准的meta-annotation类型，分别是：
    * Retention
    * Target
    * Documented
    * Inherited

>元数据的理解：String name = “atguigu”;

```java
@Retention: 只能用于修饰一个 Annotation 定义, 用于指定该 Annotation 的生命周期,       @Rentention 包含一个 RetentionPolicy 类型的成员变量, 使用@Rentention 时必须为该 value 成员变量指定值: 
RetentionPolicy.SOURCE:在源文件中有效（即源文件保留），编译器直接丢弃这种策略的注释
RetentionPolicy.CLASS:在class文件中有效（即class保留） ， 当运行 Java 程序时, JVM 
不会保留注解。 这是默认值
RetentionPolicy.RUNTIME:在运行时有效（即运行时保留），当运行 Java 程序时, JVM 会
保留注释（加载到内存里）。程序可以通过反射获取该注释。
```
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201207140738.png)
```java
public enum RetentionPolicy {
    
     * Annotations are to be discarded by the compiler.
     
    SOURCE,

    
     * Annotations are to be recorded in the class file by the compiler
     * but need not be retained by the VM at run time.  This is the default
     * behavior.
     
    CLASS,

    
     * Annotations are to be recorded in the class file by the compiler and
     * retained by the VM at run time, so they may be read reflectively.
     *
     * @see java.lang.reflect.AnnotatedElement
     
    RUNTIME
}
```
```java
@Retention(RetentionPolicy.SOURCE)
@interface MyAnnotation1{ }
@Retention(RetentionPolicy.RUNTIME) @interface MyAnnotation2{ }
```
@Target: 用于修饰 Annotation 定义, 用于指定被修饰的 Annotation 能用于修饰哪些程序元素。 @Target 也包含一个名为 value 的成员变量。
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201207150639.png)

@Documented: 用于指定被该元 Annotation 修饰的 Annotation 类将被javadoc 工具提取成文档。默认情况下，javadoc是不包括注解的。
定义为Documented的注解必须设置Retention值为RUNTIME。
@Inherited: 被它修饰的 Annotation 将具有继承性。如果某个类使用了被@Inherited 修饰的 Annotation, 则其子类继承该class后将自动具有该注解。
比如：如果把标有@Inherited注解的自定义的注解标注在类级别上，子类则可以继承父类类级别的注解
>注意：一个类型被@Inherited修饰后，类并不从它所实现的接口继承annotation，方法并从它所重载的方法继承annotation。

实际应用中，使用较少

* * *
##### 利用反射获取注解信息

JDK 5.0 在 java.lang.reflect 包下新增了 AnnotatedElement 接口, 该接口代表程序中可以接受注解的程序元素
当一个 Annotation 类型被定义为运行时 Annotation 后, 该注解才是运行时可见, 当 class 文件被载入时保存在 class 文件中的 Annotation 才会被虚拟机读取
程序可以调用 AnnotatedElement对象的如下方法来访问 Annotation 信息
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201207154822.png)

##### 注解应用结构图
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201207222355.png)
##### JDK8中注解的新特性

###### 可重复注解
Java 8对注解处理提供了两点改进：可重复的注解及可用于类型的注解。此外，
反射也得到了加强，在Java8中能够得到方法参数的名称。这会简化标注在方法
参数上的注解。
* 可重复注解示例
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201207161407.png)

1.在MyAnnotation上声明@Repeatable,成员值为MyAnnotations.class
2.MyAnnotation的Target和Retention等元注解和MyAnnotations相同    
* * *
###### 类型注解
    JDK1.8之后，关于元注解@Target的参数类型ElementType枚举值多了两个：
    TYPE_PARAMETER,TYPE_USE。 
     在Java 8之前，注解只能是在声明的地方所使用，Java8开始，注解可以应用在任何地方。      ElementType.TYPE_PARAMETER 表示该注解能写在类型变量的声明语句中（如：泛型声       明）。
     ElementType.TYPE_USE 表示该注解能写在使用类型的任何语句中。

* * *
```java
public class TestTypeDefine<@TypeDefine() U> {
private U u;
public <@TypeDefine() T> void test(T t){
} }
@Target({ElementType.TYPE_PARAMETER})
@interface TypeDefine{ }
```
```java

@MyAnnotation
public class AnnotationTest<U> {
@MyAnnotation
private String name;
public static void main(String[] args) {
AnnotationTest<@MyAnnotation String> t = null;
int a = (@MyAnnotation int) 2L;
@MyAnnotation
int b = 10;
}
public static <@MyAnnotation T> void method(T t) {
}
public static void test(@MyAnnotation String arg) throws @MyAnnotation Exception {
}
}
@Target(ElementType.TYPE_USE)
@interface MyAnnotation {
}

```
#### 补充
```
java中元注解有四个： @Retention @Target @Document @Inherited；

　　 @Retention：注解的保留位置　　　　　　　　　

　　　　　　@Retention(RetentionPolicy.SOURCE)   //注解仅存在于源码中，在class字节码文件中不包含

　　　　　　@Retention(RetentionPolicy.CLASS)     // 默认的保留策略，注解会在class字节码文件中存在，但运行时无法获得，

　　　　　　@Retention(RetentionPolicy.RUNTIME)  // 注解会在class字节码文件中存在，在运行时可以通过反射获取到

　　@Target:注解的作用目标
　　　　　　　　@Target(ElementType.TYPE)   //接口、类、枚举

　　　　　　　　@Target(ElementType.FIELD) //字段、枚举的常量

　　　　　　　　@Target(ElementType.METHOD) //方法

　　　　　　　　@Target(ElementType.PARAMETER) //方法参数

　　　　　　　　@Target(ElementType.CONSTRUCTOR)  //构造函数

　　　　　　　　@Target(ElementType.LOCAL_VARIABLE)//局部变量

　　　　　　　　@Target(ElementType.ANNOTATION_TYPE)//注解

　　　　　　　　@Target(ElementType.PACKAGE) ///包   

     @Document：说明该注解将被包含在javadoc中

　  @Inherited：说明子类可以继承父类中的该注解
————————————————
版权声明：本文为CSDN博主「SingleShu888」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/sw5131899/article/details/54947192
```
### java集合框架
* **集合框架概述**
* * *

    一方面， 面向对象语言对事物的体现都是以对象的形式，为了方便对多个对象的操作，就要对对象进行存储。另一方面，使用Array存储对象方面具有一些弊端，而Java 集合就像一种容器，可以动态地把多个对象的引用放入容器中。
    数组在内存存储方面的特点：
     数组初始化以后，长度就确定了。
     数组声明的类型，就决定了进行元素初始化时的类型
     数组在存储数据方面的弊端：
     数组初始化以后，长度就不可变了，不便于扩展
     数组中提供的属性和方法少，不便于进行添加、删除、插入等操作，且效率不高。同时无法直接获取存储元素的个数
     数组存储的数据是有序的、可以重复的。---->存储数据的特点单一
     Java 集合类可以用于存储数量不等的多个对象，还可用于保存具有映射关系的关联数组。
    

* 集合使用的场景

![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201207171017.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201207171146.png)

* Java 集合可分为 Collection 和 Map 两种体系

Collection接口：单列数据，定义了存取一组对象的方法的集合
List：元素有序、可重复的集合
Set：元素无序、不可重复的集合
 Map接口：双列数据，保存具有映射关系“key-value对”的集合

* 集合框架分类
```java
|----Collection接口：单列集合，用来存储一个一个的对象
    |----List接口：存储有序的，可重复的数据  ---> "动态"数组
        |----ArrayList，LinkedList，Vector
    
    |----Set接口：存储无序的，不可重复的数据     ---> 高中讲的"集合"
        |----HashSet，LinkedHashSet，TreeSet
    
|----Map接口：双列集合，用来存储一对(key - value)一对数据   --->高中函数：y=f(x)
    |----HashMap，LinkedHashMap，TreeMap，HashTable，Properties
```

##### 每日一题复习归纳
    1.什么是枚举类？枚举类的对象声明的修饰符都有哪些？
        枚举类：类中的对象的个数是确定的，有限个
        private final（No）---> 修饰类中属性的
        private static final（YES）---> 修饰类中对象的
        
    2.什么是元注解？说说Retention和Target元注解的作用
        元注解：对现有的注解进行解释说明的注解
      Retention：指明所修饰的注解的生命周期（SOURCE CLASS RUNTIME）
      
    3.说说你所理解的集合框架都有哪些接口，存储数据的特点是什么？
     |----Collection接口：单列集合，用来存储一个一个的对象
        |----List接口：存储有序的，可重复的数据  ---> "动态"数组
            |----ArrayList，LinkedList，Vector
        |----Set接口：存储无序的，不可重复的数据     ---> 高中讲的"集合"
            |----HashSet，LinkedHashSet，TreeSet
    |----Map接口：双列集合，用来存储一对(key - value)一对数据   --->高中函数：y=f(x)
        |----HashMap，LinkedHashMap，TreeMap，HashTable，Properties
        
    4.比较throw和throws的区别
        throw:生成一个异常对象，并抛出 在使用方法的内部 <----> 自动抛出异常对象
        throws:处理异常的方式，使用在方法声明处的末尾 <----> try-catch-finally
            总结："上游排污，下游治污"
            
    5.谈谈你对同步代码块中同步监视器和共享数据的理解及各自要求
    * 同步监视器：俗称锁
    1）任何一个类的对象都可以充当锁
    2）多个线程共用一把锁
    
    * 共享数据
    1）多个线程共同操作的数据，即为共享数据
    2）需要使用同步机制将操作共享数据的代码包起来，不能包多了，也不能包少了  

 ##### 使用enum定义枚举类之后，如何让枚举类对象分别实现接口：
```java
interface info{
    void show();
}
//使用enum关键字枚举类
enum Seasons implements info{

    //1.提供当前枚举类的对象,多个对象之间用","隔开,末尾对象";"结束
    SPRING("春天","春回大地"){
        @Override
        public void show() {

        }
    },
    SUMMER("夏天","夏日炎炎"){
        @Override
        public void show() {

        }
    },
    AUTUMN("秋天","秋高气爽"){
        @Override
        public void show() {

        }
    },
    WINTER("冬天","寒风冷冽"){
        @Override
        public void show() {

        }
    };

    //2.声明Season对象的属性:private final修饰
    private final String seasonName;
    private final String seaonDesc;
    //3.私有化类的构造器,并给对象属性赋值
    private Seasons(String seasonName,String seaonDesc){
        this.seasonName = seasonName;
        this.seaonDesc = seaonDesc;
    }
    //5.获取枚举类对象的属性
    public String getSeasonName() {
        return seasonName;
    }

    public String getSeaonDesc() {
        return seaonDesc;
    }
    //6.重写toString方法
    }
```
##### 元注解 ：对现有的注解进行解释说明的注解

* * *

* jdk 提供的4种元注解：
* [ ] Retention：指定所修饰的 Annotation 的生命周期：
SOURCE，CLASS（默认行为)，RUNTIME 只声明为RUNTIME生命周期的注解，才能通过反射获取。
* [ ] Target:用于指定被修饰的 Annotation 能用于修饰哪些程序元素
*******出现的频率较低的注解，如下*******
* [ ] Documented:表示所修饰的注解在被javadoc解析时，保留下来。
* [ ] Inherited:被它修饰的 Annotation 将具继承性。

* 如何获取注解信息:通过发射来进行获取、调用？
前提：要求此注解的元注解Retention中声明的生命周期状态为：RUNTIME.

* * *
有关注解@interfece博客链接：
>https://blog.csdn.net/sun_promise/article/details/51315032?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-3.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-3.control

若上述链接无效，重复链接
```java
https://blog.csdn.net/sun_promise/article/details/51315032?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-3.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-3.control
```

* * *

![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201207221626.png)

##### Collection接口继承树
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201208102831.png)

![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201211140357.png)

##### 单列集合框架结构
```java
|----Collection接口：单列集合，用来存储一个一个的对象
    |----List接口：存储有序的，可重复的数据  ---> "动态"数组
        |----ArrayList，LinkedList，Vector
    
    |----Set接口：存储无序的，不可重复的数据     ---> 高中讲的"集合"
        |----HashSet，LinkedHashSet，TreeSet 
```
##### Map接口继承树
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201208170812.png)

#### Collection接口方法
##### Collection接口

* Collection 接口是 List、Set 和 Queue 接口的父接口，该接口里定义的方法既可用于操作 Set 集合，也可用于操作 List 和 Queue 集合。
* JDK不提供此接口的任何直接实现，而是提供更具体的子接口(如：Set和List)实现。
* 在 Java5 之前，Java 集合会丢失容器中所有对象的数据类型，把所有对象都当成 Object 类型处理；从 JDK 5.0 增加了泛型以后，Java 集合可以记住容器中对象的数据类型。

##### Collection接口方法

* * *

1、添加
 add(Object obj)
 addAll(Collection coll) 2、获取有效元素的个数
 int size()
3、清空集合
 void clear()
4、是否是空集合 
 boolean isEmpty()
5、是否包含某个元素
 boolean contains(Object obj)：是通过元素的equals方法来判断是否是同一个对象
 boolean containsAll(Collection c)：也是调用元素的equals方法来比较的。拿两个集合的元素挨个比较。
6、删除
 boolean remove(Object obj) ：通过元素的equals方法判断是否是要删除的那个元素。只会删除找到的第一个元素
 boolean removeAll(Collection coll)：取当前集合的差集
7、取两个集合的交集
 boolean retainAll(Collection c)：把交集的结果存在当前集合中，不影响c
8、集合是否相等
 boolean equals(Object obj)
9、转成对象数组
 Object[] toArray()
10、获取集合对象的哈希值
 hashCode()
11、遍历
 iterator()：返回迭代器对象，用于集合遍历

* * *

#### Iterator迭代器接口
##### 使用 Iterator 接口遍历集合元素
     Iterator对象称为迭代器(设计模式的一种)，主要用于遍历 Collection 集合中的元素。
     GOF给迭代器模式的定义为：提供一种方法访问一个容器(container)对象中各个元素，而又不需暴露该对象的内部细节。迭代器模式，就是为容器而生。类似于“公交车上的售票员”、“火车上的乘务员”、“空姐”。 
     Collection接口继承了java.lang.Iterable接口，该接口有一个iterator()方法，那么所有实现了Collection接口的集合类都有一个iterator()方法，用以返回一个实现了Iterator接口的对象。
     Iterator 仅用于遍历集合，Iterator 本身并不提供承装对象的能力。如果需要创建Iterator 对象，则必须有一个被迭代的集合。
     集合对象每次调用iterator()方法都得到一个全新的迭代器对象，默认游标都在集合的第一个元素之前。

##### Iterator接口的方法
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201208172154.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201208172228.png)
>在调用it.next()方法之前必须要调用it.hasNext()进行检测。若不调用，且下一条记录无效，直接调用it.next()会抛出NoSuchElementException异常。

##### 迭代器的执行原理
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201208172437.png)    

##### Iterator接口remove()方法
```java
Iterator iter = coll.iterator();//回到起点
while(iter.hasNext()){
Object obj = iter.next();
if(obj.equals("Tom")){
iter.remove();
} }
```
* 注意
    * Iterator可以删除集合的元素，但是是遍历过程中通过迭代器对象的remove方法，不是集合对象的remove方法。
    * 如果还未调用next()或在上一次调用 next 方法之后已经调用了 remove 方法，再调用remove都会报IllegalStateException。
    
##### 使用 foreach 循环遍历集合元素

 Java 5.0 提供了 foreach 循环迭代访问 Collection和数组。
 遍历操作不需获取Collection或数组的长度，无需使用索引访问元素。
 遍历集合的底层调用Iterator完成操作。
 foreach还可以用来遍历数组
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201208185902.png)

* 练习：判断输出结果为何？
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201208190051.png)    

```java
|----Collection接口：单列集合，用来存储一个一个的对象
    |----List接口：存储有序的，可重复的数据  ---> "动态"数组，替换原有的数组
        |----ArrayList：作为List
        |----LinkedList
        |----Vector
```
#### Collection子接口之一：List接口
##### List接口概述
鉴于Java中数组用来存储数据的局限性，我们通常使用List替代数组
 List集合类中元素有序、且可重复，集合中的每个元素都有其对应的顺序索引。
 List容器中的元素都对应一个整数型的序号记载其在容器中的位置，可以根据序号存取容器中的元素。
 JDK API中List接口的实现类常用的有：ArrayList、LinkedList和Vector。

##### List接口方法
 List除了从Collection集合继承的方法外，List 集合里添加了一些根据索引来
操作集合元素的方法。
```java
void add(int index, Object ele):在index位置插入ele元素
boolean addAll(int index, Collection eles):从index位置开始将eles中的所有元素添加进来
Object get(int index):获取指定index位置的元素
int indexOf(Object obj):返回obj在集合中首次出现的位置
int lastIndexOf(Object obj):返回obj在当前集合中末次出现的位置
Object remove(int index):移除指定index位置的元素，并返回此元素
Object set(int index, Object ele):设置指定index位置的元素为ele
List subList(int fromIndex, int toIndex):返回从fromIndex到toIndex位置的子集合

总结：常用方法
增：add(Object obj)
删：remove(int index) / remove(Object obj)
改：set(int index,Object ele)   
查：get(int index)
插：add(int index,Object ele)
长度：size()
遍历：Iterator迭代器方式   增强for循环  普通for循环
```
#### List实现类之一：ArrayList

* ArrayList 是 List 接口的典型实现类、主要实现类
* 本质上，ArrayList是对象引用的一个”变长”数组
* ArrayList的JDK1.8之前与之后的实现区别？
    * JDK1.7：ArrayList像饿汉式，直接创建一个初始容量为10的数组
    * JDK1.8：ArrayList像懒汉式，一开始创建一个长度为0的数组，当添加第一个元素时再创建一个始容量为10的数组
* Arrays.asList(…) 方法返回的 List 集合，既不是 ArrayList 实例，也不是Vector 实例。        Arrays.asList(…) 返回值是一个固定长度的 List 集合
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201209160256.png)

#### System.arraycopy() 和 Arrays.copyOf()方法
**阅读源码的话，我们就会发现 ArrayList 中大量调用了这两个方法。比如：我们上面讲的扩容操作以及add(int index, E element)、toArray() 等方法中都用到了该方法！**

##### System.arraycopy() 方法
```java

    /**
     * 在此列表中的指定位置插入指定的元素。
     *先调用 rangeCheckForAdd 对index进行界限检查；然后调用 ensureCapacityInternal 方法保证capacity足够大；
     *再将从index开始之后的所有成员后移一个位置；将element插入index位置；最后size加1
     */
    public void add(int index, E element) {
        rangeCheckForAdd(index);

        ensureCapacityInternal(size + 1);  // Increments modCount!!
        //arraycopy()方法实现数组自己复制自己
        //elementData:源数组; index:源数组中的起始位置;
        //elementData：目标数组；index + 1：目标数组中的起始位置； 
        //size - index：要复制的数组元素的数量；
        //源数组 ---> 目标数组(复制过程)
        System.arraycopy(elementData, index, elementData, index + 1, size - index);
        elementData[index] = element;
        size++;
    }
```
**我们写一个简单的方法测试以下：**
```Java

public class ArraycopyTest {

    public static void main(String[] args) {
        // TODO Auto-generated method stub
        int[] a = new int[10];
        a[0] = 0;
        a[1] = 1;
        a[2] = 2;
        a[3] = 3;
        System.arraycopy(a, 2, a, 3, 3);
        a[2]=99;
        for (int i = 0; i < a.length; i++) {
            System.out.print(a[i] + " ");
        }
    }

}
结果：
0 1 99 2 3 0 0 0 0 0
```
##### Arrays.copyOf()方法
**个人觉得使用 Arrays.copyOf()方法主要是为了给原有数组扩容，测试代码如下：**
```java

public class ArrayscopyOfTest {

    public static void main(String[] args) {
        int[] a = new int[3];
        a[0] = 0;
        a[1] = 1;
        a[2] = 2;
        int[] b = Arrays.copyOf(a, 10);
        System.out.println("b.length"+b.length);
    }}
    
结果：10
```
##### 两者联系和区别
```java

联系：看两者源代码可以发现 copyOf()内部实际调用了 System.arraycopy()
方法区别：arraycopy() 需要目标数组，将原数组拷贝到你自己定义的数组里或者原数组，而且可以选择拷贝的起点和长度以及放入新数组中的位置 copyOf() 是系统自动在内部新建一个数组，并返回该数组。
```

```java

   /**
     以正确的顺序返回一个包含此列表中所有元素的数组（从第一个到最后一个元素）; 返回的数组的运行时类型是指定数组的运行时类型。
     */
    public Object[] toArray() {
    //elementData：要复制的数组；size：要复制的长度
        return Arrays.copyOf(elementData, size);
    }
```
##### 面试题
```java
@Test
public void testListRemove() {
List list = new ArrayList();
list.add(1);
list.add(2);
list.add(3);
updateList(list);
System.out.println(list);//
}
private static void updateList(List list) {
list.remove(2);
}
此时remove(index:2),移除的是下标index:2索引对应的元素
```
#### List实现类之二：LinkedList
* 对于频繁的插入或删除元素的操作，建议使用LinkedList类，效率较高
* 新增方法
    * void addFirst(Object obj)
    * void addLast(Object obj)
    * Object getFirst()
    * Object getLast()
    * Object removeFirst()
    * Object removeLast()

* LinkedList：双向链表，内部没有声明数组，而是定义了Node类型的first和last，
  用于记录首末元素。同时，定义内部类Node，作为LinkedList中保存数据的基
  本结构。Node除了保存数据，还定义了两个变量：
    * prev变量记录前一个元素的位置
    * next变量记录下一个元素的位置
```java
private static class Node<E> {
E item;
Node<E> next;
Node<E> prev;
Node(Node<E> prev, E element, Node<E> next) {
this.item = element;
this.next = next;
this.prev = prev;
} }
```
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201209163354.png)

##### 面试题：ArrayList,LinkedList,Vector三者的异同?
```java
相同点：三个类都是实现了List接口，存储数据的特点相同：存储有序的，可重复的数据
不同点：
|----Collection接口：单列集合，用来存储一个一个的对象
    |----List接口：存储有序的，可重复的数据  ---> "动态"数组
        |----ArrayList：作为List接口的主要实现类;线程不安全的,效率高的;底层使用Object[] elementData存储
        |----LinkedList：对于频繁的插入，删除操作，使用此类效率比ArrayList高;底层使用双向链表存储
        |----Vector：作为List接口的古老实现类;线程是安全的,效率低的;底层使用Object[] elementData存储
```
##### ArrayList的源码分析：基于JDK7版本     
```java
1.|----Collection接口：单列集合，用来存储一个一个的对象
    |----List接口：存储有序的，可重复的数据  ---> "动态"数组
        |----ArrayList：作为List接口的主要实现类;线程不安全的,效率高的;底层使用Object[] elementData存储
        |----LinkedList：对于频繁的插入，删除操作，使用此类效率比ArrayList高;底层使用双向链表存储
        |----Vector：作为List接口的古老实现类;线程是安全的,效率低的;底层使用Object[] elementData存储
2.ArrayList的源码分析: 
 2.1 基于JDK7版本
    ArrayList list = new ArrayList();//底层创建了长度是10的Object[]数组elementData
    list.add(123);//elementData[0] = new Integer(123);
    ...
    list.add(11);//如果此次的添加导致底层elementData数组容量不够，则扩容
    默认情况下，扩容为原来容量的1.5倍，同时需要将原有数组中的数据复制到新的数组中
    结论：建议开发中使用带参的构造器：ArrayList list = new ArrayList(int capacity);
 2.2 JDK8中ArrayList的变化：
    ArrayList list = new ArrayList();//底层Object[] elementData初始化为{}，并没有创建长度为10的数组
    list.add(123);//第一次调用add()时,底层才创建了长度为10的数组,并将数据123添加到elementData[0]数组中
    ...
    后续的添加和扩容操作与jdk7无差异
 2.3 小结：JDK7中的ArrayList的对象的创建类似于单例的饿汉式，而JDK8中的ArrayList的对象的创建类似于单例的懒汉式，      延迟了数据的创建，节省了内存空间
        
```
##### LinkedList的源码分析：基于JDK8版本     
```java
3. LinkedList的源码分析：
    LinkedList list = new LinkedList();//内部声明了Node类型的first和last属性,默认值为null
    list.add(123);//将数据123封装到Node结点中,并创建Node结点对象
    其中，Node定义为：体现了LinkedList的双向链表的思想
    private static class Node<E> {
        E item;
        Node<E> next;
        Node<E> prev;

        Node(Node<E> prev, E element, Node<E> next) {
            this.item = element;
            this.next = next;
            this.prev = prev;
        }
    }   
```
##### Vector的源码分析：基于JDK7和JDK8
    Vector 是一个古老的集合，JDK1.0就有了。大多数操作与ArrayList相同，区别之处在于Vector是线程安全的。
    在各种list中，最好把ArrayList作为缺省选择。当插入、删除频繁时，使用LinkedList；Vector总是比ArrayList慢，所以尽量避免使用。
    新增方法：
     void addElement(Object obj) 
     void insertElementAt(Object obj,int index)
     void setElementAt(Object obj,int index)
     void removeElement(Object obj) 
     void removeAllElements()
```java
4. Vector的源码分析：JDK7和JDK8中通过Vector()构造器创建对象时,底层都创建了长度为10的数组
    在扩容方面，默认扩容为原来的数组长度的2倍
```

##### 请问ArrayList/LinkedList/Vector的异同？谈谈你的理解？ArrayList底层是什么？扩容机制？Vector和ArrayList的最大区别?

     ArrayList和LinkedList的异同
    二者都线程不安全，相对线程安全的Vector，执行效率高。
    此外，ArrayList是实现了基于动态数组的数据结构，LinkedList基于链表的数据结构。对于
    随机访问get和set，ArrayList觉得优于LinkedList，因为LinkedList要移动指针。对于新增
    和删除操作add(特指插入)和remove，LinkedList比较占优势，因为ArrayList要移动数据。
     ArrayList和Vector的区别
    Vector和ArrayList几乎是完全相同的,唯一的区别在于Vector是同步类(synchronized)，属于 强同步类。因此开销就比ArrayList要大，访问要慢。正常情况下,大多数的Java程序员使用
    ArrayList而不是Vector,因为同步完全可以由程序员自己来控制。Vector每次扩容请求其大
    小的2倍空间，而ArrayList是1.5倍。Vector还有一个子类Stack。

#### Collection子接口之二：Set接口
##### Set接口概述
 Set接口是Collection的子接口，set接口没有提供额外的方法
 Set 集合不允许包含相同的元素，如果试把两个相同的元素加入同一个Set 集合中，则添加操作失败。
 Set 判断两个对象是否相同不是使用 == 运算符，而是根据 equals() 方法

##### Set实现类之一：HashSet
```java
HashSet 是 Set 接口的典型实现，大多数时候使用 Set 集合时都使用这个实现类。
HashSet 按 Hash 算法来存储集合中的元素，因此具有很好的存取、查找、删除性能。   

HashSet 具有以下特点：
  不能保证元素的排列顺序
  HashSet 不是线程安全的
  集合元素可以是 null
  HashSet 集合判断两个元素相等的标准：两个对象通过 hashCode() 方法比较相等，并且两  个对象的 equals() 方法返回值也相等。 
  对于存放在Set容器中的对象，对应的类一定要重写equals()和hashCode(Object obj)方法，    以实现对象相等规则。即：“相等的对象必须具有相等的散列码”。
```
```java
|----Collection接口：单列集合，用来存储一个一个的对象
    |----Set接口：存储无序的，不可重复的数据     ---> 高中讲的"集合"
        |----HashSet: 作为Set接口的主要实现类;线程不安全的;
              可以存储null值---底层HashMap
           |----LinkedHashSet: 作为HashSet的子类;遍历其内部数据时,可以按照添加的顺序进                   行遍历，添加元素时内部还是无序存储，在添加数据的同时，每个数据还维护了两                    个引用，记录此数据前一个数据和后一个数据，对于频繁的遍历操作，
                      LinkedHashSet效率高于HashSet---底层LinkedHashMap
       |----TreeSet: 可以按照添加对象的指定属性,进行排序,不允许存放null值---底层TreeMap
        
 1. Set接口中没有额外定义新的方法，使用的都是Collection中声明过的方法
 2. 要求：向Set中添加的数据，其所在的类一定要重写hashCode()和equals()方法
    要求：重写的hashCode()和equals()尽可能保持一致性：相等的对象必须具有相同的散列码 
    重写两个方法的小技巧：对象中用作equals()方法比较的Field，都应该用来计算hashCode         
Set：存储无序的,不可重复的数据
以HashSet为例说明:
1. 无序性：不等于随机性，存储的数据在底层数组中并非按照数组索引的顺序添加的，而是根据数据的哈希值(hashCode)决定的
2. 不可重复性：保证添加的元素按照equals()判断时,不能返回true,即: 相同的元素只能存放一个
    
二.添加元素的过程：以HashSet为例
    我们向HashSet中添加元素a，首先调用元素a所在类的hashCode()方法，计算元素a的哈希值，此哈希值接着又通过某种算法计算出在HashSet底层数组中的存放位置(即为：索引位置)，判断数组此位置上是否已经有元素：
    不同的哈希值通过某种算法，计算出在数组存放的位置可能相同，所以当该数组的下标位置已经存放了元素时，需要再次比较两个元素的哈希值，若不相同，以链式方式存储插入；若相同，再equals进行比较
    如果此位置上没有其他元素，则元素a添加成功。--->情况1
    如果此位置上有其它元素b(或以链表形式存在的多个元素)，则比较元素a与元素b的hash值:
       如果hash值不相同，则元素a添成功。--->情况2
       如果hash值相同，进而需要调用元素a所在类的equals()方法：
           equals()返回true，元素a添加失败!
           equals()返回false，则元素a添加成功。--->情况3
对于添加成功的情况2和情况3而言：元素a与已经存在指定索引位置上的数据以链表的方式存储。
JDK7：元素a放到数组中，指向原来的元素
JDK8：原来的元素在数组中，指向元素a
总结：七上八下   HashSet底层：数组 + 链表的结构   （前提:基于JDK7版本）     
    
```
##### hashCode() 的作用
```java
hashCode() 的作用：
    hashCode() 的作用是获取哈希码，也称为散列码；它实际上是返回一个int整数。这个哈希码的作用是确定该对象在哈希表中的索引位置。

hashCode() 定义在JDK的Object.java中，这就意味着Java中的任何类都包含有hashCode() 函数。
        虽然，每个Java类都包含hashCode() 函数。但是，仅仅当创建并某个“类的散列表”(关于“散列表”见下面说明)时，该类的hashCode() 才有用(作用是：确定该类的每一个对象在散列表中的位置；其它情况下(例如，创建类的单个对象，或者创建类的对象数组等等)，类的hashCode() 没有作用。
       上面的散列表，指的是：Java集合中本质是散列表的类，如HashMap，Hashtable，HashSet。

       也就是说：hashCode() 在散列表中才有用，在其它情况下没用。在散列表中hashCode() 的作用是获取对象的散列码，进而确定该对象在散列表中的位置。
                                                                                       
散列码的作用
    我们都知道，散列表存储的是键值对(key-value)，它的特点是：能根据“键”快速的检索出对应的“值”。这其中就利用到了散列码！
散列表的本质是通过数组实现的。当我们要获取散列表中的某个“值”时，实际上是要获取数组中的某个位置的元素。而数组的位置，就是通过“键”来获取的；更进一步说，数组的位置，是通过“键”对应的散列码计算得到的。

下面，我们以HashSet为例，来深入说明hashCode()的作用。

        假设，HashSet中已经有1000个元素。当插入第1001个元素时，需要怎么处理？因为HashSet是Set集合，它允许有重复元素。
        “将第1001个元素逐个的和前面1000个元素进行比较”？显然，这个效率是相等低下的。散列表很好的解决了这个问题，它根据元素的散列码计算出元素在散列表中的位置，然后将元素插入该位置即可。对于相同的元素，自然是只保存了一个。
        由此可知，若两个元素相等，它们的散列码一定相等；但反过来确不一定。在散列表中，
                           1、如果两个对象相等，那么它们的hashCode()值一定要相同；
                           2、如果两个对象hashCode()相等，它们并不一定相等。
                           注意：这是在散列表中的情况。在非散列表中一定如此！                   
```

##### hashCode() 和 equals() 的关系
```java
hashCode() 和 equals() 的关系：
1. 第一种 不会创建“类对应的散列表”

         这里所说的“不会创建类对应的散列表”是说：我们不会在HashSet, Hashtable, HashMap等等这些本质是散列表的数据结构中，用到该类。例如，不会创建该类的HashSet集合。

        在这种情况下，该类的“hashCode() 和 equals() ”没有半毛钱关系的！
        这种情况下，equals() 用来比较该类的两个对象是否相等。而hashCode() 则根本没有任何作用，所以，不用理会hashCode()。

下面，我们通过示例查看类的两个对象相等 以及 不等时hashCode()的取值。    
    
2. 第二种 会创建“类对应的散列表”

        这里所说的“会创建类对应的散列表”是说：我们会在HashSet, Hashtable, HashMap等等这些本质是散列表的数据结构中，用到该类。例如，会创建该类的HashSet集合。    
    
在这种情况下，该类的“hashCode() 和 equals() ”是有关系的：
        1)、如果两个对象相等，那么它们的hashCode()值一定相同。
              这里的相等是指，通过equals()比较两个对象时返回true。
        2)、如果两个对象hashCode()相等，它们并不一定相等。
               因为在散列表中，hashCode()相等，即两个键值对的哈希值相等。然而哈希值相等，并不一定能得出键值对相等。补充说一句：“两个不同的键值对，哈希值相等”，这就是哈希冲突。

        此外，在这种情况下。若要判断两个对象是否相等，除了要覆盖equals()之外，也要覆盖hashCode()函数。否则，equals()无效。
例如，创建Person类的HashSet集合，必须同时覆盖Person类的equals() 和 hashCode()方法。
        如果单单只是覆盖equals()方法。我们会发现，equals()方法没有达到我们想要的效果。    
```
##### 理解为什么hashCode相同,但是equals可能不同？
```java
理解为什么hashCode相同,但是equals可能不同？
理解底层源码:
package 集合;


 * @author 布丁熊.菲特尼斯
 * @create 2020-12-09 11:38
 
public class User {
    private String name;
    private int age;
   
    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;

        User user = (User) o;

        if (age != user.age) return false;
        return name != null ? name.equals(user.name) : user.name == null;
    }
    @Override
    public int hashCode() {
        int result = name != null ? name.hashCode() : 0;
        result = 31 * result + age;
        return result;
    }
}
String底层hashCode源代码
    public int hashCode() {
        int h = hash;
        if (h == 0 && value.length > 0) {
            char val[] = value;

            for (int i = 0; i < value.length; i++) {
                h = 31 * h + val[i];
            }
            hash = h;
        }
        return h;
    }
分析：因为String底层中的hashCode方法返回的哈希值是一个int类型的数值，而这个数值可能存在String类型(char[] value)内容不相同，即每一个char[] value对应的数组下标值val[i]的字符不同,但计算出来的hash总值相同，也就是hashCode值相同
```
##### 向HashSet中添加元素的过程
* * *

    向HashSet中添加元素的过程：
     当向 HashSet 集合中存入一个元素时，HashSet 会调用该对象的 hashCode() 方法来得到该对象的 hashCode 值，然后根据 hashCode 值，通过某种散列函数决定该对象在 HashSet 底层数组中的存储位置。（这个散列函数会与底层数组的长度相计算得到在数组中的下标，并且这种散列函数计算还尽可能保证能均匀存储元素，越是散列分布，该散列函数设计的越好）
    
     如果两个元素的hashCode()值相等，会再继续调用equals方法，如果equals方法结果为true，添加失败；如果为false，那么会保存该元素，但是该数组的位置已经有元素了，那么会通过链表的方式继续链接。
    
    如果两个元素的 equals() 方法返回 true，但它们的 hashCode() 返回值不相等，hashSet 将会把它们存储在不同的位置，但依然可以添加成功。

 ![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201209170606.png)   

##### 重写 hashCode() 方法的基本原则
 在程序运行时，同一个对象多次调用 hashCode() 方法应该返回相同的值。
 当两个对象的 equals() 方法比较返回 true 时，这两个对象的 hashCode() 方法的返回值也应相等。
 对象中用作 equals() 方法比较的 Field，都应该用来计算 hashCode 值。

##### 重写 equals() 方法的基本原则
以自定义的Customer类为例，何时需要重写equals()？
```java
 当一个类有自己特有的“逻辑相等”概念,当改写equals()的时候，总是要改写hashCode()，根据一个类的equals方法（改写后），两个截然不同的实例有可能在逻辑上是相等的，但是，根据Object.hashCode()方法，它们仅仅是两个对象。
 因此，违反了“相等的对象必须具有相等的散列码”。
 结论：复写equals方法的时候一般都需要同时复写hashCode方法。通常参与计算hashCode的对象的属性也应该参与到equals()中进行计算。
```
##### Eclipse/IDEA工具里hashCode()的重写

* **以Eclipse/IDEA为例，在自定义类中可以调用工具自动重写equals和hashCode。**

* 问题：为什么用Eclipse/IDEA复写hashCode方法，有31这个数字？
```java
 public int hashCode() {
        int h = hash;
        if (h == 0 && value.length > 0) {
            char val[] = value;

            for (int i = 0; i < value.length; i++) {
                h = 31 * h + val[i];
            }
            hash = h;
        }
        return h;
    }

 选择系数的时候要选择尽量大的系数。因为如果计算出来的hash地址越大，所谓的“冲突”就越少，查找起来效率也会提高。（减少冲突）
 并且31只占用5bits,相乘造成数据溢出的概率较小。
 31可以 由 i * 31== (i<<5)-1来表示,现在很多虚拟机里面都有做相关优化。（提高算法效率）
 31是一个素数，素数作用就是如果我用一个数字来乘以这个素数，那么最终出来的结果只能被素数本身和被乘数还有1来整除！(减少冲突)
```
#### Set实现类之二：LinkedHashSet
##### LinkedHashSet的使用
```java
 LinkedHashSet 是 HashSet 的子类
 LinkedHashSet 根据元素的 hashCode 值来决定元素的存储位置，但它同时使用双向链表维护元素的次序，这使得元素看起来是以插入顺序保存的。
 LinkedHashSet插入性能略低于 HashSet，但在迭代访问 Set 里的全部元素时有很好的性能。
 LinkedHashSet 不允许集合元素重复。  

LinkedHashSet作为HashSet的子类，在添加数据的同时，每个数据还维护了两个引用，记录此数据的前一个数据和后一个数据
设计的优点：对于频繁的遍历操作，LinkedHashSet效率高于HashSet    
```
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201209203610.png)

#### Set实现类之三：TreeSet
1. 向TreeSet中添加的数据，要求是相同类的对象
2. 两种排序方式：自然排序(实现Comparable接口)和定制排序(实现Comparator接口)
3. 自然排序中，比较两个对象是否相同的标准为：compareTo()返回0，不再是equals()   
```java
//按照姓名从大到小,年龄从小到大排序
//User类实现了Comparable接口
    @Override
    public int compareTo(Object o) {
        if (o instanceof User){
            User user = (User)o;
            int compare = -this.name.compareTo(user.name);
            if (compare != 0){
                return compare;
            }else {
                return Integer.compare(this.age,user.age);
            }
        }
        throw  new RuntimeException("输入类型不匹配!");
    }
```
4. 定制排序中，比较两个对象是否相同的标准为：compare()返回0,不再是equals() 
```java
1. 向TreeSet中添加的数据，要求是相同类的对象
2. 两种排序方式：自然排序(实现Comparable接口)和定制排序(实现Comparator接口)
3. 自然排序中，比较两个对象是否相同的标准为：compareTo()返回0，不再是equals()    
//按照姓名从大到小,年龄从小到大排序
    @Override
    public int compareTo(Object o) {
        if (o instanceof User){
            User user = (User)o;
            int compare = -this.name.compareTo(user.name);
            if (compare != 0){
                return compare;
            }else {
                return Integer.compare(this.age,user.age);
            }
        }
        throw  new RuntimeException("输入类型不匹配!");
    }
4. 定制排序中，比较两个对象是否相同的标准为：compare()返回0,不再是equals()
    @Test
    public void test(){
        Comparator comparator = new Comparator() {
            //按照年龄从小到大排序
            @Override
            public int compare(Object o1, Object o2) {
                if (o1 instanceof User && o2 instanceof User){
                    User u1 = (User)o1;
                    User u2 = (User)o2;
                    return Integer.compare(u1.age,u2.age);
                }else {
                    throw new RuntimeException("输入的数据类型不匹配!");
                }
            }
        };
        TreeSet<User> set = new TreeSet<>(comparator);
    }
```
```java
TreeSet 是 SortedSet 接口的实现类，TreeSet 可以确保集合元素处于排序状态。
TreeSet底层使用"红黑树结构(TreeMap)"存储数据

-----------------------------------------------------------------------------------------------
TreeSet的构造器

public TreeSet() {
        this(new TreeMap<E,Object>());
    }
    
public TreeSet(Comparator<? super E> comparator) {
        this(new TreeMap<>(comparator));
    }
    
public TreeSet(Collection<? extends E> c) {
        this();
        addAll(c);
    }
    
TreeSet--->add(E)操作--->底层调用TreeMap的put(k,v)操作
// Dummy value to associate with an Object in the backing Map
    private static final Object PRESENT = new Object();    

public boolean add(E e) {
        return m.put(e, PRESENT)==null;//调用TreeMap的put(k,v)操作,v ---> PRESENT
    }

public V put(K key, V value) {
        Entry<K,V> t = root;
        if (t == null) {
            compare(key, key); // type (and possibly null) check

            root = new Entry<>(key, value, null);
            size = 1;
            modCount++;
            return null;
        }
        int cmp;
        Entry<K,V> parent;
        // split comparator and comparable paths
        Comparator<? super K> cpr = comparator;
        if (cpr != null) {
            do {
                parent = t;
                cmp = cpr.compare(key, t.key);
                if (cmp < 0)
                    t = t.left;
                else if (cmp > 0)
                    t = t.right;
                else
                    return t.setValue(value);
            } while (t != null);
        }
        else {
            if (key == null)
                throw new NullPointerException();
            @SuppressWarnings("unchecked")
                Comparable<? super K> k = (Comparable<? super K>) key;
            do {
                parent = t;
                cmp = k.compareTo(t.key);
                if (cmp < 0)
                    t = t.left;
                else if (cmp > 0)
                    t = t.right;
                else
                    return t.setValue(value);
            } while (t != null);
        }
        Entry<K,V> e = new Entry<>(key, value, parent);
        if (cmp < 0)
            parent.left = e;
        else
            parent.right = e;
        fixAfterInsertion(e);
        size++;
        modCount++;
        return null;
    }
“若key值相同，则重新设定value值(默认value值：PRESENT),TreeSet若add(E)操作时，E值相同，TreeMap底层的对应的put(k,v)中的v值进行setValue()操作后，value值不变还是为PRESENT”
    public V setValue(V value) {
            V oldValue = this.value;
            this.value = value;
            return oldValue;
        }
TreeSet--->remove(Object)操作--->底层调用TreeMap的remove(E)操作
public boolean remove(Object o) {
        return m.remove(o)==PRESENT;
    }

TreeMap的remove(E)操作
public V remove(Object key) {
        Entry<K,V> p = getEntry(key);
        if (p == null)
            return null;

        V oldValue = p.value;
        deleteEntry(p);
        return oldValue;
    }
final Entry<K,V> getEntry(Object key) {
        // Offload comparator-based version for sake of performance
        if (comparator != null)
            return getEntryUsingComparator(key);
        if (key == null)
            throw new NullPointerException();
        @SuppressWarnings("unchecked")
            Comparable<? super K> k = (Comparable<? super K>) key;
        Entry<K,V> p = root;
        while (p != null) {
            int cmp = k.compareTo(p.key);
            if (cmp < 0)
                p = p.left;
            else if (cmp > 0)
                p = p.right;
            else
                return p;
        }
        return null;
    }    
    
-----------------------------------------------------------------------------------------------

 新增的方法如下： (了解)
 Comparator comparator()
 Object first()
 Object last()
 Object lower(Object e)
 Object higher(Object e)
 SortedSet subSet(fromElement, toElement) SortedSet headSet(toElement)
 SortedSet tailSet(fromElement) TreeSet 两种排序方法：自然排序和定制排序。默认情况下，TreeSet 采用自然排序。
```

 **TreeSet和后面要讲的TreeMap采用红黑树的存储结构**
 **特点：有序，查询速度比List快**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201209213911.png)
>再具体就不说了，可以参看https://www.yycoding.xyz/post/2014/3/27/introduce-red-black-tree，对红黑树的讲解写得不错。

##### 排 序—自然排序
```java
自然排序：TreeSet 会调用集合元素的 compareTo(Object obj) 方法来比较元素之间的大小关系，然后将集合元素按升序(默认情况)排列
如果试图把一个对象添加到 TreeSet 时，则该对象的类必须实现 Comparable 接口。
实现 Comparable 的类必须实现 compareTo(Object obj) 方法，两个对象即通过compareTo(Object obj) 方法的返回值来比较大小。  Comparable 的典型实现：
BigDecimal、BigInteger 以及所有的数值型对应的包装类：按它们对应的数值大小进行比较
Character：按字符的 unicode值来进行比较
Boolean：true 对应的包装类实例大于 false 对应的包装类实例
String：按字符串中字符的 unicode 值进行比较
Date、Time：后边的时间、日期比前面的时间、日期大
```
```java
向 TreeSet 中添加元素时，只有第一个元素无须比较compareTo()方法，后面添加的所有元素都会调用compareTo()方法进行比较。
因为只有相同类的两个实例才会比较大小，所以向 TreeSet 中添加的应该是同一个类的对象。
对于 TreeSet 集合而言，它判断两个对象是否相等的唯一标准是：两个对象通过 compareTo(Object obj) 方法比较返回值。
当需要把一个对象放入 TreeSet 中，重写该对象对应的 equals() 方法时，应保证该方法与 compareTo(Object obj) 方法有一致的结果：如果两个对象通过equals() 方法比较返回 true，则通过 compareTo(Object obj) 方法比较应返回 0。
否则，让人难以理解。

//按照姓名从大到小,年龄从小到大排序
    @Override
    public int compareTo(Object o) {
        if (o instanceof User){
            User user = (User)o;
            int compare = -this.name.compareTo(user.name);
            if (compare != 0){
                return compare;
            }else {
                return Integer.compare(this.age,user.age);
            }
        }
        throw  new RuntimeException("输入类型不匹配!");
    }
```
##### 排 序—定制排序
```java
TreeSet的自然排序要求元素所属的类实现Comparable接口，如果元素所属的类没有实现Comparable接口，或不希望按照升序(默认情况)的方式排列元素或希望按照其它属性大小进行排序，则考虑使用定制排序。定制排序，通过Comparator接口来
实现。需要重写compare(T o1,T o2)方法。
利用int compare(T o1,T o2)方法，比较o1和o2的大小：如果方法返回正整数，则表示o1大于o2；如果返回0，表示相等；返回负整数，表示o1小于o2。 
要实现定制排序，需要将实现Comparator接口的实例作为形参传递给TreeSet的构造器。
此时，仍然只能向TreeSet中添加类型相同的对象。否则发生ClassCastException异常。
使用定制排序判断两个元素相等的标准是：通过Comparator比较两个元素返回了0。

4. 定制排序中，比较两个对象是否相同的标准为：compare()返回0,不再是equals()
    @Test
    public void test(){
        Comparator comparator = new Comparator() {
            //按照年龄从小到大排序
            @Override
            public int compare(Object o1, Object o2) {
                if (o1 instanceof User && o2 instanceof User){
                    User u1 = (User)o1;
                    User u2 = (User)o2;
                    return Integer.compare(u1.age,u2.age);
                }else {
                    throw new RuntimeException("输入的数据类型不匹配!");
                }
            }
        };
        TreeSet<User> set = new TreeSet<>(comparator);
    }
```

##### 面试题(HashSet底层实现)
```java
package 集合;

import java.util.Objects;


 * @author 布丁熊.菲特尼斯
 * @create 2020-12-08 10:59
 * day24_集合  视频06(Set课后习题)
 
 
public class Person {
    public int age;
    public String name;


    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        person person = (person) o;
        return age == person.age &&
                name.equals(person.name);
    }
    
    @Override
    public int hashCode() {
        return Objects.hash(age, name);
    }
    
    @Override
    public String toString() {
        return "Person{" +
                "age=" + age +
                ", name='" + name + '\'' +
                '}';
    }
}

```
```java
HashSet set = new HashSet();
Person p1 = new Person(1001,"AA");
Person p2 = new Person(1002,"BB");
set.add(p1);
set.add(p2);
p1.name = "CC";
set.remove(p1);//先利用"1001","CC"的hash值去数组寻找位置,再移除
System.out.println(set);
set.add(new Person(1001,"CC"));
System.out.println(set);
set.add(new Person(1001,"AA"));
System.out.println(set);
//其中Person类中重写了hashCode()和equal()方法

[output]：    
[Person{age=1002, name='BB'}, Person{age=1001, name='AA'}]
[Person{age=1002, name='BB'}, Person{age=1001, name='CC'}]
[Person{age=1002, name='BB'}, Person{age=1001, name='CC'}, Person{age=1001, name='CC'}]
[Person{age=1002, name='BB'}, Person{age=1001, name='CC'}, Person{age=1001, name='CC'}, Person{age=1001, name='AA'}]
```

* **练习：在List内去除重复数字值，要求尽量简单(利用set集合不可重复性)**
```java
public static List duplicateList(List list) {
HashSet set = new HashSet();
set.addAll(list);
return new ArrayList(set);
}
public static void main(String[] args) {
List list = new ArrayList();
list.add(new Integer(1));
list.add(new Integer(2));
list.add(new Integer(2));
list.add(new Integer(4));
list.add(new Integer(4));
List list2 = duplicateList(list);
for (Object integer : list2) {
System.out.println(integer);
} }
```
#### Map接口
##### Map接口继承树
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201214165312.png)
#### Map接口概述
* **Map与Collection并列存在。用于保存具有映射关系的数据:key-value**
* **Map 中的 key 和 value 都可以是任何引用类型的数据**
* **Map 中的 key 用Set来存放，不允许重复，即同一个 Map 对象所对应的类，须重写hashCode()和equals()方法**
* **常用String类作为Map的“键”**
* **key 和 value 之间存在单向一对一关系，即通过指定的 key 总能找到唯一的、确定的 value**
* **Map接口的常用实现类：HashMap、TreeMap、LinkedHashMap和Properties。其中，HashMap是 Map 接口使用频率最高的实现类**

![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201214165853.png)

##### Map接口：常用方法

* **添加、删除、修改操作：**
    * **Object put(Object key,Object value)：将指定key-value添加到(或修改)当前map对象中**
    * **void putAll(Map m):将m中的所有key-value对存放到当前map中**
    * **Object remove(Object key)：移除指定key的key-value对，并返回value**
    * **void clear()：清空当前map中的所有数据**

* **元素查询的操作：**
    * **Object get(Object key)：获取指定key对应的value**
    * **boolean containsKey(Object key)：是否包含指定的key**
    * **boolean containsValue(Object value)：是否包含指定的value**
    * **int size()：返回map中key-value对的个数**
    * **boolean isEmpty()：判断当前map是否为空**
    * **boolean equals(Object obj)：判断当前map和参数对象obj是否相等**

* **元视图操作的方法：**
    * **Set keySet()：返回所有key构成的Set集合**
    * **Collection values()：返回所有value构成的Collection集合**
    * **Set entrySet()：返回所有key-value对构成的Set集合**
```java
Map map = new HashMap();
//map.put(..,..)省略
System.out.println("map的所有key:");
Set keys = map.keySet();// HashSet
for (Object key : keys) {
System.out.println(key + "->" + map.get(key));
}
System.out.println("map的所有的value：");
Collection values = map.values();
Iterator iter = values.iterator();
while (iter.hasNext()) {
System.out.println(iter.next());
}
System.out.println("map所有的映射关系：");
// 映射关系的类型是Map.Entry类型，它是Map接口的内部接口
Set mappings = map.entrySet();
for (Object mapping : mappings) {
Map.Entry entry = (Map.Entry) mapping;
System.out.println("key是：" + entry.getKey() + "，value是：" + entry.getValue());
}
```
#### Map实现类之一：HashMap
* * *
HashMap是线程不安全的，容易造成死循环
>https://coolshell.cn/articles/9606.html

HashMap源码详细分析
>http://www.tianxiaobo.com/2018/01/18/HashMap-%E6%BA%90%E7%A0%81%E8%AF%A6%E7%BB%86%E5%88%86%E6%9E%90-JDK1-8/

* * *

**HashMap是 Map 接口使用频率最高的实现类。**
**允许使用null键和null值，与HashSet一样，不保证映射的顺序。**
**所有的key构成的集合是Set:无序的、不可重复的。所以，key所在的类要重写：equals()和hashCode()**
**所有的value构成的集合是Collection:无序的、可以重复的。所以，value所在的类要重写：equals()**
**一个key-value构成一个entry**
**所有的entry构成的集合是Set:无序的、不可重复的**
**HashMap 判断两个 key 相等的标准是：两个 key 通过 equals() 方法返回 true，hashCode 值也相等。**
**HashMap 判断两个 value相等的标准是：两个 value 通过 equals() 方法返回 true。**

##### HashMap的存储结构
* **JDK 7及以前版本：HashMap是数组+链表结构(即为链地址法)**
* **JDK 8版本发布以后：HashMap是数组+链表+红黑树实现。**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201214171632.png)
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201214171942.png)

##### HashMap源码中的重要常量

```java
DEFAULT_INITIAL_CAPACITY : HashMap的默认容量，16
MAXIMUM_CAPACITY ： HashMap的最大支持容量，2^30
DEFAULT_LOAD_FACTOR：HashMap的默认加载因子
TREEIFY_THRESHOLD：Bucket中链表长度大于该默认值，转化为红黑树
UNTREEIFY_THRESHOLD：Bucket中红黑树存储的Node小于该默认值，转化为链表
MIN_TREEIFY_CAPACITY：桶中的Node被树化时最小的hash表容量。（当桶中Node的数量大到需要变红黑树时，若hash表容量小于MIN_TREEIFY_CAPACITY时，此时应执行resize扩容操作这个MIN_TREEIFY_CAPACITY的值至少是TREEIFY_THRESHOLD的4倍。）
    table：存储元素的数组，总是2的n次幂
    entrySet：存储具体元素的集
    size：HashMap中存储的键值对的数量
    modCount：HashMap扩容和结构改变的次数。
    threshold：扩容的临界值，=容量*填充因子
    loadFactor：填充因子
```

##### HashMap的存储结构：JDK 1.8之前
 **HashMap的内部存储结构其实是数组和链表的结合。当实例化一个HashMap时，系统会创建一个长度为Capacity的Entry数组，这个长度在哈希表中被称为容量(Capacity)，在这个数组中可以存放元素的位置我们称之为“桶”(bucket)，每个bucket都有自己的索引，系统可以根据索引快速的查找bucket中的元素。**
 **每个bucket中存储一个元素，即一个Entry对象，但每一个Entry对象可以带一个引用变量，用于指向下一个元素，因此，在一个桶中，就有可能生成一个Entry链。而且新添加的元素作为链表的head** 

* **添加元素的过程：**
* **向HashMap中添加entry1(key，value)，需要首先计算entry1中key的哈希值(根据key所在的hashCode()计算得到)，此哈希值经过处理以后，得到在底层Entry[]数组中要存储的位置i。**
* **如果位置i上没有元素，则entry1直接添加成功。**
* **如果位置i上已经存在entry2(或还有链表存在的entry3，entry4)，则需要通过循环的方法，依次比较entry1中key和其他的entry。**
* **如果彼此hash值不同，则直接添加成功。如果hash值相同，继续比较二者是否equals。如果返回值为true，则使用entry1的value去替换equals为true的entry的value。如果遍历一遍以后，发现所有的equals返回都为false,则entry1仍可添加成功。entry1指向原有的entry元素。**

###### HashMap的扩容

    当HashMap中的元素越来越多的时候，hash冲突的几率也就越来越高，因为数组的长度是固定的。所以为了提高查询的效率，就要对HashMap的数组进行扩容，而在HashMap数组扩容之后，最消耗性能的点就出现了：
    原数组中的数据必须重新计算其在新数组中的位置，并放进去，这就是resize。(扩容最耗性能的是：扩容完后，需要对 table数组里面的元素(以及链表元素)重新进行rehash，重新安放元素在新数组的所在位置，  此过程最耗时间)

##### 那么HashMap(1.8之前)什么时候进行扩容呢？
```java
当HashMap中元素的个数size大于等于临界值threshold(threshold = capacity * loadFactor)时,并且当前添加的table数组不为空,就会进行扩容，loadFactor 的默认 值 (DEFAULT_LOAD_FACTOR)为0.75，这是一个折中的取值。也就是说，默认情况下，数组大小(DEFAULT_INITIAL_CAPACITY)为16，那么当HashMap中元素个数超过16*0.75=12（这个值就是代码中的threshold值，也叫做临界值）的时候，就把数组的大小扩展为 2*16=32，即扩大一倍，然后重新计算每个元素在数组中的位置，而这是一个非常消耗性能的操作，所以如果我们已经预知HashMap中元素的个数，那么预设元素的个数能够有效的提高HashMap的性能
```
##### HashMap的存储结构：JDK 1.8
```java
 HashMap的内部存储结构其实是数组+链表+树的结合。当实例化一个HashMap时，会初始化initialCapacity和loadFactor，在put第一对映射关系时，系统会创建一个长度为initialCapacity的Node数组，这个长度在哈希表中被称为容量(Capacity)，在这个数组中可以存放元素的位置我们称之为“桶”(bucket)，每个bucket都有自己的索引，系统可以根据索引快速的查找bucket中的元素。  

 每个bucket中存储一个元素，即一个Node对象，但每一个Node对象可以带一个引用变量next，用于指向下一个元素，因此，在一个桶中，就有可能生成一个Node链。也可能是一个一个TreeNode对象，每一个TreeNode对象可以有两个叶子结点left和right，因此，在一个桶中，就有可能生成一个TreeNode树。而新添加的元素作为链表的last，或树的叶子结点。
```
##### 那么HashMap什么时候进行扩容和树形化呢(1.8)？
```java
当HashMap中的元素个数超过临界值threshold ， 就 会 进 行 数 组 扩 容 ， loadFactor 的默认 值 (DEFAULT_LOAD_FACTOR)为0.75，这是一个折中的取值。也就是说，默认情况下，数组大小(DEFAULT_INITIAL_CAPACITY)为16，那么当HashMap中元素个数超过16*0.75=12（这个值就是代码中的threshold值，也叫做临界值）的时候，就会扩容resize()，然后重新计算每个元素在数组中的位置，而这是一个非常消耗性能的操作，所以如果我们已经预知HashMap中元素的个数，那么预设元素的个数能够有效的提高HashMap的性能


                     
1. 如果HashMap是自定义初始化,底层会自动调用带DEFAULT_LOAD_FACTOR加载因子参数的构造方DEFAULT_LOAD_FACTOR:0.75f
//源代码,基于jdk8                     
public HashMap(int initialCapacity) {
        this(initialCapacity, DEFAULT_LOAD_FACTOR);
    }
                     
 public HashMap(int initialCapacity, float loadFactor) {
        if (initialCapacity < 0)
            throw new IllegalArgumentException("Illegal initial capacity: " +
                                               initialCapacity);
        if (initialCapacity > MAXIMUM_CAPACITY)
            initialCapacity = MAXIMUM_CAPACITY;
        if (loadFactor <= 0 || Float.isNaN(loadFactor))
            throw new IllegalArgumentException("Illegal load factor: " +
                                               loadFactor);
        this.loadFactor = loadFactor;//这里是默认的加载因子，也可以自己指定加载因子大小
        this.threshold = tableSizeFor(initialCapacity);
    }   
                     
下面我们着重分析这行代码底层原理：this.threshold = tableSizeFor(initialCapacity);废话不多说，上代码         static final int tableSizeFor(int cap) {
        int n = cap - 1;
        n |= n >>> 1;
        n |= n >>> 2;
        n |= n >>> 4;
        n |= n >>> 8;
        n |= n >>> 16;
        return (n < 0) ? 1 : (n >= MAXIMUM_CAPACITY) ? MAXIMUM_CAPACITY : n + 1;
    }
测试结果：                                           
第0组:  
[input]  cap:0     
[output] threshold:1
[input]  cap:1     
[output] threshold:1
[input]  cap:2     
[output] threshold:2
第一组:
[input]  cap:3  cap:4   
[output] threshold:4                      
第二组:                     
[input]  cap:5  cap:7  cap:8 
[output] threshold:8 
第三组:
[input]  cap:9  cap:12  cap:15  cap:16
[output] threshold:16

final Node<K,V>[] resize() {
    int oldCap = (oldTab == null) ? 0 : oldTab.length;
    int oldThr = threshold;
    int newCap, newThr = 0;
    if (oldCap > 0) {
            if (oldCap >= MAXIMUM_CAPACITY) {
                threshold = Integer.MAX_VALUE;
                return oldTab;
            }
            //注意：
            else if ((newCap = oldCap << 1) < MAXIMUM_CAPACITY &&
                     oldCap >= DEFAULT_INITIAL_CAPACITY)
                newThr = oldThr << 1; // double threshold
        }
    else if (oldThr > 0) // initial capacity was placed in threshold
    newCap = oldThr;
    else {               // zero initial threshold signifies using defaults
            newCap = DEFAULT_INITIAL_CAPACITY;
            newThr = (int)(DEFAULT_LOAD_FACTOR * DEFAULT_INITIAL_CAPACITY);
        }
    if (newThr == 0) {
            float ft = (float)newCap * loadFactor;
            newThr = (newCap < MAXIMUM_CAPACITY && ft < (float)MAXIMUM_CAPACITY ?
                      (int)ft : Integer.MAX_VALUE);
        }
    threshold = newThr;
    Node<K,V>[] newTab = (Node<K,V>[])new Node[newCap];
}
由上述代码可知，当自定义HashMap构造方法时,table数组初始化时,由于临界值threshold是不为0，threshold值赋值给newCap,newThr = 0 临界值threshold又被重新计算，最终Node<K,V>[] newTab = (Node<K,V>[])new Node[newCap]被创建，table数组长度为newCap
...put(k,v)...多次                     
for (int binCount = 0; ; ++binCount) {
                    if ((e = p.next) == null) {
                        p.next = newNode(hash, key, value, null);
                        if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
                            treeifyBin(tab, hash);
                        break;
                    }
                    if (e.hash == hash &&
                        ((k = e.key) == key || (key != null && key.equals(k))))
                        break;
                    p = e;
                }
                
重点分析：if (binCount >= TREEIFY_THRESHOLD - 1)   treeifyBin(tab, hash);
当HashMap中的其中一个链的对象个数如果达到了8个，此时如果capacity没有达到64，那么HashMap会先扩容解决(此时扩容,若此时数组长度oldCap不大于等于MAXIMUM_CAPACITY(默认值1<<30)，则容量capacity会变成原来容量的2倍，若扩容后的容量仍然小于MAXIMUM_CAPACITY并且是大于等于默认容量DEFAULT_INITIAL_CAPACITY("默认值:64"),则临界值threshold也会扩大为原来的2倍)，如果已经达到了64，那么这个链会变成树，结点类型由Node变成TreeNode类型。当然，如果当映射关系被移除后，下次resize方法时判断树的结点个数低于6个，也会把树再转为链表。                     

//链表变为红黑树时,会先判断Node<k,v> table数组的长度是否小于64,若小于64数组会先进行扩容
final void treeifyBin(Node<K,V>[] tab, int hash) {
    int n, index; Node<K,V> e;
        if (tab == null || (n = tab.length) < MIN_TREEIFY_CAPACITY)
            resize();
}                     
                     
2.如果HashMap是默认初始化的，在put(k,v)时，若Node<k,v>[] table为空，先进行初始化数组table，
newCap = DEFAULT_INITIAL_CAPACITY; newThr = (int)(DEFAULT_LOAD_FACTOR * DEFAULT_INITIAL_CAPACITY);
DEFAULT_INITIAL_CAPACITY:16    DEFAULT_LOAD_FACTOR:0.75f   newThr:12   newCap:16                     
再把newThr赋值给threshold(threshold = newThr); 创建一个长度为16的数组

```
##### 默认/自定义初始化resize()扩容
```java
resize()方法扩容：
int oldCap = (oldTab == null) ? 0 : oldTab.length;
        int oldThr = threshold;
        int newCap, newThr = 0;
if (oldCap > 0) {
            if (oldCap >= MAXIMUM_CAPACITY) {//MAXIMUM_CAPACITY = 1 << 30
                threshold = Integer.MAX_VALUE;
                return oldTab;
            }
            else if ((newCap = oldCap << 1) < MAXIMUM_CAPACITY &&
                     oldCap >= DEFAULT_INITIAL_CAPACITY)
                newThr = oldThr << 1; // double threshold
        }
//注意：若hashmap时默认初始化时，
//若是第一次put(k,v)操作时,oldCap(数组table)的长度为0,if (oldCap > 0)判断为fasle,该if语句不执行，newCap的值为临界值threshold，而临界值threshold则会从新计算
if (newThr == 0) {
float ft = (float)newCap * loadFactor;
            newThr = (newCap < MAXIMUM_CAPACITY && ft < (float)MAXIMUM_CAPACITY ?
                      (int)ft : Integer.MAX_VALUE);
    }
            threshold = newThr;
//也就是threshold = newCap * loadFactor(加载因子若hashmap初始化时，没有指定默认0.75f)
//Node<K,V>[] newTab = (Node<K,V>[])new Node[newCap];
...put(k,v)多次...
oldCap原来数组(table)的长度，if (oldCap > 0)判断为true,执行该if语句，又因为刚开始table数组长度不是那么长，
if (oldCap >= MAXIMUM_CAPACITY)语句不执行，执行如下语句：
------------------------------------------------------------------------------------------------
    else if ((newCap = oldCap << 1) < MAXIMUM_CAPACITY &&
                     oldCap >= DEFAULT_INITIAL_CAPACITY)
                newThr = oldThr << 1; // double threshold
        }
------------------------------------------------------------------------------------------------
代码分析:oldCap << 1，先左移1位，也就是容量扩容2倍再赋值给newCap，若oldCap >= DEFAULT_INITIAL_CAPACITY(默认64)，则oldThr(一开始oldThr = threshold)两倍的扩大，赋值给newThr(若oldCap < DEFAULT_INITIAL_CAPACITY,则该if语句不执行，但newCap = oldCap << 1容量会扩大两倍)，接着判断下面代码if(newThr == 0)不成立，直接将newThr赋值给threshold(加载因子)，Node<K,V>[] newTab = (Node<K,V>[])new Node[newCap];创建数组
    
//hashmap不是默认初始化时
若hashmap初始化自定义时自己定义了加载因子，则用自己定义的，若没有定义加载因子底层会调用默认的加载因子DEFAULT_LOAD_FACTOR(0.75f),而且也会根据你给的(初始值容量)initialCapacity通tableSizeFor(initialCapacity)方法算出临界值threshold,再赋值给threshold。
...put(k,v)操作...
//首次put(k,v)操作，执行resize()方法
Node<K,V>[] oldTab = table;  int oldCap = (oldTab == null) ? 0 : oldTab.length; 
int oldThr = threshold;
刚开始时，hashmap的桶bucket数组table并没有初始化，但是临界值threshold已经初始化了，将oldThr赋值给newCap(newCap = oldThr),并且一开始newThr也是默认为0的,则会执行如下代码：
    if (newThr == 0) {
            float ft = (float)newCap * loadFactor;
            newThr = (newCap < MAXIMUM_CAPACITY && ft < (float)MAXIMUM_CAPACITY ?
                      (int)ft : Integer.MAX_VALUE);
        }
 threshold = newThr;
重新计算临界值,再赋值给threshold，创建一个新的数组Node<K,V>[] newTab = (Node<K,V>[])new Node[newCap];第一次创建的新数组newCap是当时hashmap自定义初始化时的临界值threshold
```

 ##### 关于映射关系的key是否可以修改？
```java
answer：不要修改
映射关系存储到HashMap中会存储key的hash值，这样就不用在每次查找时重新计算，每一个Entry或Node（TreeNode）的hash值了，因此如果已经put到Map中的映射关系，再修改key的属性，而这个属性又参与hashcode值的计算，那么会导致匹配不上。 
```
##### 总结：JDK1.8相较于之前的变化
```java
1.HashMap map = new HashMap();//默认情况下，先不创建长度为16的数组
2.当首次调用map.put()时，再创建长度为16的数组
3.数组为Node类型，在jdk7中称为Entry类型
4.形成链表结构时，新添加的key-value对在链表的尾部（七上八下）
5.当数组指定索引位置的链表长度>8时，且map中的数组的长度> 64时，此索引位置上的所有key-value对使用红黑树进行存储。
```
##### 面试题(hashmap comprehension)
**谈谈你对HashMap中put/get方法的认识？如果了解再谈谈HashMap的扩容机制？默认大小是多少？什么是负载因子(或填充比)？什么是吞吐临界值(或阈值、threshold)？**

* **大概理解**
```java
一.谈谈你对HashMap中put/get方法的认识？ 
1.调用put(k,v)方法(jdk1.8),会先根据hash()算法算出key的hash值    
1.1).HashMap在首次put(k,v)操作时，会先判断Node<k,v> table数组是否为空,若为空就会resize()为数组分配空间,默认是数组长度为16,若HashMap不是默认初始化时,resize()初始化数组的长度则为threshold大小

1.2).然后通过(n-1) & hash 操作算出该结点在数组中的存储位置("若key=null,则存储到数组索引为0的位置"),若该位置为空，则直接将该节点赋值到该索引位置，若不为空再对比该结点的next结点，若为空直接添加，否则再对比hash值，若hash值相等，再equals(key),若key值相等，直接替换该结点的value值，返回oldValue，若一直对比hash值相等，key值不同，或者hash不同，就直接将key-value添加到该链表的尾结点

1.3).若当某个位置的链表长度大于8,扩容之前会进行判断，判断该table数组的长度是否小于64，若小于64则会先进行扩容，而不是将链表变为红黑树,扩容期间会将数组中的每个元素重新排序，重新rehash在数组的存储位置，此过程性能消耗较大

2).get(key)操作    
2.1).也会先计算key的哈希值，然后通过(n-1) * hash计算出在table数组的存储位置，然后再通过对比key的hash值，若相等，则equals()key值,若相等则直接返回该key的结点Node的value值，再重新排列链表，否则返回null

二.如果了解再谈谈HashMap的扩容机制？默认大小是多少？
2.HashMap的扩容机制    
2.1).jdk8之前,若在put(k,v)操作时，元素的的个数大于或等于临界值threshold时，并且该数组下标的元素不为null,会进行2倍的数组长度的扩容
2.2).jdk8,若在put(k,v)操作时，元素的个数大于临界值threshold时,会进行resize()扩容，默认大小为16

三.什么是负载因子(或填充比)？
3.负载因子(DEFAULT_LOAD_FACTOR)在扩容时用来计算临界值threshold，判断元素个数到达什么点时该扩容

四.什么是吞吐临界值(或阈值、threshold)？
4.threshold = capacity * load_factor(容量 * 加载因子)    
4.1).threshold临界值是判断该数组是否需要扩容的一个标记,并不需要当数组元素的个数到达数组长度是再扩容,简化底层性能，使得元素能更能分布均匀，减少不必要的性能开销  
```
##### 面试题：负载因子值的大小，对HashMap有什么影响？
* 本人见解
```java
1).负载因子决定了"数据密度"
1.1).若负载因子过小,则在添加"key-value"键值对时，若元素个数很容易大于threshold临界值,会进行频繁的扩容,而每一次扩容都要重新计算数组中的元素在新数组中的位置，也称为rehash,此过程性能消耗极大，并不推荐频繁扩容，而且数据密度也越小，意味着发生碰撞的几率越小，数组中的链表也就越短，查询和插入时比较的次数也越小，性能会更高,但是会造成内容空间的浪费。
    
1.2).若负载因子过大,则会等到数组内的元素个数接近数组长度再扩容，这个会造成在put(k,v)时有很大可能性集中在同一链表上的添加，发生的hash碰撞的几率越大，数组中的链表越容易长，遍历时时间复杂度大大提高,致使服务器性能变差。
例如，在向服务器多次发送表单post请求时,底层会帮我们创建一个hashmap集合，并将该数据存入到集合中，那么不管是人为因素还是随机因素，都有很大可能表单post请求中key的hash值是相同的，而value值不同,那么都会集中在数组一个位置添加数据，而每次put(k,v)添加数据时，都需要进行遍历，消耗的时间较多而延迟加载，很有可能导致服务器在某种意义上的瘫痪
```
* 比较中肯的回答
```java
1).负载因子的大小决定了HashMap的数据密度。
1.1).负载因子越大密度越大，发生碰撞的几率越高，数组中的链表越容易长,造成查询或插入时的比较次数增多，性能会下降。
1.2).负载因子越小，就越容易触发扩容，数据密度也越小，意味着发生碰撞的几率越小，数组中的链表也就越短，查询和插入时比较的次数也越小，性能会更高。但是会浪费一定的内容空间。而且经常扩容也会影响性能，建议初始化预设大一点的空间。
1.3).按照其他语言的参考及研究经验，会考虑将负载因子设置为"0.7~0.75"，此时平均检索长度接近于常数。
```
#### Map实现类之二：LinkedHashMap

* * *
LinkedHashMap 源码详细分析（JDK1.8）
>https://segmentfault.com/a/1190000012964859
* * *

```java
LinkedHashMap 是 HashMap 的子类
在HashMap存储结构的基础上，使用了一对双向链表来记录添加元素的顺序
与LinkedHashSet类似，LinkedHashMap 可以维护 Map 的迭代顺序：迭代顺序与 Key-Value 对的插入顺序一致
```

##### HashMap和LinkedHashMap结点类型
```java
HashMap中的内部类：Node

static class Node<K,V> implements Map.Entry<K,V> {
final int hash;
final K key;
V value;
Node<K,V> next;
}

LinkedHashMap中的内部类：Entry

static class Entry<K,V> extends HashMap.Node<K,V> {
Entry<K,V> before, after;
Entry(int hash, K key, V value, Node<K,V> next) {
super(hash, key, value, next);
}
}

```
##### HashMap基本数据结构(重新总结)
* **HashMap底层类似于邻接表，由一个定长的数组，这个数组的每一个元素都是一个链表的头结点**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/3ea08af156c887f4b16f3956f72898af.jpg)

* **headers是一个定长的数组，数组当中的每一个元素都是一个链表的头结点。也就是说根据这个头结点，我们可以遍历这个链表。数组是定长的，但是链表是变长的，所以如果我们发生元素的增删改查，本质上都是通过链表来实现的。**
* **这个就是hashmap的基本结构，如果在面试当中问到，你可以直接回答：它本质上就是一个元素是链表的数组。**
```java
一. Map的整个实现类的结构：
|----Map:双列数据,存储key-value键值对的数据    ----类似于高中的函数:y=f(x)
   |----HashMap:作为Map的主要实现类;是非线程安全的，效率比Hashtable高；HashMap 可以存储 null 的 key 和 value，但 null 作为键只能有一个，null 作为值可以有多个；
      |----LinkedHashMap：LinkedHashMap是HashMap的子类，保证在遍历map元素时，可以按照添加的顺序实现遍历
           原因：在原有的HashMap底层的结构上，添加了一对指针，用于指向前一个和后一个元素
           对于频繁的遍历操作，此类执行效率高于HashMap
           
             static class Entry<K,V> extends HashMap.Node<K,V> {
        Entry<K,V> before, after;  //双向链表
        Entry(int hash, K key, V value, Node<K,V> next) {
            super(hash, key, value, next);
        }
    }
           
   |----TreeMap：保证按照添加的key-value键值对进行排序，实现排序遍历(用key进行序)。           此时考虑key的自然排序和定制排序，底层使用红黑树
   |----Hashtable：作为古老的实现类，线程安全的，效率低，不建议使用，不允许有 null 键和 null 值，否则会抛出 NullPointerException
      |----Properties：常用来处理配置文件，key和value都是String类型
       
HashMap的底层：数组 + 链表（JDK7及之前）    数组 + 链表 + 红黑树（JDK8）
   
面试题(Map)
1. HashMap的底层实现原理？
2. HashMap和Hashtable的异同？
3. CurrentHashMap与Hashtable的异同？    
       
二. Map结构的理解：
    Map中的key：无序的，不可重复的，使用Set存储所有的key  --->  key所在的类要重写equals()和hashCode()（以HashMap为例）
    Map中的value：无序的，可重复的，使用Collection存储所有的value  ---> value所在的类要重写equals()
    一个键值对：key-value构成了一个Entry对象
    Map中的entry：无序的，不可重复的，使用Set存储所有的entry   
    
三. HashMap的底层实现原理？以JDK7为例说明
    HashMap map = new HashMap():
    在实例化以后，底层创建了长度是16的一维数组Entry[] table
    ...可能已经执行过多次put...
    map.put(key1,value1);
    put(key1,value1)方法的内部实现：首先，调用key1所在类的hashCode()计算key1哈希值，此哈希值经过某种算法计算以后，得到在Entry数组中的存放位置
    
        如果此位置上的数据为空，此时的key1-value1添加成功  ---情况1
        如果此位置上的数据不为空(意味着此位置上存在一个或多个数据[以链表的形式存在])，比较key1和已经存在的一个或多个数据的哈希值：
        
           如果key1的哈希值与已经存在的数据的哈希值不相同，此时key1-value1添加成功 ---情况2
           如果key1的哈希值和已经存在的某一个数据(key2-value2)的哈希值相同，继续比较 调用key1所在类的equals(key2)比较
           
              如果equals()返回false：此时的key1-value1添加成功  ---情况3
              如果equals()返回true：使用value1替换value2 
              
              //put()方法部分源码,基于jdk7
        for (Entry<K,V> e = table[i]; e != null; e = e.next) {
            Object k;
            if (e.hash == hash && ((k = e.key) == key || key.equals(k))) {
                V oldValue = e.value;
                e.value = value;
                e.recordAccess(this);
                return oldValue;
            }
        }
     补充：关于情况2和情况3：此时的key1-value1和原来的数据以链表的方式存储
   在不断的添加过程中，会涉及到扩容问题：
    在不断的添加过程中，会涉及到扩容问题，当元素个数(size)大于等于临界值(threshold)[且要存放的位置非空]，扩容。
    
     if ((size >= threshold) && (null != table[bucketIndex]))
        //addEntry(hash, key, value, i)方法的源代码    
        void addEntry(int hash, K key, V value, int bucketIndex) {
        if ((size >= threshold) && (null != table[bucketIndex])) {
            resize(2 * table.length);
            hash = (null != key) ? hash(key) : 0;
            bucketIndex = indexFor(hash, table.length);
        }

        createEntry(hash, key, value, bucketIndex);
    }
    
   默认的扩容方式：扩容到原来容量的2倍，并将原有的数据复制过来(Entry数组里面的元素在扩容后，需要重新哈希到新数组的相应位置上)
        
JDK8相较于JDK7在底层实现方面的不同：

1. new HashMap()：底层没有创建一个长度为16的数组
2. JDK8底层的数组是：Node[],而非Entry[]数组
3. 首次调用put()方法时，底层创建长度为16的数组
4. JDK7底层结构只有：数组 + 链表   JDK8中底层结构：数组 + 链表 + 红黑树
    JDK1.8 以后的 HashMap 在解决哈希冲突时有了较大的变化，当数组的某一个索引位置上的元素以链表形式存在且链表长度大于阈值（默认为 8）（将链表转换成红黑树前会判断，如果当前数组的长度小于 64，那么会选择先进行数组扩容，而不是转换为红黑树）时，将链表转化为红黑树，以减少搜索时间(单链表搜索的时间复杂度过高)。Hashtable 没有这样的机制。   
       
   DEFAULT_INITIAL_CAPACITY : HashMap的默认容量，16      
   DEFAULT_LOAD_FACTOR：HashMap的默认加载因子：0.75f
   threshold：扩容的临界值，=容量*填充因子：16 * 0.75 => 12
   TREEIFY_THRESHOLD：Bucket中链表长度大于该默认值，转化为红黑树，默认值：8
   MIN_TREEIFY_CAPACITY：桶中的Node被树化时最小的hash表容量，默认值：64
       
四. LinkedHashMap的底层实现原理(了解)     
    //底层源码
       static class Entry<K,V> extends HashMap.Node<K,V> {
        Entry<K,V> before, after;//能够记录添加的元素的先后顺序
        Entry(int hash, K key, V value, Node<K,V> next) {
            super(hash, key, value, next);
        }
    }

下述操作都可以用集合中Iterator进行遍历操作
Set keySet():返回所有key构成的Set集合
Collection values():返回所有value构成的Collection集合
Set entrySet():返回所有key-value键值对构成的Set集合
    
总结：常用方法
添加：put(Object key,Object value)
删除：remove(Object key)
修改：put(Object key,Object value)
查询：get(Object key)
长度：size()
遍历：keySet() / values() / entrySet()   
```
#### Map实现类之三:TreeMap
```java
TreeMap存储 Key-Value 对时，需要根据 key-value 对进行排序。TreeMap 可以保证所有的 Key-Value 对处于有序态。 
TreeSet底层使用"红黑树结构"存储数据
TreeMap 的 Key 的排序：
自然排序：TreeMap 的所有的 Key 必须实现 Comparable 接口，而且所有的 Key 应该是同一个类的对象，否则将会抛出 ClasssCastException
定制排序：创建 TreeMap 时，传入一个 Comparator 对象，该对象负责对TreeMap 中的所有 key 进行排序。此时不需要 Map 的 Key 实现Comparable 接口
TreeMap判断两个key相等的标准：两个key通过compareTo()方法或者compare()方法返回0
```
##### Comparable和Comparator底层实现
```java
比较器Comparable和Comparator
public V put(K key, V value) {
        Entry<K,V> t = root;
        if (t == null) {
            compare(key, key); // type (and possibly null) check

            root = new Entry<>(key, value, null);
            size = 1;
            modCount++;
            return null;
        }
        int cmp;
        Entry<K,V> parent;
        // split comparator and comparable paths
        Comparator<? super K> cpr = comparator;
        if (cpr != null) {
            do {
                parent = t;
                cmp = cpr.compare(key, t.key);
                if (cmp < 0)
                    t = t.left;
                else if (cmp > 0)
                    t = t.right;
                else
                    return t.setValue(value);
            } while (t != null);
        }
        else {
            if (key == null)
                throw new NullPointerException();
            @SuppressWarnings("unchecked")
                Comparable<? super K> k = (Comparable<? super K>) key;
            do {
                parent = t;
                cmp = k.compareTo(t.key);
                if (cmp < 0)
                    t = t.left;
                else if (cmp > 0)
                    t = t.right;
                else
                    return t.setValue(value);
            } while (t != null);
        }
        Entry<K,V> e = new Entry<>(key, value, parent);
        if (cmp < 0)
            parent.left = e;
        else
            parent.right = e;
        fixAfterInsertion(e);
        size++;
        modCount++;
        return null;
    }
    会先进行判断TreeMap是否实现了自定义排序Comparator,若实现了则按自定义对key进行排序，否则则用Comparable对key排序
```
#### Map实现类之四：Hashtable
```java
 Hashtable是个古老的 Map 实现类，JDK1.0就提供了;不同于HashMap，Hashtable是线程安全的
 Hashtable实现原理和HashMap相同，功能相同。底层都使用哈希表结构，查询速度快，很多情况下可以互用。 
 与HashMap不同，"Hashtable 不允许使用 null 作为 key 和 value"
 与HashMap一样，Hashtable 也不能保证其中 Key-Value 对的顺序
 Hashtable判断两个key相等、两个value相等的标准，与HashMap一致。
```
##### Hashtable底层put(k,v)源码
```java
public synchronized V put(K key, V value) {
        // Make sure the value is not null
        if (value == null) {
            throw new NullPointerException();
        }

        // Makes sure the key is not already in the hashtable.
        Entry<?,?> tab[] = table;
        int hash = key.hashCode();
        int index = (hash & 0x7FFFFFFF) % tab.length;
        @SuppressWarnings("unchecked")
        Entry<K,V> entry = (Entry<K,V>)tab[index];
        for(; entry != null ; entry = entry.next) {
            if ((entry.hash == hash) && entry.key.equals(key)) {
                V old = entry.value;
                entry.value = value;
                return old;
            }
        }

        addEntry(hash, key, value, index);
        return null;
    }
```
* **addEntry(hash, key, value, index)**
* **Hashtable向链表添加元素是添加在链表的头结点**
```java
 private void addEntry(int hash, K key, V value, int index) {
        modCount++;

        Entry<?,?> tab[] = table;
        if (count >= threshold) {
            // Rehash the table if the threshold is exceeded
            rehash();

            tab = table;
            hash = key.hashCode();
            index = (hash & 0x7FFFFFFF) % tab.length;
        }

        // Creates the new entry.
        @SuppressWarnings("unchecked")
        Entry<K,V> e = (Entry<K,V>) tab[index];
        tab[index] = new Entry<>(hash, key, value, e);
        count++;
    }
```
##### Hashtable扩容
>**Hashtable当Entry数组里面的元素个数count>=threshold,就会进行rehash(),在重新rehash期间会进行扩容,扩容容量为：(Capacity * 2 + 1) ,再将bucket里面的元素重新分配存储位置，形成相应的链表**

```java
protected void rehash() {
        int oldCapacity = table.length;
        Entry<?,?>[] oldMap = table;

        // overflow-conscious code
        int newCapacity = (oldCapacity << 1) + 1;
        if (newCapacity - MAX_ARRAY_SIZE > 0) {
            if (oldCapacity == MAX_ARRAY_SIZE)
                // Keep running with MAX_ARRAY_SIZE buckets
                return;
            newCapacity = MAX_ARRAY_SIZE;
        }
        Entry<?,?>[] newMap = new Entry<?,?>[newCapacity];

        modCount++;
        threshold = (int)Math.min(newCapacity * loadFactor, MAX_ARRAY_SIZE + 1);
        table = newMap;
       "重新rehash过程与jdk8之前的HashMap的rehash相似"
        for (int i = oldCapacity ; i-- > 0 ;) {
            for (Entry<K,V> old = (Entry<K,V>)oldMap[i] ; old != null ; ) {
                Entry<K,V> e = old;
                old = old.next;

                int index = (e.hash & 0x7FFFFFFF) % newCapacity;
                e.next = (Entry<K,V>)newMap[index];
                newMap[index] = e;
            }
        }
    }    
```
#### Map实现类之五：Properties
* **Properties 类是 Hashtable 的子类，该对象用于处理属性文件**
* **由于属性文件里的 key、value 都是字符串类型，所以 Properties 里的 key 和 value 都是字符串类型**
* **存取数据时，建议使用setProperty(String key,String value)方法和getProperty(String key)方法**

```java
package 集合.Properties;

import java.io.FileInputStream;
import java.io.IOException;
import java.util.Properties;

/**
 * @author 布丁熊.菲特尼斯
 * @create 2020-12-17 15:30
 */
public class PropertiesTest {
    private static Properties pro = null;
    private static FileInputStream fis = null;
    //Properties:常用来处理配置文件,key和value都是String类型的
    public static void main(String[] args){
        try {
             pro = new Properties();
             fis = new FileInputStream("jdbc.properties");
            pro.load(fis);//加载流对应的文件

            String name = pro.getProperty("name");
            String password = pro.getProperty("password");
            System.out.println(name+":"+password);
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            if (fis != null){
                try {
                    fis.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}

```
#### Collections工具类
>**操作数组的工具类:Arrays**

```java
1.Collections 是一个操作 Set、List 和 Map 等集合的工具类
2.Collections 中提供了一系列静态的方法对集合元素进行排序、查询和修改等操作，还提供了对集合对象设置不可变、对集合对象实现同步控制等方法
3.排序操作：（均为static方法）
reverse(List)：反转 List 中元素的顺序
shuffle(List)：对 List 集合元素进行随机排序
sort(List)：根据元素的自然顺序对指定 List 集合元素按升序排序
sort(List，Comparator)：根据指定的 Comparator 产生的顺序对 List 集合元素进行排序
swap(List，int， int)：将指定 list 集合中的 i 处元素和 j 处元素进行交换

查找、替换
Object max(Collection)：根据元素的自然顺序，返回给定集合中的最大元素
Object max(Collection，Comparator)：根据 Comparator 指定的顺序，返回给定集合中的最大元素
Object min(Collection)
Object min(Collection，Comparator)
int frequency(Collection，Object)：返回指定集合中指定元素的出现次数
void copy(List dest,List src)：将src中的内容复制到dest中
boolean replaceAll(List list，Object oldVal，Object newVal)：使用新值替换List 对象的所有旧值
```
##### Collections常用方法：同步控制
**Collections 类中提供了多个 synchronizedXxx() 方法，该方法可使将指定集合包装成线程同步的集合，从而可以解决多线程并发访问集合时的线程安全问题**
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201219194709.png)

##### 补充：Enumeration
* Enumeration 接口是 Iterator 迭代器的 “古老版本”
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201219194851.png)

```java
Enumeration stringEnum = new StringTokenizer("a-b*c-d-e-g", "-");
while(stringEnum.hasMoreElements()){
Object obj = stringEnum.nextElement();
System.out.println(obj); 
}
```
#### 数据结构脑图
![](https://gitee.com/pudding-bear-fithnis/picture-sourse/raw/master/20201219210305.png)

![](https://i.loli.net/2021/01/04/fgd8JbsBh7GpPR6.png)
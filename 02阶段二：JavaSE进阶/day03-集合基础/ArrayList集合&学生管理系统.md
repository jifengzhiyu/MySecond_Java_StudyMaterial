## 1.ArrayList

**集合和数组的区别 :** 

​	共同点：都是存储数据的容器

​	不同点：数组的容量是固定的，集合的容量是可变的

### 1.1 -ArrayList的构造方法和添加方法

| public ArrayList()                   | 创建一个空的集合对象               |
| ------------------------------------ | ---------------------------------- |
| public boolean add(E e)              | 将指定的元素追加到此集合的末尾     |
| public void add(int index,E element) | 在此集合中的指定位置插入指定的元素 |

**ArrayList<E> ：** 

​	可调整大小的数组实现 

​	<E> : 是一种特殊的数据类型，泛型。

**怎么用呢 ?**	

​	在出现E的地方我们使用引用数据类型替换即可	

​	举例：ArrayList<String>, ArrayList<Student>

### 1.2ArrayList类常用方法【应用】

**成员方法 : **

| public boolean remove(Object o)   | 删除指定的元素，返回删除是否成功       |
| --------------------------------- | -------------------------------------- |
| public E remove(int index)        | 删除指定索引处的元素，返回被删除的元素 |
| public E set(int index,E element) | 修改指定索引处的元素，返回被修改的元素 |
| public E get(int index)           | 返回指定索引处的元素                   |
| public int size()                 | 返回集合中的元素的个数                 |

**示例代码 :** 

```java
public class ArrayListDemo02 {
    public static void main(String[] args) {
        //创建集合
        ArrayList<String> array = new ArrayList<String>();

        //添加元素
        array.add("hello");
        array.add("world");
        array.add("java");

        //public boolean remove(Object o)：删除指定的元素，返回删除是否成功
//        System.out.println(array.remove("world"));
//        System.out.println(array.remove("javaee"));

        //public E remove(int index)：删除指定索引处的元素，返回被删除的元素
//        System.out.println(array.remove(1));

        //IndexOutOfBoundsException
//        System.out.println(array.remove(3));

        //public E set(int index,E element)：修改指定索引处的元素，返回被修改的元素
//        System.out.println(array.set(1,"javaee"));

        //IndexOutOfBoundsException
//        System.out.println(array.set(3,"javaee"));

        //public E get(int index)：返回指定索引处的元素
//        System.out.println(array.get(0));
//        System.out.println(array.get(1));
//        System.out.println(array.get(2));
        //System.out.println(array.get(3)); //？？？？？？ 自己测试

        //public int size()：返回集合中的元素的个数
        System.out.println(array.size());

        //输出集合
        System.out.println("array:" + array);
    }
}
```

### 1.3 ArrayList存储字符串并遍历

**案例需求 :** 

​	创建一个存储字符串的集合，存储3个字符串元素，使用程序实现在控制台遍历该集合

**实现步骤 :** 

 	1:创建集合对象
 	    2:往集合中添加字符串对象
 	    3:遍历集合，首先要能够获取到集合中的每一个元素，这个通过get(int index)方法实现
 	    4:遍历集合，其次要能够获取到集合的长度，这个通过size()方法实现
 	    5:遍历集合的通用格式

**代码实现 :** 

```java
/*
    思路：
        1:创建集合对象
        2:往集合中添加字符串对象
        3:遍历集合，首先要能够获取到集合中的每一个元素，这个通过get(int index)方法实现
        4:遍历集合，其次要能够获取到集合的长度，这个通过size()方法实现
        5:遍历集合的通用格式
 */
public class ArrayListTest01 {
    public static void main(String[] args) {
        //创建集合对象
        ArrayList<String> array = new ArrayList<String>();

        //往集合中添加字符串对象
        array.add("刘正风");
        array.add("左冷禅");
        array.add("风清扬");

        //遍历集合，其次要能够获取到集合的长度，这个通过size()方法实现
//        System.out.println(array.size());

        //遍历集合的通用格式
        for(int i=0; i<array.size(); i++) {
            String s = array.get(i);
            System.out.println(s);
        }
    }
}
```

### 1.4 ArrayList存储学生对象并遍历

**案例需求 :** 

​	创建一个存储学生对象的集合，存储3个学生对象，使用程序实现在控制台遍历该集合

**实现步骤 : ** 

​	1:定义学生类    

​	2:创建集合对象    

​	3:创建学生对象    

​	4:添加学生对象到集合中    

​	5:遍历集合，采用通用遍历格式实现

**代码实现 :**

```java
/*
    思路：
        1:定义学生类
        2:创建集合对象
        3:创建学生对象
        4:添加学生对象到集合中
        5:遍历集合，采用通用遍历格式实现
 */
public class ArrayListTest02 {
    public static void main(String[] args) {
        //创建集合对象
        ArrayList<Student> array = new ArrayList<>();

        //创建学生对象
        Student s1 = new Student("林青霞", 30);
        Student s2 = new Student("风清扬", 33);
        Student s3 = new Student("张曼玉", 18);

        //添加学生对象到集合中
        array.add(s1);
        array.add(s2);
        array.add(s3);

        //遍历集合，采用通用遍历格式实现
        for (int i = 0; i < array.size(); i++) {
            Student s = array.get(i);
            System.out.println(s.getName() + "," + s.getAge());
        }
    }
}
```

### 1.5 键盘录入学生信息到集合

**案例需求 :** 

​	创建一个存储学生对象的集合，存储3个学生对象，使用程序实现在控制台遍历该集合

​        学生的姓名和年龄来自于键盘录入

**实现步骤 :**

​	1:定义学生类，为了键盘录入数据方便，把学生类中的成员变量都定义为String类型    

​	2:创建集合对象    

​	3:键盘录入学生对象所需要的数据    

​	4:创建学生对象，把键盘录入的数据赋值给学生对象的成员变量    

​	5:往集合中添加学生对象    

​	6:遍历集合，采用通用遍历格式实现

**代码实现 :** 

```java
/*
    思路：
        1:定义学生类，为了键盘录入数据方便，把学生类中的成员变量都定义为String类型
        2:创建集合对象
        3:键盘录入学生对象所需要的数据
        4:创建学生对象，把键盘录入的数据赋值给学生对象的成员变量
        5:往集合中添加学生对象
        6:遍历集合，采用通用遍历格式实现
 */
public class ArrayListTest {
    public static void main(String[] args) {
        //创建集合对象
        ArrayList<Student> array = new ArrayList<Student>();

        //为了提高代码的复用性，我们用方法来改进程序
        addStudent(array);
        addStudent(array);
        addStudent(array);

        //遍历集合，采用通用遍历格式实现
        for (int i = 0; i < array.size(); i++) {
            Student s = array.get(i);
            System.out.println(s.getName() + "," + s.getAge());
        }
    }

    /*
        两个明确：
            返回值类型：void
            参数：ArrayList<Student> array
     */
    public static void addStudent(ArrayList<Student> array) {
        //键盘录入学生对象所需要的数据
        Scanner sc = new Scanner(System.in);

        System.out.println("请输入学生姓名:");
        String name = sc.nextLine();

        System.out.println("请输入学生年龄:");
        String age = sc.nextLine();

        //创建学生对象，把键盘录入的数据赋值给学生对象的成员变量
        Student s = new Student();
        s.setName(name);
        s.setAge(age);

        //往集合中添加学生对象
        array.add(s);
    }
}
```


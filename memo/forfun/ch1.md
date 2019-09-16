
[TOC]

### 1. 实现Singleton

**饿汉式单例**

```java
/**
 * 基本的饿汉式单例
 * 简介：利用JVM对类的初始化机制保证单例，线程安全，不能延时加载
 */
public class BasicHangerySingleton {
    private static BasicHangerySingleton instance = new BasicHangerySingleton();
    private BasicHangerySingleton(){}
    public static BasicHangerySingleton getInstance() {
        return instance;
    }
}

```

**懒汉式单例**

```java
/**
 * 最基本的懒汉式单例
 * 简介：延时加载，线程不安全，因为多个线程同时调用getInstance会导致同时生成多个实例
 */
public class BasicLazySingleton {
    private static BasicLazySingleton instance;
    private BasicLazySingleton(){}
    public static BasicLazySingleton getInstance() {
        if (instance == null) {
            instance = new BasicLazySingleton();
        }
        return instance;
    }
}
```

**双重检查懒汉式单例**

```java
/**
 * 配合锁的双重检查单例
 * 简介：具备延时加载特性，只有在实例化时才会上锁，线程安全
 */
public class DoubleCheckLazySingleton {
    private volatile static DoubleCheckLazySingleton instance;
    private DoubleCheckLazySingleton(){}
    public static DoubleCheckLazySingleton getInstance() {
        if (instance == null) {
            synchronized (DoubleCheckLazySingleton.class) {
                if (instance == null) {
                    instance = new DoubleCheckLazySingleton();
                }
            }
        }
        return instance;
    }
}
```

**利用枚举的单例**

```java
/**
 * 基于枚举的单例
 * 简介：线程安全，编写简单，能防止反射和序列化对单例的破坏，不能派生
 */
public enum EnumSingleton {
    INSTANCE;
}
```

**静态内部类实现单例**

```java
/**
 * 基于静态内部类的单例模式
 * 简介：由类加载机制保证线程安全，具备延时加载特性，缺点是多引入一个类
 */
public class InnerStaticHolderSingleton {
    private static class SingletonHolder {
        private static final InnerStaticHolderSingleton INSTANCE = new InnerStaticHolderSingleton();
    }
    private InnerStaticHolderSingleton(){}
    public InnerStaticHolderSingleton getInstance() {
        return SingletonHolder.INSTANCE;
    }
}
```

**含有缓存支持批量管理的单例**

```java
/**
 * Spring中单例Bean的管理模式
 * 简介：单例被注册到一个Map中，所有获取对象的行为都要通过管理类获取。由管理类负责保证单例的创建和唯一。
 */
```

### 2. 数组中重复的数字

```java
/**
 * 题目一：找出数组中重复的数字
 * 说明：在一个长度为 n 的数组里所有的数字都在 0~n-1 的范围内
 *      数组中某些数字是重复的，但不知道有几个重复了，也不知道每个数字重复多少次
 *      请找出数组中任意一个重复的数字
 *      如：输入长度 7 的数组{2, 3, 1, 0, 2, 5, 3}，那么对应的输出应该是 2 或者 3
 */
public class FindDuplicateNumber {

    /**
     * 第一种思路，对数组进行排序
     */
    public int getBySort(int[] array) {}

    /**
     * 第二种思路，遍历数组，将元素放入哈希表，利用哈希表来检查
     */
    public int getByHash(int[] array) {}

    /**
     * 第三种思路，利用题目特性，将数字与数组元素下标对应，类似快速排序的方式通过交换让数字被放入对应的位置，当交换时发现两个数字相同则重复数字找到
     */
    public int getBySwap(int[] array) {
        for(int i = 0; i < array.length; i++) {
            while(array[i] != i) {
                int temp = array[i];
                if (temp == array[temp]) {
                    return temp;
                } else {
                    array[i] = array[temp];
                    array[temp] = temp;
                }
            }
        }
        //假定找不见的情况返回-1
        return -1;
    }
}
```

```java
/**
 * 题目二：找出数组中重复的数字
 * 说明：在一个长度为 n+1 的数组里所有的数字都在 0~n 的范围内，所以数组中至少有一个数字重复
 *      请找出数组中任意一个重复的数字，但不能修改数组
 *      如：输入长度 8 的数组{2, 3, 5, 4, 3, 2, 6, 7}，那么对应的输出应该是 2 或者 3
 */
public class FindDuplicateNumberWithNoEdit {
    /**
     * 不允许修改，考虑使用辅助数组，在辅助数组中完成排序或者哈希或者交换
     */

    /**
     * 不使用额外空间，利用二分法统计不同区间数字出现的次数，逐步缩小范围，最后找到数字
     */
}

```

### 3. 二维数组中的查找

```java
/**
 * 题目：在一个二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序
 *      请完成一个函数，输入这样的一个二维数组和整数，判断数组中是否有该整数
 *      如下二维数组中，查找 7 则返回true，查找 5 则返回false
 *          1   2   8   9
 *          2   4   9   12
 *          4   7   10  13
 *          6   8   11  15
 */
public class FindInMatrix {
}

```

### 4. 替换空格

### 5. 从头到尾打印链表

### 6. 重建二叉树

### 7. 二叉树的下一个节点

### 8. 用两个栈实现队列

### 9. 斐波那契数列

### 10. 旋转数组的最小数字

### 11. 矩阵中的路径

### 12. 机器人的运动范围

### 13. 剪绳子

### 14. 二进制中的一个数

### 15. 数值的整数次方

### 16. 打印从1到最大的n位数

### 17. 删除链表的节点

### 18. 正则表达式匹配

### 19. 表示数值的字符串

### 20. 调整数组顺序使奇数位于偶数前面

### 21. 链表中倒数第k个节点

### 22. 链表中环的入口节点

### 23. 反转链表

### 24. 合并两个排序的链表

### 25. 树的子结构

### 26. 二叉树的镜像

### 27. 对称的二叉树

### 28. 顺时针打印矩阵

### 29. 包含min函数的栈

### 30. 栈的压入、弹出序列

### 31. 从上到下打印二叉树

### 32. 二叉搜索树的后序遍历序列

### 33. 二叉树中为某一值的路径

### 34. 复杂链表的复制

### 35. 二叉搜索树与双向链表

### 36. 序列化二叉树

### 37. 字符串的排列

### 38. 数组中出现次数超过一半的数字

### 39. 最小的k个数

### 40. 数据流中的中位数

### 41. 连续子数组的最大和

### 42. 1~n整数中1出现的次数

### 43. 数字序列中某一位的数字

### 44. 把数组排成最小的数

### 45. 把数字翻译成字符串

### 46. 礼物的最大价值

### 47. 最长不含重复字符的字符串

### 48. 丑数

### 49. 第一个只出现一次的字符

### 50. 数组中的逆序对

### 51. 两个链表的第一个公共节点

### 52. 在排序数组中查找数字

### 53. 二叉搜索树的第k大节点

### 54. 二叉树的深度

### 55. 数组中数字出现的次数

### 56. 和为s的数字

### 57. 翻转字符串

### 58. 队列的最大值

### 59. n个色子的点数

### 60. 扑克牌中的顺子

### 61. 圆圈中最后剩下的数字

### 62. 股票的最大利润

### 63. 求1+2+···+n

### 64. 不用加减乘除做加法

### 65. 构建乘积数组

### 66. 把字符串转换成整数

### 67. 树种两个节点的最低公共祖先

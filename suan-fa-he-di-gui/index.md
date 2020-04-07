# 算法和递归

# 算法

## 冒泡排序（bubble）

冒泡排序(Bubble Sorting)的基本思想是:通过对待排序序列从前向后(从下标较小的元素开始),依次比较 相邻元素的值，若发现逆序则交换，使值较大的元素逐渐从前移向后部，就象水底下的气泡一样逐渐向上冒。

<!-- more -->

小结上面的图解过程:
 (1) 一共进行 数组的大小-1 次 大的循环
 (2)每一趟排序的次数在逐渐的减少
 (3) 如果我们发现在某趟排序中，没有发生一次交换， 可以提前结束冒泡排序。这个就是优化

![](https://linon419.github.io/post-images/1582671024250.png)
```java
package com.yang.sort.bubble;

import java.util.Arrays;

public class BubbleTest {

    public static void main(String[] args) {
        int arr[] = {3, 9, -1, 10, -2};
        BubbleSort(arr);


        System.out.println(Arrays.toString(arr));

    }
    //封装为方法
    public static void BubbleSort(int arr[]){
        int temp;
        boolean flag = false;
        // 两个指针(i,j)指向0和1号元素

        // 判断两个元素的大小，如果arr[i]>arr[j]，两个元素数值交换

        //依次类推，直到i=arr.length-1,第一回合结束
        for (int k = 0; k < arr.length-1; k++) {

            for (int i = 0; i < arr.length-1-k; i++) {
                int j = i+1;
                if (arr[i] > arr[j]) {
                    flag = true;
                    temp = arr[j];
                    arr[j] = arr[i];
                    arr[i] = temp;
                }

            }
            if(flag==false){//如果flag为false，表示一次交换都没发生过，表示为顺序
                break;
            }
            else flag = false;
        }
    }
}

```

## 选择排序（select）

选择排序(select sorting)也是一种简单的排序方法。它的基本思想是:第一次从 arr[0]~arr[n-1]中选取最小值，

与 arr[0]交换，第二次从 arr[1]~arr[n-1]中选取最小值，与 arr[1]交换，第三次从 arr[2]~arr[n-1]中选取最小值，与 arr[2] 交换，...，第 i 次从 arr[i-1]~arr[n-1]中选取最小值，与 arr[i-1]交换，..., 第 n-1 次从 arr[n-2]~arr[n-1]中选取最小值， 与 arr[n-2]交换，总共通过 n-1 次，得到一个按排序码从小到大排列的有序序列。

先找出最小值，然后与第一个交换

![](https://linon419.github.io/post-images/1582671057143.png)

代码

```java
package com.yang.sort.select;

import java.util.Arrays;

public class SelectTest {
    public static void main(String[] args) {
        int arr[] = {3, 9, -1, 10, -2};
        //假定a[0]是最小的
        //a[0]去和a[1]-a[arr.length-1]比较
        //如果a[0]>a[j],交换

        for (int k = 0; k < arr.length-1; k++) {
            int minIndex = k;
            int min = arr[k];
            for (int i = k+1; i < arr.length; i++) {
                if (min>arr[i]){//说明假定的最小值，并不是最小值
                    min = arr[i];
                    minIndex = i;
                }
            }
            //看看最小值是不是arr[0]
            if (minIndex!=k){
                arr[minIndex] = arr[k];
                arr[k] = min;
            }
        }

        System.out.println(Arrays.toString(arr));
    }


//        int minIndex= 0;
//        int min = arr[0];
//        //第一回合
//        //先查找最小值
//        for (int i = 0+1; i < arr.length; i++) {
//            if (min>arr[i]){//说明假定的最小值，并不是最小值
//                min = arr[i];
//                minIndex = i;
//            }
//        }
//        //看看最小值是不是arr[0]
//        if (minIndex!=0){
//            arr[minIndex] = arr[0];
//            arr[0] = min;
//        }
//        System.out.println(Arrays.toString(arr));
//
//        //第二回合
//        //查找最小值从a[1]开始
//        //假定a[1]是最小值
//        minIndex = 1;
//        min = arr[1];
//        for (int i = 0+2; i < arr.length; i++) {
//            if (arr[i]<min){//如果假定的最小不是最小
//                minIndex = i;//找出最小值下标
//                min = arr[i];//找出最小值
//            }
//        }
//
//        if (minIndex!=1){
//            arr[minIndex] = arr[1];
//            arr[1] = min;
//        }
//        System.out.println(Arrays.toString(arr));
//
//    }
}

```

## 插入排序（insert）

插入排序(Insertion Sorting)的基本思想是:把 **n** 个待排序的元素看成为一个有序表和一个无序表，开始时有 序表中只包含一个元素，无序表中包含有 **n-1** 个元素，排序过程中每次从无序表中取出第一个元素，把它的排 序码依次与有序表元素的排序码进行比较，将它插入到有序表中的适当位置，使之成为新的有序表。

![](https://linon419.github.io/post-images/1582671071018.png)

```java
package com.yang.sort.insert;

import java.util.Arrays;

public class InsertTest {
    public static void main(String[] args) {
        int[] arr = {101,34,119,1};
        selectSort(arr);

    }

    public static void selectSort(int[] arr){

        for (int i = 1; i < arr.length; i++) {
            int insertVal = arr[i];//要插入的数值
            int insertIndex = i-1;//要插入的位置

            System.out.println(Arrays.toString(arr));
            while(insertIndex>=0&&insertVal<arr[insertIndex]){
                arr[insertIndex+1] = arr[insertIndex];
                arr[insertIndex] = insertVal;
                insertIndex--;
            }
        }

        //先把数组分为有序数组和无序数组

        //a[0]为有序数组，其他为无序数组

        // 把a[1]存储到临时变量中

        // 把a[1]与a[0]比较，如果a[1]<a[0]，a[0]后移一位，原来的a[0]与临时变量交换
        //第一回合

//        int insertVal = arr[1];//要插入的数值
//        int insertIndex = 0;//要插入的位置
//
//        System.out.println(Arrays.toString(arr));
//        while(insertIndex>=0&&insertVal<arr[insertIndex]){
//            arr[insertIndex+1] = arr[insertIndex];
//            arr[insertIndex] = insertVal;
//            insertIndex--;
//        }
        System.out.println(Arrays.toString(arr));
    }
}

```

## 希尔排序（shell）



希尔排序是把记录按下标的一定增量分组，对每组使用直接插入排序算法排序;随着增量逐渐减少，每组包含

的关键词越来越多，当增量减至 **1** 时，整个文件恰被分成一组，算法便终止



![](https://linon419.github.io/post-images/1582671087725.png)




```java
package com.yang.sort.shell;

import java.util.Arrays;

public class Shell {
    public static void main(String[] args) {
        int[] arr = {8,9,1,7,2,3,5,4,6,0};
        shellSort(arr);
        System.out.println(Arrays.toString(arr));
    }

    public static void shellSort(int[] arr){
        int temp = 0;
        //遍历所有步长
        for (int gap = arr.length/2; gap > 0; gap=gap/2) {
            //遍历所有元素
            for (int i = gap; i <arr.length ; i++) {
                //遍历本组中所有的元素
                for (int j = i-gap; j >=0 ; j-=gap) {
                    //如果当前元素大于加上步长的哪个元素
                    if (arr[j]>arr[j+gap]){
                        temp = arr[j];
                        arr[j] = arr[j+gap];
                        arr[j+gap] = temp;
                    }
                }
            }
        }
//        //第一轮
//        //将10个数据分为5组，每组2个数据
//        //每组数据进行比较，如果a[i]>a[i+5]，交换
//        int temp = 0;
//        for (int i = 5; i <arr.length ; i++) {
//            //遍历各组所有元素，步长5
//            for (int j = i-5; j >= 0; j=j-5) {
//                if (arr[j]>arr[j+5]){
//                    temp = arr[j];
//                    arr[j] = arr[j+5];
//                    arr[j+5] = temp;
//                }
//            }
//        }
//        System.out.println("第一轮排序后"+Arrays.toString(arr));
//
//        //第二轮排序，分为了5/2 = 2组
//        for (int i = 2; i < arr.length; i++) {
//            //遍历所有元素，共2组，每组5个元素，步长为2
//            for (int j = i-2; j >=0; j-=2) {
//                if (arr[j]>arr[j+2]){
//                    temp = arr[j];
//                    arr[j] = arr[j+2];
//                    arr[j+2] = temp;
//                }
//            }
//        }
//        //第三轮排序，分为1组
//        for (int i = 1; i < arr.length; i++) {
//            //遍历所有元素，共一组，10个元素
//            for (int j = i-1; j >=0; j-=1) {
//                if (arr[j]>arr[j+2]){
//                    temp = arr[j];
//                    arr[j] = arr[j+2];
//                    arr[j+2] = temp;
//                }
//            }
//        }

    }
}

```



## 快速排序(Quicksort)

快速排序(Quicksort)是对冒泡排序的一种改进。基本思想是:通过一趟排序将要排序的数据分割成独立的两 部分，其中一部分的所有数据都比另外一部分的所有数据都要小，然后再按此方法对这两部分数据分别进行快速排 序，整个排序过程可以递归进行，以此达到整个数据变成有序序列



![](https://linon419.github.io/post-images/1582671102783.png)
```java
package com.yang.sort.quicksort;

import java.util.Arrays;

public class QuickSort {
    public static void main(String[] args) {
        int[] arr = {-9,78,0,23,-567,70, -1,900, 4561};
        quickSort(arr,0,arr.length-1);
        System.out.println(Arrays.toString(arr));
     }
    public static void quickSort(int[] arr, int low, int high){
        if (low<high){
            //定义左标，右标
            int i = low;
            int j = high;
            //定义基础值
            int x = arr[low];

            while (i<j){
                //若右标数值大于x，左移
                while (i<j&&arr[j]>x){
                    j--;
                }
                //如果不是，交换
                arr[i] = arr[j];
                //若左标值小于x，右移
                while (i<j&&arr[i]<x){
                    i++;
                }
                //如果不是，交换
                arr[j] = arr[i];
            }
            arr[i] = x;

            //递归
            //从小的开始
            quickSort(arr,low,i);
            //大的开始
            quickSort(arr,i+1,high);
        }
    }
}

```



## 归并排序（merge）

原理：

![](https://linon419.github.io/post-images/1582671114227.png)


```java
package com.yang.sort.merge;

import java.util.Arrays;

public class MergeSort {
 public static void main(String[] args) {
        int[] arr = new int[]{-9,78,0,23,-567,70, -1,900, 4561};
        mergeSort(arr, 0, arr.length-1);
        System.out.println(Arrays.toString(arr));
    }

    public static void mergeSort(int[] arr, int low, int high){
        int middle = (low+high)/2;
        if (low<high){
            //处理左边
            mergeSort(arr,low,middle);
            //处理右边
            mergeSort(arr,middle+1,high);
            //归并
            merge(arr,low,middle,high);
        }

    }
    public static void merge(int[] arr, int low, int middle, int high){
        //用于临时存储的数组
        int[] temp = new int[high-low+1];
        //记录第一个数组的下标
        int i = low;
        //记录第二个数组的下标
        int j = middle+1;
        //临时数组下标
        int index = 0;
        //遍历两个数组取出最小的数，放入临时数组
        while (i<=middle&&j<=high){
            if (arr[i]<=arr[j]){
                temp[index] = arr[i];
                i++;
            }
            else {
                temp[index] = arr[j];
                j++;
            }
            index++;
        }
        //处理多余数据
        //当左侧数据多余时
        while (i<=middle){
            temp[index] = arr[i];
            index++;
            i++;
        }
        while (j<=high){
            temp[index] = arr[j];
            index++;
            j++;
        }
        for (int k = 0; k < temp.length; k++) {
            arr[k+low] = temp[k];
        }

    }
}

```



## 基数排序（radix）

原理：


![](https://linon419.github.io/post-images/1582671148394.png)

```java
package radixsort;

import java.util.Arrays;

public class RadixSort {
    public static void main(String[] args) {
        int[] arr = new int[]{789,6,12,943,23,88,1,50,10,3,49};
        radixSort(arr);
        System.out.println(Arrays.toString(arr));
    }

    public static void radixSort(int[] arr) {
        //找出数组中最大的数字
        int max = Integer.MIN_VALUE;
        for (int i = 0; i < arr.length; i++) {
            if (max<arr[i]){
                max = arr[i];
            }
        }
        //System.out.println(max);

        //计算最大的数是几位数
        int maxlength = (max+"").length();
        //用于临时存储数据的数组
        int temp[][] = new int[10][arr.length];
        //用于记录在temp中相应的数组中个数
        int counts[] = new int[10];
        //根据最大的长度决定比较的次数
        for (int i = 0, n=1; i < maxlength; i++,n*=10) {
            //计算出每个数字的余数
            for (int j = 0; j < arr.length; j++) {
                //计算余数
                int ys = arr[j] / n % 10;
                //把当前遍历的数组放入指定数组中
                temp[ys][counts[ys]] = arr[j];
                //记录数量
                counts[ys]++;
            }
                //记录个数
            int index = 0;

                //把数字取出来
            for (int k = 0; k < counts.length; k++) {
                //记录的数组中当前余数记录的数量不为0
                if (counts[k]!=0){
                    //循环取出元素
                    for (int l = 0; l < counts[k]; l++) {
                        //取出元素
                        arr[index] = temp[k][l];
                        index++;
                    }
                    //把数量置为0
                    counts[k]=0;
                }
            }
        }
    }
}
```



# 递归(Recursion)

## 概念

简单的说: 递归就是方法自己调用自己,每次调用时传入不同的变量.递归有助于编程者解决复杂的问题,同时

可以让代码变得简洁。

![](https://linon419.github.io/post-images/1582671164600.png)
## 递归要遵守的规则

1.   执行一个方法时，就创建一个新的受保护的独立空间(栈空间)
2.   方法的局部变量是独立的，不会相互影响,比如n变量
3.   如果方法中使用的是引用类型变量(比如数组)，就会共享该引用类型的数据.
4.   递归必须向退出递归的条件逼近，否则就是无限递归,出现StackOverflowError，死龟了:)
5.   当一个方法执行完毕，或者遇到return，就会返回，遵守谁调用，就将结果返回给谁，同时当方法执行完毕或者返回时，该方法也就执行完毕



# 排序

## 选择排序

选择排序（Selection sort）是一种简单直观的排序算法。它的工作原理如下。首先在未排序序列中找到最小（大）元素，存放到排序序列的起始位置，然后，再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。以此类推，直到所有元素均排序完毕。
选择排序的主要优点与数据移动有关。如果某个元素位于正确的最终位置上，则它不会被移动。选择排序每次交换一对元素，它们当中至少有一个将被移到其最终位置上，因此对n个元素的表进行排序总共进行至多n−1
次交换。在所有的完全依靠交换去移动元素的排序方法中，选择排序属于非常好的一种。

```java
public static void selection_sort(int[] arr) {
    int i, j, min, temp, len = arr.length;
    for (i = 0; i < len - 1; i++) {
        min = i;//未排序序列中最小数据数组下标
        for (j = i + 1; j < len; j++)//在未排序元素中继续寻找最小元素，并保存其下标
            if (arr[min] > arr[j]){
                min = j;}
        temp = arr[min]; //将最小元素放到已排序序列的末尾
        arr[min] = arr[i];
        arr[i] = temp;
    }
}

```

## 插入排序

插入排序（英语：Insertion Sort）是一种简单直观的排序算法。它的工作原理是通过构建有序序列，对于未排序数据，在已排序序列中从后向前扫描，找到相应位置并插入。插入排序在实现上，通常采用in-place排序（即只需用到
O(1)
{\displaystyle O(1)}的额外空间的排序），因而在从后向前扫描过程中，需要反复把已排序元素逐步向后挪位，为最新元素提供插入空间。

```java
public void insertionSort(int[] array) {
        for (int i = 1; i < array.length; i++) {
            int key = array[i];
            int j = i - 1;
            while (j >= 0 && array[j] > key) {
                array[j + 1] = array[j];
                j--;
            }
        array[j + 1] = key;
        }
    }
```

## 冒泡排序

冒泡排序
Bubble sort animation.gif
使用冒泡排序为一列数字进行排序的过程
分类        排序算法
数据结构        数组
最坏时间复杂度  {\displaystyle O(n^{2})} O(n^{2})
最优时间复杂度  {\displaystyle O(n)} O(n)
平均时间复杂度  {\displaystyle O(n^{2})} O(n^{2})
最坏空间复杂度  总共 {\displaystyle O(n)} O(n)，需要辅助空间 {\displaystyle O(1)} O(1)

冒泡排序
冒泡排序（英语：Bubble Sort）是一种简单的排序算法。它重复地走访过要排序的数列，一次比较两个元素，如果他们的顺序错误就把他们交换过来。走访数列的工作是重复地进行直到没有再需要交换，也就是说该数列已经排序完成。这个算法的名字由来是因为越小的元素会经由交换慢慢“浮”到数列的顶端。

冒泡排序对 {\displaystyle n} n个项目需要O( {\displaystyle n^{2}} n^{2})的比较次数，且可以原地排序。尽管这个算法是最简单了解和实现的排序算法之一，但它对于包含大量的元素的数列排序是很没有效率的。

冒泡排序是与插入排序拥有相等的运行时间，但是两种算法在需要的交换次数却很大地不同。在最坏的情况，冒泡排序需要 {\displaystyle O(n^{2})} O(n^{2})次交换，而插入排序只要最多 {\displaystyle O(n)} O(n)交换。冒泡排序的实现（类似下面）通常会对已经排序好的数列拙劣地运行（ {\displaystyle O(n^{2})} O(n^{2})），而插入排序在这个例子只需要 {\displaystyle O(n)} O(n)个运算。因此很多现代的算法教科书避免使用冒泡排序，而用插入排序取代之。冒泡排序如果能在内部循环第一次运行时，使用一个旗标来表示有无需要交换的可能，也可以把最优情况下的复杂度降低到 {\displaystyle O(n)} O(n)。在这个情况，已经排序好的数列就无交换的需要。若在每次走访数列时，把走访顺序反过来，也可以稍微地改进效率。有时候称为鸡尾酒排序，因为算法会从数列的一端到另一端之间穿梭往返。

冒泡排序算法的运作如下：

比较相邻的元素。如果第一个比第二个大，就交换他们两个。
对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对。这步做完后，最后的元素会是最大的数。
针对所有的元素重复以上的步骤，除了最后一个。
持续每次对越来越少的元素重复上面的步骤，直到没有任何一对数字需要比较。

```java
public static void bubbleSort(int[] arr) {
    int i, temp, len = arr.length;
    boolean changed;
    do {
      changed = false;
      len-=1;
      for (i = 0; i < len; i++) {
        if (arr[i] > arr[i + 1]) {
          temp = arr[i];
          arr[i] = arr[i + 1];
          arr[i + 1] = temp;
          changed = true;
        }
      }
    } while (changed);
  }
  
  public static void bubbleSort2(Comparable[] arr) {
        int n = arr.length;
        int newn;
        do {
            newn = 0;
            for (int i = 1; i < n; i++)
                if (arr[i - 1].compareTo(arr[i]) > 0) {
                    swap(arr, i - 1, i);
                    newn = i;
                }
            n = newn;
        } while (newn > 0);
  }

```

## 归并排序

归并排序（英语：Merge sort，或mergesort），是创建在归并操作上的一种有效的排序算法，效率为 O(n\log n) O(n\log n)（大O符号）。1945年由约翰·冯·诺伊曼首次提出。该算法是采用分治法（Divide and Conquer）的一个非常典型的应用，且各层分治递归可以同时进行。

### 递归法（Top-down)

1.申请空间，使其大小为两个已经排序序列之和，该空间用来存放合并后的序列  
2.设定两个指针，最初位置分别为两个已经排序序列的起始位置  
3.比较两个指针所指向的元素，选择相对小的元素放入到合并空间，并移动指针到下一位置  
4.重复步骤3直到某一指针到达序列尾  
5.将另一序列剩下的所有元素直接复制到合并序列尾

```java


static void merge_sort_recursive(int[] arr, int[]result, int start, int end) {
    if (start >= end)
        return;
    int len = end - start, mid = (len >> 1) + start;
    int start1 = start, end1 = mid;
    int start2 = mid + 1, end2 = end;
    merge_sort_recursive(arr, result, start1, end1);
    merge_sort_recursive(arr, result, start2, end2);
    int k = start;
    while (start1 <= end1 && start2 <= end2)
        result[k++] = arr[start1] < arr[start2] ? arr[start1++] : arr[start2++];
    while (start1 <= end1)
        result[k++] = arr[start1++];
    while (start2 <= end2)
        result[k++] = arr[start2++];
    for (k = start; k <= end; k++)
        arr[k] = result[k];
}
public static void merge_sort(int[] arr) {
    int len = arr.length;
    int[] result = new int[len];
    merge_sort_recursive(arr, result, 0, len - 1);
}

```

### 迭代法（Bottom-up）

原理如下（假设序列共有n个元素）：  
1.将序列每相邻两个数字进行归并操作，形成 {\displaystyle ceil(n/2)} {\displaystyle ceil(n/2)}个序列，排序后每个序列包含两/一个元素  
2.若此时序列数不是1个则将上述序列再次归并，形成 {\displaystyle ceil(n/4)} {\displaystyle ceil(n/4)}个序列，每个序列包含四/三个元素  
3.重复步骤2，直到所有元素排序完毕，即序列数为1  

### 归排小结

归并排序是稳定排序，它也是一种十分高效的排序，能利用完全二叉树特性的排序一般性能都不会太差。java中Arrays.sort()采用了一种名为TimSort的排序算法，就是归并排序的优化版本。从上文的图中可看出，每次合并操作的平均时间复杂度为O(n)，而完全二叉树的深度为|log2n|。总的平均时间复杂度为O(nlogn)。而且，归并排序的最好，最坏，平均时间复杂度均为O(nlogn)。

### 快速排序

快速排序（英语：Quicksort），又称划分交换排序（partition-exchange sort），简称快排，一种排序算法，最早由东尼·霍尔提出。在平均状况下，排序 {\displaystyle n} n个项目要 {\displaystyle \ O(n\log n)} {\displaystyle \ O(n\log n)}（大O符号）次比较。在最坏状况下则需要 {\displaystyle O(n^{2})} {\displaystyle O(n^{2})}次比较，但这种状况并不常见。事实上，快速排序 {\displaystyle \Theta (n\log n)} {\displaystyle \Theta (n\log n)}通常明显比其他算法更快，因为它的内部循环（inner loop）可以在大部分的架构上很有效率地达成。

快速排序采用“分而治之、各个击破”的观念，此为原地（In-place）分区版本。
快速排序使用分治法（Divide and conquer）策略来把一个序列（list）分为两个子序列（sub-lists）。  
步骤为：
1.从数列中挑出一个元素，称为"基准"（pivot）  
2.重新排序数列，所有比基准值小的元素摆放在基准前面，所有比基准值大的元素摆在基准后面（相同的数可以到任何一边）。在这个分区结束之后，该基准就处于数列的中间位置。这个称为分区（partition）操作。  
3.递归地（recursively）把小于基准值元素的子数列和大于基准值元素的子数列排序。  
递归到最底部时，数列的大小是零或一，也就是已经排序好了。这个算法一定会结束，因为在每次的迭代（iteration）中，它至少会把一个元素摆到它最后的位置去。  

```java
public static void q1Sort(int[] arr, int lo, int hi) {
        if (lo >= hi)
            return;
        int i = lo, j = hi + 1;
        while (true) {
            while (arr[lo] > arr[++i]) {
                if (i == hi)
                    break;
            }
            while (arr[lo] < arr[--j]) ;
            if (j > i) {
                swap(arr, i, j);
            } else {
                break;
            }
        }
        swap(arr, lo, j);
        q1Sort(arr, lo, j - 1);
        q1Sort(arr, j+1, hi);
    }

public static void qSort(int[] arr, int head, int tail) {
        if (head >= tail || arr == null || arr.length <= 1) {
            return;
        }
        int i = head, j = tail, pivot = arr[(head + tail) / 2];
        while (i <= j) {
            while (arr[i] < pivot) {
                ++i;
            }
            while (arr[j] > pivot) {
                --j;
            }
            if (i < j) {
                int t = arr[i];
                arr[i] = arr[j];
                arr[j] = t;
                ++i;
                --j;
            } else if (i == j) {
                ++i;
            }
        }
        qSort(arr, head, j);
        qSort(arr, i, tail);
    }

    private static void swap(int[] arr, int i, int j) {
        int tmp = arr[i];
        arr[i] = arr[j];
        arr[j] = tmp;
    }

    public static void main(String[] args) {
        int[] arr = new int[]{1, 4, 8, 2, 55, 3, 4, 8, 6, 4, 0, 11, 34, 90, 23, 54, 77, 9, 2, 9, 4, 10};
        q1Sort(arr, 0, arr.length - 1);
        String out = "";
        for (int digit : arr) {
            out += (digit + ",");
        }
        System.out.println(out);
    }
```

#### 快排小结  

注意:
1.基准选择
2.基准前的元素小于基准基准后的元素大于基准，循环退出条件
3.递归终止条件，递归参数数组的的起始位置和结束位置

## 堆排序

堆排序（英语：Heapsort）是指利用堆这种数据结构所设计的一种排序算法。堆积是一个近似完全二叉树的结构，并同时满足堆积的性质：即子结点的键值或索引总是小于（或者大于）它的父节点  
通常堆是通过一维数组来实现的。在数组起始位置为0的情形中:  

1. 父节点i的左子节点在位置 (2i+1);
2. 父节点i的右子节点在位置 (2i+2);  
3. 子节点i的父节点在位置  floor((i-1)/2)  

在堆的数据结构中，堆中的最大值总是位于根节点(在优先队列中使用堆的话堆中的最小值位于根节点)。堆中定义以下几种操作：

1. 最大堆调整（Max_Heapify）：将堆的末端子节点作调整，使得子节点永远小于父节点  
2. 创建最大堆（Build_Max_Heap）：将堆所有数据重新排序  
3. 堆排序（HeapSort）：移除位在第一个数据的根节点，并做最大堆调整的递归运算  

```java
import java.util.Arrays;

public class HeapSort {
    private int[] arr;

    public HeapSort(int[] arr){
        this.arr = arr;
    }
    /**
     * 堆排序的主要入口方法，共两步。
     */
    public void sort(){
        /*
         *  第一步：将数组堆化
         *  beginIndex = 第一个非叶子节点。
         *  从第一个非叶子节点开始即可。无需从最后一个叶子节点开始。
         *  叶子节点可以看作已符合堆要求的节点，根节点就是它自己且自己以下值为最大。
         */
        int len = arr.length - 1;
        int beginIndex = (len - 1) >> 1;
        for(int i = beginIndex; i >= 0; i--){
            maxHeapify(i, len);
        }
        /*
         * 第二步：对堆化数据排序
         * 每次都是移出最顶层的根节点A[0]，与最尾部节点位置调换，同时遍历长度 - 1。
         * 然后从新整理被换到根节点的末尾元素，使其符合堆的特性。
         * 直至未排序的堆长度为 0。
         */
        for(int i = len; i > 0; i--){
            swap(0, i);
            maxHeapify(0, i - 1);
        }
    }

    private void swap(int i,int j){
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }

    /**
     * 调整索引为 index 处的数据，使其符合堆的特性。
     *
     * @param index 需要堆化处理的数据的索引
     * @param len 未排序的堆（数组）的长度
     */
    private void maxHeapify(int index,int len){
        int li = (index << 1) + 1; // 左子节点索引
        int ri = li + 1;           // 右子节点索引
        int cMax = li;             // 子节点值最大索引，默认左子节点。

        if(li > len) return;       // 左子节点索引超出计算范围，直接返回。
        if(ri <= len && arr[ri] > arr[li]) // 先判断左右子节点，哪个较大。
            cMax = ri;
        if(arr[cMax] > arr[index]){
            swap(cMax, index);      // 如果父节点被子节点调换，
            maxHeapify(cMax, len);  // 则需要继续判断换下后的父节点是否符合堆的特性。
        }
    }

    /**
     * 测试用例
     *
     * 输出：
     * [0, 0, 0, 1, 1, 1, 2, 2, 2, 3, 3, 3, 4, 4, 4, 5, 5, 5, 6, 6, 6, 7, 7, 7, 8, 8, 8, 9, 9, 9]
     */
    public static void main(String[] args) {
        int[] arr = new int[]{3,5,3,0,8,6,1,5,8,6,2,4,9,4,7,0,1,8,9,7,3,1,2,5,9,7,4,0,2,6};
        new HeapSort(arr).sort();
        System.out.println(Arrays.toString(arr));
    }

}
```

### 希尔排序

思想：  

1. 通过不同的步长将原序列分成不同的组。
2. 组内进行插入排序。
3. 逐渐缩小步长，直至缩减到步长为一，整个序列有序

```java
public class shellSort {

    public static void shellSort(int[] array) {
        int number = array.length / 2;
        int i;
        int j;
        int temp;
        while (number >= 1) {
            for (i = number; i < array.length; i++) {
                temp = array[i];
                j = i - number;
                while (j >= 0 && array[j] < temp) {
                    array[j + number] = array[j];
                    j = j - number;
                }
                array[j + number] = temp;
            }
            number = number / 2;
        }
    }

    // 打印完整序列
    public static void printAll(int[] list) {
        for (int value : list) {
            System.out.print(value + "\t");
        }
        System.out.println();
    }

    public static void main(String[] args)
    {

        int[] array = {
                9, 1, 2, 5, 7, 4, 8, 6, 3, 5
        };

        // 调用希尔排序方法
        System.out.print("排序前:\t\t");
        printAll(array);
        shellSort(array);
        System.out.print("排序后:\t\t");
        printAll(array);
    }
}
```

说明：希尔排序内部循环中，上面代码不是一次性将步长相同的元素一起进行插入排序，而是将i之前的步长相同的先排序，然后等到i自增到一个步长后，在进行这个步长的的排序，如此循环。

## 桶排序

桶排序（Bucket sort）或所谓的箱排序，是一个排序算法，工作的原理是将数组分到有限数量的桶里。每个桶再个别排序（有可能再使用别的排序算法或是以递归方式继续使用桶排序进行排序）。桶排序是鸽巢排序的一种归纳结果。当要被排序的数组内的数值是均匀分配的时候，桶排序使用线性时间（ {\displaystyle \Theta (n)} {\displaystyle \Theta (n)}（大O符号））。但桶排序并不是比较排序，他不受到 {\displaystyle O(n\log n)} {\displaystyle O(n\log n)}下限的影响

桶排序以下列程序进行：

1. 设置一个定量的数组当作空桶子 。
2. 寻访序列，并且把项目一个一个放到对应的桶子去。
3. 对每个不是空的桶子进行排序。
4. 从不是空的桶子里把项目再放回原来的序列中。



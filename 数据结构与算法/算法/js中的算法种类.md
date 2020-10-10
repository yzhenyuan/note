
# 排序算法


#### 排序对比
![avatar](https://user-gold-cdn.xitu.io/2016/11/29/4abde1748817d7f35f2bf8b6a058aa40?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)
**图片名词解释： n: 数据规模 k:“桶”的个数 In-place: 占用常数内存，不占用额外内存 Out-place: 占用额外内存**

# 查找算法
1. 顺序查找
2. 二分查找
3. 插值查找
4. 斐波那契查找
5. 树表查找
6. 分块查找
7. 哈希查找

### 1. 顺序查找
| 说明：顺序查找适合于存储 结构为:顺序存储或链接存储 的线性表。
基本思想：顺序查找也称为线形查找，属于无序查找算法。从数据结构线形表的一端开始，顺序扫描，依次将扫描到的结点关键字与给定值k相比较，若相等则表示查找成功；若扫描结束仍没有找到关键字等于k的结点，表示查找失败。

顺序查找的时间复杂度为O(n)。
```
function SequenceSearch(arr, value) {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] == value) {
            return i;
        }
    }
    return -1;
}
var arr = [1,3,4,5,2,4,2]
console.log(SequenceSearch(arr,2))
```
### 2. 二分查找
| 说明：元素必须是有序的，如果是无序的则要先进行排序操作

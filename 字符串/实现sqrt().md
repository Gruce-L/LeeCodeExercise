https://leetcode-cn.com/problems/sqrtx/submissions/



### 方法一：暴力解法

​		让ans从1开始自增，x不断与ans相除（前提是ans <= x / ans）,如果不满足，返回ans - 1 

```java
class Solution {
    public int mySqrt(int x) {
        if(x == 0){
            return x;
        }

        int ans = 1;
        while(ans <= x  / ans){
            ans++;
        }

        return ans - 1;
    }
}
```

### 方法二：牛顿迭代法

下面这种方法可以很有效地求出根号 aa 的近似值：首先随便猜一个近似值 xx，然后不断令 xx 等于 xx 和 a/xa/x 的平均数，迭代个六七次后 xx 的值就已经相当精确了。

例如，我想求根号 22 等于多少。假如我猜测的结果为 44，虽然错的离谱，但你可以看到使用牛顿迭代法后这个值很快就趋近于根号 22 了。

```
示例：
( 4 + 2/ 4 ) / 2 = 2.25

( 2.25 + 2/ 2.25 ) / 2 = 1.56944..

( 1.56944..+ 2/1.56944..) / 2 = 1.42189..

( 1.42189..+ 2/1.42189..) / 2 = 1.41423..

```



```java
class Solution {
    int s;

    public int mySqrt(int x) {
        s = x;
        if(x == 0){
            return 0;
        }

        return ((int)(sqrts(x)));
    }

    private double sqrts(double x){
        double ret = (x + s / x) / 2;

        if(ret == x){
            return x;
        }else {
            return sqrts(ret);
        }
    }
}
```


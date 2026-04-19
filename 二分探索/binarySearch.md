## 目次
- [二分探索](#二分探索)
  - [基本実装](#基本実装)
  - [標準ライブラリ](#標準ライブラリ)


## 二分探索
Javaでの二分探索（binary search）は、「ソート済み配列に対して高速に値を探すアルゴリズム」である。<br>
計算量は O(log N) で非常に高速に処理できる。

<img src="https://github.com/user-attachments/assets/de76c25a-15c5-4c03-b475-7e200360ab62.jpg" width="30%">

### 基本実装
```Java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        // 入力：ソート済みの配列
        int[] arr = {1, 3, 5, 7, 9, 11, 13};
        
        // 二分探索
        // 例：5を探す
        int index = binarySearch(arr, 5);

        // 出力
        System.out.println(index); // → 2
    }

    // 二分探索の実装
    public static int binarySearch(int[] arr, int target) {
        int left = 0;
        int right = arr.length - 1;

        while (left <= right) {
            // 中央のインデックス（配列の中央）を計算
            int mid = (left + right) / 2;

            if (arr[mid] == target) {   
                // 中央値がターゲットと一致した場合
                // インデックスを返す
                return mid;
            } else if (arr[mid] < target) {
                // 中央値がターゲットより小さい場合
                // ターゲットは中央より右側にあるので、探索範囲を右へ移動
                // 左端を中央の1つ右の位置に更新
                left = mid + 1;
            } else {
                // 中央値がターゲットより大きい場合
                // ターゲットは中央より左側にあるので、探索範囲を左へ移動
                // 右端を中央の1つ左の位置に更新
                right = mid - 1;
            }
        }

        return -1; // 見つからない
    }
}
```

### 標準ライブラリ
```Java
import java.util.*;
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        // 入力：ソート済みの配列
        int[] arr = {1, 3, 5, 7, 9, 11, 13};

        // 二分探索
        // 例：5を探す
        int index = Arrays.binarySearch(arr, 5);

        // 出力
        System.out.println(index); // → 2
    }
}
```

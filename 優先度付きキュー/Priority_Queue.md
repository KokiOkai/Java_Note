## 目次
- [優先度付きキュー](#優先度付きキュー)
  - [長さの取得](#長さの取得)
  - [要素の追加](#要素の追加)
  - [最も優先度が高い値の取得](#最も優先度が高い値の取得)
  - [最も優先度が高い値の削除](#最も優先度が高い値の削除)
  - [要素の全削除](#要素の全削除)
  - [要素が空かどうか確認](#要素が空かどうか確認)
  - [計算量](#計算量)
- [コード例](#コード例)
  - [要素の出力](#要素の出力) 

 
## 優先度付きキュー
優先度付きキュー（PriorityQueue）は、要素が追加された順序ではなく、要素の順位づけに基づいて順序が決定される特殊なキューである。<br>
「キュー」の一種ではあるが、「先入れ先出し」の原則は無視される。<br>
PriorityQueue クラスを宣言するときには、何を優先させるかを決めることができる。<br>

- 最小値を優先する場合
```Java
PriorityQueue<Integer> pq = new PriorityQueue<>();
```

- 最大値を優先する場合
```Java
PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());
```

- 文字列を辞書順に優先する場合
```Java
PriorityQueue<String> pq = new PriorityQueue<>();
```

典型用途としては以下のような場合である。
- 最小値 / 最大値を何度も取りたい
- 「今いちばん条件が良いもの」を取り出す
- イベントを時刻順で処理
- スケジューリング
- 上位K件の管理
- Dijkstra法

### 要素の追加
PriorityQueue クラスで用意されている add メソッド または offer メソッドを使用する。<br>
両者どちらを使っても、特に違いはない。

```Java
pq.add();
pq.offer();
```

### 長さの取得
PriorityQueue クラスで用意されている size メソッドを使用する。

```Java
pq.size();
```

### 最も優先度が高い値の取得
PriorityQueue クラスで用意されている peek メソッドを使用する。

```Java
pq.peek();
```

### 最も優先度が高い値の削除
PriorityQueue クラスで用意されている poll メソッドを使用する。

```Java
pq.poll();
```

### 要素の全削除
PriorityQueue クラスで用意されている clear メソッドを使用する。

```Java
pq.clear();
```

### 要素が空かどうか確認
PriorityQueue クラスで用意されている isEmpty メソッドを使用する。<br>
要素が存在しない場合は「true」、存在する場合は「false」を返す。

```Java
pq.isEmpty();
```

### 計算量
| 操作 | 計算量 |
| :--- | :--- |
| add() / offer() | O(log N) |
| poll() | O(log N) |
| peek() | O(1) |
| size() | O(1) |
| contains() | O(N) |
| remove(インデックス または 削除する要素) | O(N) |


## コード例
### 要素の出力
```Java
import java.util.PriorityQueue;

public class Main {
    public static void main(String[] args) {

        // 優先度付きキューを作成
        PriorityQueue<Integer> pq = new PriorityQueue<>();

        // 優先度付きキューに要素を追加
        pq.add(8);
        pq.add(2);
        pq.add(5);
        pq.add(1);

        // 中身確認
        System.out.println(pq); 

        // 出力
        while (!pq.isEmpty()) {
            System.out.println(pq.poll());
        }
    }
}

/*
出力結果
[8, 2, 5, 1] ← 中身がソートされているわけではない
1
2
5
8
*/
```



## 目次
- [Map](#Map)
  - [インターフェースとクラス](#インターフェースとクラス)
- [HashMap](#HashMap)
- [TreeMap](#TreeMap)


## Map
### インターフェースとクラス
Map は「キー」と「値」を対応付けて保存するデータ構造 を指す。<br>
Map は「インターフェース（interface）」として定義されている。<br>
そのため、プログラム中では Map を直接使うのではなく、Map を実装した「クラス（class）」を用いる。<br>

```
Map
 ├─ HashMap
 ├─ TreeMap
 └─ LinkedHashMap
```

| クラス | 計算量 | 順序 |
| :--- | :--- | :--- |
| HashMap | O(1) | なし |
| LinkedHashMap | O(1) | 挿入順 |
| TreeMap | O(logN) | 昇順 |

Map を使うときは次のように宣言する。<br>
LinkedHashMap は少なくとも競技プログラミングでは使用することはない。<br>

```Java
Map<キーのデータ型, 値のデータ型> 変数名 = new HashMap<>();
Map<キーのデータ型, 値のデータ型> 変数名 = new TreeMap<>();
```


### HashMap







### TreeMap


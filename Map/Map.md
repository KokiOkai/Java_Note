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

Map は次のように宣言する。<br>
宣言するときにはキーと値のデータ型を指定する必要がある。<br>

```Java
Map<キーのデータ型, 値のデータ型> 変数名 = new HashMap<>();
Map<キーのデータ型, 値のデータ型> 変数名 = new LinkedHashMap<>();
Map<キーのデータ型, 値のデータ型> 変数名 = new TreeMap<>();
```


## HashMap
### キーと値のペアの追加
HashMap クラスで用意されている put メソッドを使用する。<br>

```Java
Map<String,Integer> map = new HashMap<>();

map.put("りんご", 80);
map.put("ぶどう", 120);
```

また、すでに追加されているキーに対して put メソッドを使用した場合は、新たに値が更新される。<br>

```Java
Map<String,Integer> map = new HashMap<>();

map.put("りんご", 80);
System.out.println(map.get("りんご"));   // 80

map.put("りんご", 100);
System.out.println(map.get("りんご"));   // 100
```


### 指定したキーの値の取得
HashMap クラスで用意されている get メソッドを使用する。<br>

```Java
Map<String,Integer> map = new HashMap<>();

map.put("りんご", 80);
System.out.println(map.get("りんご"));   // 80
```


### キーと値のペア数の取得
HashMap クラスで用意されている get メソッドを使用する。<br>

```Java
Map<String,Integer> map = new HashMap<>();

map.put("りんご", 80);
map.put("ぶどう", 120);

int n = map.size();
System.out.println(n);   // 2
```


## TreeMap


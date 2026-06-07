## 目次
- [文字列](#文字列)
  - [文字列の等号](#文字列の等号)
  - [長さの取得](#長さの取得)
  - [長さの比較](#長さの比較)
  - [指定した文字列が最初に出現するインデックスの取得](#指定した文字列が最初に出現するインデックスの取得)
  - [指定した文字列が最後に出現するインデックスの取得](#指定した文字列が最後に出現するインデックスの取得)
  - [指定したインデックスの文字の取得](#指定したインデックスの文字の取得)
  - [指定した範囲の文字の取得](#指定した範囲の文字の取得)
  - [文字列を大文字にする](#文字列を大文字にする)
  - [文字列を小文字にする](#文字列を小文字にする)
  - [文字列を反転させる](#文字列を反転させる)
  - [文字列の回文判定](#文字列の回文判定)
  - [文字列の連結](#文字列の連結)
  - [複数の文字列を区切り文字で連結](#複数の文字列を区切り文字で連結)
  - [文字列の置換](#文字列の置換)
  - [文字列の先頭と末尾から空白文字を取り除く](#文字列の先頭と末尾から空白文字を取り除く)
 

## 文字列
### 文字列の等号
Java で文字列は参照型のため、同じ文字列を参照しているか比較するには == 演算子を使い、<br>
同じ値を持っているかどうか比較するには String クラスの equals メソッドを使用する。

```Java
// 文字列の宣言
String hello = "Hello";
String str_01 = hello;               // 同じオブジェクト
String str_02 = new String(hello);   // 異なるオブジェクト

// 出力
System.out.println(hello == str_01);        // true
System.out.println(hello == str_02);        // false
System.out.println(hello.equals(str_02));   // true
```


### 長さの取得
String クラスで用意されている length メソッドを使用する。<br>

```Java
String s = "abcde";
int n = s.length();   // 5
```


### 長さの比較
String クラスで用意されている compareTo メソッドを使用する。<br>
文字列の長さが同じ場合は「0」、異なる場合はその差の値を返す。<br>

```Java
String str1 = "AAAAAAAA";
String str2 = "AAAAAAAA";
String str3 = "AAA";
String str4 = "ABCD";

System.out.println(str1.compareTo(str2));   // 0
System.out.println(str1.compareTo(str3));   // 5
System.out.println(str1.compareTo(str4));   // -1
```


### 指定した文字列が最初に出現するインデックスの取得
String クラスで用意されている indexOf メソッドを使用する。<br>
第一引数に検索したい文字列を指定する。<br>
先頭の文字から順に検索し最初に出現したインデックス（部分文字列の最初の文字のインデックス）を戻り値として返す。<br>

```Java
String str = "東京都と京都府";
// ０１２３４５６
// 東京都と京都府

System.out.println(str.indexOf("京都"));   // 1
```

第二引数にインデックスを指定すると、その位置から末尾に向かって順に検索し最初に出現したインデックスを戻り値として返す。<br>
また、検索対象の文字列が見つからなかった場合は「-1」を返す。<br>

```Java
String str = "東京都と京都府";
// ０１２３４５６
// 東京都と京都府

System.out.println(str.indexOf("京都"), 2);   // 4
```


### 指定した文字列が最後に出現するインデックスの取得
String クラスで用意されている lastIndexOf メソッドを使用する。<br>
第一引数に検索したい文字列を指定する。<br>
末尾の文字から順に検索し最初に出現したインデックス（部分文字列の最初の文字のインデックス）を戻り値として返す。<br>

```Java
String str = "東京都と京都府";
// ０１２３４５６
// 東京都と京都府

System.out.println(str.lastIndexOf("京都"));   // 4
```

第二引数にインデックスを指定すると、その位置から末尾に向かって順に検索し最初に出現したインデックスを戻り値として返す。<br>
また、検索対象の文字列が見つからなかった場合は「-1」を返す。<br>

```Java
String str = "東京都と京都府";
// ０１２３４５６
// 東京都と京都府

System.out.println(str.lastIndexOf("京都"), 3);   // 1
```


### 指定したインデックスの文字の取得
String クラスで用意されている charAt メソッドを使用する。<br>

```Java
String str = "ABCDEFG";
// 0123456
// ABCDEFG

System.out.println(str.charAt(0));   // A
System.out.println(str.charAt(3));   // D
```


### 指定した範囲の文字の取得
String クラスで用意されている substring メソッドを使用する。<br>
開始インデックスと終了インデックスを指定して、文字列の中の部分文字列を取得する。<br>

```Java
String str = "ABCDEFG";
// 0123456
// ABCDEFG

System.out.println(msg.substring(3, 5));   // DE
System.out.println(msg.substring(5, 7));   // FG
```


### 文字列を大文字にする
String クラスで用意されている toUpperCase メソッドを使用する。<br>

```Java
String str = "Apple";

System.out.println(str.toUpperCase());   // APPLE
```


### 文字列を小文字にする
String クラスで用意されている toLowerCase メソッドを使用する。<br>

```Java
String str = "Apple";

System.out.println(str.toLowerCase());   // apple
```


### 文字列を反転させる
StringBuilder クラスで用意されている reverse メソッドを使用する。<br>

```Java
String s = "ABC";
String rev = new StringBuilder(s).reverse().toString();

System.out.println(rev);   // CBA
```

### 文字列の回文判定
元の文字列と反転させた文字列を比較することで、回文判定ができる。<br>

```Java
String s = "ABCBA";
String rev = new StringBuilder(s).reverse().toString();

if (s.equals(rev)) {
    System.out.println("Yes");
} else {
    System.out.println("No");
}
```


### 文字列の連結
＋演算子を使用する、または String クラスで用意されている concat メソッドを使用する。<br>

```Java
String str1 = "東京都";
String str2 = "港区";

System.out.println(str1 + str2);         // 東京都港区
System.out.println(str1.concat(str2));   // 東京都港区
```


### 複数の文字列を区切り文字で連結
String クラスで用意されている join メソッドを使用する。<br>
第一引数に文字列の間に挟む区切り文字を指定する。<br>
第二引数以降に連結する文字列を必要なだけ指定する。<br>
戻り値として連結した新しい文字列を返す。<br>

```Java
String str = String.join("-", "Apple", "Grape", "Melon");

System.out.println(str);   // Apple-Grape-Melon
```

区切り文字は文字列としても指定できる。<br>
List クラスで複数の文字列を格納し、第二引数に指定することもできる。<br>

```Java
import java.util.List;

List<String> strings = List.of("One", "Two", "Three");
String str = String.join(" * ", strings);

System.out.println(str);   // One * Two * Three
```


### 文字列の置換
String クラスで用意されている replace メソッドを使用する。<br>
第一引数で指定した文字列を、第二引数で指定した文字列に置換する。<br>

```Java
String str1 = "Herro Java";
String str2 = "東京都港区";

System.out.println(str1.replace('r', 'l'));          // Hello Java
System.out.println(str2.replace("港区", "中央区"));   // 東京都中央区
```


### 文字列の先頭と末尾から空白文字を取り除く
String クラスで用意されている trim メソッドを使用する。<br>
また、strip メソッドでも同様の使い方ができる。<br>
両者の違いは、trim メソッドが半角空白だけを取り除くのに対し、strip メソッドは全角空白も含めて取り除く。<br>

```Java
String str1 = " ABCD ";
String str2 = " AB CD ";

System.out.println(str1.trim());   // ABCD
System.out.println(str2.trim());   // AB CD
```


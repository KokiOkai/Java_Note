## 目次
- [文字列](#文字列)
  - [文字列の等号](#文字列の等号)
  - [長さの取得](#長さの取得)
  - [長さの比較](#長さの比較)
  - [指定した文字のインデックスの取得](#指定した文字のインデックスの取得)
 

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


### 指定した文字のインデックスの取得
String クラスで用意されている charAt メソッドを使用する。<br>

```Java
String str = "ABCDEFG";

System.out.println(str.charAt(0));   // A
System.out.println(str.charAt(3));   // D
```





# Java_Note
Javaコーディング用のメモ


## 目次
- [変数変換](#変数変換)
  - [文字列から数値に変換](#文字列から数値に変換)
  - [数値から文字列に変換](#数値から文字列に変換)
- [演算](#演算)
  - [演算時の型変換](#演算時の型変換)
    - [自動変換のルール](#自動変換のルール)
    - [型を一致させる方法](#型を一致させる方法)
  - [文字列の等号](#文字列の等号)
  - [数字の切り上げ](#数字の切り上げ)
  - [数字の切り捨て](#数字の切り捨て)
  - [数字の四捨五入](#数字の四捨五入)
- [配列](#配列)
  - [文字列を1文字ずつ取り出す](#文字列を1文字ずつ取り出す)
  - [重複](#重複)
- [リスト](#リスト)


## 変数変換
### 文字列から数値に変換
| 変換前の型 | 変換後の型 | メソッド | 値 |
| :--- | :--- | :--- | :--- |
| String | short | Short.parseShort | 16ビット整数 -32,768～32,767 |
| String | int | Integer.parseInt | 32ビット整数 -2,147,483,648 ～ 2,147,483,647 |
| String | long | Long.parseLong | 64ビット整数 -9,223,372,036,854,775,808 ～ 9,223,372,036,854,775,807 |
| String | float | Float.parseFloat | 32ビット単精度浮動小数点数 |
| String | double | Double.parseDouble | 64ビット倍精度浮動小数点数 |

```Java
// 文字列の宣言
String str_s = "1";
String str_i = "11";
String str_l = "111";
String str_f = "0.1";
String str_d = "0.11";

// 文字列から数値に変換
short s = Short.parseShort(str_s);
int i = Integer.parseInt(str_i);
long l = Long.parseLong(str_l);
float f = Float.parseFloat(str_f);
double d = Double.parseDouble(str_d);
```

### 数値から文字列に変換
| 変換前の型 | 変換後の型 | メソッド |
| :--- | :--- | :--- |
| 整数値型（short, int, long） | String | String.valueOf |
| 小数点数型（float, double） | String | String.valueOf |

```Java
// 整数値の宣言
int m = 1;
// 小数点数の宣言
double n = 0.1;

// 数値から文字列に変換
String str_m = String.valueOf(m);
String str_n = String.valueOf(n);
```


## 演算
### 演算時の型変換
#### 自動変換のルール
1. どちらかの値が double 型の場合は、他の値を double 型に変換する
2. どちらかの値が float 型の場合は、他の値を float 型に変換する
3. どちらかの値が long 型の場合は、他の値を long 型に変換する
4. 上記のいずれにも該当しない場合は、両方の値を int 型に変換する

このルールは(1)から順に適用され、いずれかに適用されればそれ以降の変換は行われない。

#### 型を一致させる方法
```Java
// 演算例
double d = 10 * 0.2;       // d = 2.0
int i = (int)(10 * 0.2);   // i = 2

// 演算のエラー例
int error = 10 * 0.2;
```

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

### 数字の切り上げ
Math クラスで用意されている ceil メソッドを使用する。
```Java
System.out.println(Math.ceil(1.34));    // 2.0
System.out.println(Math.ceil(3.67));    // 4.0
System.out.println(Math.ceil(8.0));     // 8.0
System.out.println(Math.ceil(-0.23));   // -0.0
System.out.println(Math.ceil(-3.89));   // -3.0
```

### 数字の切り捨て
Math クラスで用意されている floor メソッドを使用する。
```Java
System.out.println(Math.floor(1.34));    // 1.0
System.out.println(Math.floor(3.67));    // 3.0
System.out.println(Math.floor(8.0));     // 8.0
System.out.println(Math.floor(-0.23));   // -1.0
System.out.println(Math.floor(-3.89));   // -4.0
```

### 数字の四捨五入
Math クラスで用意されている round メソッドを使用する。
```Java
System.out.println(Math.round(1.34));    // 1
System.out.println(Math.round(3.67));    // 4
System.out.println(Math.round(4.499));   // 4
System.out.println(Math.round(4.5));     // 5
System.out.println(Math.round(-0.23));   // 0
System.out.println(Math.round(-3.89));   // -4
```


## 配列
### 文字列を1文字ずつ取り出す

### 重複


## リスト

# Java_Note
Javaコーディング用のメモ


## 目次
- [変数変換](#変数変換)
  - [文字列から数値に変換](#文字列から数値に変換)
- [演算](#演算)
  - [演算時の型変換](#演算時の型変換)
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
| 変換前の型 | 変換後の型 | メソッド |
| :--- | :--- | :--- |
| String | short | Short.parseShort |
| String | int | Integer.parseInt |
| String | long | Long.parseLong |
| String | double | Double.parseDouble |

```Java
String str_s = "1";
String str_i = "11";
String str_l = "111";
String str_d = "0.1";

// 変換
short s = Short.parseShort(str_s);
int i = Integer.parseInt(str_i);
long l = Long.parseLong(str_l);
double d = Double.parseDouble(str_d);
```


## 演算
### 演算時の型変換

### 文字列の等号

### 数字の切り上げ

### 数字の切り捨て

### 数字の四捨五入


## 配列
### 文字列を1文字ずつ取り出す

### 重複


## リスト

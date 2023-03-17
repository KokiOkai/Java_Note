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
  - [文字列を分割する](#文字列を分割する) 
  - [文字列を1文字ずつ取り出す](#文字列を1文字ずつ取り出す)
  - [重複](#重複)
- [リスト](#リスト)
  - [要素の追加](#要素の追加)
  - [要素の削除](#要素の削除)
    - [1つの要素を削除する](#1つの要素を削除する) 
    - [複数の要素を削除する（重複している要素の削除）](#複数の要素を削除する重複している要素の削除)
    - [重複していない要素を削除する](#重複していない要素を削除する)
    - [条件付きで要素を削除する](#条件付きで要素を削除する)
- [Atcoder](#Atcoder)
  - [標準入力](#標準入力)


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

このルールは上から順に適用され、いずれかに適用されればそれ以降の変換は行われない。

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
### 文字列を分割する
String クラスで用意されている split メソッドを使用する。<br>
第一引数にマッチした位置で文字列を分割し、分割した結果を文字列配列として返す。<br>
デフォルトではすべての区切り文字位置で分割するが、第二引数を指定した場合には、その値を上限に分割します。<br>
分割されなかった文字列は、最後の文字列にすべて含まれることになる。

第二引数を指定しない場合（第二引数に 0 を指定したときも同様）
```Java
// 文字列の宣言
String str = "あ,い,う,え,お,,";

// 文字列を分割して配列に格納
String[] splited = str.split(",");

/*
配列イメージ
[0]あ
[1]い
[2]う
[3]え
[4]お
*/
```

第二引数に 1 を指定した場合（分割されないので意味なし）
```Java
// 文字列の宣言
String str = "あ,い,う,え,お,,";

// 文字列を分割して配列に格納
String[] splited = str.split(",", 1);

/*
配列イメージ
[0]あ,い,う,え,お,,
*/
```

第二引数に 2 を指定した場合
```Java
// 文字列の宣言
String str = "あ,い,う,え,お,,";

// 文字列を分割して配列に格納
String[] splited = str.split(",", 2);

/*
配列イメージ
[0]あ
[1]い,う,え,お,,
*/
```

第二引数に 3 を指定した場合
```Java
// 文字列の宣言
String str = "あ,い,う,え,お,,";

// 文字列を分割して配列に格納
String[] splited = str.split(",", 3);

/*
配列イメージ
[0]あ
[1]い
[2]う,え,お,,
*/
```

### 文字列を1文字ずつ取り出す
String クラスで用意されている split メソッドを使用する。

```Java
// 文字列の宣言
String str = "あいうえお";

// 文字列を分割して配列に格納
String[] splited = str.split("");

/*
配列イメージ
[0]あ
[1]い
[2]う
[3]え
[4]お
*/
```

### 重複
Set クラスで用意されている HashSet メソッドを使用する。<br>
Set クラスは、List クラスと同じように大きさを決めない配列のようなものである。<br>
List クラスは同じ値を持つことができますが、Set クラスは同じ値を持つことはできない。<br>
この特徴を活かして、重複を確認する。

```Java
import java.util.HashSet;
import java.util.Set;

public class Main {
    public static void main(String[] args) throws Exception {

        // 整列型配列の宣言
        int num[] = {1, 2, 3, 4, 5, 6, 1, 7, 8, 9, 1, 6};
        
        // 重複確認用のセットを作成
        Set<Integer> set = new HashSet<Integer>();
        
        for(int duplicateCheck : num) {
            // setに追加してみて、追加できなかった（重複していた）場合
            if(!set.add(duplicateCheck)) {
                System.out.println(duplicateCheck + "が重複しています。");
            }
        }
    }
}

/*
出力結果
1が重複しています。
1が重複しています。
6が重複しています。
*/
```


## リスト
### 要素の追加
List クラスで用意されている add メソッドを使用する。<br>
1つの値をリストの要素としてに追加するメソッドである。<br>
第一引数をインデックス、第二引数を追加する値として指定することで、リストに要素を追加する。

```Java
list.add(インデックス, 追加する要素);
```

リストの最後に要素を追加する場合（第一引数を指定しない場合）
```Java
import java.util.ArrayList; 
import java.util.List;
 
public class Main {
    public static void main(String[] args) throws Exception {
        
       // 文字列型リストを作成
       List<String> listA = new ArrayList<String>(); 
       
       // リストの最後に要素を追加 
       listA.add("あいうえお"); 
       listA.add("かきくけこ");
       listA.add("さしすせそ");
       System.out.println("要素追加後A:" + listA);   // 要素追加後A: [あいうえお, かきくけこ, さしすせそ]
       
       
       // 整数型リストを作成 
       List<Integer> listB = new ArrayList<Integer>(); 
       
       // リストの最後に要素を追加 
       listB.add(1); 
       listB.add(2);
       listB.add(3);
       System.out.println("要素追加後B:" + listB);   // 要素追加後B: [1, 2, 3]
    }
}
```

インデックスを指定してリストに要素を追加する場合
```Java
import java.util.ArrayList; 
import java.util.List;

public class Main {
    public static void main(String[] args) throws Exception {
        
       // 文字列型リストを作成 
       List<String> listA = new ArrayList<String>(); 
       
       // リストの最後に要素を追加 
       listA.add("あいうえお"); 
       listA.add("かきくけこ");
       listA.add("さしすせそ");
       System.out.println("要素追加後A:" + listA);   // 要素追加後A: [あいうえお, かきくけこ, さしすせそ]
          
       // インデックスを指定して要素を追加 
       listA.add(1, "わをん"); 
       System.out.println("要素追加後A:" + listA);   // 要素追加後A: [あいうえお, わをん, かきくけこ, さしすせそ]
    }
}
```

### 要素の削除
#### 1つの要素を削除する
List クラスで用意されている remove メソッドを使用する。<br>
引数としてインデックス、削除する要素（文字列など）を指定することで、リストから指定した要素を削除する。<br>
削除された要素の後に格納されていた要素は、インデックス番号が1つずつずれる。

```Java
List.remove(インデックス または 削除する要素);
```

インデックスを指定した場合
```Java
import java.util.ArrayList;
import java.util.List;
 
public class Main {
    public static void main(String[] args) throws Exception {
           
        // 文字列型リストを作成
        List<String> list = new ArrayList<String>();
        
        // リストに要素を追加 
        list.add("あいうえお"); 
        list.add("かきくけこ"); 
        list.add("さしすせそ");
        
        System.out.println("削除前:" + list);          // 削除前: [あいうえお, かきくけこ, さしすせそ]
        System.out.println("要素数:" + list.size());   // 要素数: 3
        
        // インデックス指定での要素の削除 
        list.remove(1);
        
        System.out.println("削除後:" + list);          // 削除後: [あいうえお, さしすせそ]
        System.out.println("要素数:" + list.size());   // 要素数: 2
    }
}
```

削除する要素（文字列など）を指定した場合
```Java
import java.util.ArrayList;
import java.util.List;
 
public class Main {
    public static void main(String[] args) throws Exception {
         
        // 文字列型リストを作成
        List<String> list = new ArrayList<String>();
        
        // リストに要素を追加 
        list.add("あいうえお"); 
        list.add("かきくけこ"); 
        list.add("さしすせそ");
        list.add("あいうえお");
        
        System.out.println("削除前:" + list);          // 削除前: [あいうえお, かきくけこ, さしすせそ, あいうえお]
        System.out.println("要素数:" + list.size());   // 要素数: 4
        
        // インスタンス指定での要素の削除 
        list.remove("あいうえお");
        
        System.out.println("削除後:" + list);          // 削除後: [かきくけこ, さしすせそ, あいうえお]
        System.out.println("要素数:" + list.size());   // 要素数: 3
    }
}
```
指定したインスタンスが複数ある場合は、最初の1つ目の要素が削除されるが、2つ目の要素は削除されない。

#### 複数の要素を削除する（重複している要素の削除）
List クラスで用意されている removeAll メソッドを使用する。<br>
List 型に指定した要素をすべて削除するためのメソッドである。

```Java
listA.removeAll(listB);
```
removeAll の引数で、削除したい要素が入ったリスト（listB）指定することで、listA と重複している要素を削除することができる。

```Java
import java.util.ArrayList;
import java.util.List;
 
public class Main {
    public static void main(String[] args) throws Exception {
        
        // 文字列型リストを作成
        List<String> listA = new ArrayList<String>();
        
        // リストに要素を追加 
        listA.add("あいうえお"); 
        listA.add("かきくけこ"); 
        listA.add("さしすせそ");
        listA.add("かきくけこ");
        listA.add("さしすせそ");
        
        // 削除したい要素を格納する文字列型リストを作成
        List<String> listB = new ArrayList<String>();
        
        // リストに削除したい要素を追加
        listB.add("かきくけこ"); 
        listB.add("がぎぐげご"); 
        listB.add("さしすせそ"); 
        listB.add("ざじずぜぞ");
        
        System.out.println("削除前:" + listA);            // 削除前: [あいうえお, かきくけこ, さしすせそ, かきくけこ, さしすせそ]
        System.out.println("削除したいリスト:" + listB);   // 削除したいリスト: [かきくけこ, がぎぐげご, さしすせそ, ざじずぜぞ]
        
        // listA の要素のうち listB にもあるものを削除 
        listA.removeAll(listB);
        
        System.out.println("削除後:" + listA);   // 削除後: [あいうえお]
    }
}
```

#### 重複していない要素を削除する
List クラスで用意されている retainAll メソッドを使用する。<br>
List 型に指定した以外の要素をすべて削除するためのメソッドである。

```Java
listA.retainAll(listB);
```

retainAll の引数で、削除対象外の要素が入ったリスト（ListB）を指定することで、ListA と重複していない要素を削除することができる。<br>
retainAll メソッドは「A」と「a」のように、大文字と小文字の同じ意味である場合も重複していないと判断して削除する。

```Java
import java.util.ArrayList;
import java.util.List;
 
public class Main {
    public static void main(String[] args) throws Exception {
        
        // 文字列型リストを作成
        List<String> listA = new ArrayList<String>();
        
        // リストに要素を追加 
        listA.add("あいうえお"); 
        listA.add("かきくけこ"); 
        listA.add("さしすせそ");
        listA.add("たちつてと");
        
        // 削除対象外の要素を格納する文字列型リストを作成
        List<String> listB = new ArrayList<String>();
        
        // リストに要素を追加
        listB.add("かきくけこ"); 
        listB.add("がぎぐげご"); 
        listB.add("さしすせそ"); 
        listB.add("ざじずぜぞ");
        
        System.out.println("削除前:" + listA);              // 削除前: [あいうえお, かきくけこ, さしすせそ, たちつてと]
        System.out.println("削除対象外のリスト:" + listB);   // 削除対象外のリスト: [かきくけこ, がぎぐげご, さしすせそ, ざじずぜぞ]
        
        // listA の要素のうち listB にないものを削除 
        listA.retainAll(listB);
        
        System.out.println("削除後:" + listA);   // 削除後: [かきくけこ, さしすせそ]
    }
}
```

#### 条件付きで要素を削除する
List クラスで用意されている removeIf メソッドを使用する。<br>
ラムダ式で記述した、引数として渡された条件でリストの要素を削除する。

```Java
import java.util.ArrayList;
import java.util.List;
 
public class Main {
    public static void main(String[] args) throws Exception {
           
        // 文字列型リストを作成
        List<String> list = new ArrayList<String>();
        
        // リストに要素を追加 
        list.add("あいうえお"); 
        list.add("かきくけこ"); 
        list.add("さしすせそ");
        
        System.out.println("削除前:" + list);   // 削除前: [あいうえお, かきくけこ, さしすせそ]
        
        // 条件付きでの要素の削除 
        list.removeIf(element -> element.startsWith("か"));
        
        System.out.println("削除後:" + list);   // 削除後: [あいうえお, さしすせそ]
    }
}
```


## Atcoder
### 標準入力
<img src="https://user-images.githubusercontent.com/105481222/225970260-4a00590d-91f0-4bdd-b362-7bc59e3f8e81.jpg" width="30%">
<img src="https://user-images.githubusercontent.com/105481222/225971011-baca69fc-a3cf-4ce9-823a-dce1d1a23259.jpg" width="30%">

```Java
import java.util.*;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) throws Exception {
        Scanner scan = new Scanner(System.in);
        
        // 入力
        int H = scan.nextInt();
        int W = scan.nextInt();
        int[][] array = new int[H][W];
        for (int i = 0; i < H; i++) {
            for (int j = 0; j < W; j++) {
                array[i][j] = scan.nextInt();
            } 
        }
    }
}
```

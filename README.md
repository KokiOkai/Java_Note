# Java_Note
Javaコーディング用のメモ


## 目次
- [変数変換](#変数変換)
  - [文字列から数値に変換](#文字列から数値に変換)
  - [数値から文字列に変換](#数値から文字列に変換)
  - [10進数をn進数表記にする](#10進数をn進数表記にする)
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
  - [長さの取得](#長さの取得)
  - [要素の取得](#要素の取得)
  - [要素の追加](#要素の追加)
  - [要素の置換](#要素の置換)
    - [指定した1つの要素を置換する](#指定した1つの要素を置換する) 
    - [すべての要素を任意の文字列に置換する](#すべての要素を任意の文字列に置換する)
    - [特定の要素を任意の文字列に置換する](#特定の要素を任意の文字列に置換する)
  - [要素の削除](#要素の削除)
    - [指定した1つの要素を削除する](#指定した1つの要素を削除する) 
    - [指定した複数の要素を削除する](#指定した複数の要素を削除する)
    - [指定した要素以外を削除する](#指定した要素以外を削除する)
    - [重複している要素を削除する](#重複している要素を削除する)
    - [条件付きで要素を削除する](#条件付きで要素を削除する)
  - [要素の検索](#要素の検索)
- [Atcoder](#Atcoder)
  - [標準入力例（数字）](#標準入力例数字)
  - [標準入力例（文字列）](#標準入力例文字列)
  - [標準入力例（二次元配列）](#標準入力例二次元配列)
  - [アルファベットの文字列リスト](#アルファベットの文字列リスト)
- [Track](#Track)
  - [標準入力例](#標準入力例)
  - [標準入力の取得](#標準入力の取得)


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

### 10進数をn進数表記にする
| 説明 | 戻り値の型 | メソッド |
| :--- | :--- | :--- |
| 数値 i を2進数表記の文字列で返す | String | Integer.toBinaryString(i) |
| 数値 i を8進数表記の文字列で返す | String | Integer.toOctalString(i) |
| 数値 i を16進数表記の文字列で返す | String | Integer.toHexString(i) |

```Java
// 入力
int i = 127;

// int値をn進数表記に変換する
System.out.println("10進数：" + i);
System.out.println("2進数：" + Integer.toBinaryString(i));
System.out.println("8進数：" + Integer.toOctalString(i));
System.out.println("16進数：" + Integer.toHexString(i));

/*
出力結果
10進数：127
2進数：1111111
8進数：177
16進数：7f
*/
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
### 長さの取得
List クラスで用意されている size メソッドを使用する。<br>

```Java
list.size();
```

### 要素の取得
List クラスで用意されている get メソッドを使用する。<br>

```Java
list.get(インデックス);
```

### 要素の追加
List クラスで用意されている add メソッドを使用する。<br>
1つの値をリストの要素として追加するメソッドである。<br>
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

### 要素の置換
#### 指定した1つの要素を置換する
List クラスで用意されている set メソッドを使用する。<br>
リストに追加されている要素の中で、指定したインデックスの要素を別の要素に置き換えるメソッドである。<br>
第一引数をインデックス、第二引数を新たに格納する値として指定することで、リストから指定した要素を置換する。

```Java
list.set(インデックス, 新たに格納する要素);
```

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
       
       
       // リストの最後に要素を追加 
       listA.set(0, "わ"); 
       listA.set(1, "を");
       listA.set(2, "ん");
       System.out.println("要素置換後A:" + listA);   // 要素置換後A: [わ, を, ん]
    }
}
```

#### すべての要素を任意の文字列に置換する
String クラスで用意されている replaceAll メソッドを使用する。<br>
リストに追加されているすべての要素を、任意の文字列に置き換えるメソッドである。

```Java
list.replaceAll(引数 -> 処理);
```

```Java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args) throws Exception {

        // 文字列型リストを作成
        List<String> list = new ArrayList<>(Arrays.asList("A", "B", "C", "D"));
        System.out.println("要素置換前:" + list);   // 要素置換前: [A, B, C, D]

        // すべての要素に特定の文字列を追加して置換する
        list.replaceAll(s -> s + "++");
        System.out.println("要素置換後:" + list);   // 要素置換後: [A++, B++, C++, D++]

        // すべての要素を任意の文字列に置換する
        list.replaceAll(s -> "あ");
        System.out.println("要素置換後:" + list);   // 要素置換後: [あ, あ, あ, あ]
    }
}
```

#### 特定の要素を任意の文字列に置換する
String クラスで用意されている replaceAll メソッドを使用する。<br>
リストに追加されているすべての要素を、任意の文字列に置き換えるメソッドである。

```Java
list.replaceAll(引数 -> 処理);
```

処理の部分をラムダ式で記述することで、if文と同じ処理を行うこともできる。
| 記号 | 意味 |
| :--- | :--- |
| ? | ～ならば |
| : | ～でなければ |

```Java
// 引数をsとする
list.replaceAll(s -> s != null ? s : "");

// if文で表した場合
s -> {
    if (s != null) {
        return s;
    } else {
        return "";
    }
}
```

```Java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args) throws Exception {

        // 文字列型リストを作成
        List<String> list = new ArrayList<>(Arrays.asList("A", "B", "C", "D"));
        System.out.println("要素置換前:" + list);   // 要素置換前: [A, B, C, D]

        // すべての要素に特定の文字列を追加して置換する
        list.replaceAll(s -> s != "B" ? s : "あ");
        System.out.println("要素置換後:" + list);   // 要素置換後: [A, あ, C, D]
    }
}
```

### 要素の削除
#### 指定した1つの要素を削除する
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

#### 指定した複数の要素を削除する
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

#### 指定した要素以外を削除する
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

#### 重複している要素を削除する
Stream APIで用意されている distinct メソッドを使用する。<br>
リストの中で重複している要素をすべて削除するためのメソッドである。

```Java
list.stream().distinct().collect(Collectors.toList());
```

```Java
import java.util.ArrayList;
import java.util.List;
import java.util.stream.Collectors;
 
public class Main {
    public static void main(String[] args) throws Exception {
        
        // 文字列型リストを作成
        List<String> list = new ArrayList<String>();
        
        // リストに要素を追加 
        list.add("あいうえお"); 
        list.add("かきくけこ"); 
        list.add("さしすせそ");
        list.add("かきくけこ");

        System.out.println("削除前:" + listA);   // 削除前: [あいうえお, かきくけこ, さしすせそ, かきくけこ]
        listA = listA.stream().distinct().collect(Collectors.toList());
        System.out.println("削除後:" + listA);   // 削除後: [あいうえお, かきくけこ, さしすせそ]
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

### 要素の検索
List クラスで用意されている contains メソッドを使用する。<br>
リストに追加されている要素の中で、指定したオブジェクトが含まれるかを判定するメソッドである。<br>
リストの中に一致する要素が存在する場合は「true」、存在しない場合は「false」を返す。

```Java
list.contains(検索する要素);
```

List クラスで用意されている indexOf メソッドを使用する。<br>
リストに追加されている要素の中で、指定したオブジェクトが含まれる最初の要素を検索するメソッドである。<br>
リストの中に一致する要素が複数存在する場合は最初のインデックスを返す。
リストの中に一致する要素が存在しない場合は「-1」を返す。

```Java
list.indexOf(検索する要素);
```

List クラスで用意されている lastIndexOf メソッドを使用する。<br>
リストに追加されている要素の中で、指定したオブジェクトが含まれる最後の要素を検索するメソッドである。<br>
リストの中に一致する要素が複数存在する場合は最後のインデックスを返す。
リストの中に一致する要素が存在しない場合は「-1」を返す。

```Java
list.lastIndexOf(検索する要素);
```

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
        list.add("かきくけこ");

        System.out.println("最初から" + list.indexOf("かきくけこ") + "番目");                // 最初から1番目
        System.out.println("最後から" + list.lastIndexOf("かきくけこ") + "番目");            // 最後から3番目
        System.out.println("存在しないときは" + list.indexOf("たちつてと") + "を出力");       // 存在しないときは-1を出力
        System.out.println("存在しないときは" + list.lastIndexOf("たちつてと") + "を出力");   // 存在しないときは-1を出力
    }
}
```

## Atcoder
### 標準入力例（数字）
```Java
import java.util.*;
import java.util.Scanner;
import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void main(String[] args) throws Exception {
        Scanner scan = new Scanner(System.in);

        // 整数型リストを作成
        ArrayList<Integer> list_P = new ArrayList<Integer>();
        
        // 入力
        int N = scan.nextInt();
        for (int i = 0; i < N; i++) {
            list_P.add(scan.nextInt());
        }
    }
}
```

### 標準入力例（文字列）
<img src="https://github.com/user-attachments/assets/d08ec2a4-d2d5-4b30-8024-29e647de22c8" width="40%">
<br>
<img src="https://github.com/user-attachments/assets/bae73842-adbc-4082-855a-f9f706a7d0dc" width="10%">

```Java
import java.util.*;
import java.util.Scanner;
import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void main(String[] args) throws Exception {
        Scanner scan = new Scanner(System.in);
        
        // 入力
        int N = scan.nextInt();
        String S = scan.next();
        String T = scan.next();

        // 文字列型リストを作成
        ArrayList<String> list_S = new ArrayList<String>();
        ArrayList<String> list_T = new ArrayList<String>();

        // 文字列を一文字ずつリストに詰める
        for (int i = 1; i <= N; i++) {
            list_S.add(S.substring(i - 1, i));
            list_T.add(T.substring(i - 1, i));
        }
    }
}
```

### 標準入力例（二次元配列）
<img src="https://user-images.githubusercontent.com/105481222/225970260-4a00590d-91f0-4bdd-b362-7bc59e3f8e81.jpg" width="20%">
<img src="https://user-images.githubusercontent.com/105481222/225971011-baca69fc-a3cf-4ce9-823a-dce1d1a23259.jpg" width="10%">

```Java
import java.util.*;
import java.util.Scanner;
import java.util.ArrayList;
import java.util.List;

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

### アルファベットの文字列リスト
アルファベットは全部で26文字ある。<br>
リストの0番目を空にしているので、要素番号は1から順に対応している。

```Java
String[] array = {"","A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","Z"};
```


## Track
### 標準入力例
```Java
package track;
import java.util.Scanner;
import java.util.ArrayList;

public class App {
  public static void main(String[] args) {
    // このコードは標準入力と標準出力を用いたサンプルコードです。
    // このコードは好きなように編集・削除してもらって構いません。
    // ---
    // This is a sample code to use stdin and stdout.
    // Edit and remove this code as you like.
    
    String[] lines = getStdin();
    for (int i = 0, l = lines.length; i < l; i++) {
      String output = String.format("line[%s]: %s", i, lines[i]);
      System.out.println(output);
    }
  }
  
  private static String[] getStdin() {
    Scanner scanner = new Scanner(System.in);
    ArrayList<String> lines = new ArrayList<>();
    while (scanner.hasNext()) {
      lines.add(scanner.nextLine());
    }
    return lines.toArray(new String[lines.size()]);
  }
}
```

### 標準入力の取得
```Java
import java.util.*;
import java.util.Scanner;
import java.util.Arrays;

public class Main {
    public static void main(String[] args) throws Exception {
        Scanner scan = new Scanner(System.in);
        
        // 標準入力
        String[] lines = {"3", "3 1 5"};
        
        // 標準入力の取得
        int n = Integer.parseInt(lines[0]);
        // 文字列配列として取得
        String[] str = lines[1].split(" ");
        // 整数配列に変換
        int[] array = new int[n];
        for (int i = 0; i < n; i++) {
            array[i] = Integer.parseInt(str[i]);
        }
            
        // 確認
        System.out.println(n);
        String answer = "";
        for (int i = 0; i < n; i++) {
            answer += array[i] + " ";
        }
        System.out.println(answer);
    }
}
```

## Atcoderメモ
### 問題1
```Java
import java.util.*;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) throws Exception {
        Scanner scan = new Scanner(System.in);
        
        ArrayList<String> list_S = new ArrayList<String>();
        ArrayList<String> list_T = new ArrayList<String>();
        
        // 入力
        int N = scan.nextInt();
        String S = scan.next();
        String T = scan.next();
        
        // 重複数の合計
        int count = 0;
        
        // 文を一文字ずつlistに詰める
        for (int i = 1; i <= N; i++) {
            list_S.add(S.substring(i - 1, i));
            list_T.add(T.substring(i - 1, i));
        }
        
        // listを0番から順番に抜出し等しければcountにプラス１
        for (int i = 0; i < N; i++) {
            if (list_S.get(i).equals(list_T.get(i))){
                count++;
            }
        }
        
        // 出力
        System.out.println(N - count);
    }
}
```
### 問題2
```Java
import java.util.*;
import java.util.Scanner;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;

public class Main {
    public static void main(String[] args) throws Exception {
        Scanner scan = new Scanner(System.in);
        
        ArrayList<Integer> list_P = new ArrayList<Integer>();
        ArrayList<Integer> list_N = new ArrayList<Integer>();
        
        ArrayList<Integer> list_PP = new ArrayList<Integer>();
        
        // 入力
        int N = scan.nextInt();
        for (int i = 0; i < N; i++) {
            list_P.add(scan.nextInt());
            list_N.add(0);
        }
        list_PP = new ArrayList<>(list_P);
        
        // 変数
        int r = 1;
        int count = 0;
        int Rest = N;
        
        // 処理
        do {
            // count初期化
            count = 0;
            // 最大値の取得
            int max = Collections.max(list_PP);
            
            // 最大値の人を順位付け
            for (int j = 0; j < N; j++) {
                if (list_P.get(j).equals(max)) {
                    // 順位付け
                    list_N.set(j, r);
                    // 残り人数更新
                    Rest = Rest - 1;
                    // カウント
                    count++;
                }
            }
            //削除に使うリスト型の宣言
            List<Integer> set = new ArrayList<Integer>();
            set.add(max);
            // 要素削除
            list_PP.removeAll(set);
            // rの更新
            r = r + count;
        } while (Rest > 0);

        // 出力
        for (int i = 0; i < N; i++) {
            System.out.println(list_N.get(i));
        }
    }
}
```

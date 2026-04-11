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
  - [数字の絶対値](#数字の絶対値)
  - [数字の累乗](#数字の累乗)
- [配列](#配列)
  - [文字列を分割する](#文字列を分割する) 
  - [文字列を1文字ずつ取り出す](#文字列を1文字ずつ取り出す)
  - [重複](#重複)
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

### 数字の絶対値
Math クラスで用意されている abs メソッドを使用する。<br>
引数のデータ型に対応して、引数の絶対値を戻り値として返す。

```Java
System.out.println(Math.abs(-18));      // 18
System.out.println(Math.abs(-7.224));   // 7.224
```

### 数字の累乗
累乗した値を取得するには Math クラスで用意されている pow メソッドを使用する。<br>
第一引数に指定した値を、第二引数で指定した値だけ累乗した結果を戻り値として返す。<br>
引数と戻り値は double 型である。

```Java
double n = Math.pow(3.0, 4.0);   // 81.0
```

10 の累乗した値を取得する場合は、e を使った表現方法がある。<br>
戻り値は double 型である。

```Java
double n = 2.35e3    // 2350.0
double N = 3.79e-3   // 0.00379
```

例えば、10 の 9 乗のような大きな値を用意する場合、浮動小数点で表すときは上記の方法を取るが、<br>
精度が必要な整数計算では int型 や long型の使用を推奨する。<br>
Java 7 以降では、数値リテラルにアンダースコア「 _ 」を使って桁区切りができ、可読性を向上させることができる。

```Java
double n = Math.pow(1.0, 9.0);
double N = 1e9
int i = 1_000_000_000
long l = 1_000_000_000L
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

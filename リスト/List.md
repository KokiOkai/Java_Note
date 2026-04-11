## 目次
- [リスト](#リスト)
  - [長さの取得](#長さの取得)
  - [要素の取得](#要素の取得)
    - [指定したインデックスの要素を取得する](#指定したインデックスの要素を取得する)
    - [最大値・最小値を取得する](#最大値最小値を取得する)
    - [合計値・平均値を取得する](#合計値平均値を取得する)
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
  - [要素の並び替え](#要素の並び替え)
 

## リスト
### 長さの取得
List クラスで用意されている size メソッドを使用する。<br>

```Java
list.size();
```

### 要素の取得
#### 指定したインデックスの要素を取得する
List クラスで用意されている get メソッドを使用する。<br>

```Java
list.get(インデックス);
```

#### 最大値・最小値を取得する
Collections クラスで用意されている max メソッド、min メソッドを使用する。<br>

```Java
int max = Collections.max(list);
int min = Collections.min(list);
```

#### 合計値・平均値を取得する
Stream API で用意されている sum メソッド、average メソッドを使用する。<br>
リストが空の場合は 0 を返す。

```Java
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args) throws Exception {

        // 整数型リストを作成
        List<Integer> listA = Arrays.asList(10, 20, 30, 40, 50);

        // 浮動小数点型リストを作成
        List<Double> listB = Arrays.asList(10.5, 20.0, 30.5, 40.0, 50.5);

        // 合計値を算出
        int sum_A = listA.stream().mapToInt(Integer::intValue).sum();           // 150
        double sum_B = listB.stream().mapToDouble(Double::doubleValue).sum();   // 151.5

        // 平均値を算出
        double average_A = listA.stream().mapToInt(Integer::intValue).average().orElse(0);   // 30.0
        double average_B = listB.stream().mapToInt(Integer::intValue).average().orElse(0);   // 30.3
    }
}
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

### 要素の並び替え
Collections クラスで用意されている sort メソッドを使用する。<br>
リストに追加されている要素を昇順に並び替えるメソッドである。

```Java
Collections.sort(list);
```

リストに追加されている要素を降順で並び替えたい場合は、sort メソッドの第二引数に Collections.reverseOrder メソッドを指定する。

```Java
Collections.sort(list, Collections.reverseOrder());
```

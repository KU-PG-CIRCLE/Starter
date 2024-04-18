# Starter
プログラミングはプログラミングである、C言語でプログラムを書くのも、Javaでプログラムを書くのもプログラミングである。
あなたは入学してすぐC言語を学ぶかもしれない、2年生になってJava, Pythonを習うかもしれない、でもそれは紛れもなくプログラミングである。

C言語でint型の変数の宣言を書ける様になりましたか？ 大学でプログラミングを習ってない人も難しいことではありません。
`int num;`と書くだけです。
書けたならあなたはC++, C#, Java, etcでもint型の変数を宣言する事ができます。

このスターターは**プログラミングを学ぶ**ことを目標にしています、
体系的にプログラミングを学ぶと言語の差など〇〇と〇〇の順番が変わっただけ、〇〇が要らなくなっただけと思えることが多いです。
`var num int`と書ければあなたはGo言語で変数を宣言できる様になりました。

# 一般的な言語の機能
- 関数宣言
  - 引数
  - 返り値
- 変数宣言
  - 初期化
- 式
  - 演算
  - 関数呼び出し
  - 代入
- 制御構文
  - 分岐
  - ループ

# 言語の特色の機能 (パラダイム)
## オブジェクト指向
関数, 変数 などの要素を一塊に扱うオブジェクトを基礎としてプログラミングするパラダイム。

ここでは一旦Javaについて語る。

`class`(クラス) はそのオブジェクトの構造を書いた設計書である。
クラスは
- `method` : (メソッド/クラスの持つ関数)
- `field` : (フィールド/クラスの持つ変数)

を一塊にしたものです。

`class`(クラス) を実体化したものを `object`(オブジェクト) と言い、ややこしいのが実体化した `object`(オブジェクト)を`instance`(インスタンス) と呼びます。
`object`と`instance`の違いに定義はなくみんな感覚的に呼び分けてるし、さっきまで`instance`と言っていたのに`object`と言っても全然通じます。
オブジェクトってなんなんでしょうね。

`javax`というJavaの公式のパッケージの中には`ObjectInstance`という`class`があります、インスタンスってなんなんでしょうね。

java的には`new`されたものが、`instance`で、すべてのクラスは`object`であり、すべてのクラスを実体化したものも`object`でありそうです。
多分オブジェクトが好きすぎてなんでもオブジェクトにしちゃったんじゃないですかね。

```
public class Student { // Studentクラスの宣言
    string name;
    StudentID id; // StudentIDクラスの変数
    
}
```

プログラミングをしていると感じるのが、整数一つの単位で扱うことは珍しく大抵はゲームなら`敵` `プレイヤー` `アイテム`などのデータの塊である。
だからデータの塊をオブジェクトとし、そのオブジェクトをメインに開発していく言語は必然な言語の進化であったと思う。

他にも，C言語に`struct`と呼ばれる、一塊のデータ構造を作成する方法はあった、がいろいろな問題があった、例えば簡単な問題に、大規模なプログラムを書く際
```C
typedef struct {
    const char* name;
    unsigned int id;
    double data;
} StructSample;

struct_sample_init(StructSample* sampleData, const char* name, const double data);
```
の様に関数名が長くなる事、何度も同じ名前を書かなければならないことなどが一つの問題であり`method`を持つことも必然な進化であった。

keyword : `class` `struct` `inherit` `extends` `derived` `instance` `method` `field`

## ジェネリック (最初は見なくて大丈夫！)
型を変数のように関数やクラスに渡すことができるパラダイム。

そうすることで特定のクラスに依存しない型を作ることができたりする。
例えば
```C++
class AList {
    A* buffer = nullptr;
    unsigned int last_idx = 0;
public:
    AList(const unsigned int size) {
        buffer = new A[size];
    }

    void add(const A& a) {
        buffer[last_idx++] = a;
    }

    A& get(const unsigned int idx) {
        return buffer[idx];
    }
}
```
があったときBのリストを作りたかったら、また同じような`BList`を作る必要があるが、ジェネリックパラダイムがあると、
```C++
template<T>
class List {
    T* buffer = nullptr;
    unsigned int last_idx = 0;
public:
    List(const unsigned int size) {
        buffer = new T[size];
    }

    void add(const T& a) {
        buffer[last_idx++] = a;
    }

    T& get(const unsigned int idx) {
        return buffer[idx];
    }
}
```
と書くことで`List<A>` `List<B>`のように書くことができ、わざわざAとBそれぞれにListを書く必要がなくなる。

keyword : `generics` `template`

## コンポーネントベース (最初は見なくて大丈夫！)
プログラムの一塊ををコンポーネントやパッケージなどの単位で考え、そのコンポーネントやパッケージを再利用できるようにする考えである。

C言語にもライブラリはある、がC言語における#includeは本来そのファイルの中身を#includeの位置に展開するプリプロセッサ命令でしかなくとても扱いにくいものだった。
なので、コンポーネントベースとは言語自体がコンポーネントやパッケージなどと呼ばれるライブラリやプログラムを再利用する機能を備えたパラダイムである。

keyword : `package` `component`

## 並行 (最初は見なくて大丈夫！)
執筆中

## 構造化 (詳しく知りたい人向け!)
連結, 条件分岐(`if`), ループ(`for`, `while`), 関数/ルーチン(`function`) がある事、これは特色というか今はもう一般的であるが、昔はない時代があった`goto`で全てを解決していたのだ。
構造化の代表といえばフローチャート
`goto`だけでプログラムを書くと案外普通に動くものが書けてしまう、が`goto`はバグらせることも簡単だし、バグったら原因は分かりずらいし、何せどこに飛ばせばいいのか確認するのもめんどくさい。
`goto`だけで動くプログラムを見せようと思ったがめんどくさいのでここで終わりにする。

おまけ
- COBOLは2002年まで関数が無かった
- 構造化にはダイクストラ法で習うダイクストラさんの論文が大炎上して注目されました。[論文](https://homepages.cwi.nl/~storm/teaching/reader/Dijkstra68.pdf)

keyword : `goto`

## 関数型 (最初は見なくて大丈夫！)
変数として変数の中身の値を変えるのではなく、値から値を計算して、またそれから値を計算することで副作用(変数への代入)を無くす事ができる(執筆中)

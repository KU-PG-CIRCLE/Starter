# Starter
## 一般的な言語の機能
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

## 言語の特色の機能 (パラダイム)
### オブジェクト指向
関数, 変数 などの要素を一塊に扱うオブジェクトを基礎としてプログラミングするパラダイム。

C言語にも`struct`と呼ばれる、一塊のデータ構造作成する方法はあったが、いろいろな問題があった、

keyword : `class` `struct` `interface` `extends` `derived` `instance`

### 関数型
執筆中

### ジェネリック
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

### コンポーネントベース
プログラムの一塊ををコンポーネントやパッケージなどの単位で考え、そのコンポーネントやパッケージを再利用できるようにする考えである。

C言語にもライブラリはある、がC言語における#includeは本来そのファイルの中身を#includeの位置に展開するプリプロセッサ命令でしかなくとても扱いにくいものだった。
なので、コンポーネントベースとは言語自体がコンポーネントやパッケージなどと呼ばれるライブラリやプログラムを再利用する機能を備えたパラダイムである。

keyword : `package` `component`
### 並行
執筆中

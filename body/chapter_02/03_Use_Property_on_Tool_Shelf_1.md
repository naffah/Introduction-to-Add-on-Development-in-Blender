<div id="sect_title_img_2_3"></div>

<div id="sect_title_text"></div>

# ツール・シェルフのオプションを活用する①

<div id="preface"></div>

###### ここまでの説明で、アドオンの開発の仕方が何となくわかってきたのではないかと思います。本節では前節のサンプルを改良し、拡大率をツール・シェルフから変更できるようにします。

## 作成するアドオンの仕様

* *3Dビュー* エリアのメニューである、*オブジェクト* に *選択オブジェクトの拡大* と *選択オブジェクトの縮小* を追加
* 追加したメニューである、*選択オブジェクトの拡大* を実行すると、*3Dビュー* エリアのツール・シェルフの *拡大率* で指定した倍率で、選択中のオブジェクトのサイズを拡大する（初期値: 2倍）
* 追加したメニューである、*選択オブジェクトの縮小* を実行すると、*3Dビュー* エリアのツール・シェルフの *縮小率* で指定した倍率で、選択中のオブジェクトの大きさを縮小する（初期値: 1/2倍）

### ツール・シェルフとは？


<div id="sidebyside"></div>

|右図のように、*3Dビュー* エリアの左端のツール群をツール・シェルフと呼び、*T* キーにより表示/非表示を切り替えることができます。|![ツールシェルフ](https://dl.dropboxusercontent.com/s/ys4r22wz8lvimpn/tool-shelf.png "ツールシェルフ")|
|---|---|


Blenderでは何かしら操作を行う度に、直前の操作に対するパラメータ設定のためのUI（本書ではオプションと呼びます）がツール・シェルフの下側に表示されます。**直前に行った操作に対し、パラメータを調節して再度操作を実行** する時に使用します。

今回作成するアドオンでは、ツール・シェルフから拡大率や縮小率を指定できるようにします。

## アドオンを作成する

[1-5節](../chapter_01/05_Install_own_Add-on.md) を参考にして以下のソースコードを入力し、ファイル名 ```sample_2_3.py``` で保存します。

[import](../../sample/src/chapter_02/sample_2_3.py)

## アドオンを使用する

### アドオンを有効化する

[1-5節](../chapter_01/05_Install_own_Add-on.md) を参考にして、作成したアドオンを有効化します。

アドオンを有効化すると、コンソールウィンドウに以下の文字列が出力されます。

```sh
サンプル2-3: アドオン「サンプル2-3」が有効化されました。
```

<div id="sidebyside"></div>

|右図のように、*3Dビュー* のエリアのメニューに *オブジェクト* > *選択オブジェクトの拡大（拡大率任意指定）* と *オブジェクト* > *選択オブジェクトの縮小（縮小率任意指定）* が追加されていることを確認します。|![メニューの追加確認](https://dl.dropboxusercontent.com/s/e97r8hbr4kxr8ef/enable_add-on.png "メニューの追加確認")|
|---|---|


### アドオンの機能を使用する

以下の手順に従い、作成したアドオンの機能を使います。

<div id="space_s"></div>

<div id="process_title"></div>

##### Work

<div id="process_noimg"></div>

|<div id="box">1</div>|Blender起動直後に生成されるオブジェクト *Cube* を選択します。|
|---|---|

<div id="process_sep"></div>

---

<div id="process"></div>

|<div id="box">2</div>|*3Dビュー* エリアのメニューである、*オブジェクト* > *選択オブジェクトの拡大（拡大率任意指定）* を実行すると、選択したオブジェクト *Cube* のサイズが2倍に拡大されます。<br>この状態でツール・シェルフの下側を見てみましょう。*選択オブジェクトの拡大（拡大率任意指定）* のラベルの下に *拡大率* というオプションが追加され、数値を入力できるようになっています。|![選択オブジェクトの拡大・縮小 手順2](https://dl.dropboxusercontent.com/s/q989u68qznr9j10/use_add-on_2.png "選択オブジェクトの拡大・縮小 手順2")|
|---|---|---|

<div id="process_sep"></div>

---

<div id="process"></div>

|<div id="box">3</div>|*拡大率* の数値を好きな値に変更します。<br>指定した拡大率の値に応じて、オブジェクトの拡大率が変わります。また、数値変更の度に拡大したことを示すメッセージがスクリプト実行ログに表示されます。|![選択オブジェクトの拡大・縮小 手順3](https://dl.dropboxusercontent.com/s/nvtlavprah8elk5/use_add-on_3.png "選択オブジェクトの拡大・縮小 手順3")|
|---|---|---|

<div id="process_sep"></div>

---

<div id="process_noimg"></div>

|<div id="box">4</div>|*3Dビュー* エリアのメニューである、*オブジェクト* > *選択オブジェクトの縮小（縮小率任意指定）* を実行すると、ツール・シェルフの選択オブジェクトの縮小（縮小率任意指定）ラベルの下に、*縮小率* というオプションが追加されます。|
|---|---|

<div id="process_sep"></div>

---

<div id="process"></div>

|<div id="box">5</div>|*縮小率* の数値を変更することで、オブジェクトの縮小率を変えることができます。|![選択オブジェクトの拡大・縮小 手順5](https://dl.dropboxusercontent.com/s/yiktzp7fbujdumn/use-add-on_5.png "選択オブジェクトの拡大・縮小 手順5")|
|---|---|---|

<div id="process_start_end"></div>

---


### アドオンを無効化する

[1-5節](../chapter_01/05_Install_own_Add-on.md) を参考に、有効化したアドオンを無効化します。

アドオンが無効化されると、コンソールウィンドウに以下の文字列が出力されます。

```sh
サンプル2-3: アドオン「サンプル2-3」が無効化されました。
```


<div id="space_s"></div>


## ソースコードの解説

作成したアドオンのソースコードを解説します。


### オプションの作成

ツール・シェルフのオプションから直前に行った処理のパラメータを調整して再実行できるようにするためには、```bpy.props``` に定義されている **プロパティクラスをオペレータクラスのメンバに追加** します。

プロパティクラスにはツール・シェルフのオプションを作成する以外の用途もありますが、オプション作成時に利用するクラスは以下の通りです。

|クラス名|型|
|---|---|
|```IntProperty```|整数|
|```IntVectorProperty```|整数（グループ）|
|```FloatProperty```|浮動小数点|
|```FloatVectorProperty```|浮動小数点（グループ）|
|```StringProperty```|文字列|
|```BoolProperty```|ブーリアン <br> Blender上ではセレクトボックスのUIとなる|
|```BoolVectorProperty```|ブーリアン（グループ）|
|```EnumProperty```|列挙 <br> Blender上ではリストボックスのUIとなる|

プロパティクラス作成時に引数を指定することで、ユーザがクラスの設定を決めることができます。以下に代表的な引数を示しますが、クラスによって指定可能な引数が異なるため注意が必要です。

|引数|値の説明|
|---|---|
|```name```|ツール・シェルフに表示されるオプション名|
|```description```|オプションの説明文|
|```default```|オプションのデフォルト値|
|```max```|オプションに指定できる最大値|
|```min```|オプションに指定できる最小値|

今回は以下のように、 ```FloatPropery``` クラスを用いて拡大率と縮小率を指定できるようにします。

[import:"prop_enlarge_object_2", unindent:"true"](../../sample_raw/src/chapter_02/sample_2_3.py)

[import:"prop_reduce_object_2", unindent:"true"](../../sample_raw/src/chapter_02/sample_2_3.py)


次に、*オブジェクト* > *選択オブジェクトの拡大（拡大率任意指定）* を実行した時の処理について解説します。

引数 ```name``` はオプションの名称で、本節のサンプルでは ```"拡大率"``` を指定しています。引数 ```description ``` はオプションをマウスオーバーした時に表示される説明文を指定します。引数 ```default``` には ```2.0``` が指定されているため、デフォルトの拡大率は2.0倍となります。また拡大率は、引数 ```max``` に指定した ```10.0``` 倍、引数 ```min``` に指定した ```1.0``` 倍の間で変化させることができます。

オプションの値を変更すると、オペレータクラスの ```execute()``` メソッドが実行されます。

<div id="column"></div>

本節のサンプルのように値を連続的に変更可能なオプションを作成した場合、値が変更される度にexecute()メソッドが呼ばれます。execute()メソッドの処理が重い場合は値の変更だけで時間がかかってしまうため、ユーザがオプションによるパラメータ調整をできるようにしたい場合は、execute()メソッドの処理を可能な限り軽くするようにしましょう。

```execute()``` メソッドの中で指定されたオプションの値は、以下のように通常のクラス変数と同様、self変数からアクセスすることで取得します。

[import:"access_to_prop", unindent:"true"](../../sample_raw/src/chapter_02/sample_2_3.py)


## まとめ

事前に実行した処理に対して、ユーザがツール・シェルフのオプションから細かい制御ができるようにするための方法を紹介しました。本節では浮動小数点数の値を指定するオプションを紹介しましたが、他にも整数やブーリアンなどの異なる型もオプションとして利用できます。

<div id="point"></div>

### ポイント

<div id="point_item"></div>

* ユーザが直前に実行した操作に対して、ツール・シェルフのオプションからパラメータを調整して再実行することができる
* オペレータクラスのクラス変数にプロパティクラスを追加することで、ツール・シェルフのオプションによる処理の制御が可能となる
* ツール・シェルフのオプションに指定した値を変更すると、値を変更するたびにオペレータクラスの ```execute()``` メソッドが実行される

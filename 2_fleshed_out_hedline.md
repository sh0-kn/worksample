## lambda式とは

lambda式とは、関数を式として扱い、変数に代入できるようにする手法であり、プログラムのコードを簡潔にするメリットがあります。

## lambda式の基本的な書き方
商品の価格と利益(10%)を入れた販売価格を計算する処理を実装するとします。

    #lambda式を使わ図に通常の関数を用いる場合
    def fanc(price,profit):
     return price + (price * profit)

    sellingPrice1 = func(100,0.1)
    print(sellingPrice)

    #lambda式を用いる場合
    sellingPrice2 = (lambda price,profit:price + (price * profit))(100,0.1)

実行結果

    110.0
    110.0

lambda式を使用しない場合、まず価格と利益を掛け合わせて販売価格を計算する関数(func)を提起しています。

その後、関数(fanc)の引数20歳の値(100,0.1)を設定し、その結果を変数(sellingPrice1)に格納しています。

一方、labda式を用いる場合はdefによる関数定義は登場せず、代わりに*lambdaと書いて、その横に引数そしてコロン(:)の後に引数を使用した処理の内容*という形式にて書くことができます。

ですが、引数なしの処理も以下のように書くことはできます。

    #引数なしのlambda式
    greeting = (lambda:'hello')()
    print(greeting)

実行結果

    hello

## lambda式の実践的な使い方

基本的な書き方を確認したところで、次はより実践的な使い方を学んでいきましょう。

### labda式でfor文処理を実装する方法

例えば、様々な商品の価格を抜き出したリストがあり、そのリストに対して利益を上乗せきた販売価格情報を取得する処理を実装するとします。

そのような場合、販売価格のリストをfor文を使用して以下のように実装することができます。

    prices = [3000, 2500, 10500, 4300]
    profitList = []

    for price in prices:
      profitList.append(price * 1.1)

    print(profitList)

実行結果

    [3300.0, 2750.0, 10605.0, 4730.0]

同じ処理内容を今度はlambda式を利用して実装します。
その際に、合わせて使用する関数が*map関数*です。

map関数は**第一関数に処理内容、第二引数に処理対象のリストを指定**します。

    prices = [3000, 2500, 10500, 4300]
    profitList = list(map(lambda price:price * 1.1 , prices))

実行結果

    [3300.0, 2750.0, 10605.0, 4730.0]

このように**lambda式とmap関数を併用することで、for文の処理を実装することが可能**です。

### labmda式でif文処理を実装する方法
次にfor文でリストの要素を一つ一つ処理する際に、if文の条件が入るケースについてもlambda式を活用できます。

同じく例として様々な商品の価格を抜き出したリストがあり、そのリストからある金額以下のものを抜き出し、価格の安い順に並べた情報を取得するプログラムを実装するとします。

こちらもまずはlambda式を用いない場合の実装方法の例を見ていただきましょう。

    prices = [3000, 2500, 10500, 4300]
    priceList = []

    for price in prices:
      if price < 4000
      priceList.append(price)

    priceList.sort()
    print(priceList)


実行結果

    [2500, 3000]

これをlambda式を用いて書くと以下のようになります。

     prices = [3000, 2500, 10500, 4300]
     priceList = list(filter(lambda price:price < 4000, prices))
     priceList.sort()
     print(priceList)

実行結果

     [2500, 3000]

上記サンプルにてlabmda式と合わせて*list関数*と*filter関数*を使用しました。

list関数は引数の値をlist型へ変換し、その後、sort関数にて並び替えを行うために使用しています。

そして、filter関数は**第二引数に指定された配列の各要素に対して、第一引数の関数処理を実施し、Trueとなるものだけを抽出する処理**を行なっています。

これまで見ていただいたmap関数とfilter関数と合わせて活用したlambda式は、特に**無名関数**と呼ばれる使い方となります。

下記の通り名前がある関数(checkPrice)を使用した処理とは対照的にlambda式では関数名を定義せずに使用することができることから無名関数と呼ばれています。

    def checkPrice(price):
      return price < 4000

    prices = [3000, 2500, 10500, 4300]
    priceList = list(filter(checkPrice, prices))
    priceList.sort()
    print(priceList)

実行結果

    [2500, 3000]


## まとめ

ここでは、lambda式について、基本的な使い方から応用的な具体例についても紹介しました。

様々な箇所で共通的に使用したい処理内容であれば、通常のdefを用いた関数を活用し、**使用範囲が限られる処理内容であれば、lambda式を用いて簡潔に読みやすいコードを書く事を優先する**ことを今後は検討してみて下さい。

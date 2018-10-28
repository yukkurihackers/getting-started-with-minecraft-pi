##Pythonプログラミングインターフェースを使用する

Minecraftを起動して世界を新規作成したら、 `Tab` キーを押してマウスを解放します。アプリケーションメニューからPython3を開き、ウィンドウを左右に移動させます。

コマンドを直接Python3ウィンドウに入力するか、ファイルを作成してコードを保存してもう一度実行することができます。

ファイルを新規作成する場合は `File > New window` 、 `File > Save`の順で選択します。ホームフォルダまたは新しいプロジェクトフォルダに保存することをお勧めします。

まず、Minecraftライブラリをインポートし、ゲームへの接続を作成し、画面に「Hello world」というメッセージをポストしてテストします。

```python
from mcpi.minecraft import Minecraft

mc = Minecraft.create()

mc.postToChat("Hello world")
```

コマンドを直接Pythonウィンドウに入力する場合は、各行の後に`Enter`キーを押してください。ファイルの場合は`Ctrl + S`で保存し、`F5`で実行します。コードが実行されると、ゲームの画面にメッセージが表示されます。

![](images/helloworld.gif)

### 現在地を見つける

現在地を見つけるには、次のように入力します。

```python
pos = mc.player.getPos()
```

`pos`にはあなたの場所が含まれています。座標セットの各部分に`pos.x`、`pos.y`、`pos.z`でアクセスします。

別の方法として、座標の別々の変数にするには、Pythonのアンバック手法を使用するのが良い方法です。

```python
x, y, z = mc.player.getPos()
```

`x`、`y`、`z`には、それぞれの位置座標が含まれています。`x`、`z`は歩行方向（前後左右）、`y`は上下です。

`getPos()`はその時点のプレーヤーの位置を返します。位置を移動する場合は、関数を再度呼び出すか、格納された位置を使用する必要があります。

### テレポート

あなたの現在の場所を見つけるだけでなく、テレポートする特定の場所を指定することもできます。

```python
x, y, z = mc.player.getPos()
mc.player.setPos(x, y+100, z)
```

これはあなたのアバターを空中の高さ100のところに運びます。これは、空の真ん中にテレポートして、あなたがこの世界を始めた場所に戻ることを意味しています。

別の場所にテレポートしてみてください！

### ブロックを置く

`mc.setBlock()`を使用して、与えられた座標セットに1つのブロックを置くことができます。

```python
x, y, z = mc.player.getPos()
mc.setBlock(x+1, y, z, 1)
```

あなたの立っている所の前に石ブロックが現れます。それがあなたのすぐ前になければ、それはあなたの横にあるかもしれません。Minecraftウィンドウに戻り、あなたの目の前に灰色のブロックが現れるまで、マウスを使ってその場で回転して見てください。

![](images/mcpi-setblock.png)

`set block`に渡される引数は`x`、`y`、`z`、`id`です。`(x, y, z)`は世界の位置を指しています（プレイヤーが`x+1`で立っている場所から1ブロック離れて指定されています）。`id`は配置したいブロックのタイプを表します。`1`は石です。

あなたが試せる他のブロックの例

```
空気:　0
草:   2
土:   3
```

ブロックが見えたら、別のものに変更してみてください。

```python
mc.setBlock(x+1, y, z, 2)
```

目の前に灰色の石ブロックの変化が見られるはずです！

![](images/mcpi-setblock2.png)

#### Block constants

You can use a inbuilt block constants to set your blocks, if you know their names. You'll need another `import` line first though.

```python
from mcpi import block
```

Now you can write the following to place a block: 

```python
mc.setBlock(x+3, y, z, block.STONE.id)
```

Block ids are pretty easy to guess, just use ALL CAPS, but here are a few examples to get you used to the way they are named.

```
WOOD_PLANKS
WATER_STATIONARY
GOLD_ORE
GOLD_BLOCK
DIAMOND_BLOCK
NETHER_REACTOR_CORE
```

### Block as variable

If you know the id of a block it can be useful to set it as a variable. You can use the name or the integer id.

```python
dirt = 3
mc.setBlock(x, y, z, dirt)
```

or

```python
dirt = block.DIRT.id
mc.setBlock(x, y, z, dirt)
```

### Special blocks

There are some blocks which have extra properties, such as Wool which has an extra setting you can specify the colour. To set this use the optional fourth parameter in `setBlock`:

```python
wool = 35
mc.setBlock(x, y, z, wool, 1)
```

Here the fourth parameter `1` sets the wool colour to orange. Without the fourth parameter it is set to the default (`0`) which is white. Some more colours are:

```
2: Magenta
3: Light Blue
4: Yellow
```

Try some more numbers and watch the block change!

Other blocks which have extra properties are wood (`17`): oak, spruce, birch, etc; tall grass (`31`): shrub, grass, fern; torch (`50`): pointing east, west, north, south; and more. See the [API reference](http://www.stuffaboutcode.com/p/minecraft-api-reference.html) for full details.

### Set multiple blocks

As well as setting a single block with `setBlock` you can fill in a volume of space in one go with `setBlocks`:

```python
stone = 1
x, y, z = mc.player.getPos()
mc.setBlocks(x+1, y+1, z+1, x+11, y+11, z+11, stone)
```

This will fill in a 10 x 10 x 10 cube of solid stone.

![](images/mcpi-setblocks.png)

You can create bigger volumes with the `setBlocks` function but it may take longer to generate!


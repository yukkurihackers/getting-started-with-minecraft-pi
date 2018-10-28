## Pythonプログラミングインタフェースを使用する

Minecraftを走らせて世界を創り上げたら、Tabキーを押してあなたのマウスを解放します。アプリケーションメニューからPython 3を開き、ウィンドウを左右に移動させます。
コマンドを直接Pythonウィンドウに入力するか、ファイルを作成してコードを保存してもう一度実行することができます。

ファイルを作成する場合は、[ファイル]> [新規作成]、[ファイル]> [保存]の順に選択します。ホームフォルダまたは新しいプロジェクトフォルダに保存することをお勧めします。
まず、Minecraftライブラリをインポートし、ゲームへの接続を作成し、画面に「Hello world」というメッセージをポストしてテストします。

```python
from mcpi.minecraft import Minecraft

mc = Minecraft.create()

mc.postToChat("Hello world")
```

コマンドを直接Pythonウィンドウに入力する場合は、各行の後にEnterキーを押してください。ファイルの場合はCtrl + Sで保存し、F5で実行します。コードが実行されると、ゲームの画面にメッセージが表示されます。

![](images/helloworld.gif)

### あなたの場所を見つける

現在地を見つけるには、次のように入力します。

```python
pos = mc.player.getPos()
```

`pos` にはあなたの場所が含まれています。  `pos.x`, `pos.y`, `pos.z`で座標セットの各部分にアクセスします。

別の方法として、座標を別々の変数にするには、Pythonのアンパック手法を使用するのが良い方法です。
```python
x, y, z = mc.player.getPos()
```

`x`, `y`, `z` には、それぞれの位置座標が含まれています。 `x`, `z` は歩行方向（前後左右）、 `y`は上下方向です。
`getPos()`はその時点のプレーヤーの位置を返します。位置を移動する場合は、関数を再度呼び出すか、格納された位置を使用する必要があります。
### テレポート

あなたの現在の場所を見つけるだけでなく、テレポートする特定の場所を指定することもできます。

```python
x, y, z = mc.player.getPos()
mc.player.setPos(x, y+100, z)
```

これはあなたのプレーヤーを空中の100のスペースに運びます。これは、空の真ん中にテレポートして、あなたが始めた場所にまっすぐに戻ることを意味します。

別の場所にテレポートしてみてください！

### ブロックを設定する

`mc.setBlock()`を使用して、与えられた座標セットに1つのブロックを配置することができます。

```python
x, y, z = mc.player.getPos()
mc.setBlock(x+1, y, z, 1)
```

あなたが立っているところの石ブロックが現れます。それがあなたのすぐ前になければ、それはあなたの横にあるかもしれません。 Minecraftウインドウに戻り、あなたの目の前に灰色のブロックが現れるまで、マウスを使ってその場で回転してください。

![](images/mcpi-setblock.png)

The arguments passed to `set block` are `x`, `y`, `z` and `id`. The `(x, y, z)` refers to the position in the world (we specified one block away from where the player is standing with `x + 1`) and the `id` refers to the type of block we'd like to place. `1` is stone.

あなたが試すことができる他のブロック:

```
Air:   0
Grass: 2
Dirt:  3
```

ブロックが見えたら、別のものに変更してみてください:

```python
mc.setBlock(x+1, y, z, 2)
```

目の前で灰色の石ブロックの変化が見られるはずです！

![](images/mcpi-setblock2.png)

#### ブロック定数

名前を知っていれば、ブロックを設定するためにinbuiltブロック定数を使うことができます。しかし、最初に別の`import` 行が必要になります。

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


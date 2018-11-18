## 歩きながらブロックを落とす

今度はブロックを落とす方法を学び移動するとブロックを落とすようにしましょう。

次のコードは、歩くとどこにでも花を落とします：

```python
from mcpi.minecraft import Minecraft
from time import sleep

mc = Minecraft.create()

flower = 38

while True:
    x, y, z = mc.player.getPos()
    mc.setBlock(x, y, z, flower)
    sleep(0.1)
```

前方に歩いて、ふり返りあなたが後ろに残した花を見てください。

![](images/mcpi-flowers.png)

whileループを使用しているので、これは永遠に続きます。 それを止めるには、PythonウィンドウでCtrl + Cキーを押します.

空を飛んで、あなたが空に残す花を見てみましょう：

![](images/mcpi-flowers-sky.png)

プレイヤーが芝生の上を歩いているときに花を落としたければどうでしょうか？ getBlockを使用して、ブロックのタイプを調べることができます。

```python
x, y, z = mc.player.getPos()  # player position (x, y, z)
this_block = mc.getBlock(x, y, z)  # block ID
print(this_block)
```

これはあなたが立っているブロックの位置を示します（これは0になります - エアブロック） このために、y値から1を減算し、getBlock（）を使用して、どのタイプのブロックが立っているかを判別します。

```python
x, y, z = mc.player.getPos()  # player position (x, y, z)
block_beneath = mc.getBlock(x, y-1, z)  # block ID
print(block_beneath)
```

これは、プレイヤーが立っているブロックのIDを示します。

現在立っているもののブロックIDを出力するループを実行して、これをテストします。

```python
while True:
    x, y, z = mc.player.getPos()
    block_beneath = mc.getBlock(x, y-1, z)
    print(block_beneath)
```

![](images/blockbeneath.gif)

if文を使用して、花を植えるかどうかを選択できます。

```python
grass = 2
flower = 38

while True:
    x, y, z = mc.player.getPos()  # player position (x, y, z)
    block_beneath = mc.getBlock(x, y-1, z)  # block ID

    if block_beneath == grass:
        mc.setBlock(x, y, z, flower)
    sleep(0.1)
```

次のものは、下のブロックが芝生でない場合ブロックの上に芝生を生やすことができます。

```python
if block_beneath == grass:
    mc.setBlock(x, y, z, flower)
else:
    mc.setBlock(x, y-1, z, grass)
```

今草の上を歩くと、花を残します。 前のブロックが芝生でない場合、ブロックは芝生に変わります。 向きを変えて歩いていくと、後ろに花が残ります。
![](images/mcpi-flowers-grass.png)


## 流れる溶岩で遊ぼう

流れる溶岩は遊ぶと楽しいブロックです

```python
from mcpi.minecraft import Minecraft

mc = Minecraft.create()

x, y, z = mc.player.getPos()

lava = 10

mc.setBlock(x+3, y+3, z, lava)
```

配置したばかりのブロックを見つけたら、ブロックから地面に溶岩が流れているのを見てみてください。

溶岩の面白いところは、冷えると岩になることです。あなたの世界の別の場所に移動し、実際に試してみてください。

```python
from mcpi.minecraft import Minecraft
from time import sleep

mc = Minecraft.create()

x, y, z = mc.player.getPos()

lava = 10
water = 8
air = 0

mc.setBlock(x+3, y+3, z, lava)
sleep(20)
mc.setBlock(x+3,y+5, z, water)
sleep(4)
mc.setBlock(x+3, y+5, z, air)

```

スリープパラメータを調整して、様々な量の溶岩が流れるようにすることができます。

![lava](images/lava.png)


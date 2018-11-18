## 流れる溶岩で遊ぼう

楽しく遊べるブロックのひとつに流れる溶岩があります。

```python
from mcpi.minecraft import Minecraft

mc = Minecraft.create()

x, y, z = mc.player.getPos()

lava = 10

mc.setBlock(x+3, y+3, z, lava)
```

配置したばかりのブロックを見つけて、そのブロックから地面に溶岩が流れているのを見てみてください。

溶岩の面白いところは、冷えると岩になることです。あなたの世界の別の場所に移動して、実際に試してみてください。

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

`sleep` パラメータを調整して、様々な量の溶岩を流れるようにすることができます。

![lava](images/lava.png)


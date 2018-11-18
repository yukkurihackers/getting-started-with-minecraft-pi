## TNTで遊びましょう

このTNTは実に興味深いです！ ここには、普通のTNTブロックがおかれます

```python
tnt = 46
mc.setBlock(x, y, z, tnt)
```

![](images/mcpi-tnt.png)

しかし、このブログはやはり退屈です.dateを1として適用してみてください

```python
tnt = 46
mc.setBlock(x, y, z, tnt, 1)
```

あなたの剣を使い、TNTブロックを左クリックしてください：それは起動され、数秒で爆発するでしょう。

今度はTNTの大きな立方体を作ってみてください!

```python
tnt = 46
mc.setBlocks(x+1, y+1, z+1, x+11, y+11, z+11, tnt, 1)
```

![](images/mcpi-tnt-blocks.png)

これで、TNTで出来た、大きなブロックが表示されます。 一つのブロックを起動して、爆発を見るために逃げてください！ 一度にたくさんのものが変化するので、グラフィックをレタリングするのが遅くなります。

![](images/mcpi-tnt-explode.png)


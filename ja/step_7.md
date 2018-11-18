
## TNTで遊びましょう

もう一つの興味深いブロックはTNTです！通常のTNTブロックを配置するには：

```python
tnt = 46
mc.setBlock(x, y, z, tnt)
```

![](images/mcpi-tnt.png)

しかし、このTNTブロックはかなり退屈です。 `data` を `1` として適用してみてください：

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

これで、TNTブロックでいっぱいの大きなキューブが表示されます。移動してブロックの1つをアクティブにしてから、ショーを見るために逃げる！一度に多くのことが変わるので、グラフィックをレンダリングするのは本当に遅いでしょう。

![](images/mcpi-tnt-explode.png)
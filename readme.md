# 支持

MoT支持魔改以下的毛伊物语内容：

- 铁匠砧
- 铸形
- 坩埚炉配方
- 坩埚炉燃料
- 钓鱼掉落物
- 大锅

# 魔改

每个内容都支持添加或删除配方。

<font color=#FF0000>**以下被标红的变量是可选的。**</font>

## 铁匠砧

####添加配方

**使用方法**
mods.mariculture.Anvil.addRecipe(输入物品, 输出物品, 打击次数);

**实例**
mods.mariculture.Anvil.addRecipe(\<minecraft:stone>, \<minecraft:cobblestone>, 50);

####删除配方

**使用方法**
mods.mariculture.Anvil.removeRecipe(输入物品);

**实例**
mods.mariculture.Anvil.removeRecipe(\<minecraft:red_flower>);

## 铸形

<font color=#0000FF>**Wiki原文这里有错误，与给出的例子不符，已修正。**</font>

#### 添加配方

**粒铸形**
mods.mariculture.Casting.addNuggetRecipe(输入流体, 输出物品);

**锭铸形**
mods.mariculture.Casting.addIngotRecipe(输入流体, 输出物品);

**方块铸形**
mods.mariculture.Casting.addBlockRecipe(输入流体, 输出物品);

**实例**
mods.mariculture.Casting.addNuggetRecipe(\<liquid:gunpowder> * 16, \<minecraft:gunpowder>);
mods.mariculture.Casting.addIngotRecipe(\<liquid:gunpowder> * 144, \<Mariculturedroplet:6>);
mods.mariculture.Casting.addBlockRecipe(\<liquid:gunpowder> * 1296, \<minecraft:tnt>);

####删除配方

**粒铸形**
mods.mariculture.Casting.removeNuggetRecipe(输出物品);

**锭铸形**
mods.mariculture.Casting.removeIngotRecipe(输出物品);

**方块铸形**
mods.mariculture.Casting.removeBlockRecipe(输出物品);

**实例**
mods.mariculture.Casting.removeNuggetRecipe(\<Mariculture:materials:38>);
mods.mariculture.Casting.removeIngotRecipe(\<Mariculture:materials:4>);
mods.mariculture.Casting.removeBlockRecipe(\<Mariculture:metals>);

##坩埚炉配方
#### 添加配方

**使用方法**
mods.mariculture.Crucible.addRecipe(融化温度, 输入物品, <font color=#FF0000>输出流体</font>, <font color=#FF0000>输出物品</font>, <font color=#FF0000>输出物品生成概率</font>);
注意:其中输出物品生成概率为n时，实际概率为(100/n)%
**实例**
mods.mariculture.Crucible.addRecipe(1064, \<minecraft:sponge>, \<liquid:gold.molten> * 288, \<Mariculture:rocks>, 4);

####删除配方

**使用方法**
mods.mariculture.Crucible.removeRecipe(输入物品);

**实例**
mods.mariculture.Crucible.removeRecipe(\<minecraft:dirt>);

##坩埚炉燃料

#### 添加配方

**使用方法**
mods.mariculture.Crucible.addFuel(输入物品 或 输入流体 或 输入矿物词典, 最高温度, 每单位升温, 消耗所需时间(Ticks));

**实例**
mods.mariculture.Crucible.addFuel(\<minecraft:blaze_powder>, 3000, 50, 450); 
参考：煤炭最高温度为2000，每单位升温为40，消耗所需时间为450游戏刻。
mods.mariculture.Crucible.addFuel(\<liquid:water>, 500, 10, 240); 
参考：岩浆最高温度为1500，每单位升温为20，消耗所需时间为360游戏刻，每单位为10mb。
mods.mariculture.Crucible.addFuel(\<ore:treeLeaves>, 160, 4, 100);

#### 删除配方

**使用方法**
mods.mariculture.Crucible.removeFuel(输入物品 或 输入流体 或 输入矿物词典);

**实例**
mods.mariculture.Crucible.removeFuel(\<minecraft:coal>);
mods.mariculture.Crucible.removeFuel(\<liquid:pyrotheum>);
mods.mariculture.Crucible.removeFuel(\<ore:plankWood>);

##钓鱼掉落物
####添加配方

**使用方法**
垃圾
mods.mariculture.Fishing.addJunk(掉落物品, 概率, <font color=#FF0000>钓竿种类(String)</font>, <font color=#FF0000>匹配特定钓竿</font>, <font color=#FF0000>维度数组</font>);
宝藏
mods.mariculture.Fishing.addGood(掉落物品, 概率, <font color=#FF0000>钓竿种类(String)</font>, <font color=#FF0000>匹配特定钓竿</font>, <font color=#FF0000>维度数组</font>);

钓竿种类有：NET;OLD;GOOD;DIRE;SUPER;FLUX;blood
关于这个概率作者没有给出计算方式，个人估计应该与坩埚炉的输出物品生成概率计算方式相同。
垃圾和宝藏的区别在于，当你钓鱼时会先判定你钓到的是垃圾还是宝藏，然后再到指定的LootTable进行后续操作。
如果维度数组存在，那么该配方只在维度数组内指定的维度生效。

**实例**
mods.mariculture.Fishing.addJunk(\<minecraft:stick>, 25, "old", false, [0]);
mods.mariculture.Fishing.addGood(\<minecraft:emerald>, 5, "SUPER", true, [0, -1]);
mods.mariculture.Fishing.addGood(\<minecraft:diamond>, 1, "DIRE", true, [0, -1, 1]);

####删除配方

**使用方法**
mods.mariculture.Fishing.removeLoot(掉落物品);

**实例**
mods.mariculture.Fishing.removeLoot(\<minecraft:stick>);

##大锅
#### 添加配方

**使用方法**
mods.mariculture.Vat.addRecipe(输入流体1, 输入流体2, 输入物品, 输出流体, 输出物品, 消耗时间(Ticks));
作者虽然给出了通用使用方法，但是该配方比较特殊，部分输入输出可以直接删除而不留下null，以下做出分类讨论。
输入流体1 + 输入流体2 == 输出流体
mods.mariculture.Vat.addRecipe(输入流体1, 输入流体2, 输出流体, 消耗时间(Ticks));
输入流体1 + 输入流体2 == 输出物品
mods.mariculture.Vat.addRecipe(输入流体1, 输入流体2, 输出物品, 消耗时间(Ticks));
输入流体1 + 输入流体2 == 输出流体 + 输出物品
mods.mariculture.Vat.addRecipe(输入流体1, 输入流体2, 输出流体, 输出物品, 消耗时间(Ticks));
输入流体 + 输入物品 == 输出流体
mods.mariculture.Vat.addRecipe(输入流体, 输入物品, 输出流体, 消耗时间(Ticks));
输入流体  + 输入物品 == 输出物品
mods.mariculture.Vat.addRecipe(输入流体, 输入物品, 输出物品, 消耗时间(Ticks));
输入流体 + 输入物品 == 输出流体 + 输出物品
mods.mariculture.Vat.addRecipe(输入流体, 输入物品, 输出流体, 输出物品, 消耗时间(Ticks));
输入流体1 + 输入流体2 + 输入物品 == 输出流体
mods.mariculture.Vat.addRecipe(输入流体1, 输入流体2, 输入物品, 输出流体, 消耗时间(Ticks));
输入流体1 + 输入流体2 + 输入物品 == 输出物品
mods.mariculture.Vat.addRecipe(输入流体1, 输入流体2, 输入物品, 输出物品, 消耗时间(Ticks));

**实例**
mods.mariculture.Vat.addRecipe(\<liquid:water> * 1000, \<liquid:custard> * 1000, \<liquid:milk> * 2000, 10); 
mods.mariculture.Vat.addRecipe(\<liquid:titanium.molten> * 4608 , \<liquid:water> * 4000, \<minecraft:bedrock>, 600);
mods.mariculture.Vat.addRecipe(\<liquid:salt.molten> * 50 , \<liquid:water> * 1000, \<liquid:dirt> * 25, \<Mariculture:materials:12>, 2000);
mods.mariculture.Vat.addRecipe(\<liquid:water> * 1000, \<minecraft:gunpowder> * 16, \<liquid:gunpowder> * 1000, 5);
mods.mariculture.Vat.addRecipe(\<liquid:quicklime> * 50, \<minecraft:sand:1> * 4, \<minecraft:sand> * 4, 30);
mods.mariculture.Vat.addRecipe(\<liquid:lava> * 8000, \<minecraft:iron_ore>, \<liquid:dirt> * 200, \<minecraft:iron_ingot> * 2, 800);
mods.mariculture.Vat.addRecipe(\<liquid:lava> * 2000, \<liquid:flux> * 200, \<Mariculture:pearls:5> * 3, \<liquid:gold.molten> * 144, 90);
mods.mariculture.Vat.addRecipe(\<liquid:water> * 4000, \<liquid:fastwater> * 4000, \<Mariculture:pearls:9>, \<Mariculture:pearls>, 25);

#### 删除配方

**使用方法**
mods.mariculture.Vat.removeRecipe(输出物品, 输出流体);
mods.mariculture.Vat.removeRecipe(输入物品);
mods.mariculture.Vat.removeRecipe(输入流体);

**实例**
mods.mariculture.Vat.removeRecipe(\<Mariculture:materials:13>, \<liquid:water>);
mods.mariculture.Vat.removeRecipe(\<minecraft:obsidian>);
mods.mariculture.Vat.removeRecipe(\<liquid:titanium.molten>);
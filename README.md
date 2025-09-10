weekin 的模板自带 build 工作流，每次 commit 之后只需要下载它自动构建的 firmware 就好了

我需要在这里解释一下我做的一些改动与设计

# 约定

左手的 thumb cluster 有5键，从左到右从上到下编为 1 2 3 \\ 4 5
右手的 thumb cluster 有3键，位置上对应的是左手的 2 3 \\ 5
简称 thumb cluster 为 [r/l]tc

双手各4*6，直接编为 R/L(n,m) ，左边从左到右从上到下，右边镜像
第一位表示第几行，第二位表示第几列

# 沿袭我之前在 Keychron K15 Max 上的一些配置

这是为了利用之前养成的肌肉记忆

我把 Num_Lock 放在了 ltc 2 上，这是我控制 WM 用的键，具体是什么键都行，就是不能是 win 键
把 keyboard mouse layer 放在了 ltc 3 上

# 如何处理一些符号缺失

-=[]` （和对应的 _+{}~ ）在默认的按键下是缺失的


应该参考一下 [Miryoku](https://github.com/manna-harbour/miryoku) 的设计
右手三个键加上 layer 可能是可行的？
实际上如果加上了 hold 配置的话就不能自动连续输入回车和空格了，这是我不想要的

我选择的解决方案是把他们放在 keyboard mouse layer 里，保持他们的相对位置不变，分别覆盖在 p\ 和 ;' 上，也就是 R(2/3,1/2)

这又带来了麻烦，如果我想要输入 C-S-[ 这样的键呢？当然我可以同时用食指去按 ltc 1，用小拇指去按 shift，
但是还是感觉一只手按三个键还是有点别扭，可以把 rtc 5 也当做类似的前导键，这样两只手大拇指和小拇指都按一个键就有点正常了

# snip 模式下的鼠标左右键应该放在哪里

首先，左手和右手都需要有
在长时间控制的时候左手更方便，都用右手会加速疲惫
在临时控制的时候右手更方便，不需要多移动一下左手大拇指，还需要考虑左手大拇指需要按其他控制键可能的冲突情况

我选择左手放在 ltc 45 位，右手放在 jk 上

因为我可能需要同时按着 ltc 2、移动光标和按左右键，所以其实要考虑挺多地方的
snip 模式下我不可能再用我的右手大拇指，手型也不太可能有太大的变化，所以右手就放在了可能的方案中最省力的地方
至于左手，因为我不希望在先按 s 后按 ltc 2 的时候被误认为想输入 &mkp 所以我只能避开，剩下最可能的地方就是 ltc 45

# keyboard mouse layer 相比原来的键盘的改动

让 left click 放在 rtc2，right click 放在 rtc3
放弃之前直观的左键在左的模式，因为 rtc2 是大拇指放置的最自然的位置，更符合人体工学

# 默认的 layer 0 绑定

vim 用户必须的 Caps_Lock <-> Escape

ltc 1: ctrl
ltc 2: Num_Lock
ltc 3: keyboard mouse layer
ltc 4: alt
ltc 5: win

rtc 2: space
rtc 3: enter
rtc 5: delete / hjkl to arrow layer

s: snip layer
f: scroll layer

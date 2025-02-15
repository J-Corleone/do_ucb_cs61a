Hog是由两名玩家轮流掷骰子的游戏，直到某一名玩家得分先达到`GOAL`，默认100

每回合中，当前的玩家选择骰的次数，最多10次。得分是所有骰到的点数之和

在Hog中，有三个规则：（其中前2个为骰之时的规则，第3个为骰之后的规则）
1. **Sow Sad**
   - 如果任何一次的点数为1，则本回合玩家得分为1
2. **Boar Brawl**
   - 如果玩家在本回合骰0次，他获得的点数为 `max(1, abs(对手分数的十位-该玩家当前分数的个位)*3)`
3. **Sus Fuss**
   - sus数指它有3/4个因子（包括1和它本身）。如果骰完之后，玩家的得分是一个sus数，他的得分会立即增加到下一个质数


### GUI
当完成代码的时候，可以在终端执行`python3 hog_gui.py`在浏览器玩hog

---
交互式测试code：加`-i`会在用例失败时打开一个具有上下文环境的解释器，方便调试
```python
python3 ok -q [question number] -i 
```

在代码中打印debug信息：
```python
print("DEBUG:", x) 
```

### P0
sides应该是骰子的面数，2面的，4个面的，6个面的
`make_fair_dice(n)`是生成n面的骰子，`make_fair_dice(n)()`会来掷这个骰子
`make_test_dice(x1, x2, ...)`生成固定序列的点数，用来方便测试我们的实现

### P4
实现`num_factors`时，不能直接从2开始，这忽略了n=1的情况

### P5
num0, num1写到if外边就不对，不理解了
```py
   while score0 < goal and score1 < goal:
      num0 = strategy0(score0, score1)
      num1 = strategy1(score1, score0)
      print("DEBUG: who:%d num0:%d num1:%d" %(who, num0, num1))
      if who == 0:
         score0 = update(num0, score0, score1, dice)
      else:
         score1 = update(num1, score1, score0, dice)
      
      who = 1 - who
```
报错是这样的：
```py
>>> import tests.play_utils
>>> turns = tests.play_utils.describe_game(hog, test_number=69484, score0=15, score1=10, goal=32, update=hog.simple_update)
DEBUG: who:0 num0:8 num1:8
DEBUG: who:1 num0:4 num1:4
DEBUG: who:0 num0:5 num1:5
DEBUG: who:1 num0:3 num1:3
DEBUG: who:0 num0:10 num1:10
DEBUG: who:1 num0:3 num1:3
>>> print(turns[0])
Start scores = (15, 10).
Player 0 rolls 8 dice and gets outcomes [2, 1, 6, 6, 6, 5, 4, 4].
End scores = (16, 10)
>>> print(turns[1])
Start scores = (16, 10).
Player 0 rolls 4 dice and gets outcomes [4, 2, 4, 6].
End scores = (16, 26)

# Error: expected
#     Start scores = (16, 10).
#     Player 1 rolls 5 dice and gets outcomes [4, 2, 4, 6, 2].
#     End scores = (16, 28)
# but got
#     Start scores = (16, 10).
#     Player 0 rolls 4 dice and gets outcomes [4, 2, 4, 6].
#     End scores = (16, 26)

Run only this test case with "python3 ok -q 05 --suite 2 --case 1"
```
player显示就错了，不过是正常计算的player1

### P9
为啥是要平均得分，不是很理解，我直接算这一轮骰几个得分最高不是行了？

为啥要求骰i个n次的平均得分...哦，每次的运气不一样
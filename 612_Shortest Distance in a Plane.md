## 单词
+ coordinates 坐标
+ decimals 小数

## 内置函数
+ sqrt() 开根号。
+ power() n次方，power(10, 9),10的9次方。
+ exp() 以e为底n次方。
+ min() 数组中取值最小的那个。

## 逻辑符号
+ 不等于 mysql中用<>与!=都是可以的
+ and 表示两个条件必须都不同
+ or 表示两个至少有一个不同

本题中有一个维度坐标不同，就是另外一个点。因此，需要用or。

##Mysql如何组成笛卡尔积
![join图解](https://www.runoob.com/wp-content/uploads/2019/01/sql-join.png "join图解")
#### 表格形式
重复的部分在后面。

|t1.x|t1.y|t2.x|t2.y|
|----|----|----|----|
|-1|-1|-1|-1|
|0|0|-1|-1|
|-1|-2|-1|-1|
|-1|-1|0|0|
|0|0|0|0|
|-1|-2|0|0|
|-1|-1|-1|-2|
|0|0|-1|-2|
|-1|-2|-1|-2|

## 距离公式
![距离公式](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAANIAAAAgBAMAAACV7TtjAAAAMFBMVEX///8EBATMzMx0dHQwMDAMDAxQUFBiYmKKiooWFhZAQEC2trYiIiLm5uaenp4AAADoCVTMAAAAAXRSTlMAQObYZgAAA1NJREFUSA29VkFoE0EUfdltukl2NyZ66aHY9OChHiQqeJIaMYoIQuilUA/NwUovynqoB1EbL/ZStF4qosIqnkQhJ8GCGBAUrJKI4EEpXUHsRW3QVsVq65/Z3WR2bbaXJR8yM+//N//NzJ8dAgSZVF0LzYJ0gFguOB5etNMIL1dwJs0KjocXjdTCyxWc6XVwOMTo5xBzBac6GxyWrr4KJrjRjYkHXOr6fWftxfoBv3dj4jH/FC+WMOl1tEIbE+uA1Go2MhTZI0QZXtcy5CXiFxZ8AMjDR6ZtwBy2qQXgvAv+63eRR6iT0vKLcIizxE+uUDOC+SwDgsk5qEUBe4caoFhN18Pm0DdyiCx5/Bc1eUSLPqWEAa3sm9aEmoWFJoJvrhBxiIxwZpqaQcxbPnbcQsC3K5uSqbIju8Sy6ilqpAwbNs3GDpGS64U8BVf1p/51baphL9BRiG1uTgYO4mKGYTUVXRtkA64kV3D3jlJg2DUXO0RSSmRHaDm/9xtMKZ5Op7sdbi9wD+jf8qnkTqZe/tA/yqH+1/FypYSpzq1AVGpgh0jJt+EK3Yq6ftO/J3qMnlG2+4aT0u4Szx3I7hEzrqQVIadgcofTNLBNJKWX+WoNyhQWywRc04tUP+Aa4Sf0s2jX18nKdGp12K/LKvmB3nRPeiudhYGOnGoxIvqIeIOOnXBfd40Kw3i0jWSO7gI6TCxaTSV97DtwGGDrXyzjnXAs9E3Yr4t3TwaihuIhMnxSMwF3T9EMIlm2pnGhTsnYMjDA66QfL0IVlN4eoodjklbwjX7MnDohUvrqITKciVVc4ixO0NZNzJekLk+dhkuoA+cgfXzTZQhKO47unOCvC52ibVxJqUAbpS9dWBLDkGmZNnE2sVTG6R9SdShveZT2TalTVAUoAxgSE4xloiZ/hugFsY0rSSlItzMikWNoNTjEZmlomggiq7IJ0NEyE5fKsGJRwUsQjY56t49IGBcaRDG5R0n+k8jS/zCDZ/MrLZA3LuoAE1ArXiWGkzTfIbZUQs+jMuUy6edNQJA/Q5d5pNEk9L6ah8jxdjyGQ2ytNF5lWd7zVDN05wXjz5AlOGioz9yiViAmGB5eNmBRH2gRuuftsc6l9ujQcfxslxJOtU1pLlSlf9yuLI/T1c4FAAAAAElFTkSuQmCC "距离公式")

# 粒子滤波追踪算法(初级版) Matlab版
#### 可根据自身需求修改参数
----
主要原理：

1. 对第一张图片进行初始化，需要手工选取追踪的区域{left top width height}

2. 对该区域计算feature，(默认使用intensity作为feature)

3. 在区域的中心处，设置N个particle，作为粒子

4. label:让粒子高斯运动，扩散

5. 在下一张图中，对每个粒子所在的区域，计算feature，与之前的feature做比较，求出相似度(这里使用corr2)，计算每个粒子的weight，并且进行归一化处理

6. 找到其中weight最大的粒子，即与上一刻最接近的那个点，代表所追踪的物体(这时，feature需要及时更新，但若中途出现整体miss的情况，就会追踪失效，故存在一些瑕疵)
7. 根据weights，重新分配每个粒子附近产生的其他粒子的个数，总数仍然为N，称为resample

8. goto label


不足：
1. resample_step.m 既消耗时间，又消耗空间，需要优化

*更正:但matlab自己的内存分配方式是不知的，故无需修改*

**2016.5.7**

----

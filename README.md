# TraditionalCV
#### 传统车道线检测
1.提取特征
1.1 Sobel算子
-图像边缘检测
![image](https://user-images.githubusercontent.com/6326768/131777283-94a86938-6328-4130-bed9-1e9797854da6.png)
-原始像素灰度值，通过卷积，变成右边像素值减去左边像素值，反映了水平方向的变化
![image](https://user-images.githubusercontent.com/6326768/131777303-5013187e-a051-465d-a232-ba09e4650d23.png)
-原始像素灰度值，通过卷积，变成下边像素值减去上边像素值，反映了垂直方向的变化
1.2 HLS图像中的S通道
-HLS分别是图象亮度,饱和度,色度。车道线有黄色和白色，通过S通道可以提取出黄色的车道线。
2.过滤特征
-将上一步中提取出的特征过滤。将大于阈值的置为255，小于的置为0.
3.直方图找出车道线起点
-对x，将所有y上的数值相加，取左右两边的峰值为中心点。
4.滑动窗口定位车道线
-以左右两边峰值为x的中心点，在x左右一定范围内，从y的底部往上查找车道线。由于车道线有一定弧度，查找过程中需要不断更新x中心点。
5.拟合车道线
-将找出的x，y点拟合成一条曲线。X=aY^2+bY+C

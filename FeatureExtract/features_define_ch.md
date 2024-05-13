# [Histomicstk.features](https://digitalslidearchive.github.io/HistomicsTK/histomicstk.features.html#module-histomicstk.features)

## 标识符

> 输入标记掩码中核的位置及其编码。列名以 *Identifier.* 开头，包括：

1. Identifier.Label (int) - 输入标记掩码中的核标签
2. Identifier.Xmin (int) - 左边界
3. Identifier.Ymin (int) - 上边界
4. Identifier.Xmax (int) - 右边界
5. Identifier.Ymax (int) - 下边界
6. Identifier.CentroidX (float) - X 轴质心（列）
7. Identifier.CentroidY (float) - Y 轴质心（行）
8. Identifier.WeightedCentroidX (float) - 强度加权的 X 轴质心
9. Identifier.WeightedCentroidY (float) - 强度加权的 Y 轴质心

## 形态测量（核的大小、形状和方向）特征

> 详见 histomicstk.features.compute_morphometry_features。特征名前缀为 *Size.*、*Shape.* 或 *Orientation.*。

9. Orientation.Orientation: float

   椭圆主轴与水平轴之间的角度，角度值从 -π/2 到 π/2，逆时针方向。

10. ⭕ Size.Area: int

    物体占据的像素数量。

11. Size.ConvexHullArea: int

    凸包图像的像素数量，即包围该区域的最小凸多边形。

12. ⭕ Size.MajorAxisLength: float

    与物体具有相同归一化第二中心矩的椭圆的主轴长度。

13. ⭕ Size.MinorAxisLength: float

    与区域具有相同归一化第二中心矩的椭圆的次轴长度。

14. ⭕ Size.Perimeter: float

    物体的周长，通过连接边界像素中心的直线近似轮廓，使用4连通性。

15. ⭕ Shape.Circularity: float

    衡量物体形状与圆形的相似度。

16. ⭕ Shape.Eccentricity: float

    用来计算形状的偏心率，即与物体区域具有相同第二矩的椭圆的偏心率。偏心率是焦点距离（焦点之间的距离）与主轴长度的比率。值在 [0, 1) 区间内，当为 0 时，椭圆变为圆形。

17. ⭕ Shape.EquivalentDiameter: float

    与物体面积相同的圆的直径。

18. ⭕ Shape.Extent: float

    物体面积与其轴对齐边界框面积的比率。

19. Shape.FractalDimension: float

    Minkowski–Bouligand 维数，亦称盒计数维数。这是一个衡量边界复杂性的指标。详情见 [Minkowski–Bouligand dimension](https://en.wikipedia.org/wiki/Minkowski%E2%80%93Bouligand_dimension)

20. ⭕ Shape.MinorMajorAxisRatio: float

    形状的长宽比，即与物体区域具有相同第二矩的椭圆的次轴与主轴的比率。

21. ⭕ Shape.Solidity: float

    凸度测量，计算为物体像素数与其凸包像素数的比率。

22. Shape.HuMoments-k: float

    k 的范围从 1 到 7，为 7 个 Hu 矩特征。前六个矩是平移、缩放和旋转不变的，而第七个矩如果形状是镜像则其符号会反转。详情见 [shape matching using Hu moments](https://learnopencv.com/shape-matching-using-hu-moments-c-python/)

29. Shape.WeightedHuMoments-k: float

    与 Hu 矩相同，但使用强度图像代替二值掩码。

## 傅立叶形状描述符特征

> 更多细节请见 histomicstk.features.compute_fsd_features。特征名前缀为 *FSD*。

36. ⭕ Shape.FSD-k

    为每个对象计算傅立叶形状描述符。参见 [D. Zhang et al. “A comparative study on shape retrieval using Fourier descriptors with different shape signatures,” In Proc. ICIMADE01, 2001.]()

## 细胞核和胞质通道的强度特征

> 有关更多详细信息，请查阅 histomicstk.features.compute_fsd_features。细胞核特征的特征名前缀为 *Nucleus.Intensity.*，胞质特征的前缀为 *Cytoplasm.Intensity.*。

42. ⭕ Intensity.Min: float

    对象像素的最小强度。

43. ⭕ Intensity.Max: float

    对象像素的最大强度。

44. ⭕ Intensity.Mean: float

    对象像素的平均强度。

45. ⭕ Intensity.Median: float

    对象像素的中位数强度。

46. ⭕ Intensity.MeanMedianDiff: float

    对象像素的平均强度与中位数强度之间的差值。

47. ⭕ Intensity.Std: float

    对象像素强度的标准偏差。

48. ⭕ Intensity.IQR: float

    对象像素强度的四分位距。

49. ⭕ Intensity.MAD: float

    对象像素强度的中位数绝对偏差。

50. ⭕ Intensity.Skewness: float

    对象像素强度的偏度。当所有强度值相等时，该值为0。

51. ⭕ Intensity.Kurtosis: float

    对象像素强度的峰度。当所有值相等时，该值为-3。

52. ⭕ Intensity.HistEnergy: float

    对象像素强度直方图的能量。

53. ⭕ Intensity.HistEntropy: float

    对象像素强度直方图的熵。

## 细胞核和胞质通道的梯度/边缘特征

> 有关更多详细信息，请查阅 histomicstk.features.compute_gradient_features。细胞核特征的特征名前缀为 *Nucleus.Gradient.*，胞质特征的前缀为 *Cytoplasm.Gradient.*。

54. ⭕ Gradient.Mag.Mean: float

    梯度数据的平均值。

55. ⭕ Gradient.Mag.Std: float

    梯度数据的标准偏差。

56. ⭕ Gradient.Mag.Skewness: float

    梯度数据的偏度。当所有值相等时，该值为0。

57. ⭕ Gradient.Mag.Kurtosis: float

    梯度数据的峰度。当所有值相等时，该值为-3。

58. ⭕ Gradient.Mag.HistEnergy: float

    对象像素的梯度幅度直方图的能量。

59. ⭕ Gradient.Mag.HistEntropy: float

    对象像素的梯度幅度直方图的熵。

60. ⭕ Gradient.Canny.Sum: float

    Canny滤波后的梯度数据之和。

61. ⭕ Gradient.Canny.Mean: float

    Canny滤波后的梯度数据的平均值。

## 细胞核和胞质通道的哈拉里克特征

> 有关更多详细信息，请查阅 histomicstk.features.compute_haralick_features。细胞核特征的特征名前缀为 *Nucleus.Haralick.*，胞质特征的前缀为 *Cytoplasm.Haralick.*。

62. ⭕ Haralick.ASM.Mean: float

63. ⭕ Haralick.ASM.Range: float

    角二阶矩（ASM）的平均值和范围。它是图像均匀性的度量，计算公式如下：

    𝐴𝑆𝑀=∑𝑖,𝑗=0𝑙𝑒𝑣𝑒𝑙𝑠−1𝑝(𝑖,𝑗)²

64. ⭕ Haralick.Contrast.Mean: float

65. ⭕ Haralick.Contrast.Range: float

    对比度特征的平均值和范围，它度量相邻像素强度的变化量，对于恒定图像为零，随变化增加而增加，计算公式如下：

    𝐶𝑜𝑛𝑡𝑟𝑎𝑠𝑡=∑𝑖,𝑗=0𝑙𝑒𝑣𝑒𝑙𝑠−1(𝑖−𝑗)²𝑝(𝑖,𝑗)

66. ⭕ Haralick.Correlation.Mean: float

67. ⭕ Haralick.Correlation.Range: float

    相关性特征的平均值和范围，度量相邻像素强度值的相关性，计算公式如下：

    𝐶𝑜𝑟𝑟𝑒𝑙𝑎𝑡𝑖𝑜𝑛=∑𝑖,𝑗=0𝑙𝑒𝑣𝑒𝑙𝑠−1𝑝(𝑖,𝑗)[(𝑖−𝜇𝑖)(𝑗−𝜇𝑗)𝜎𝑖𝜎𝑗]

68. ⭕ Haralick.SumOfSquares.Mean: float

69. ⭕ Haralick.SumOfSquares.Range: float

    平方和特征的平均值和范围，度量方差，计算公式如下：

    𝑆𝑢𝑚𝑜𝑓𝑆𝑞𝑢𝑎𝑟𝑒=∑𝑖,𝑗=0𝑙𝑒𝑣𝑒𝑙𝑠−1(𝑖−𝜇)²𝑝(𝑖,𝑗)

70. ⭕ Haralick.IDM.Mean: float

71. ⭕ Haralick.IDM.Range: float

    逆差矩（IDM）的平均值和范围，度量均匀性，计算公式如下：

    𝐼𝐷𝑀=∑𝑖,𝑗=0𝑙𝑒𝑣𝑒𝑙𝑠−111+(𝑖−𝑗)²𝑝(𝑖,𝑗)

72. ⭕ Haralick.SumAverage.Mean: float

73. ⭕ Haralick.SumAverage.Range: float

    和平均特征的平均值和范围，计算公式如下：

    𝑆𝑢𝑚𝐴𝑣𝑒𝑟𝑎𝑔𝑒=∑𝑘=22𝑙𝑒𝑣𝑒𝑙𝑠𝑘𝑝𝑥+𝑦(𝑘),其中𝑝𝑥+𝑦(𝑘)=∑𝑖,𝑗=0𝑙𝑒𝑣𝑒𝑙𝑠−1𝛿𝑖+𝑗,𝑘𝑝(

(𝑖)𝑝(𝑖,𝑗)

74. ⭕ Haralick.SumVariance.Mean: float

75. ⭕ Haralick.SumVariance.Range: float

    和方差特征的平均值和范围，计算公式如下：

    𝑆𝑢𝑚𝑉𝑎𝑟𝑖𝑎𝑛𝑐𝑒=∑𝑘=22𝑙𝑒𝑣𝑒𝑙𝑠(𝑘−𝑆𝑢𝑚𝐸𝑛𝑡𝑟𝑜𝑝𝑦)𝑝𝑥+𝑦(𝑘)

76. ⭕ Haralick.SumEntropy.Mean: float

77. ⭕ Haralick.SumEntropy.Range: float

    和熵特征的平均值和范围，计算公式如下：

    𝑆𝑢𝑚𝐸𝑛𝑡𝑟𝑜𝑝𝑦=−∑𝑘=22𝑙𝑒𝑣𝑒𝑙𝑠𝑝𝑥+𝑦(𝑘)log(𝑝𝑥+𝑦(𝑘))

78. ⭕ Haralick.Entropy.Mean: float

79. ⭕ Haralick.Entropy.Range: float

    熵特征的平均值和范围，计算公式如下：

    𝐸𝑛𝑡𝑟𝑜𝑝𝑦=−∑𝑖,𝑗=0𝑙𝑒𝑣𝑒𝑙𝑠−1𝑝(𝑖,𝑗)log(𝑝(𝑖,𝑗))

80. ⭕ Haralick.DifferenceVariance.Mean: float

81. ⭕ Haralick.DifferenceVariance.Range: float

    差异方差特征的平均值和范围，计算公式如下：

    𝐷𝑖𝑓𝑓𝑒𝑟𝑒𝑛𝑐𝑒𝑉𝑎𝑟𝑖𝑎𝑛𝑐𝑒=方差 𝑝𝑥−𝑦, 其中𝑝𝑥−𝑦(𝑘)=∑𝑖,𝑗=0𝑙𝑒𝑣𝑒𝑙𝑠−1𝛿|𝑖−𝑗|,𝑘𝑝(𝑖,𝑗)

82. ⭕ Haralick.DifferenceEntropy.Mean: float

83. ⭕ Haralick.DifferenceEntropy.Range: float

    差异熵特征的平均值和范围，计算公式如下：

    𝐷𝑖𝑓𝑓𝑒𝑟𝑒𝑛𝑐𝑒𝐸𝑛𝑡𝑟𝑜𝑝𝑦=差异熵 𝑝𝑥−𝑦

84. ⭕ Haralick.IMC1.Mean: float

85. ⭕ Haralick.IMC1.Range: float

    第一信息测度相关性特征的平均值和范围，计算公式如下：

    𝐼𝑀𝐶1=𝐻𝑋𝑌−𝐻𝑋𝑌1/max(𝐻𝑋,𝐻𝑌), 其中𝐻𝑋𝑌, 𝐻𝑋𝑌1, 𝐻𝑋, 和𝐻𝑌 的计算依赖于𝑝𝑥(𝑖), 𝑝𝑦(𝑗)

86. ⭕ Haralick.IMC2.Mean: float

87. ⭕ Haralick.IMC2.Range: float

    第二信息测度相关性特征的平均值和范围，计算公式如下：
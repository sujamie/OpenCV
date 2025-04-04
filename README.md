# OpenCV
<details>
<summary>
<h1>imread() 開啟圖片<h1>

</summary>

``` python
import cv2  
img = cv2.imread('lenna.jpg')   # 開啟圖片，預設使用 cv2.IMREAD_COLOR 模式
cv2.imshow('oxxostudio', img)  # 使用名為 oxxostudio 的視窗開啟圖片
cv2.waitKey(0)                 # 按下任意鍵停止
cv2.destroyAllWindows()        # 結束所有圖片視窗
```
<h1>色彩模式數字對照表<h1>

<H6><table><H6>
  <tr>
    <td>數字</td>
    <td>模式</td>
    <td>說明</td>
  </tr>
  <tr>
    <td>1</td>
    <td>cv2.IMREAD_UNCHANGED</td>
    <td>原本的圖像（ 如果圖像有 alpha 通道則會包含 )</td>
  </tr>
  <tr>
    <td>2</td>
    <td>cv2.IMREAD_GRAYSCALE</td>
    <td>灰階圖像</td>
  </tr>
  <tr>
    <td>3</td>
    <td>cv2.IMREAD_COLOR</td>
    <td>BGR彩色圖像</td>
  </tr>
  <tr>
    <td>4</td>
    <td>cv2.IMREAD_ANYDEPTH</td>
    <td>具有對應的深度時返回 16/32 位元圖像，否則將其轉換為 8 位元圖像</td>
  </tr>
  <tr>
    <td>5</td>
    <td>cv2.IMREAD_ANYCOLOR</td>
    <td>以任何可能的顏色格式讀取圖像</td>
  </tr>
  <tr>
    <td>6</td>
    <td>cv2.IMREAD_LOAD_GDAL</td>
    <td>使用 gdal 驅動程式加載圖像</td>
  </tr>
  <tr>
    <td>7</td>
    <td>cv2.IMREAD_REDUCED_GRAYSCALE_2</td>
    <td>灰階圖像，圖像尺寸減小 1/2</td>
  </tr>
  <tr>
    <td>8</td>
    <td>cv2.IMREAD_REDUCED_COLOR_2</td>
    <td>BGR 彩色圖像，圖像尺寸減小 1/2</td>
  </tr>
  <tr>
    <td>9</td>
    <td>cv2.IMREAD_REDUCED_GRAYSCALE_4</td>
    <td>灰階圖像，圖像尺寸縮小 1/4</td>
  </tr>
  <tr>
    <td>10</td>
    <td>cv2.IMREAD_REDUCED_COLOR_4</td>
    <td>BGR 彩色圖像，圖像尺寸減小 1/4</td>
  </tr>
  <tr>
    <td>11</td>
    <td>cv2.IMREAD_REDUCED_GRAYSCALE_8</td>
    <td>灰階圖像，圖像尺寸縮小 1/8</td>
  </tr>
  <tr>
    <td>12</td>
    <td>cv2.IMREAD_REDUCED_COLOR_8</td>
    <td>灰階圖像，圖像尺寸縮小 1/8</td>
  </tr>
  <tr>
    <td>13</td>
    <td>cv2.IMREAD_IGNORE_ORIENTATION</td>
    <td>不要根據 EXIF 資訊的方向標誌旋轉圖像</td>
  </tr>
</table>
不同模式  
  
``` python
import cv2
img = cv2.imread('lenna.jpg', cv2.IMREAD_GRAYSCALE)  # 使用 cv2.IMREAD_GRAYSCALE 模式
# img = cv2.imread('meme.jpg', 2) # 也可使用數字代表模式
cv2.imshow('oxxostudio', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
``` 


  
</details>

<details>
<summary>
<h1>imwrite() 寫入並儲存圖片 <h1>

</summary>

``` python
import cv2
img = cv2.imread('lenna.jpg', cv2.IMREAD_GRAYSCALE)   # 以灰階模式開啟圖片
cv2.imwrite('oxxostudio_2.jpg', img, [cv2.IMWRITE_JPEG_QUALITY, 80])  # 存成 jpg
cv2.imwrite('oxxostudio_3.png', img)  # 存成 png
```

</details>

<details>
<summary>
<h1>VideoCapture() 讀取攝影鏡頭、開啟影片<h1>
  

</summary>
cap = cv2.VideoCapture(0)         # 讀取攝影鏡頭
  
ap = cv2.VideoCapture('影片路徑') # 讀取電腦中的影片

``` python
import cv2
cap = cv2.VideoCapture(0)
if not cap.isOpened():
    print("Cannot open camera")
    exit()
while True:
    ret, frame = cap.read()             # 讀取影片的每一幀
    if not ret:
        print("Cannot receive frame")   # 如果讀取錯誤，印出訊息
        break
    cv2.imshow('oxxostudio', frame)     # 如果讀取成功，顯示該幀的畫面
    if cv2.waitKey(1) == ord('q'):      # 每一毫秒更新一次，直到按下 q 結束
        break
cap.release()                           # 所有作業都完成後，釋放資源
cv2.destroyAllWindows()                 # 結束所有視窗
```

讀取cctv
``` python
import cv2
cap = cv2.VideoCapture('https://cctvn.freeway.gov.tw/abs2mjpg/bmjpg?camera=15771')

if not cap.isOpened():
    print("Cannot open camera")
    exit()
while True:
    ret, frame = cap.read()             # 讀取影片的每一幀
    if not ret:
        print("Cannot receive frame")   # 如果讀取錯誤，印出訊息
        # 出現錯誤就再讀取一次，避免程式到此處就停止
        cap = cv2.VideoCapture('https://cctvn.freeway.gov.tw/abs2mjpg/bmjpg?camera=15771')
        continue
    cv2.imshow('oxxostudio', frame)     # 如果讀取成功，顯示該幀的畫面
    if cv2.waitKey(1) == ord('q'):      # 每一毫秒更新一次，直到按下 q 結束
        break
cap.release()                           # 所有作業都完成後，釋放資源
cv2.destroyAllWindows()                 # 結束所有視窗
``` 
</details>

<details>
<summary>
<h1>flip() 翻轉影像<h1>

</summary>

```python
import cv2
from matplotlib import pyplot as plt
import matplotlib.image as img

img = cv2.imread('lenna.jpg')   # 開啟圖片
im2 = img[:,:,::-1] # OpenCV 讀取的圖片是 BGR 順序，轉換成 RGB 順序
output_0 = cv2.flip(im2, 0)    # 上下翻轉
output_1 = cv2.flip(im2, 1)    # 左右翻轉
output_2 = cv2.flip(im2, -1)   # 上下左右翻轉
cv2.imwrite('lenna0.jpg', output_0)
cv2.imwrite('lenna1.jpg', output_1)
cv2.imwrite('lenna2.jpg', output_2)

plt.figure(figsize=(8,8))

plt.subplot(221)
plt.imshow(im2)               # 顯示原圖
plt.axis('off')     #不顯示座標尺寸

plt.subplot(222)
plt.imshow(output_0)
plt.axis('off')     #不顯示座標尺寸

plt.subplot(223)
plt.imshow(output_1)
plt.axis('off')     #不顯示座標尺寸

plt.subplot(224)
plt.imshow(output_2)
plt.axis('off')     #不顯示座標尺寸

plt.show()
```
>![](https://github.com/sujamie/OpenCV/blob/main/flip.png?raw=true) 

</details>

<details>
<summary>
<h1>rotate() 旋轉影像 <h1>  
  
</summary>
rotate() 方法可以設定逆時針旋轉 90 度、順時針旋轉 90 度，以及旋轉 180 度。  

```python
import cv2
from matplotlib import pyplot as plt
import matplotlib.image as img


img = cv2.imread('lenna.jpg')   # 開啟圖片
im2 = img[:,:,::-1] # OpenCV 讀取的圖片是 BGR 順序，轉換成 RGB 順序
output_ROTATE_90_CLOCKWISE = cv2.rotate(im2, cv2.ROTATE_90_CLOCKWISE)
output_ROTATE_90_COUNTERCLOCKWISE = cv2.rotate(im2, cv2.ROTATE_90_COUNTERCLOCKWISE)
output_ROTATE_180 = cv2.rotate(im2, cv2.ROTATE_180)
cv2.imwrite('output_1.jpg', output_ROTATE_90_CLOCKWISE)
cv2.imwrite('output_2.jpg', output_ROTATE_90_COUNTERCLOCKWISE)
cv2.imwrite('output_3.jpg', output_ROTATE_180)

output_0 = cv2.imread('output_1.jpg')
output_1 = cv2.imread('output_2.jpg')
output_2 = cv2.imread('output_3.jpg')

plt.figure(figsize=(8,8))

plt.subplot(221)
plt.imshow(im2)               # 顯示原圖
plt.axis('off')     #不顯示座標尺寸

plt.subplot(222)
plt.imshow(output_0)
plt.axis('off')     #不顯示座標尺寸

plt.subplot(223)
plt.imshow(output_1)
plt.axis('off')     #不顯示座標尺寸

plt.subplot(224)
plt.imshow(output_2)
plt.axis('off')     #不顯示座標尺寸

plt.show()
```
>![](https://github.com/sujamie/OpenCV/blob/main/rotate.png)

</details>

<details>
<summary>
<h1>影像模糊化<h1>  
  
</summary>
  <details>
  <summary>
  <h1>blur() 平均模糊<h1>  
  </summary>
    
  cv2.blur(img, ksize)  
  
  >img 來源影像
  
  >ksize 指定區域單位
  ```python
  import cv2
  from matplotlib import pyplot as plt
  img = cv2.imread('lenna.jpg')
  im2 = img[:,:,::-1] # OpenCV 讀取的圖片是 BGR 順序，轉換成 RGB 順序
  outputb1 = cv2.blur(im2, (5, 5))     # 指定區域單位為 (5, 5)
  outputb2 = cv2.blur(im2, (25, 25))   # 指定區域單位為 (25, 25)

  plt.figure(figsize=(8,8))

  plt.subplot(2,2,1)
  plt.imshow(im2)              
  plt.axis('off')     #不顯示座標尺寸

  plt.subplot(2,2,2)
  plt.imshow(outputb1)              
  plt.axis('off')     #不顯示座標尺寸

  plt.subplot(2,2,3)
  plt.imshow(outputb2)
  plt.axis('off')     #不顯示座標尺寸
  ```
  >![](https://github.com/sujamie/OpenCV/blob/main/blur.png)
  
  </details>

  <details>
  <summary>
  <h1>GaussianBlur() 高斯模糊<h1>

  </summary>
  
  cv2.GaussianBlur(img, ksize, sigmaX, sigmaY)  
  
  >img 來源影像
  
  >ksize 指定區域單位 ( 必須是大於 1 的奇數 )

  >sigmaX X 方向標準差，預設 0，sigmaY Y 方向標準差，預設 0

  ```python
  import cv2
  from matplotlib import pyplot as plt

  img = cv2.imread('lenna.jpg')
  im2 = img[:,:,::-1] # OpenCV 讀取的圖片是 BGR 順序，轉換成 RGB 順序
  outputg1 = cv2.GaussianBlur(im2, (5, 5), 0)   # 指定區域單位為 (5, 5)
  outputg2 = cv2.GaussianBlur(im2, (25, 25), 0) # 指定區域單位為 (25, 25)
  plt.figure(figsize=(8,8))

  plt.subplot(2,2,1)
  plt.imshow(im2)              
  plt.axis('off')     #不顯示座標尺寸

  plt.subplot(2,2,2)
  plt.imshow(outputg1)              
  plt.axis('off')     #不顯示座標尺寸

  plt.subplot(2,2,3)
  plt.imshow(outputg2)
  plt.axis('off')     #不顯示座標尺寸
  ```

  >![](https://github.com/sujamie/OpenCV/blob/main/GaussianBlur.png)
  </details>

  <details>
  <summary>
  <h1>medianBlur() 中值模糊<h1>

  </summary>
  cv2.medianBlur(img, ksize)  
  
  >img 來源影像
  
  >ksize 模糊程度 ( 必須是大於 1 的奇數 )

  ```python
  import cv2
  from matplotlib import pyplot as plt
  img = cv2.imread('lenna.jpg')
  im2 = img[:,:,::-1] # OpenCV 讀取的圖片是 BGR 順序，轉換成 RGB 順序
  outputm1 = cv2.medianBlur(im2, 5)   # 模糊程度為 5
  outputm2 = cv2.medianBlur(im2, 25)  # 模糊程度為 25

  plt.figure(figsize=(8,8))

  plt.subplot(2,2,1)
  plt.imshow(im2)              
  plt.axis('off')     #不顯示座標尺寸

  plt.subplot(2,2,2)
  plt.imshow(outputm1)              
  plt.axis('off')     #不顯示座標尺寸

  plt.subplot(2,2,3)
  plt.imshow(outputm2)
  plt.axis('off')     #不顯示座標尺寸
  ```
  >![](https://github.com/sujamie/OpenCV/blob/main/medianBlur.png)
  
  </details>

  <details>
  <summary>
  <h1>bilateralFilter() 雙邊模糊<h1>

  </summary>

  cv2.bilateralFilter(img, d, sigmaColor, sigmaSpace)  
  
  >img 來源影像

  >d 相鄰像素的直徑，預設使用 5，數值越大運算的速度越慢

  >sigmaColor 相鄰像素的顏色混合，數值越大，會混合更多區域的顏色，並產生更大區塊的同一種顏色

  >sigmaSpace 會影響像素的區域，數值越大，影響的範圍就越大，影響的像素就越多

  ```python
  import cv2
  from matplotlib import pyplot as plt
  img = cv2.imread('lenna.jpg')
  im2 = img[:,:,::-1] # OpenCV 讀取的圖片是 BGR 順序，轉換成 RGB 順序
  
  outputbi1 = cv2.bilateralFilter(im2, 50, 0, 0)
  outputbi2 = cv2.bilateralFilter(im2, 50, 50, 100)
  outputbi3 = cv2.bilateralFilter(im2, 50, 100, 1000)
  
  plt.figure(figsize=(8,8))
  
  plt.subplot(2,2,1)
  plt.imshow(im2)              
  plt.axis('off')     #不顯示座標尺寸
  
  plt.subplot(2,2,2)
  plt.imshow(outputbi1)              
  plt.axis('off')     #不顯示座標尺寸
  
  plt.subplot(2,2,3)
  plt.imshow(outputbi2)
  plt.axis('off')     #不顯示座標尺寸
  
  plt.subplot(2,2,4)
  plt.imshow(outputbi3)
  plt.axis('off')     #不顯示座標尺寸
  ```
  >![](https://github.com/sujamie/OpenCV/blob/main/bilateralFilter.png)

  </details>
  
</details>

<details>
<summary>
<h1>二值化黑白影像<h1>

</summary>
二值化是一種影像處理技術，其目的在於將影像的灰度值轉換為二進制的 0 或 1，以便進行後續的分析或處理。  

二值化的原理是將影像的灰度值分為兩類，例如黑色和白色，而閾值 ( Threshold ) 則是用來決定哪些灰度值是黑色，哪些是白色。  

二值化會根據「閾值」( 類似臨界值 ) 進行轉換，例如某個像素的灰度值大於閾值，則轉換為黑色，如果這個像素的灰度小於閾值則轉換為白色，進而實現二值化的轉換效果，經過二值化轉換的圖片，通常只會剩下黑和白兩個值。  

許多影像辨識或影像處理的領域 ( 例如輪廓偵測、邊緣偵測...等 )，都會使用二值化影像進行運算，有些影像處理甚至會先將圖片二值化後，再進行後續的計算處理。  

</details>

<details>
<summary>
<h1>threshold() 產生黑白影像<h1>

</summary>  

ret, output = cv2.threshold(img, thresh, maxval, type)  

>ret 是否成功轉換，成功會顯示閾值

>output 轉換後的影像

>img 來源影像

>thresh 閾值，通常設定 127

>maxval 最大灰度，通常設定 255

>type 轉換方式


<H6><table><H6>
  <tr>
    <td>轉換方式</td>
    <td>說明</td>
    
  </tr>
  <tr>
    <td>cv2.THRESH_BINARY</td>
    <td>如果大於 127 就等於 255，反之等於 0</td>
  </tr>
  <tr>
    <td>cv2.THRESH_BINARY_INV</td>
    <td>如果大於 127 就等於 0，反之等於 255</td>
  </tr>
  <tr>
    <td>cv2.THRESH_TRUNC</td>
    <td>如果大於 127 就等於 127，反之數值不變</td>
  </tr>
  <tr>
    <td>cv2.THRESH_TOZERO</td>
    <td>如果大於 127 數值不變，反之數值等於 0</td>
  </tr>
  <tr>
    <td>cv2.THRESH_TOZERO_INV</td>
    <td>如果大於 127 等於 0，反之數值不變</td>
  </tr>
</table>

```python
import cv2
from matplotlib import pyplot as plt
img = cv2.imread('lenna.jpg')
#im2 = img[:,:,::-1] # OpenCV 讀取的圖片是 BGR 順序，轉換成 RGB 順序
img_gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY); # 轉換前，都先將圖片轉換成灰階色彩
ret, outputth1 = cv2.threshold(img_gray, 127, 255, cv2.THRESH_BINARY)     # 如果大於 127 就等於 255，反之等於 0。
ret, outputth2 = cv2.threshold(img_gray, 127, 255, cv2.THRESH_BINARY_INV) # 如果大於 127 就等於 0，反之等於 255。
ret, outputth3 = cv2.threshold(img_gray, 127, 255, cv2.THRESH_TRUNC)      # 如果大於 127 就等於 127，反之數值不變。
ret, outputth4 = cv2.threshold(img_gray, 127, 255, cv2.THRESH_TOZERO)     # 如果大於 127 數值不變，反之數值等於 0。
ret, outputth5 = cv2.threshold(img_gray, 127, 255, cv2.THRESH_TOZERO_INV) # 如果大於 127 等於 0，反之數值不變。

plt.figure(figsize=(8,8))

plt.subplot(3,2,1)
plt.imshow(img_gray, cmap='gray')              
plt.axis('off')     #不顯示座標尺寸

plt.subplot(3,2,2)
plt.imshow(outputth1, cmap='gray')              
plt.axis('off')     #不顯示座標尺寸

plt.subplot(3,2,3)
plt.imshow(outputth2, cmap='gray')
plt.axis('off')     #不顯示座標尺寸

plt.subplot(3,2,4)
plt.imshow(outputth3, cmap='gray')
plt.axis('off')     #不顯示座標尺寸

plt.subplot(3,2,5)
plt.imshow(outputth4, cmap='gray')
plt.axis('off')     #不顯示座標尺寸

plt.subplot(3,2,6)
plt.imshow(outputth5, cmap='gray')
plt.axis('off')     #不顯示座標尺寸
```

>![](https://github.com/sujamie/OpenCV/blob/main/threshold.png)

</details>

<details>
<summary>
<h1>adaptiveThreshold() 自適應二值化 <h1>

</summary>



cv2.adaptiveThreshold(img, maxValue, adaptiveMethod, thresholdType, blockSize, C)  

>img 來源影像

>maxValue 最大灰度，通常設定 255

>adaptiveMethod 自適應二值化計算方法

>thresholdType 二值化轉換方式

>blockSize 轉換區域大小，通常設定 11

>C 偏移量，通常設定 2

```python
import cv2
from matplotlib import pyplot as plt
img = cv2.imread('lenna.jpg')

img_gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY); # 轉換前，都先將圖片轉換成灰階色彩

ret, outputad1 = cv2.threshold(img_gray, 127, 255, cv2.THRESH_BINARY)
outputad2 = cv2.adaptiveThreshold(img_gray, 255, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, 11, 2)
outputad3 = cv2.adaptiveThreshold(img_gray, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C, cv2.THRESH_BINARY, 11, 2)

plt.figure(figsize=(8,8))

plt.subplot(2,2,1)
plt.imshow(img_gray, cmap='gray')              
plt.axis('off')     #不顯示座標尺寸

plt.subplot(2,2,2)
plt.imshow(outputad1, cmap='gray')              
plt.axis('off')     #不顯示座標尺寸

plt.subplot(2,2,3)
plt.imshow(outputad2, cmap='gray')
plt.axis('off')     #不顯示座標尺寸

plt.subplot(2,2,4)
plt.imshow(outputad3, cmap='gray')
plt.axis('off')     #不顯示座標尺寸
```

>![](https://github.com/sujamie/OpenCV/blob/main/adaptiveThreshold.png)

先模糊化後在二值化，可降低圖片雜訊

```python
import cv2
from matplotlib import pyplot as plt
img = cv2.imread('lenna.jpg')

img_gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY); # 轉換前，都先將圖片轉換成灰階色彩
img_gray2 = cv2.medianBlur(img_gray, 5);   # 模糊化
ret, outputad1 = cv2.threshold(img_gray2, 127, 255, cv2.THRESH_BINARY)
outputad2 = cv2.adaptiveThreshold(img_gray2, 255, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, 11, 2)
outputad3 = cv2.adaptiveThreshold(img_gray2, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C, cv2.THRESH_BINARY, 11, 2)

plt.figure(figsize=(8,8))

plt.subplot(2,2,1)
plt.imshow(img_gray, cmap='gray')              
plt.axis('off')     #不顯示座標尺寸

plt.subplot(2,2,2)
plt.imshow(outputad1, cmap='gray')              
plt.axis('off')     #不顯示座標尺寸

plt.subplot(2,2,3)
plt.imshow(outputad2, cmap='gray')
plt.axis('off')     #不顯示座標尺寸

plt.subplot(2,2,4)
plt.imshow(outputad3, cmap='gray')
plt.axis('off')     #不顯示座標尺寸
```
>![](https://github.com/sujamie/OpenCV/blob/main/adaptiveThreshold2.png)

</details>

<details>
<summary>
<h1>影像的侵蝕與膨脹<h1>

</summary>
  <details>
  <summary>
  <h1>什麼是侵蝕 ( Erosion )？<h1>
  
  </summary>
  當空間中有兩個集合 ( A 集合和 B 集合 )，當 A 集合的部分空間被 B 集合所取代，則稱之為「侵蝕 ( Erosion )」，通常進行侵蝕後的影像，黑色區域會擴張，白色區域會縮小。
  </details>

  <details>
  <summary>
  <h1>什麼是膨脹 ( Dilation )？<h1>
  
  </summary>
  當空間中有兩個集合 ( A 集合和 B 集合 )，當 A 集合的部分空間擴張到 B 集合，則稱之為「膨脹 ( Dilation )」，通常進行膨脹後的影像，白色區域會擴張，黑色區域會縮小。
  </details>
  
  <details>
  <summary>
  <h1>透過侵蝕與膨脹，去除影像中的雜訊<h1>
  
  </summary>
  kernel = cv2.getStructuringElement(shape, ksize)  
  
  >返回指定大小形狀的結構元素

  >shape 的內容：cv2.MORPH_RECT ( 矩形 )、cv2.MORPH_CROSS ( 十字交叉 )、cv2.MORPH_ELLIPSE ( 橢圓形 )

  >ksize 的格式：(x, y)

  >img = cv2.erode(img, kernel)   # 侵蝕

  >img = cv2.dilate(img, kernel)  # 擴張
  
```python
  import cv2
  from matplotlib import pyplot as plt
  img = cv2.imread('lenna.jpg')
  im2 = img[:,:,::-1] # OpenCV 讀取的圖片是 BGR 順序，轉換成 RGB 順序
  img1 = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
  kernel = cv2.getStructuringElement(cv2.MORPH_RECT, (11, 11))
  
  img2 = cv2.dilate(img1, kernel)    # 膨脹
  img3 = cv2.erode(img1, kernel)     # 侵蝕
  img4 = cv2.erode(img2, kernel)     # 膨脹侵蝕
  img5 = cv2.dilate(img3, kernel)     # 侵蝕膨脹
  
  plt.figure(figsize=(8,8))
  
  plt.subplot(3,2,1)
  plt.imshow(im2, cmap='gray')              
  plt.axis('off')     #不顯示座標尺寸
  
  plt.subplot(3,2,2)
  plt.imshow(img1, cmap='gray')              
  plt.axis('off')     #不顯示座標尺寸
  
  plt.subplot(3,2,3)
  plt.imshow(img2, cmap='gray')              
  plt.axis('off')     #不顯示座標尺寸
  
  plt.subplot(3,2,4)
  plt.imshow(img3, cmap='gray')              
  plt.axis('off')     #不顯示座標尺寸
  
  plt.subplot(3,2,5)
  plt.imshow(img4, cmap='gray')
  plt.axis('off')     #不顯示座標尺寸
  
  plt.subplot(3,2,6)
  plt.imshow(img5, cmap='gray')
  plt.axis('off')     #不顯示座標尺寸
  ```
  </details>
  >![](https://github.com/sujamie/OpenCV/blob/main/ED.png)
  

</details>

<details>
<summary>
<h1>imread() 開啟圖片<h1>

</summary>

</details>

<details>
<summary>
<h1>imread() 開啟圖片<h1>

</summary>

</details>

<details>
<summary>
<h1>imread() 開啟圖片<h1>

</summary>

</details>

<details>
<summary>
<h1>imread() 開啟圖片<h1>

</summary>

</details>

<details>
<summary>
<h1>imread() 開啟圖片<h1>

</summary>

</details>

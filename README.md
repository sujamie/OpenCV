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
<h1>imread() 開啟圖片<h2>

</summary>

</details>

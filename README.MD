# I’m Something of a Painter Myself
利用CycleGan將照片轉換成莫內風格
https://www.kaggle.com/code/huayee/monet-cyclegan/
![image](https://user-images.githubusercontent.com/103236841/164942976-f838ddf0-01b4-4e1f-9636-fd3d84d63629.png)

# CycleGan
https://junyanz.github.io/CycleGAN/
CycleGAN是一種無監督學習(Unsupervised learning)，不需要事先標記過的成對訓練範例，主要應用在影像對影像的變換。

CycleGan的想法是將X的影像轉成Y，再從Y的圖轉回X，轉回的還原圖跟原本給的X越像越好

* 兩個generator
  * 產生假X
  * 產生假Y
* 兩個discriminator
  * 分辨X/假X
  * 分辨Y/假Y

* 三個loss函數

  * discriminator loss(loss_DX、loss_DY)，有兩項(loss_D_real、loss_D_fake )，一項是真的X跟Y之間，以及假的X跟Y之間，discriminator學習分辨X與Y。

  * generator loss(loss_GX、loss_GY)，假X跟Y，generator學習如何讓discriminator認為假X跟假Y是真的。

  * cycle-consistency loss(loss_cycX、loss_cycY)，經過兩個generator產生的cyclic X)，跟最原本的真實資料X。

![image](https://user-images.githubusercontent.com/103236841/164939805-2ece1d65-5150-443b-a71f-19bb5332a149.png)

# 使用工具
* Python 3
* Tensorflow
* Numpy
* Pandas
* OpenCV
* Pillow
* Matplotlib
* TPU
# 流程
1. 讀取數據
2. 資料預處理(Preprocessing)
   * 增強資料(Augmentations)
   * 調整大小(Resize)
   * 重新縮放(Rescale to (0,1))
3. 構建模型(build the classifer model)
   * Genertor
   * Discriminator
4. 設定loss function
   * discriminator loss
   * generator loss
   * cycle-consistency loss
6. 訓練(Training)
7. 分析結果

# 增強資料(Augmentations)
隨機的對影像進行旋轉及切割，並將影像大小統一

# Model
## Genertor Model
* U-Net(Downsample & Upsample)
> 分成(Downsample)與上抽樣(Upsample)，
> 下抽樣會先對影像進行卷積和池化抓取輸入的影像特徵，
> 上抽樣則是將影像進行反卷積，再與上抽樣產生的特徵圖進行連接，
> 最後可以得到一個與輸入影像尺寸相同的結果。
![image](https://user-images.githubusercontent.com/103236841/164943392-406a865b-e3ef-493b-9e44-58eaedacbc36.png)
## Discriminator Model
使用CNN layers




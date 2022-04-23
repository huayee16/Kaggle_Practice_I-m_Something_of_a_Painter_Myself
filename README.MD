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

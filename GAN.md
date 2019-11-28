# GAN

- 评价指标
  - IS Inception score
    - 越大越好
    - clearer images
    - diversity
    - 是有一些问题的，natural image==a sharp distribution??
    - model collapse == uniform distributed over all categories?
  - FID score
- improve GAN
  - not-so-easy to train
  - do not to train a good D
    - D太好会出现梯度消失
    - D不好会出现不正确的梯度
    - JS散度
      - 不合适
      - 大多数情况下，Pdata和PG不重叠
        - 数据本身不重叠
        - 或者即使重叠，采样也并没有采到重叠
  - WGAN
  - WGAN-GP 直接对导数约束
  - Conditional GAN
  - infoGAN 输入分为c和z，z就是我想控制的那一部分 有一个calssifer，把c还原出来。
  - stackGAN 输入是一句话
  - cycleGAN 输入是一张图 encoder-decoder
  - starGAN multi-domian image-to-image 一堆图片到一堆图片
  - 架构变化
    - DCGAN
    - self-attention GAN
    - bigGAN
    - unsupervised word translation
    - NMT(neural mechine translation) GAN来做。D的作用就是用来判断是人翻译的还是NMT
    - ELECTRA
# Robust Machine Learning

- is machine learning model reliable enough？
  - 实际生活中有boundary case
  - 现实生活中有faked examples
- 通过attack
- standard trained image model is sensitive to noise perturbations
  - noise   --universality
  - harmonic perturbation（非常光滑的一个灰度图片） 
  - spatial transformation
  - camera stickers
- 还有很多其他领域
  - TEXT:ICLR 2018 MIT
  - 换了一个字，翻译出来的东西就完全不同了。
  - 语音audio ICML 2019
  - video：characterizing Attacks on DRL,berkeley
  - graph：加个边，减个边就会出错。

- 算法
  - attack and defense
  - Adversarial Attack
  - problems
  - robustness verification
    - ICML 2019出现第一个工作
- 理论
  - Adversarial robust generalization is harder 后来被NIPS接受
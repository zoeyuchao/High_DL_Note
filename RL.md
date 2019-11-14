# 高等机器学习--RL笔记

- POMDP(partial observation MDP，观测不等于状态，比如扑克牌)
- MDP($S,A,P,R,\gamma$)
- 状态到动作：
  - 确定：$a=\pi(s)$
  - 随机：$p=\pi(s, a)$
- action-value function:

$$q_{\pi}(s, a)=E[r_{t+1} + \gamma r_{t+2} + ...|s_t = s, a_t = a]$$

  - 引出bellman方程

- 最优value 方程 就是加max
  - bellman最优方程 加max

- planning 环境已知，RL环境未知（narrow的说法）全都是RL（广义的说法）

- state-value function

  $v_\pi=r_\pi+\gamma P_\pi v_\pi$

- action-state function

  $q_\pi (s, a)=E_\pi[r_{t+1} + \gamma q_\pi(s',a')|(s,a)]$

- planning
  - policy evaluation
  - 给定一个确切的model和一个fixed policy
- Bellman最优方程
  - optimal value function
    - action-value
    - state-value
  - bellman optimallity equation
    - $v*$有max
    - $q*$没有max

- learning in MDPs
  - trajectory （一系列的o，a，r）
  - model-based（把p和r学出来）
  - model-free

- Monte-Carlo Policy Evalution
  - 均值V=S/N逼近期望，N->无穷
  - incremental MC
    - 不平稳的情况 换$\alpha$,超过1\N,表示我可能更在乎最近的值，不是平均都需要。
  - 局限性
    - 要等结束，会有问题
    - 均值逼近期望
- TD Policy Evaluation
  - 不需要等结束$r_{t+1}+\gamma v(s_{t+1})$
  - TD error，常见的都是TD(0),就是估计一步
  - TD(1)课件上有问题，应该是r$r_{t+1}+\gamma v(r_{t+1}) + \gamma v(s_{t+2})$
- Policy improvement
- Policy iteration
- 策略探索 exploration$\theta$-greedy
- MC Policy iteration 
  - $\theta$-greedy 有一定概率选到新的action
- summary to RL
- large scale RL
  - 之前都是look up table
  - 状态数特别多
  - 进入深度学习时代
- function approximation for RL
- Deep RL
  - 选择性介绍一些工作
  - model-free RL（policy & Q-learning）
  - model-based RL（learn the model & given the model）
  - 讲DQN & distributional RL（SOTA on Atari games）
  - Nature 2015 ：human level control
  - Atari 用卷积+FC变18维向量。
  - 假设max那步跟$\theta$无关，不求导。
  - 目标变得太快，学不出来
  - DQN 
    - 有replay buffer，
    - DQN 会fix一下target，过一会再换，用老一点的target，避免目标总换学不出来。
    - DQN：reward clip to [-1,1]，先做norm
    - 问题：
      - 看最近的4帧，有的情况不大够，可以引入LSTM、attention
      - 根据TD error来多看几眼这些数据，因为error很大，说明这部分数据学的不好，所以 prioritied experience replay
  - Distributional RL
    - 高斯分布可能出现-10 和 10 ，不是0
    - 怎么来刻画分布？
    - C51
      - 输出不再是一个值，而是一个向量，是一个分布
      - C51就是50个向量
      - 为啥好？都是直观解释，因为考虑的信息更多了。
    - QR-DQN
    - IQN
  - value-based 和policy-based
  - policy optimization【从这里开始重新学习一下】
    - MC policy gradient
    - 有一些问题：首先是无偏的，但是large variance
    - reward-to-go
    - expected grad-log-prob lemma
    - baseline
    - actor critic
    - advantage

- A3C vs A2C
  - 3这个会有不同步的问题。个别agent可能会跑的很快
  - 2不会有这个问题。
- off-policy
  - 前面讲的都是on-policy
  - $\beta$也是一个policy
  - importance weight
- model-based DRL 
  - Atari会失败
  - 但是机器人control会成功，十几维的向量，物理规律。
- challenges and frontiers
  - imperfect-information games & multi-agent games
  - 有一些paper，见课件。
  - robustness-random seeds，看运气，多次实验看平均值。很难说哪个方法就是好的，换个环境就不一样了。
  - 但是跟DL对比，resnet就一直挺好的。
  - sample efficiency。需要太多样本才能学得好。Rainbow
  - safe RL
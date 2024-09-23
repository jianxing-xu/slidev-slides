---
layout: center
highlighter: shiki
css: unocss
colorSchema: dark
transition: fade-out
mdc: true
glowSeed: 4
title: Docker
remoteAssets: true
---

<img src="/docker.logo.svg" width="300" />

<!--
开场互动：

1. 为什么要分享
2. 上台的机会
3. 未来的机会，隐形的机会（等待trigger的伏笔）
4. 费曼学习法
    - 输出倒逼输入
    - 以教促学
5. 为什么是Docker
    - 实际情况
    - 探究
 -->

---
layout: intro
class: pl-30
glowSeed: 14
---

# 一句话概括

<v-click>
  Docker 是一种开源的 轻量化 容器化平台，旨在简化应用的部署和运行，可实现应用的快速部署、隔离运行和高效迁移
</v-click>

<!--容器平台概念，web应用部署相关内容，简化流程，隔离性，应用迁移相关-->

---
glowSeed: 14
---

# 虚拟化 vs 容器化

<div grid="~ cols-2 gap-10" mt-10 mb-4>
  <img v-click src="https://www.docker.com/wp-content/uploads/2021/11/container-vm-whatcontainer_2.png" />
  <img v-click src="https://www.docker.com/wp-content/uploads/2021/11/docker-containerized-appliction-blue-border_2.png" />
</div>
<v-clicks>

> 容器完全跨平台，通过 Docker Engin 驱动

</v-clicks>

<!--
传统虚拟机： 包含独立的硬件、系统组件、网络等资源、占用资源大，启动慢，单元之间完全隔离
容器化： 共享宿主机计算资源，仅包含必须得应用组件，进行环境隔离，系统资源层共享，占用小大概几十m-几百m
-->

---
glowSeed: 24
layout: intro
---

<h1 class="transition duration-500" :class="$clicks === 0 ? 'translate-y-140px' : 'translate-y-0'">为什么使用</h1>

<div grid="~ cols-2 gap-10" mt10>
<div v-click>

  ### 环境
  生产 与 本地 完全一致，不受操作系统影响，避免环境差异导致的问题
</div>
<div v-click>

  ### 部署/可用性/可观测性
  通过预先编写好的 Dockerfile 构建成镜像包，直接启动，减少手动配置环境
</div>
<div v-click>

  ### 依赖隔离
  Docker 容器间环境完全隔离，互不影响，不同容器可以独立不同的依赖版本 e.g
</div>
<div v-click>

  ### 快速扩展与缩减
  通过与集群平台配合，实现根据负载情况快速启动容器实现集群
</div>
</div>
<!--
1. 开发： 只要本地能跑，生成就一定能跑，还能跨平台
2. 部署： 自动重启，资源观测，减少环境配置
3. 依赖隔离：e.g
 -->

---
glowSeed: 24
title: 例子
---

<h1 class="transition duration-500">{{ $clicks <= 6 ? '一个例子' : '快速回滚' }}</h1>

<div v-show="$clicks <= 6">

  - 部署一个app Node@16

  <div grid="~ cols-2 gap-10">
    <div v-click>
      <li>1. 打包应用</li>
      <li>2. 装环境，还必须得和本地一致或保持兼容</li>
      <li>3. 配置环境e.g</li>
      <li>4. 上传可运行文件</li>
      <li>5. 启动应用</li>
    </div>
    <div v-click>
      <li>使用Docker</li>
      <li>1. 编写 Dockerfile</li>
      <li>2. 执行 docker build</li>
      <li>3. 执行 docker push/pull</li>
      <li>4. 执行 docker run</li>
    </div>
  </div>

  <div my-4 />

  <v-click>

  - 部署第二个app<div border inline-block px2>Node@21</div>
  </v-click>

  <div grid="~ cols-2 gap-10">
    <div v-click>
      <li>？？？？？？？</li>
      <li>强行降低版本？</li>
    </div>
    <div v-click>
      <li>使用Docker</li>
      <li>1. 修改 Dockerfile 指定 node@21</li>
      <li>其他不变</li>
    </div>
  </div>

  <v-click>

  > 这还只是node上的差异，复杂应用中会有更多繁琐的配置
  </v-click>

</div>

<div v-click>在一次发布后生产出现 <b text-red>P(-9999) BUG</b> 问题，需要立刻回滚</div>

<h1 v-click text-center mt10>Dcoker中怎么做？</h1>

<v-click>

```bash
  docker stop app

  # 然后
  docker run app:[preTag]

  # 结束了
```

</v-click>

<!--
1. 区别 传统部署方案与docker，装环境，配置环境，本地运行没问题，线上有问题，差异，

2. 后期维护问题，依赖更新，系统版本更新等

3. 负载重启

4. docker: 通过Dockerfile，之后的所有操作可完全自动化

5. tag快照，可快速恢复
-->

---
glowSeed: 34
title: docker 核心概念
layout: two-cols
---

# Docker 核心组件

<v-clicks>

- Dcoker Engine{style="font-size: 24px; margin-top: 20px;"}
  + Server: Daemon （守护进程）
  + CLI: Command Line
  + Rest API

- Dcoker Images（镜像）{style="font-size: 24px; margin-top: 20px;"}
  + 包含文件系统和运行环境的一个包

- Dcoker Containers（容器）{style="font-size: 24px; margin-top: 20px;"}
  + 是镜像运行后的实例，一个隔离的运行环境
  + 可以在任何支持Docker的平台上运行

</v-clicks>

::right::

<v-clicks>

- Docker Registry（镜像仓库）{style="font-size: 24px; margin-top: 20px;"}
  + 类似于 npm源，用于存储和分发Docker镜像
  + 公共的有 docker hub
  + 可以搭建私有镜像源

+ Docker Compose
+ Docker Volumes
+ Docker Networking
+ Docker Swarm
+ ...
</v-clicks>

---
glowSeed: 34
title: 架构图
layout: center
---

# 架构图

## ![](https://docs.docker.com/get-started/images/docker-architecture.webp)

<!--
1. 在 client 端执行命令后的交互流程
2. Daemon
-->

---
glowSeed: 34
title: 上手体验
---

# 上手体验

## 安装

```bash
# ubuntu case
apt-get install docker.io
```

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

# Docker{style="font-size: 70px"}

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

  ### 开发环境
  依托于统一的 Docker 容器标准，可以让生产环境与本地环境完全一致，不受操作系统影响，避免环境差异导致的问题
</div>
<div v-click>

  ### 部署流程
  通过预先编写好的 dockerfile 构建成镜像包，直接启动镜像
</div>
<div v-click>

  ### 依赖隔离
  Docker 容器间环境完全隔离，互不影响，不同容器可以独立不同的依赖版本 e.g
</div>
<div v-click>

  ### 快速扩展与缩减
  通过与k8s配合，实现根据负载情况快速启动容器实现集群
</div>
</div>
<!-- 依赖隔离的例子 -->

---
glowSeed: 24
title: 例子
---

<h1 class="transition duration-500">一个例子</h1>

- 部署第一个app Node@16

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
    <li>死路</li>
    <li>强行降低版本？</li>
  </div>
  <div v-click>
    <li>使用Docker</li>
    <li>1. 编写 Dockerfile 指定 node@21</li>
    <li>2. 执行 docker build</li>
    <li>3. 执行 docker push/pull</li>
    <li>4. 执行 docker run</li>
  </div>
</div>

<v-click>

> 这还只是node上的差异，复杂应用中会有更多繁琐的配置
</v-click>

<!--
区别 传统部署方案与docker，装环境，配置环境，本地运行没问题，线上有问题，差异，

后期维护问题，依赖更新，系统版本更新等

负载重启

docker: 通过dockerfile，之后的所有操作可完全自动化
-->

---
glowSeed: 34
title: docker 核心概念
---

# Dcoekr 核心组件

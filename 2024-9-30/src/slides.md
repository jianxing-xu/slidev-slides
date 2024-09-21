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
---

# 为什么使用

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

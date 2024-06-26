---
title: Fruchterman
order: 8
---

Fruchterman 布局是一种力导布局。算法原文： <a href='http://www.mathe2.uni-bayreuth.de/axel/papers/reingold:graph_drawing_by_force_directed_placement.pdf' target='_blank'>Graph Drawing by Force-directed Placement</a>

<img src='https://gw.alipayobjects.com/mdn/rms_f8c6a0/afts/img/A*jK3ITYqVJnQAAAAAAAAAAABkARQnAQ' width=600 alt='img'/>

```javascript
const graph = new G6.Graph({
  container: 'mountNode',
  width: 1000,
  height: 600,
  layout: {
    type: 'fruchterman',
    center: [200, 200], // 可选，默认为图的中心
    gravity: 20, // 可选
    speed: 2, // 可选
    clustering: true, // 可选
    clusterGravity: 30, // 可选
    maxIteration: 2000, // 可选，迭代次数
    workerEnabled: true, // 可选，开启 web-worker
    gpuEnabled: true, // 可选，开启 GPU 并行计算，G6 4.0 支持
  },
});
```

当你希望固定某个节点的位置，不受力的影响时，可以在该节点数据中配置 `fx` 与 `fy` 作为固定的坐标。[Fruchterman 布局固定被拖拽节点位置的 Demo](/zh/examples/net/fruchtermanLayout#fructhermanFix)。

## layoutCfg.center

**类型**： Array<br />**示例**：[ 0, 0 ]<br />**默认值**：图的中心<br />**是否必须**：false<br />**说明**：布局的中心

## layoutCfg.preset

_自 G6 v4.7.0 起支持。_

**类型**: 

```javascript
{
  type: string; // 布局名称，可以是 random、concentric、grid、circular、radial、dagre 等静态布局
  [key: string]: unkown; // 对应布局的配置项
}
```
<br />

**默认值**: undefined<br />**是否必须**: false<br />**说明**: 力导向布局的初始化布局，将先执行 preset 指定的布局，再进行力导向计算。由于力导向布局的结果非常依赖节点的初始位置，配置 preset 的可以给力导向布局一个好的初始化，让力导向算法更快收敛、效果更好。默认情况下，力导向的初始化为格子布局（grid）的结果

## layoutCfg.maxIteration

**类型**： Number<br />**默认值**：1000<br />**是否必须**：false<br />**说明**：最大迭代次数

## layoutCfg.gravity

**类型**： Number<br />**默认值**：10<br />**是否必须**：false<br />**说明**：重力的大小，影响布局的紧凑程度

## layoutCfg.speed

**类型**： Number<br />**默认值**：1<br />**是否必须**：false<br />**说明**：每次迭代节点移动的速度。速度太快可能会导致强烈震荡

## layoutCfg.clustering

**类型**： Boolean<br />**默认值**：false<br />**是否必须**：false<br />**说明**：是否按照聚类布局

## layoutCfg.clusterGravity

**类型**： Number<br />**默认值**：10<br />**是否必须**：false<br />**说明**：聚类内部的重力大小，影响聚类的紧凑程度，在 `clustering` 为 `true` 时生效

## layoutCfg.workerEnabled

**类型**: Boolean<br />**默认值**: false<br />**是否必须**: false<br />**说明**: 是否启用 web-worker 以防布局计算时间过长阻塞页面交互。
<span style="background-color: rgb(251, 233, 231); color: rgb(139, 53, 56)"><strong>⚠️ 注意:</strong></span> `workerEnabled: true` 时，不支持所有函数类型的参数。

## layoutCfg.gpuEnabled

**类型**: Boolean<br />**默认值**: false<br />**是否必须**: false<br />**说明**: 是否启用 GPU 并行计算。若用户的机器或浏览器不支持 GPU 计算，将会自动降级为 CPU 计算。自 G6 4.0 起支持，性能提升概览： <img src='https://gw.alipayobjects.com/mdn/rms_f8c6a0/afts/img/A*4ogTQKrWhIkAAAAAAAAAAAAAARQnAQ' width='80%' alt=''/>

<template>
    <div class="aboutView">
        <div class="about" id="container"></div>
    </div>
</template>

<script setup>
import { Graph } from '@antv/x6'
import { onMounted } from 'vue'

const data = {
  //移动画布
  panning: true,
  // 节点
  nodes: [
    {
      id: 'node1', // String，可选，节点的唯一标识
      x: 40,       // Number，必选，节点位置的 x 值
      y: 40,       // Number，必选，节点位置的 y 值
      width: 80,   // Number，可选，节点大小的 width 值
      height: 40,  // Number，可选，节点大小的 height 值
      label: 'hello', // String，节点标签
    },
    {
      id: 'node2', // String，节点的唯一标识
      x: 160,      // Number，必选，节点位置的 x 值
      y: 180,      // Number，必选，节点位置的 y 值
      width: 80,   // Number，可选，节点大小的 width 值
      height: 40,  // Number，可选，节点大小的 height 值
      label: 'world', // String，节点标签
    },
    {
      id: 'node3', // String，可选，节点的唯一标识
      x: 80,       // Number，必选，节点位置的 x 值
      y: 80,       // Number，必选，节点位置的 y 值
      width: 80,   // Number，可选，节点大小的 width 值
      height: 40,  // Number，可选，节点大小的 height 值
      label: '猪猪侠', // String，节点标签
    },
  ],
  // 边
  edges: [
    {
      source: 'node1', // String，必须，起始节点 id
      target: 'node2', // String，必须，目标节点 id
      // eslint-disable-next-line no-dupe-keys
      //target: 'node3', // String，必须，目标节点 id
    },
  ],
  container: document.getElementById('container'),
  width: 800,
  height: 600,
};

const init = () => {
  new Graph({
    //网格
    grid: {
      size: 20,
      visible: true,
      type: 'mesh', // 'dot' | 'fixedDot' | 'mesh'
      args: {
        color: '#000', // 网格线/点颜色
        thickness: 1,     // 网格线宽度/网格点大小
      },
    },
    //支持画布的平移拖拽
    panning: true,
    modifiers: 'shift',
    //看到画布
    scroller: {
      enabled: true,
      pannable: true,
      pageVisible: true,
      pageBreak: false,
    },
    mousewheel: {
      enabled: true,
      modifiers: ['ctrl', 'meta'],
    },
    container: document.getElementById('container'),
    width: 800,
    height: 600
  }).fromJSON(data)
}

onMounted(() => {
  init()
})
</script>

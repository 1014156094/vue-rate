<h3 align="center" style="margin: 30px 0 35px;">支持双击评半星的 Vue 评分组件</h3>

---

## 效果演示
![image](https://github.com/1014156094/vue-audio-player/blob/master/public/1.gif?raw=true)

## 注意事项
组件CSS使用 `less` 预编译语言

## 使用
```
<template>
  <div>
    <rate v-model="rateValue" />
  </div>
</template>

<script>
import Rate from 'vue-rate'

export default {
  components: {
    Rate
  },
  data() {
    return {
      rateValue: 1.5
    }
  }
}
</script>
```

## Props
| 参数 | 说明 | 类型 | 默认值 |
| - | - | - | - |
| v-model | 当前分值 | `Number` | - |
| count | 星星个数 | `Number` | `5` |
| disabled | 	是否禁用评分 | `Boolean` | `false` |

## Event
| 事件 | 说明 | 回调参数 |
| - | - | - |
| change | 	当前分值变化时触发的事件 | 当前分值 |

## 最后
欢迎Star，使用过程中发现任何问题都可以提 Issue，也非常欢迎提PR

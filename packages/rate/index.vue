<template>
  <section class="star-section">
    <template v-for="(item, index) in count">
      <img :key="item"
           v-if="index === selectIndex && isHalf"
           src="./icon-star-highlight-half.png"
           class="star"
           @click="onHighlightHalf(item, index)">
      <img :key="item"
           v-else-if="item <= selectValue"
           src="./icon-star-highlight.png"
           class="star"
           @click="onHighlight(item, index)">
      <img :key="item"
           v-else
           src="./icon-star.png"
           class="star"
           @click="onSelect(item, index)">
    </template>
  </section>
</template>

<script>
export default {
  name: 'Rate',
  model: {
    prop: 'value',
    event: 'change'
  },
  props: {
    // 当前分值
    value: {
      default: 0,
      type: Number
    },
    // 是否禁用评分
    disabled: {
      default: false,
      type: Boolean
    },
    // 星星数
    count: {
      default: 5,
      type: Number
    }
  },
  data () {
    return {
      isHalf: false, // 是否为半星
      selectIndex: null, // 当前选中的索引
      selectValue: this.value // 当前选中的值
    }
  },
  created () {
    // 有小数点
    if (String(this.value).indexOf('.') > -1) {
      this.isHalf = true
      this.selectIndex = Math.floor(this.value)
    }
  },
  watch: {
    value (newVal) {
      // 有小数点
      if (String(this.value).indexOf('.') > -1) {
        this.isHalf = true
        this.selectIndex = Math.floor(this.value)
      } else {
        this.isHalf = false
        this.selectIndex = this.value - 1
      }
    }
  },
  methods: {
    // 处理选中的高亮星星
    onHighlight (val, index) {
      if (this.disabled) {
        return
      }
      if (this.selectIndex !== index) {
        this.onSelect(val, index)
        return
      }
      this.selectValue -= 0.5
      this.$emit('change', this.selectValue)
    },
    // 处理选中的半亮星星
    onHighlightHalf (val, index) {
      if (this.disabled) {
        return
      }
      if (this.selectIndex !== index) {
        this.onSelect(val, index)
        return
      }
      this.selectValue += 0.5
      this.$emit('change', this.selectValue)
    },
    // 处理选择星星
    onSelect (val, index) {
      if (this.disabled) {
        return
      }
      this.selectValue = val
      this.$emit('change', this.selectValue)
    }
  }
}
</script>

<style lang="less" scoped>
.star-section {
  display: flex;
  align-items: center;
  justify-content: center;
  .star {
    width: 22px;
    height: 21px;
    margin: 0 2px;
  }
}
</style>

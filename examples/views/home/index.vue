<template>
  <div>
    <rate v-model="rateValue" />
  </div>
</template>

<script>
import Rate from '../../../packages/rate'

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

<style lang="less" scoped>
</style>

<template>
  <div class="app-container">
    <el-link type="primary">1. 双击编辑组件</el-link>
    <span v-for="item in list" :key="item.id">
      <dbl-edit :id="item.id" :value.sync="item.name" @change="editHandle" />
    </span>
    <el-link type="primary">2. 骨架屏</el-link><br>
    <skeleton />
  </div>
</template>

<script>
import DblEdit from './dbl-edit'
import skeleton from '@/views/hik/skeleton'
export default {
  name: 'WordEdit',
  components: {
    DblEdit,
    skeleton
  },
  data() {
    return {
      list: [
        { id: '1', name: 'hello' },
        { id: '2', name: 'world' },
        { id: '3', name: 'octopus' }
      ]
    }
  },
  methods: {
    editHandle(value) {
      console.log(value)
    }
  }
}
</script>

<style scoped lang="scss">
</style>

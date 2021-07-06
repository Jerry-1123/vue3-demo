<template>
  <h1>{{ count }} * 2 = {{ double }}</h1>
  <button @click="handleAdd">累加</button>
  <h1>{{ title }}</h1>
  <button @click="handleClickTitle">👋</button>
</template>

<script>
import { reactive, computed, toRefs, onMounted, onUnmounted } from 'vue'

export default {
  name: 'Test',
  setup () {

    let state = reactive({
      count: 1,
      title: 'hello world'
    })

    const double = computed(() => state.count * 2)

    const handleAdd = () => state.count++

    const handleClickTitle = () => state.title = state.title.toUpperCase()

    onMounted(() => {
      console.log('onMounted')
    })

    onUnmounted(() => {
      console.log('onUnmounted')
    })

    return {
      ...toRefs(state),
      double,
      handleAdd,
      handleClickTitle
    }
  }
}
</script>

<style scoped>

</style>

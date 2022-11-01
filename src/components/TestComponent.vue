<template>
  <div class="inner">
    <h3>{{ bigtext }}</h3>
    요런 식으로 컴포넌트 붙여넣기
  </div>
</template>

<script>
export default {
  name: "TestComponent",
  props:{
    bigtext: String
  }
}
</script>

<style scoped>
.inner{max-width: 1200px;margin: 0 auto;padding:20px 0;}
</style>
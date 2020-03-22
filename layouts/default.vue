<template>
  <div>
    <div class="fixed top-0 left-0 right-0">
      <heeader />
    </div>
    <div class="pad">
      <nuxt />
    </div>
  </div>
</template>

<script>
import heeader from '~/components/heeader.vue'  
export default {  
  components: {
    heeader
  }
}
</script>
<style>
.pad{
  padding-top: 100px;
}
</style>

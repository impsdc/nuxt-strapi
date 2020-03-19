<template>
  <div>
    <div class="fixed top-0">
      <heeader />
    </div>
    <div class="pt-5">
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

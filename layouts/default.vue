<template>
  <div>
    <div class="fixed top-0">
      <heeader />
    </div>
    <nuxt />
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

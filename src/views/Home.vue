<template>
  <div class="home">
    <DemoApp msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import DemoApp from '@/components/DemoApp.vue'

export default {
  name: 'Home',
  components: {
    DemoApp
  }
}
</script>

<template>
  <div class="home">
    <card-component></card-component>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import CardComponent from '@/components/CardComponent.vue'

export default {
  name: 'home',
  components: {
    HelloWorld,
    CardComponent
  }
}
</script>

<template>
<!-- <h3>hello world</h3> -->
<Counter
        :year="2024"
        :month="1"
        :date="24"
        :hour="19"
        :minute="25"
        :second="10"
        :millisecond="31" />

</template>

<script>
import Counter from './assets/components/Counter.vue'

export default {
  name: 'App',
  components: {
    Counter
  }
}
</script>

<style>



</style>

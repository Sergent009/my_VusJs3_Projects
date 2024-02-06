<template>

<!-- <PageLoader v-if="!isLoading" /> -->
<!-- <MyPage @keyup="loaded" /> -->

<MyPractise />

</template>

<script>
// import PageLoader from './components/PageLoader.vue'
// import MyPage from './components/MyPage.vue'

import MyPractise from './components/MyPractise.vue'

export default {
  name: 'App',
  components: {
    // PageLoader,
    // MyPage,
    MyPractise
  },
  data(){
    return{
      isLoading: false,
    }
  },
  // mounted(){
  //   setTimeout(() => {
  //     this.isLoading = true
  //   }, 5000)
  // }
}
</script>

<style>

</style>

<template>
  <Header />
  <main class="main-view">
    <router-view />
  </main>
  <Footer />
  <QuizApp />
</template>

<script>
import Header from "@/components/Header"
import Footer from "@/components/Footer"
import QuizApp from "@/views/QuizApp.vue"

export default {
  components: {
    Header,
    Footer,
    QuizApp,
  },
}
</script>

<style scoped>
.main-view {
  padding: 0 2rem;
  width: 100%;
}
</style>

<style>
body {
  color: #2c3e50;
  overflow-x: hidden;
}
</style>

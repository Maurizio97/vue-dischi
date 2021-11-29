<template>
  <div id="app">
    <MyHeader/>
    <main>
      <ListPersonages/>
    </main>
  </div>
</template>

<script>
import ListPersonages from './components/ListPersonages.vue'
import MyHeader from './components/MyHeader.vue'


export default {
  name: 'App',
  components: {
    MyHeader,
    ListPersonages,
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

main {
  background-color: #1e2d3b;
}
</style>

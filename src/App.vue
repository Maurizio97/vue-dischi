<template>
  <div id="app">
    <header id="banner-logo">
        <!-- <img src="@/assets/logo-spotify.png" alt=""> -->
      <div id="cont-select">
        <!-- :list="listGen" -->
          <FilterDisk  :list="newListGenFromSon" @search="selectOption"/>
      </div>
    </header>
    <main>
      <ListPersonages :details="optionChoise" @newListDisk="creationList"/>
    </main>
  </div>
</template>

<script>
import FilterDisk from '@/components/FilterDisk.vue'
import ListPersonages from './components/ListPersonages.vue'
// import MyHeader from './components/MyHeader.vue'


export default {
  name: 'App',
  components: {
    // MyHeader,
    ListPersonages,
    FilterDisk,
  },
  data() {
    return {
      optionChoise: "all",
      newListGenFromSon: null,
    }
  },
  computed: {
    listGen2(){
      return this.listGen3
    }
  },
  methods: {
    // salvo il valore della scelta utente
    selectOption(genere){
      this.optionChoise = genere;
      console.log("hai selezionato: ",this.optionChoise);
    },

    creationList(item){
      this.newListGenFromSon = item
    }
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
  min-height: calc(100vh - 80px);
}
#banner-logo {
  height: 80px;
  background-color: #2e3a46;
}
#cont-select {
  text-align: end;
  padding: 10px 0;
}
</style>

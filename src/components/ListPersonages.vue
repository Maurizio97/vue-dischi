<template>
<div>
  <div id="cont-select">
  <FilterDisk 
  v-for="gen, i in listGen" 
  :key="i" 
  :details="gen"
  @search="selectOption"/>
  <select name="genre" id="" @change="$emit('search', $event)">
    <option :value="'all'">All</option>
    <option 
    v-for="gen, i in listGen" 
    :key="i" 
    :value="gen">{{gen}}</option>
  </select>
  </div>

  <div id="container">
    <Disk 
    v-for="disk, i in filteredListDisk" 
    :key="i" 
    :details="disk"/> 
  </div>
</div>
  
</template>

<script>
import FilterDisk from '@/components/FilterDisk.vue'
import Disk from '@/components/Disk.vue'
import Axios from 'axios'


export default {
  name: "ListDisk",
  components: {
    Disk,
    FilterDisk,
  },

  data() {
    return {
        apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
        listDisk: [],
        // genListDisk: [],
        optionChoise: "all",
        /* listGen: null, */
    };
  },

  created(){
    this.getArray()
    this.allGen()
    console.log(this.listGen);
  },

  computed:{
    // creo un nuovo array per filtrare i contenuti in pagina
    filteredListDisk(){
      if(this.optionChoise === "all"){
        return this.listDisk
      }

      return this.listDisk.filter((item) => {
        return item.genre.toLowerCase().includes(this.optionChoise.toLowerCase())
      })
    },
  },

  methods: {
    getArray(){
      Axios
      .get(this.apiUrl)
      .then((result) =>{
        this.listDisk = result.data.response
      });
    },


    // funzione che ultilizzo per creare un array senza doppioni
    allGen(){
      const listGen = this.listDisk.filter((item) => {
          if(listGen.toLowerCase().includes(item.genre.toLowerCase())){
            return
          }
          return item.genre
          
      })
    },
    
    // salvo il valore della scelta utente
    selectOption(event){
      this.optionChoise = event.target.value
      console.log("hai selezionato: ",this.optionChoise);
    },
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    #container {
        margin: 0 auto;
        width: 60%;
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        padding: 100px 0;
    }

    #cont-select {
      text-align: center;
      padding: 10px 0;
    }
</style>

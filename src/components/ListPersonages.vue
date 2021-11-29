<template>
<div>
  <div id="cont-select">
    <FilterDisk 
      :list="listGen" 
      @search="selectOption"
    />
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
        optionChoise: "all",
        listGen: [],
    };
  },

  created(){
    this.getArray();
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
        this.allGen();
      });
    },
    // funzione che ultilizzo per creare un array senza doppioni
    allGen(){
      for(let i = 0; i < this.listDisk.length; i++){
        if(!this.listGen.includes(this.listDisk[i].genre)){
          this.listGen.push(this.listDisk[i].genre)
        }
      }
    },
    
    // salvo il valore della scelta utente
    selectOption(genere){
      this.optionChoise = genere;
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

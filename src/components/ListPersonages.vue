<template>
<div>
  <div id="container">
    <Disk 
    v-for="disk, i in filteredListDisk" 
    :key="i" 
    :details="disk"/> 
    
  </div>
</div>
  
</template>

<script>
import Disk from '@/components/Disk.vue'
import Axios from 'axios'


export default {
  name: "ListDisk",
  components: {
    Disk,
  },
  props: {
    details:String
  },
  data() {
    return {
      // devo spostare il valore di listGen nell'app tramite un emit
        apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
        listDisk: [],
        listGen: [],
    };
  },

  created(){
    this.getArray();
    this.$emit('newListDisk', this.listGen)
  },

  computed:{
    // creo un nuovo array per filtrare i contenuti in pagina
    filteredListDisk(){
      if(this.details === "all"){
        return this.listDisk
      }

      return this.listDisk.filter((item) => {
        return item.genre.toLowerCase().includes(this.details.toLowerCase())
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
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  #container {
    margin: 0 auto;
    width: 60%;
    display: flex;
    flex-wrap: wrap;
    align-items: stretch;
    padding: 100px 0;
  }
</style>

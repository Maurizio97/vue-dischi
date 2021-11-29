<template>
  <div id="container">
    <Disk v-for="disk, i in listDisk" :key="i" :details="disk"/> 
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
  data() {
    return {
        apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
        listDisk: [],
    };
  },
  created(){
    this.getArray()
  },
  methods: {
    getArray(){
      Axios
      .get(this.apiUrl)
      .then((result) =>{
        // console.log(result.data.response);
        this.listDisk = result.data.response
      });

    }
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
</style>

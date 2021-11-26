<template>
  <div id="container">
    <Disk/>
    <Disk/>
    <Disk/>
    <Disk/>
    <Disk/>
    <!-- v-for="diskt, i in ListDisk" :key="i" :details="diskt" -->
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
        ListDisk: [],
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
        this.listPersonages = result.data.response
      });

    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    #container {
        margin: 0 auto;
        width: 70%;
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
    }
</style>

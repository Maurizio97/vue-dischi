<template>
    <div class="disk-card">
        <img :src="disk.poster" :alt="disk.title">
        <h3>{{ disk.title }}</h3>
        <div>{{ disk.author }}</div>
        <div>{{ disk.year }}</div>
        <!-- "poster": "https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg",
            "title": "New Jersey",
            "author": "Bon Jovi",
            "genre": "Rock",
            "year": "1988" -->
    </div>
</template>

<script>
export default {
  name: "Disk",
  props: {
      details:Object
  },
  data(){
      return {
          disk:{
            "poster": "https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg",
            "title": "New Jersey",
            "author": "Bon Jovi",
            "genre": "Rock",
            "year": "1988"
          }
      }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    .disk-card {
        width: 17%;
        img {
            max-width: 100%;
        }
    }
</style>
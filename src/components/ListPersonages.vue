<template>
  <div id="container">
    <h1>Richy and Morty APP</h1>
    <div id="container-item">

    </div>
  </div>
</template>

<script>
export default {
  name: "ListPersonages",
  data() {
    return {
        apiUrl: "",
        listPersonages: [],
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    #container {
        margin: 20px auto;
        width: 70%;
    }
</style>

<template>
    <div class="disk-card">
        <img :src="details.poster" :alt="details.title">
        <h2>{{ details.title }}</h2>
        <div>{{ details.author }}</div>
        <div>{{ details.year }}</div>
    </div>
</template>

<script>
export default {
  name: "Disk",
  props: {
      details:Object
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    .disk-card {
        width: 17%;
        background-color: #2e3a46;
        margin-bottom: 50px;
        padding: 10px;
        text-align: center;

        img {
            max-width: 85%;
        }

        h2 {
            color: white;
            margin: 15px 0;
        }

        div {
            color: gray;
            margin: 10px 0;
            font-size: 18px;
            font-weight: bold;
        }
    }
</style>
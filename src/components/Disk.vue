<template>
    <div class="container-card">
        <div class="card">
            <img :src="details.poster" :alt="details.title">
            <h2>{{ details.title }}</h2>
            <div>{{ details.author }}</div>
            <div>{{ details.year }}</div>
        </div>
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
    .container-card {
        width: 20%;
        padding: 10px;
        margin-bottom: 50px;
        text-align: center;
        .card {
            background-color: #2e3a46;
            min-height: 100%;
            

            img {
                max-width: 85%;
                margin-top: 20px;
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
    }
</style>
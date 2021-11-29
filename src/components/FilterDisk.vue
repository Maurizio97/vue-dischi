<template>
    <div>
        <select name="genre" id="" @change="$emit('search', $event)">
            <option :value="'all'">All</option>
            <option :value="'rock'">Rock</option>
            <option :value="'pop'">Pop</option>
            <option :value="'jazz'">Jazz</option>
            <option :value="'metal'">Metal</option>
        </select>
    </div>
</template>

<script>
export default {
  name: "FilterDisk",
  data(){
      return {
          optionChoise: "",
      }
  },
  methods: {
      selectOption(event){
          this.optionChoise = event.target.value
          console.log("hai selezionato: ",this.optionChoise);
      }
  }
};
</script>

<style scoped lang="scss">
  select {
      margin: 0 auto;
  }
</style>
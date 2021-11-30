<template>
    <div>
        <select name="genre" id="" @change="$emit('search', $event.target.value)">
            <option :value="'all'">All</option>
            <option v-for="item, i in list" :key="i">{{item}}</option>
        </select>
    </div>
</template>

<script>
export default {
  name: "FilterDisk",
  props: {
      list:Array
  }
};
</script>

<style scoped lang="scss">
  select {
    margin: 0 auto;
    width: 200px;
    height: 30px;
    text-align: center;
    background-color: #2e3a46;
    color: white;
  }
</style>
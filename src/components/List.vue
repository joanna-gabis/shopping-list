<template>
  <div class='list'>
    <ul>
      <li v-for='item in list'>{{ item }}</li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'List',
  data() {
    return {
      list: ['kasza', 'pomidory'],
    };
  },
}
</script>
<style scoped lang="scss">
  li {
    list-style-type: none;
  }

</style>



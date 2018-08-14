<template>
  <div class="header">
    <h1>{{ header }}</h1>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      header: 'Shopping list',
    };
  }
}
</script>

<style scoped lang="scss">
  h1 {
    color: #5e5757;
    margin: 50px;
  }
</style>

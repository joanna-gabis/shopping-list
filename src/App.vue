<template>
  <div id="app">
    <Header/>
    <Input/>
    <List/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Input from './components/Input.vue';
import List from './components/List.vue';

export default {
  name: 'app',
  components: {
    Header,
    Input,
    List,
  },
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
}
</style>

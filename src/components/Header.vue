<template>
<div class="app">
 <div class='header'>
    <h1>Shopping list</h1>
  </div>

  <div class="input">
    <input
      type='text'
      placeholder='add item'
      v-model='newItem'
      @keyup.enter='saveItem'
    />
    <div
      class='button'
      @click='saveItem'>
      <i class="fas fa-plus"></i>
    </div>
  </div>

  <div class='list'>
    <ul>
      <li v-for='item in list'>{{ item }} <i class="fas fa-times"></i></li>
    </ul>
  </div>

</div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      newItem: '',
      list: ['kasza', 'pomidory',],
    };
  },
  methods: {
    saveItem: function() {
      this.list.push(this.newItem);
      this.newItem = '';
    },
  }
}
</script>

<style scoped lang="scss">
  h1 {
    color: #5e5757;
    margin: 50px;
  }
  input {
    border: none;
    border-bottom: 1px solid black;
    height: 50px;
    width: 250px;
    outline: none;
    font-size: 1.25rem;
    margin: 20px;

    &::placeholder {
      text-align: center;
    }
  }
  .button {
    display: inline-block;
    width: 50px;
    height: 50px;
    line-height: 50px;
    background-color: #4193e0;
    border-radius: 5px;
    color: #fff;
    font-size: 1.5rem;
  }
  li {
    list-style-type: none;
  }
</style>

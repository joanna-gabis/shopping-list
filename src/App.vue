<template>
  <div class="app">
    <Header/>
    <Input
      @saveItem='saveItem'
      @deleteBought='deleteBought'
      @clearList='clearList'
      v-model='inputValue' />
    <div v-if='list.length===0'>Congratulations, you have nothing to buy!</div>
    <List
      :list='list'
      @togglePurchased='togglePurchased'
    />
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
  data() {
    return {
      list: [],
    }
  },
  methods: {
  saveItem: function(item) {
    if(item) {
      this.list.push({
        name: item,
        purchased: false,
      });
    }
  },
  deleteBought: function() {
    // let itemToDelete = this.list.find((elem) => elem.name===item.name);
    // let index = this.list.indexOf(itemToDelete);
    // this.list = this.list.slice(0, index).concat(this.list.slice(index+1));
    let resultArray = [];
    for(let i=0; i<this.list.length; i++) {
      if(!this.list[i].purchased) {
        resultArray.push(this.list[i]);
      }
    };
    this.list = resultArray;
  },
  togglePurchased: function(item) {
    item.purchased = !item.purchased;
  },
  clearList: function() {
    this.list=[];
  }
}
}
</script>

<style lang="scss">
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  .app {
    width: 100%;
    text-align: center;
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
  }
</style>

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
    <div v-if='list.length===0'>Congratulations, you have nothing to buy!</div>

    <div class='list'>
      <ul>
        <li v-for='item in list' :class="{strikeout: item.purchased}" @click='togglePurchased(item)' >{{item.name}}</li>
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
        list: [],
      };
    },
    methods: {
      saveItem: function() {
        if(this.newItem) {
          this.list.push({
            name: this.newItem,
            purchased: false,
          });
          this.newItem = '';
        }
      },
      // deleteItem: function(item) {
      //   let itemToDelete = this.list.find((elem) => elem.name===item.name);
      //   let index = this.list.indexOf(itemToDelete);
      //   this.list = this.list.slice(0, index).concat(this.list.slice(index+1));
      // },
      togglePurchased: function(item) {
        item.purchased = !item.purchased;
      }
    }
  }
</script>

<style scoped lang="scss">
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  .app {
    width: 100%;
  }
  h1 {
    color: #696969;
    margin: 50px;
  }
  input {
    border: none;
    border-bottom: 1px solid black;
    height: 50px;
    width: 200px;
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
  .list {
    li {
      list-style-type: none;
      font-size: 1.5rem;

      &:nth-child(odd) {
        background-color: #DCDCDC;
      }
    }
    .strikeout {
      color: 	#696969;
      text-decoration: line-through;
    }
  }

</style>

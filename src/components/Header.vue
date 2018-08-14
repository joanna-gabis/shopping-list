<template>
  <div class="app">
    <div class='header'>
      <img src='../assets/header-pic.png'/>
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
        class='button add'
        @click='saveItem'>
        <i class="fas fa-plus"></i>
      </div>
      <div
        class='button delete'
        @click='deleteBought'>
        Delete bought
      </div>
      <div
        class='button clear'
        @click='clearList'>
        Clear list
      </div>
    </div>
    <div v-if='list.length===0'>Congratulations, you have nothing to buy!</div>

    <div class='list'>
      <ul>
        <li v-for='item in list' :class="{strikeout: item.purchased}" :key='' @click='togglePurchased(item)'><i class="fas fa-check"></i>{{item.name}}</li>
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

<style scoped lang="scss">
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  .app {
    width: 100%;
  }
  // HEADER STYLES
  .header {
    h1 {
      color: #282828;
      margin: 50px;
      }
    img {
      width: 100%;
    }
  }

  // INPUT STYLES
  .input {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 50px;

    input {
    border: none;
    border-bottom: 1px solid #282828;
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
      height: 50px;
      line-height: 50px;
      border-radius: 5px;
      color: #fff;
      margin: 2px;
      &.add {
        width: 50px;
        background-color: #4388D3;
        font-size: 1.5rem;
      }
      &.delete {
        width: 120px;
        background-color: #F6C500;
        font-size: 1rem;
      }
      &.clear {
        width: 120px;
        background-color: #EA0000;
        font-size: 1rem;
      }
    }
  }

  //LIST STYLES
  .list {
    text-align: left;
    margin-left: 30vw;
    li {
      list-style-type: none;
      font-size: 1.5rem;
      color: #282828;
      .fa-check {
        font-size: 1rem;
        line-height: 1rem;
        margin: 10px;
      }
    }
    .strikeout {
      color: 	#7E815D;
      text-decoration: line-through;
      .fa-check {
        color: #66CB26;
      }
    }
  }

</style>

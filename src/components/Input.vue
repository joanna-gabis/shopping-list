<template>
 <div class="input">
  <input
    type='text'
    placeholder='add item'
    v-model='inputValue'
    @keyup.enter='saveItem'
  />
  <div
    class='button add'
    @click='saveItem'>
    <i class="fas fa-plus"></i>
  </div>
  <div
    class='button delete'
    @click='$emit("deleteBought")'>
    Delete bought
  </div>
  <div
    class='button clear'
    @click='$emit("clearList")'>
    Clear list
  </div>
</div>
</template>
<script>
export default {
  name: 'Input',
  methods: {
    saveItem(e) {
      this.$emit('saveItem', this.inputValue);
      this.inputValue = '';
    }
  },
  data() {
    return {
      inputValue: '',
    };
  },
}
</script>
<style scoped lang="scss">
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

</style>

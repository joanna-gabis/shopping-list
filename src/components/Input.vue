<template>
  <div class="input">
    <input
      type='text'
      placeholder='add item'
      v-model='inputValue'
      @keyup.enter=''
    />
    <div
      class='button'
      @click=''>
      <i class="fas fa-plus"></i>
    </div>
  </div>

</template>
<script>
export default {
  data() {
    return {
      inputValue: '',
    };
  },
}
</script>
<style scoped lang="scss">
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

</style>

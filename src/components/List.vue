<template>
  <div class='list'>
    <ul>
      <li v-for='item in list' :class="{strikeout: item.purchased}" :key='' @click='$emit("togglePurchased", item)'><i class="fas fa-check"></i>{{item.name}}</li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'List',
  props: {
    list: {
      type: Array,
      required: true,
    }
  }
}
</script>
<style scoped lang="scss">
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



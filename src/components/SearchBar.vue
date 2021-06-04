<template>

    <!-- Search:
    <input @input="onInput"/> -->
<div>
<nav class="navbar navbar-dark bg-dark">
  <div class="container-fluid">
    <a class="navbar-brand"> <h2 class="text-white">Video Watch</h2></a>
    <form class="d-flex">
      <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" @input="onInput"/>
    </form>
  </div>
</nav>
</div>
</template>

<script>
export default {
  name: 'SearchBar',
  methods: {
    onInput: function(event) {
      // console.log(event.target.value);
      this.$emit('termChange',event.target.value);
    }
  }
};
</script>

<style scoped>
  form {
    width: 70%;

  }
    nav {
    width: 100%;

  }
  div {
    text-align: center;
    margin: 20px;
  }
  
  
</style>
<template>
  <header class="header">
    <h1>Todo List</h1>
  </header>
</template>

<script>
export default {
  name: 'HeaderSection',
};
</script>

<style scoped>
.header {
  background: #333;
  color: #fff;
  text-align: center;
  padding: 8px;
}
.header a {
  color: #fff;
  padding-right: 5px;
}
h1 {
  display: block;
  font-size: 2em;
  margin-block-start: 0.4em;
  margin-block-end: 0.4em;
}
</style>

<template>
  <div>
    <Header />
    <TodoList />
  </div>
</template>

<script>
import Header from "./components/Header";
import TodoList from "./components/TodoList";
export default {
  name: "App",
  components: {
    TodoList,
    Header,
  },
};
</script>

<style>
body {
  background-color: rgb(66, 66, 66);
  color: aliceblue;
}
</style>

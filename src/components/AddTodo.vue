<template>
  <form @submit.prevent="addTodo()" class="col-12 col-lg-6 mb-3 form-inline">
    <div class="form-group">
      <input
        v-model="newTodo"
        placeholder="Enter Todo..."
        type="text"
        class="form-control"
      />
    </div>
    <button class="btn btn-outline-light ml-3" type="submit">
      Add
    </button>
  </form>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      newTodo: "",
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.length > 1) {
        this.$emit("on-addtodo", this.newTodo);
      }
      this.newTodo = "";
    },
  },
};
</script>

<style scoped></style>

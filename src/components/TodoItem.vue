<template>
  <li class="d-flex align-items-center list-group-item">
    <button
      v-if="!isEditing"
      :class="{ completed }"
      @click="$emit('on-toggle')"
      class="btn border-0 text-left flex-grow-1"
    >
      {{ todoString }}
    </button>
    <form v-else @submit.prevent="endEditing()" class="flex-grow-1">
      <input
        type="text"
        class="form-control"
        v-model="newTodoString"
        @blur="startEditing()"
      />
    </form>
    <button @click="startEditing()" class="btn btn-outline-primary">
      Edit
    </button>
    <button @click="$emit('on-delete')" class="btn btn-outline-danger ml-2">
      Delete
    </button>
  </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todoString: String,
    completed: Boolean,
  },
  data() {
    return {
      isEditing: false,
      newTodoString: "",
    };
  },
  methods: {
    startEditing() {
      if (!this.isEditing) {
        this.newTodoString = this.todoString;
        this.isEditing = true;
      } else {
        this.endEditing();
      }
    },
    endEditing() {
      this.isEditing = false;
      this.$emit("on-edit", this.newTodoString);
    },
  },
};
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}
</style>

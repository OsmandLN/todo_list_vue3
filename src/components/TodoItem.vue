<template>
  <li>{{ initialTodo.content }}</li>
  <button @click="onDeleteBtnClicked">X</button>
</template>

<script>
export default {
  props: {
    initialTodo: {
      required: true,
      type: Object
    }
  },
  methods: {
    onDeleteBtnClicked() {
      this.$emit("delete")
    }
  }
}
</script>
<style lang="scss" scoped>
ul {
  display: flex;

  li {
    border: 1px black solid
  }
}
</style>
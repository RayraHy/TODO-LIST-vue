<template>
  <div class="new-task">
    <input v-model.trim="name" class="form-element" type="text" placeholder="Adicionar nova tarefa" @keydown.enter="add">
    <button class="form-element" @click="add">+</button>
  </div>
</template>

<script>
export default {
    name: 'new-task',
    data() {
        return {
            name: ''
        }
    },
    methods: {
        add() {
            if(this.name) {
                this.$emit('taskAdded', {name: this.name});
                this.name = '';
            }
        }
    }
}
</script>

<style scoped>
.new-task {
    margin: 35px;
}

.form-element {
    outline: none;
    font-size: 2rem;
    border: 1px solid white;
    padding: 5px 10px;
    color: white;
}

input {
    width: 500px;
    background-color: #FFF2;
    border-top-left-radius: 8px;
    border-bottom-left-radius: 8px;
}

button {
    border-left: none;
    background-color: #2196F3;
    border-top-right-radius: 8px;
    border-bottom-right-radius: 8px;
}
</style>
<template>
    <!-- If item item is completed them put a line through it -->
     <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
         <input type="checkbox" v-on:change="markComplete">
        <p>{{todo.title}}</p>
    </div>
</template>

<script>
export default {
    name: 'TodoItem',
    props:["todo"],
    methods: {
        //Change the state of a item by clicking the checkbox to complete if not and vice-versa
        markComplete(){
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
    .todo-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }
  .is-complete {
    text-decoration: line-through;
  }
  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>
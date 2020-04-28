<template>
    <div>
        <form @submit="addTodo">
            <input type="text" name="title" v-model="title" placeholder="Add todo">
            <input class="btn" type="submit" value="Submit">
        </form>
    </div>
</template>

<script>
export default {
    name: 'AddTodo',
    data(){
        return{
            title: ''
        }
    },
    methods:{
        addTodo(e){
            e.preventDefault();
            const newTodo ={
                title: this.title,
                completed: false
            }
            //Send to parent
            this.$emit('add-todo', newTodo);
        }
    }
}
</script>

<style scoped>
  form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }
</style>
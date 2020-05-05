<template>
    <div>
        <form @submit="addTodo">
        <input type="text" v-model="title" name="title" placeholder="Add Todo...">
        <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
import uuid from 'uuid';

export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault(); // prevents it form from sending it to a file
            const newTodo = {
                id: uuid.v4(),
                title: this.title,
                completed: false
            }
            //send up to parent
            this.$emit('add-todo', newTodo); // send up to parent using $emit event
            this.title = ''; // when submit something the form clears
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
<template>
    <div class="container">
            <h1>To do List</h1>
            <Form v-on:add-todo="addTodo"></Form>
            <div class="list-group">
                <p v-if="todos.length <= 0">No to do yet. Add one to your list.</p>
                <div class="list-group-item" v-for="(todo, index) in allTodos" v-bind:key="index">
                    <span class="comment__author">To do: <strong>{{ todo.name }}</strong></span>
                        <div>
                            <a href="#" v-on:click.prevent="removeTodo(index)" title="Remove">Remove</a>
                        </div>
                </div>
            </div>
    </div>
</template>

<script>
    import Form from './Form'
    export default {
        components: {
            Form
        },
        data() {
            return {
                todos: []
            }
        },
        methods: {
            addTodo(todo) {
                this.todos.push(todo);
            },
            removeTodo(index) {
                this.todos.splice(index, 1);
            }
        },
        computed: {
            allTodos() {
                return this.todos.map(todo =>({
                    ...todo,
                    name: todo.name
                }))
            }
        },
        watch: {
            todos(val) {
                console.log('val',val);
            }
        }
    }
</script>
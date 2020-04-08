<template>
    <div class="form-todo form-group">
        <p>
            <input type="text" placeholder="Type your to do" name="name" class="form-control" v-model="name"/>
        </p>
        <button v-on:click="addTodo" type="submit" class="btn btn-primary">Add</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            name: ''
        }
    },
    methods: {
        addTodo() {
            if(this.name.trim() === '') {
                return;
            }

            this.$emit('add-todo', {
                name: this.name
            });

            this.name = '';
        }
    }
}
</script>
<script>
let id = 0;

export default {
    data() {
        return {
            newTodo: '',
            todos: [],
            todoTag: ''
        }
    },
    methods: {
        addTodo() {
            this.todos.push({ id: id++, text: this.newTodo, done: false, tag: this.todoTag })
            this.newTodo = '';
            console.log('todos', this.todos);
        },
        clearTodos() {
            this.todos = [];
        }
    },
    computed: {
        priorityTodos: function () {
            return this.todos.filter(todo => todo.tag === 'priority');
        },
        normalTodos: function () {
            return this.todos.filter(todo => todo.tag === 'to-do');
        },
        laterTodos: function () {
            return this.todos.filter(todo => todo.tag === 'anotherDay');
        }
    }
}



</script>


<template>
    <div id="container">

        <form @submit.prevent="addTodo">
            <h3>To Do List</h3>
            <input type="text" v-model="newTodo" />
            <input type="radio" id="priority" v-model="todoTag" value="priority" />
            <label for="priority">Priority</label>
            <input type="radio" id="to-do" v-model="todoTag" value="to-do" />
            <label for="to-do">To Do</label>
            <input type="radio" id="anotherDay" v-model="todoTag" value="anotherDay" />
            <label for="anotherDay">Another Day</label>
            <button type="submit">Add Task</button>
            <button @click="clearTodos" type="reset">Reset</button>
        </form>
        <h2>Priority</h2>
        <ul>
            <li v-for="todo in priorityTodos" :key="todo.id">
                <input type="checkbox" v-model="todo.done">
                <span :class="{ done: todo.done }">{{ todo.text }}</span>
            </li>
        </ul>
        <h2>To Do</h2>
        <ul>
            <li v-for="todo in normalTodos" :key="todo.id">
                <input type="checkbox" v-model="todo.done">
                <span :class="{ done: todo.done }">{{ todo.text }}</span>
            </li>
        </ul>
        <h2>Another Day</h2>
        <ul>
            <li v-for="todo in laterTodos" :key="todo.id">
                <input type="checkbox" v-model="todo.done">
                <span :class="{ done: todo.done }">{{ todo.text }}</span>
            </li>
        </ul>
    </div>
</template>

<style scoped>
h3 {
    padding: 0 1em;
}

input[type=text] {
    width: 100%;
}

li {
    list-style-type: none;
    display: flex;
}

.done {
    text-decoration: line-through;
}


#container {
    display: flex;
}
</style>
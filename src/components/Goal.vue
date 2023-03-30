<script>
let id = 0;

export default {
    data() {
        return{
            newGoal: '',
            goals: []
        }
    },
    methods: {
        addGoal() {
            this.goals.push({id: id++, text: this.newGoal, done: false})
            this.newGoal = '';
        }
    }
}



</script>


<template>
    <div id="container">

    <form @submit.prevent="addGoal">
        <h3>GOALS FOR THE DAY</h3>
        <input type="text" v-model="newGoal" />
        <button>Add Goal</button>
    </form>
    <ul>
        <li v-for="goal in goals" :key="goal.id">
            <input type="checkbox" v-model="goal.done">
            <span :class="{ done: goal.done }">{{ goal.text }}</span>
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
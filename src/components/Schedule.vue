<script>
import _ from 'lodash';
let id = 0;



export default {
    data() {
        return{
            newAppt: '',
            appts: [],
            times: _.range(7, 13).concat(_.range(1, 9))
        }
    },
    methods: {
        addAppt() {
            this.appts.push({id: id++, text: this.newAppt})
            this.newAppt = '';


        },
        clear() {
            this.appts = [];
        }
    }
}





</script>


<template>
    <ul>
        <li v-for="time in times" :key="time">
            <label >{{ time }}</label>
            <input type="text" />
        </li>
    </ul>

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
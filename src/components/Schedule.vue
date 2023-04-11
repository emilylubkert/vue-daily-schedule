<script>
import _ from 'lodash';
let id = 0;



export default {
    data() {
        return{
            newAppt: '',
            appts: [],
            times: _.range(7, 13).concat(_.range(1, 9)),
            isSelected: false,
            workSelected: [],
            personalSelected: []
        }
    },
    methods: {
        addAppt() {
            this.appts.push({id: id++, text: this.newAppt})
            this.newAppt = '';

        },
        clear() {
            this.appts = [];
        },

        handleWorkSelect(index) {
            if(this.workSelected.includes(index)) {
                this.workSelected = this.workSelected.filter(el => el !== index)
            } else {
                this.workSelected.push(index);
            }
        },

        handlePersonalSelect(index) {
            if(this.personalSelected.includes(index)) {
                this.personalSelected = this.personalSelected.filter(el => el !== index)
            } else {
                this.personalSelected.push(index);
            }
        }
    }
}





</script>


<template>
    <ul>
        <li v-for="(time, index) in times" :key="time">
            <label >{{ time }}</label>
            <input type="text"  :class="workSelected.includes(index)  && 'work-selected' || personalSelected.includes(index) && 'personal-selected'"/>
            <button type="button" @click="handlePersonalSelect(index)"  >Personal</button>
            <button type="button" @click="handleWorkSelect(index)"  >Work</button>
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

.work-selected {
    background-color: #B7A1FF;
}

.personal-selected {
    background-color: #e9ffa1;
}


#container {
    display: flex;
}
</style>
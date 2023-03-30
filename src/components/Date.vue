<script>
export default {
    data() {
        return {
            date: '',
            days: ['M', 'T', 'W', 'Th', 'F', 'Sa', 'Su'],
            currentDay: 0,
            isSelected: false,
        }
    },
    methods: {
        handleSelect(index) {
            this.isSelected = index;
        }
    }
}



</script>

<template>
    <div id="container">
        <h3>Date</h3>
        <!-- <p v-if="date.length > 3">{{ date }}</p> -->
        <input v-model="date" />
        <ul>
            <li v-for="(day, index) in days" @click="handleSelect(index)" :class="index === isSelected && 'selected'">{{ day
            }}</li>
        </ul>
    </div>
</template>

<style scoped>
h3 {
    padding: 0 1em;
}

ul li {
    display: inline;
    padding: 1em;
    cursor: pointer;
}

.selected {
    text-decoration: underline;
    text-decoration-color: #B7A1FF;
    text-decoration-thickness: 2px;
    text-underline-offset: 4px;
}

#container {
    display: flex;
}
</style>
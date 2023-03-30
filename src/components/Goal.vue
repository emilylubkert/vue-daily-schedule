<script>
export default {
    data() {
        goal: ''
    }

}



</script>

<template>
    <div id="container">
        <h3>GOAL FOR THE DAY</h3>
        <input v-model="goal" />
    </div>
</template>

<style scoped>
h3 {
    padding: 0 1em;
}

input {
    width: 100%;
}


#container {
    display: flex;
}
</style>
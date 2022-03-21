<template>
    <h1>{{ title }}</h1>
    <input type="text" ref="name" />
    <button @click="handleClick">click me</button>

    <!-- creating prop in the component as an attribute -->
    <!-- adding custom theme prop in the model as an attribute -->
    <Modal v-bind:header="header" v-bind:text="text" theme="sale"/>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
    name: "App",
    // Registering sub-components that you want to use
    components: {
        Modal,
    },
    data() {
        return {
            title: "My First Vue App :)",
            header: "Sign up for the Giveaway!",
            text: "Grab your ninja swag for half price!",
        };
    },
    methods: {
        handleClick() {
            // console.log(this.$refs);
            console.log(this.$refs.name);
            this.$refs.name.classList.add("active");
            this.$refs.name.focus();
        },
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

h1 {
    border-bottom: 1px solid #ddd;
    display: inline-block;
    padding-bottom: 10px;
}
</style>

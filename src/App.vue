<template>
    <h1>{{ title }}</h1>
    <br />
    <input type="text" ref="name" />
    <button @click="handleClick">click me</button>
    <p>Welcome...</p>

    <!-- creating prop in the component as an attribute -->
    <!-- adding custom theme prop in the model as an attribute -->

    <div v-if="showModal">
        <!-- listen to the event emitted by the Modal component i.e. child component -->
        <Modal theme="sale" @close="toggleModal">
            <!-- Template passed inside here is known as slot -->
            <h1>Ninja Giveaway!</h1>
            <p>Grab your ninja swag for half price!</p>

            <!-- using slot directive to give template a slot name -->
            <template v-slot:links>
                <a href="#">Sign up now</a>
                <a href="#">more info</a>
            </template>
        </Modal>
    </div>
    <button @click.alt="toggleModal">open modal (alt)</button>

    <div v-if="showModalTwo">
        <Modal @close="toggleModalTwo">
            <h1>Sign up to the newsletter</h1>
            <p>For updates and promo codes!</p>
        </Modal>
    </div>
    <button @click="toggleModalTwo">open modal 2</button>
</template>

<script>
// challenge
//  - create an extra button to open a different modal
//  - use the same modal component but pass in a different template (slot)
//  - use a different method (e.g. toggleModalTwo) and data (e.g. showModalTwo)

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
            showModal: false,
            showModalTwo: false,
        };
    },
    methods: {
        handleClick() {
            // console.log(this.$refs);
            console.log(this.$refs.name);
            this.$refs.name.classList.add("active");
            this.$refs.name.focus();
        },
        toggleModal() {
            this.showModal = !this.showModal;
        },
        toggleModalTwo() {
            this.showModalTwo = !this.showModalTwo;
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

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
            showModal: false,
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

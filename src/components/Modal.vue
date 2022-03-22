<template>
    <div class="backdrop" @click="closeModal">
        <!-- check based on the value of that theme inside the <Modal/> 
            we could add conditional class to style it differently.

            :class="{ key : boolean }" 
        -->
        <div class="modal" :class="{ sale: theme === 'sale' }">
            <h1>{{ header }}</h1>
            <p>{{ text }}</p>
        </div>
    </div>
</template>

<!-- accepts certain props in the component-->
<script>
export default {
    // passing / registering any values or props we will be accepting into this component

    props: ["header", "text", "theme"],

    /*  doesn't need to be defined in data() function because 
        we passed it in <Modal /> as an attribute in root component 
    */

    methods: {
        closeModal() {
            // emit the custom events from the component
            this.$emit("close");
        },
    },
};
</script>

<!-- creating the Modal component style scoped 
    <style scoped></style>
-->

<style>
.modal {
    width: 400px;
    padding: 20px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;
}

.backdrop {
    top: 0;
    position: fixed;
    background: rgba(0, 0, 0, 0.5);
    width: 100%;
    height: 100%;
}

/* making the selector more specific */
.modal h1 {
    color: #03cfb4;
    border: none;
    padding: 0;
}

/* overides the global style css rules */
.modal p {
    font-style: normal;
}

/* customize the theme of the modal*/
.modal.sale {
    background: crimson;
    color: white;
}

.modal.sale h1 {
    color: white;
}
</style>

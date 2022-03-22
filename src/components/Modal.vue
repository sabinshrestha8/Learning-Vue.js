<template>
    <div class="backdrop" @click.self="closeModal">
        <!-- check based on the value of that theme inside the <Modal/> 
            we could add conditional class to style it differently.

            :class="{ key : boolean }" 
        -->
        <div class="modal" :class="{ sale: theme === 'sale' }">
            <!-- using the slot in the custom component i.e. default slot -->
            <slot>default content</slot>
            <div class="actions">
                <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>

<!-- accepts certain props in the component-->
<script>
// create local registration for Vue component
export default {
    // passing / registering any values or props we will be accepting into this component

    props: ["theme"],

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

/* style up the link inside actions */
.modal .actions {
    text-align: center;
    margin: 30px 0 10px 0;
    color: #333;
}

.modal .actions a {
    color: #333;
    padding: 8px;
    border: 1px solid #eee;
    border-radius: 4px;
    text-decoration: none;
    margin: 10px;
}

/* customize the theme of the modal*/
.modal.sale {
    background: crimson;
    color: white;
}

.modal.sale h1 {
    color: white;
}

/* style slightly different if sale theme is enabled*/
.modal.sale .actions {
    color: white;
}

.modal.sale .actions a {
    color: white;
}
</style>

<script setup>
import { ref } from 'vue';

defineProps({
    handleToggleModal: Function,
})

const currYear = new Date().getFullYear()
const name = ref("")
const day = ref(1)
const month = ref(1)
const year = ref(currYear)

const lifeExpectancy = ref(80)
</script>

<template>
    <section id="form">
        <div>
            <h4 class="text-gradient">Your Details</h4>
            <button @click="handleToggleModal" class="link-button"><i class="fa-solid fa-xmark"></i></button>
        </div>
        <div>
            <label for="name">Name</label>
            <input type="text" id="name" required />
        </div>
    </section>
</template>

<style scoped></style>

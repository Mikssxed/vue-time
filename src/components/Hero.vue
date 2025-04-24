<script setup>
const { name, data, handleToggleModal, percentage, resetData } = defineProps({ name: String, data: Object, handleToggleModal: Function, percentage: Object, resetData: Function })


function copyLink() {
    navigator.clipboard.writeText("https://www.wojtula.com/")
}
</script>

<template>
    <section id="hero">
        <h3 class="text-large">{{ name }}, you have {{ data.weeks }} weeks left. Make them count.</h3>
        <div class="btns-container">
            <button @click="handleToggleModal">Not {{ name }}?</button>
            <button class="link-button" @click="copyLink">Copy link</button>
            <button class="link-button" @click="resetData">Reset data</button>
        </div>
        <div class="progress-bar">
            <div :style="{ width: percentage }">
                <div>
                    <i class="fa-solid fa-baby"></i>
                    <h6 class="bar-label">Birth</h6>
                </div>
                <h6>{{ percentage }}</h6>
            </div>
            <div>
                <h6 class="bar-label">Death</h6>
                <i class="fa-solid fa-skull"></i>
            </div>
        </div>
    </section>
</template>

<style scoped></style>

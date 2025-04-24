<script setup>
import { ref } from "vue";
import Calendar from "./components/Calendar.vue";
import Clocks from "./components/Clocks.vue";
import Form from "./components/Form.vue";
import Hero from "./components/Hero.vue";
import Layout from "./components/layouts/Layout.vue";
import Portal from "./components/Portal.vue";
import Summary from "./components/Summary.vue";
import { calculateTimeLeft } from "./utils";

const defaultBD = '1995-06-15'
const defaultLE = 80

const birthDate = ref(defaultBD)
const lifeExpectancy = ref(defaultLE)
const name = ref('John Doe')
const data = ref(calculateTimeLeft(birthDate.value, lifeExpectancy.value))

const showModal = ref(false)

function handleToggleModal() {
  showModal.value = !showModal.value
}

function handleUpdateData(n, b, e) {
  if (!n || !b || !e) { return }

  name.value = n
  birthDate.value = b
  lifeExpectancy.value = parseInt(e)
  data.value = calculateTimeLeft(b, parseInt(e))
  showModal.value = false
}

const totalProps = {
  birthDate, lifeExpectancy, name, data
}
</script>

<template>
  <Layout>
    <Portal :handleCloseModal="handleToggleModal" :showModal="showModal">
      <Form />
    </Portal>
    <Hero :name="name" :data="data" :handleToggleModal="handleToggleModal" />
    <Form />
    <Clocks v-bind="totalProps" />
    <Calendar v-bind="totalProps" />
    <Summary />
  </Layout>
</template>

<style scoped></style>

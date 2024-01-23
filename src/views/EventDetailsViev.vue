<script setup>
import {onMounted, ref} from "vue";
import EventService from "../../services/EventService.js";
import {useRoute} from "vue-router";

const props = defineProps({
  id: {
    required: true
  }
})

const event = ref(null);
const isReady = ref(false);
// const route = useRoute();

onMounted(async () => {
  const response = await EventService.getEvent(props.id);
  event.value = response.data;
  isReady.value = true;
})


</script>

<template>
  <div v-if="isReady">
    <h1>{{ event.title }} # {{props.id}}</h1>
    <p>{{ event.time }} on {{ event.date }} at {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>


<style scoped>
</style>


<script setup>

import EventCard from "@/components/EventCard.vue";

import {ref} from "vue";

// const url = "https://my-json-server.typicode.com/Code-Pop/Real-World_Vue-3/events";

import { onMounted } from 'vue'
import EventService from "../../services/EventService.js";
// import axios from "axios";

const events = ref(null);

onMounted(async () => {
  const response = await EventService.getEvents();
  events.value = response.data
  // axios.get(url).then((response) => {
  //   events.value = response.data;
  //   console.log(response.data)
  // })
});


</script>

<template>
  <main>
    <div class="events">
      <EventCard v-for="event in events" v-bind:event="event"></EventCard>
    </div>
  </main>
</template>

<style>
.events {  display: flex;
  flex-direction: column;  align-items: center;
}
</style>

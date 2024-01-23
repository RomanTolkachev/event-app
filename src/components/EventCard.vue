<script setup>

defineProps({
  event: {
    type: Object,
  }
})

</script>

<template>
  <router-link class="event-link" v-bind:to="{name:'event-details', params:{id: event.id}}">
    <div class="event-card">
      <h2>
        {{event.title}}
      </h2>
      <p>{{event.description}}</p>
    </div>
  </router-link>
</template>

<style>
.event-card {  padding: 20px;
  width: 250px;  cursor: pointer;
  border: 1px solid #39495c;  margin-bottom: 18px;
}
.event-card:hover {
  transform: scale(1.01);  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2);
}

.event-link {
  text-decoration: none;
  color: #42b983;
}

</style>
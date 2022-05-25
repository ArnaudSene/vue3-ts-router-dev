<script lang="ts">
import { defineComponent } from "vue";
import type { EventItem } from "@/types/EventType";
import EventService from "@/services/EventService";

export default defineComponent({
  props: {
    id: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      event: {} as EventItem,
    };
  },
  created() {
    EventService.getEvent(this.id)
      .then((response) => {
        this.event = response.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
});
</script>

<template>
  <div v-if="event">
    <h1>Event Detail</h1>
    <p>id: {{ event.id }}</p>
    <p>origin: {{ event.origin }}</p>
    <p>title: {{ event.title }}</p>
    <p>description: {{ event.description }}</p>
    <p>date: {{ event.date }}</p>
    <p>time: {{ event.time }}</p>
  </div>
</template>

<style>

</style>

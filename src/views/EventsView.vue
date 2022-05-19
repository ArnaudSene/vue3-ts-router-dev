<script lang="ts">
import { defineComponent } from "vue";
import EventItemComp from "@/components/EventItem.vue";
import type { EventItem } from "@/types/EventType";
import EventService from "@/services/EventService";

export default defineComponent({
  name: "EventsSummary",
  components: {
    EventItemComp,
  },
  data() {
    return {
      events: {} as EventItem[],
    };
  },
  created() {
    EventService.getEvents()
      .then((response) => {
        this.events = response.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
});
</script>

<template>
  <div class="events">
    <h1>Events</h1>
    <EventItemComp v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<style>

</style>

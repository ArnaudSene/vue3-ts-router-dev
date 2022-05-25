<template>
  <div class="events">
    <div class="event-card">
      <span class="date-time">{{ event.date }}@{{ event.time }}</span> |
      <span class="origin">{{ event.origin }}</span> |
      <span class="event">{{ event.title }}</span> |
      <span class="description">{{ event.description }}</span>
      <router-link
        class="event-link"
        :to="{ name: 'eventDetail', params: { id: event.id } }"
      >
        <button class="detail-button">Detail</button>
      </router-link>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import type { PropType } from "vue";
import type { EventItem } from "@/types/EventType";

export default defineComponent({
  props: {
    event: {
      type: Object as PropType<EventItem>,
      required: true,
    },
  },
});
</script>

<style scoped>
.event-card {
  padding: 5px;
}
.event-link {
  /*pointer-events: none;*/
  /*cursor: default;*/
  /*text-decoration: none;*/
  color: white;
}
.detail-button:hover {
  cursor: pointer;
  transform: scale(1.01);
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2);
}
</style>
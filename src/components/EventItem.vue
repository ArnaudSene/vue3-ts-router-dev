<template>
  <div class="events">
    <div class="event-card">
      <span class="date-time">{{ event.date }}@{{ event.time }}</span> |
      <span class="origin">{{ event.origin }}</span> |
      <span class="event">{{ event.title }}</span> |
      <span class="description">{{ event.description }}</span>
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
  cursor: pointer;
  /*border: 1px solid #39495c;*/
  /*margin-bottom: 10px;*/
}
</style>
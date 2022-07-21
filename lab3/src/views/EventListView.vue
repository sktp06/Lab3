<template>
  <h1>Events for Good</h1>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
  <div class="category">
    <Categories v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from '@/components/EventCard.vue'
import Categories from '@/components/Categories.vue'
import EventService from '@/services/EventService.js'
export default {
  name: 'EventListView',
  components: {
    EventCard,
    Categories
  },
  data() {
    return {
      events: null
    }
  },
  created() {
    EventService.getEvents()
      .then((response) => {
        this.events = response.data
      })
      .catch((error) => {
        console.log(error)
      })
  }
}
</script>
<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
h4 {
  font-size: 20px;
}
.category {
  display: flex;
  text-align: right;
  flex-direction: column;
  align-items: center;
}
</style>

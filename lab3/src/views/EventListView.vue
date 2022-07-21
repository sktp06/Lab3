<template>
  <h1>Events For Good</h1>
  <div class="events">
    <!-- <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
  <div class="events">
    <!-- <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <Categories v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from '@/components/EventCard.vue'
import Categories from '@/components/Categories.vue'
import axios from 'axios'
export default {
  name: 'EventListView',
  components: {
    //   HelloWorld
    // }
    EventCard, //register it as a child component
    Categories
  },
  data() {
    return {
      // events: [
      //   {
      //     id: 5928101,
      //     category: 'animal welfare',
      //     title: 'Cat Adoption Day',
      //     description: 'Find your new feline friend at this event.',
      //     location: 'Meow Town',
      //     date: 'January 28, 2022',
      //     time: '12:00',
      //     petsAllowed: true,
      //     organizer: 'Kat Laydee'
      //   },
      //   {
      //     id: 4582797,
      //     category: 'food',
      //     title: 'Community Gardening',
      //     description: 'Join us as we tend to the community edible plants.',
      //     location: 'Flora City',
      //     date: 'March 14, 2022',
      //     time: '10:00',
      //     petsAllowed: true,
      //     organizer: 'Fern Pollin'
      //   },
      //   {
      //     id: 8419988,
      //     category: 'sustainability',
      //     title: 'Beach Cleanup',
      //     description: 'Help pick up trash along the shore.',
      //     location: 'Playa Del Carmen',
      //     date: 'July 22, 2022',
      //     time: '11:00',
      //     petsAllowed: false,
      //     organizer: 'Carey Wales'
      //   }
      // ]
      events: null
    }
  },
  created() {
    axios
      .get('http://localhost:3004/events')
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
</style>

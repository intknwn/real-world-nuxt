<template>
  <div>
    <h1>Events</h1>

    <EventCard
      v-for="(event, index) in events"
      :key="event.id"
      :event="event"
      :data-index="index"
    />
  </div>
</template>

<script>
import { mapState } from 'vuex'
import EventCard from '~/components/EventCard.vue'

export default {
  name: 'IndexPage',
  components: {
    EventCard,
  },
  async fetch({ store, error }) {
    try {
      await store.dispatch('events/fetchEvents')
    } catch (e) {
      error({
        statusCode: e.statusCode,
        message: 'Unable to fetch events at this time. Please try again.',
      })
    }
  },
  head() {
    return {
      title: 'Event Listing',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content:
            'Where you can find all events taking place in your neighborhood',
        },
      ],
    }
  },
  computed: mapState('events', ['events']),
}
</script>

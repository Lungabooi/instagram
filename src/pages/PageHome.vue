<template>
  <q-page class="constrain q-pa-md">
    <q-card 
    v-for='post in posts'
     :key="post.id"
    class="card-post q-mb-md"
    >
      <q-item>
        <q-item-section avatar>
          <q-avatar>
            <img src="https://cdn.quasar.dev/img/avatar2.jpg">
          </q-avatar>
        </q-item-section>

        <q-item-section>
          <q-item-label>Lunga</q-item-label>
          <q-item-label caption>{{post.location}}</q-item-label>
        </q-item-section>
      </q-item>

      <img :src="post.imageUrl">
      <q-card-section>
        <div >{{ post.caption}}</div>
        <div class="text-caption text-grey">{{post.date | niceDate}}</div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
// import { setServers } from 'dns';
import { date } from 'quasar'

export default {
  name: 'PageHome',
  data() {
    return {
      posts: [
        {
        id: 1,
        caption: "Golden Gate Bridge",
        date: 1665395411362,
        location: 'Cape Town Western Cape',
        imageUrl:'https://cdn.quasar.dev/img/parallax2.jpg'
        },

        {
        id: 2,
        caption: "Golden Gate Bridge",
        date: 1665395411362,
        location: 'Cape Town Western Cape',
        imageUrl:'https://cdn.quasar.dev/img/parallax2.jpg'
        },
        {
        id: 3,
        caption: "Golden Gate Bridge",
        date: 1665395411362,
        location: 'Cape Town Western Cape',
        imageUrl:'https://cdn.quasar.dev/img/parallax2.jpg'
        }
      ]
    }
  },
  filters:{
    niceDate(value) {
      return date.formatDate(value, 'MMMM D h:mmA')
    }
  }

}
</script>

<style lang="sass">
  .card-post
    .q-img
      min-height: 200px
</style>

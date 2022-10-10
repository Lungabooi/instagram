<template>
  <q-page class="constrain q-pa-md">
    <q-card class="my-card">
      <q-item>
        <q-item-section avatar>
          <q-avatar>
            <img src="https://cdn.quasar.dev/img/avatar2.jpg">
          </q-avatar>
        </q-item-section>

        <q-item-section>
          <q-item-label>Lunga</q-item-label>
          <q-item-label caption>Subhead</q-item-label>
        </q-item-section>
      </q-item>

      <img src="https://cdn.quasar.dev/img/parallax2.jpg">
      <q-card-section>
        <div class="text-h6">Golden Gate Bridge</div>
        <div class="text-subtitle2">June 10:09 AM</div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
export default {
  name: 'PageHome'
}
</script>

<style lang="sass">
  .card-post
    .q-img
      min-height: 200px
</style>

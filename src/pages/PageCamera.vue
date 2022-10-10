<template>
  <q-page class="constrain-more q-pa-md" >
   <div class="camera-frame q-pa-md">
    <img 
    class='full-width'
     src="https://cdn.quasar.dev/img/parallax2.jpg">
  
   </div>
   <div class="text-center q-pa-md">
    <q-btn
    color="grey-10"
    icon="eva-camera"
    size="lg"
    round >

    </q-btn>
    <div class="div row justify-center q-ma-md">
      <q-input
      v-model="text"
      label="Caption"
      class="col"
      >
    </q-input>
    </div>
    <div class="div row justify-center q-ma-md">
      <q-input
      v-model="text"
      label="Location"
      class="col"
      >
      

      <template v-slot:append>
        <q-btn 
        rounded 
        flat 
        icon="eva-navigation-2-outline">
      </q-btn>
      </template>
    </q-input>
    </div>
    <div class="row justify-center q-ma-md">  <q-btn unelevated rounded color="primary" label="Submit" /></div>
   </div>
  

  </q-page>
</template>

<script>
export default {
    name: 'PageCamera'
}
</script>

<style lang="sass">
.camera-frame
  border: 2px solid $grey-10
  border-radius: 10px

</style>
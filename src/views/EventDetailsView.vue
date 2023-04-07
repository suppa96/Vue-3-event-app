<template>
  <div>
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { EventService } from '@/services/EventService.js'
const event = ref(null) //abbiamo questo evento che faremo vedere utilizzando un metodo che recupera un evento solo dall'api

onMounted(() => {
  //quando viene mountata l'app facciamo la nostra chiamata API Axios
  EventService.getEvent(id).then(
    ((response) => {
      event.value = response.data
    }).catch((error) => console.log(error))
  )
})
</script>

<style lang="scss" scoped></style>

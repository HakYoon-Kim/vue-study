<template>
  <div v-for="(oneroom,i) in 원룸들" :key="i">
    <img :src="oneroom.image" class="room-img">
    <h4>{{ oneroom.title }}</h4>
    <p>{{ oneroom.price }}원</p>
  </div>
</template>

<script>
// @click="모달창열렸니 = true; 누른거 = i"
export default {
    name : "Card",
    props : {
        원룸들 : Object
    }
}
</script>

<style>

</style>
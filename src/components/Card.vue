<template>
  <div>
    <img :src="원룸.image" class="room-img">
    <h4 @click="send">{{ 원룸.title }}</h4>
    <p>{{ 원룸.price }}원</p>
  </div>
</template>

<script>
// 부모 App.vue의 데이터 변경불가능
// custom event 사용법(부모에게 메세지보내기)
// 1.자식은 $emit('작명')
// 2.부모는 메세지 받으려면 @작명한거=""
export default {
    name : "Card",
    props : {
        원룸 : Object
    },
    methods : {
      send(){
        this.$emit('openModal', this.원룸.id)
      }
    }
}
</script>

<style>

</style>
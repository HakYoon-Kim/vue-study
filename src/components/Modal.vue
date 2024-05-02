<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <img :src=원룸들[누른거].image class="room-img">
      <h4>{{ 원룸들[누른거].title }}</h4>      
      <p>{{ 원룸들[누른거].content }}</p>
      <p>{{ 원룸들[누른거].price }}원</p>
      <!-- <button @click="모달창열렸니 = false">닫기</button> -->
    </div>
  </div>
</template>

<script>
export default {
    name : 'Modal',
    props : {
        // props:{데이터이름:자료형이름}
        // 받아온 데이터의 자료형 이름을 대문자로
        원룸들 : Object,
        누른거 : Number,
        모달창열렸니 : Boolean
        // (주의)props는 read-only임
        // 받아온거 수정하면 큰일남
    }
}
</script>

<style>

</style>
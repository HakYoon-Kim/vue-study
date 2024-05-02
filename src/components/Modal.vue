<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <img :src=원룸들[누른거].image class="room-img">
      <h4>{{ 원룸들[누른거].title }}</h4>      
      <p>{{ 원룸들[누른거].content }}</p>
      <!-- <input @input="month = $event.target.value"> 아래꺼랑 같은거 -->
      <!-- <textarea v-model="month"></textarea> -->
      <!-- <select v-model="month"></select> -->
      <input v-model.number="month">
      <!-- 사용자가 input에 입력한 것은 전부 문자자료형 
      자바스크립트는 원래 숫자랑 문자랑 곱셈 이런거 됨, 덧셈은 문제 있음.. 문자열 옆에 붙어버림
      -->
      <p>{{ month }}개월 선택함 : {{ 원룸들[누른거].price * month }}원</p>
      <button @click="$emit('closeModal')">닫기</button>
      <!-- <button @click="모달창열렸니 = false">닫기</button> 이거 절대 안됨 -->
    </div>
  </div>
</template>

<script>
export default {
    name : 'Modal',
    data(){
      return {
        // 문자 입력받을거면 초기값을 문자로 하셈
        month : 1,
      }
    },
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
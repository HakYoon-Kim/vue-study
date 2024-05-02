<template>

  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <!-- <a v-for="(a,i) in 메뉴들" :key="i">{{ a }}</a> -->
    <a v-for="a in 메뉴들" :key="a">{{ a }}</a>
  </div>

  <!-- 
   = 반복문 = 
   <태그 v-for="작명 in 몇회">
  -->
  <!-- <div v-for="a in products" :key="a">
    <h4>{{ a }}</h4>
    <p>50 만원</p>
  </div> -->

  <div v-for="(oneroom,i) in 원룸들" :key="i">
    <img :src="원룸들[i].image" class="room-img">
    <h4 @click="모달창열렸니 = true">{{ 원룸들[i].title }}</h4>
    <p>{{ 원룸들[i].price }}원</p>
  </div>
     
</template>

<script>

import data from './assets/oneroom';

export default {
  name: 'App',
  // 데이터 보관함(object자료로 저장해야함)
  data(){
    return {
      // 동적인 UI만드는 법
      // 0.디자인해두고
      // 1.UI의 현재 상태를 데이터로 기록
      // 2.데이터에 따라 UI가 어떻게보일지 작성
      모달창열렸니 : false,
      신고수 : [0, 0, 0],
      메뉴들 : ['Home', 'Shop', 'About'],
      //products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      원룸들 : data
    }
  },
  methods : {
    // Vue에서 함수만들 때 주의사항
    // 함수안에서 데이터 쓸 땐 this.데이터명 걍 암기!!
    increase(){
      this.신고수++;
    }
  },
  components: {
    
  }
}

</script>

<style>
body  {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

</style>

<template>

  <!-- 
    자식컴포넌트가 부모가 갖고 있는 데이터 쓰려면
    props로 데이터를 전송해야함

    1.데이터보내고
    2.등록하고
    3.쓰셈

    v-bind :
  -->
  <!-- <div class="start" :class="{ end : 모달창열렸니 }"> -->
  <!-- 위에꺼랑 똑같은건데, 좀 편하게 할 수 있는방법 from to -->
  <transition name="fade">
    <Modal @closeModal="모달창열렸니=false" 
    :원룸들="원룸들" :누른거="누른거" 
    :모달창열렸니="모달창열렸니" />
  </transition>  
  <!-- </div> -->

  <div class="menu">
    <!-- <a v-for="(a,i) in 메뉴들" :key="i">{{ a }}</a> -->
    <a v-for="a in 메뉴들" :key="a">{{ a }}</a>
  </div>

  <Discount/>

  <button @click="priceSort">가격순정렬</button>
  <button @click="sortBack">되돌리기</button>

  <!-- 
    축약해둔 컴포넌트 쓰는 법
    1.vue파일 import해오고
    2.등록하고
    3.쓰셈

    왜 컴포넌트 사용?
    1. 아름다워
    2. 재사용쉬움

    초보 특)
    온갖거 다 컴포넌트로 만들어둠
    반복적으로 출현할 부분만 컴포넌트화 권장
  -->

  <!-- 
   = 반복문 = 
   <태그 v-for="작명 in 몇회">
  -->
  <!-- <div v-for="a in products" :key="a">
    <h4>{{ a }}</h4>
    <p>50 만원</p>
  </div> -->

  <Card @openModal="모달창열렸니 = true; 누른거 = $event" :원룸="원룸들[i]" v-for="(one,i) in 원룸들" :key="one"/>
     
</template>

<script>

import data from './assets/oneroom';
import Discount from './components/Discount.vue';
import Modal from './components/Modal.vue';
import Card from './components/Card.vue';

export default {
  name: 'App',
  // 데이터 보관함(object자료로 저장해야함)
  data(){
    return {
      // array/object데이터의 각각 별개의 사본을 만들려면
      // [...array자료] 이거도 암기!
      원룸들오리지널 : [...data],
      // 동적인 UI만드는 법
      // 0.디자인해두고
      // 1.UI의 현재 상태를 데이터로 기록
      // 2.데이터에 따라 UI가 어떻게보일지 작성
      모달창열렸니 : false,
      신고수 : [0, 0, 0],
      메뉴들 : ['Home', 'Shop', 'About'],
      //products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      원룸들 : data,
      누른거 : 0,
      오브젝트 : { name : 'kim', age : 20 }
    }
  },
  methods : {
    // Vue에서 함수만들 때 주의사항
    // 함수안에서 데이터 쓸 땐 this.데이터명 걍 암기!!
    increase(){
      this.신고수++;
    },
    priceSort(){
      // var array = [3,5,2].sort()
      // 이거는 문자 정렬임
      // 숫자 정렬은 어떻게 하냐면
      // array.sort(function(a,b){return a - b});
      // 그냥 암기하는게 좋음
      // (참고)sort()하면 원본이 변형됨(요즘 코딩 관습과 약간 맞지 않음)
      // map() filter() 등은 원본을 보존해줌

      // 해볼것
      // 가격낮은순정렬, 가격높은순정렬, 상품명 가나다순 정렬
      this.원룸들.sort(function(a,b){
        return a.price - b.price
      })
    },
    sortBack(){
      this.원룸들 = this.원룸들오리지널;
    }
  },
  components: {
    Discount : Discount,
    Modal : Modal,
    Card : Card
  }
}

</script>

<style>
.fade-leave-from { 
  opacity: 1;
}
.fade-leave-active { 
  transition: all 1s;
}
.fade-leave-to { 
  opacity: 0;
} 

.fade-enter-from { 
  /* opacity: 0; */
  transform: translateY(-1000px);
}
.fade-enter-active { 
  transition: all 1s;
}
.fade-enter-to { 
  /* opacity: 1; */
  transform: translateY(0px);
} 

.start {
  opacity: 0;
  transition: all 1s;
}
.end {
  opacity: 1;
}

body  {
  margin: 0;
}
div {
  box-sizing: border-box;
}

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
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

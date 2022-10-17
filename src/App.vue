<template>
  <h1>
    <img alt="Vue logo" src="./assets/logo.png" />
    <span>VUE DONG SAN</span>
  </h1>

  <div class="menu">
    <a v-for="(link,i) in menu" :key="i" href="javascript:;">{{link}}</a>
  </div>

  <!-- <div class="start" :class="{end:isShowPopup}"> -->
  <transition name="fade">
    <Modal
      :rooms="rooms" 
      :itemId="itemId"
      :isShowPopup="isShowPopup" 
      @closeModal="isShowPopup=$event" 
    />
  </transition>


  <!-- <Discount v-if="showDiscount==true" /> -->
  <Discount v-if="showDiscount==true" />

  <button @click="priceSort">가격순정렬</button>
  <button @click="sortBack">되돌리기</button>

  <div class="list-wrap">
    <Card 
      @openModal="isShowPopup=true" 
      @report="rooms[i].report++" 
      :room="rooms[i]" 
      v-for="(room, i) in rooms" :key="i" 
    />
  </div>


<!-- if, else if, else
  <div v-if="1 == 2">
    안녕하세요1
  </div>
  <div v-else-if="1 == 3">
    안녕하세요2
  </div>
  <div v-else>
    안녕하세요3
  </div>
-->

</template>




<script>
import roomData from './assets/oneroom';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';

export default {
  name: 'vuedongsan',
  data(){ // state
    return{
      showDiscount:true,
      roomsOriginal:[...roomData], // 별개의 사본 만들기
      itemId:0,
      rooms:roomData,
      menu:['Home', 'Shop', 'About'],
      isShowPopup:false,
    }
  },
  methods:{ // function
    increase(i){
      this.rooms[i].report++; // 함수안에서 데이터 쓸 땐 this.데이터명
    },
    priceSort(){
      this.rooms.sort(function(a,b){
        return a.price - b.price;
      })
    },
    sortBack(){
      // this.rooms = this.roomsOriginal;
      this.rooms = [...this.roomsOriginal]; // 값 공유할때도 복사본으로
    },
  },
  // vue lifecycle hook (여러개 있음)
  mounted(){
    // mount 되고 난 후에 실행할 소스
    //setTimeout(function(){  <= function을 쓰면 this 위치가 달라지므로 화살표함수 사용
    
    setTimeout(()=>{
      this.showDiscount = false;
    },2000)
  },
  components:{
    Discount:Discount,
    Modal:Modal,
    Card:Card,
  }
}
</script>



<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  display:flex;
  justify-content: center;
  align-content: center;
}
h1 img {
  height:30px;
  position: relative;
  top:3px;
}

.menu {
  background: darkslateblue;
  padding:15px;
  border-radius:5px;
}
.menu a{
  color:white;
  padding:10px;
  text-decoration: none;
}
body{
  margin:0;
}
div{
  box-sizing:border-box;
}

.list-wrap {
  display:flex;
  justify-content: center;
  align-content: center;
  flex-wrap: wrap;
  padding:20px;
}
.start{
  opacity: 0;
  transition:all 1s;
}
.end {
  opacity: 1;
}

.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition:all 1s;
}
.fade-enter-to {
  opacity: 1;
}
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition:all 1s;
}
.fade-leave-to {
  opacity: 0;
}
</style>

<template>
  <h1>
    <img alt="Vue logo" src="./assets/logo.png" />
    <span>UE DONG SAN</span>
  </h1>

  <div class="menu">
    <a v-for="(link,i) in menu" :key="i" href="javascript:;">{{link}}</a>
  </div>

  <Modal
    :rooms="rooms" 
    :itemId="itemId"
    :isShowPopup="isShowPopup" 
    @closeModal="isShowPopup=$event" 
  />
  <Discount />

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
      itemId:0,
      rooms:roomData,
      menu:['Home', 'Shop', 'About'],
      isShowPopup:true,
    }
  },
  methods:{ // function
    increase(i){
      this.rooms[i].report++; // 함수안에서 데이터 쓸 땐 this.데이터명
    },
    showPopup(i){
      // console.log(this.itemId)
      this.isShowPopup=true;
      this.itemId=i;
      /* this.popup.image=this.rooms[i].image;
      this.popup.title=this.rooms[i].title;
      this.popup.content=this.rooms[i].content; */
    },
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

</style>

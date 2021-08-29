<template>

  <h1>
    <img alt="Vue logo" src="./assets/logo.png" />
    <span>UE DONG SAN</span>
  </h1>

  <div class="menu">
    <a v-for="(link,i) in menu" :key="i" href="javascript:;">{{link}}</a>
  </div>

  <div class="list-wrap">
    <div v-for="(room,i) in rooms" :key="i" class="list">
      <!-- <img src="./asssets/room0.jpg" alt=""> -->
      <img :src="room.image" :alt="room.title + '방 이미지'">
      <a href="javascript:;" class="room-title" @click="showPopup(i)">{{room.title}}</a>
      <p>{{room.price}} 만원</p>
      <button @click="increase(i)">허위매물신고</button> 
      <span>신고수 : {{room.report}}</span>
    </div>
  </div>

  <div class="popup" v-if="isShowPopup" @click="isShowPopup=false">
    <div class="contents">
      <img :src="popup.image" alt="선택한 방 이미지">
      <h4>{{popup.title}}</h4>
      <p>{{popup.content}}</p>
      <button class="close-button" @click="isShowPopup=false">X</button>
    </div>
  </div>

</template>




<script>
import roomData from './assets/oneroom';

export default {
  name: 'vuedongsan',
  data(){ // state
    return{
      rooms:[
        ...(roomData.map(data => {
          return(
            {...data, report:0}
          )
        }))
      ],
      menu:['Home', 'Shop', 'About'],
      popup:{
        image:'방 이미지',
        title:'방 이름',
        content:'방 설명'
      },
      isShowPopup:false,
    }
  },
  methods:{ // function
    increase(i){
      this.rooms[i].report++; // 함수안에서 데이터 쓸 땐 this.데이터명
    },
    showPopup(i){
      this.isShowPopup=true;
      this.popup.image=this.rooms[i].image;
      this.popup.title=this.rooms[i].title;
      this.popup.content=this.rooms[i].content;
    },
  },
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
.list-wrap .list {
  width:33.3333%;
  padding:45px 15px;
}
.list-wrap .list img {
  width:100%;
}
.room-title {
  display:block;
  margin-top:20px;
  font-weight: bold;
  color:#333;
}
.room-title:hover {
  color: blue;
}


/* 팝업창 */
.popup {
  width:100%; height:100%;
  background: rgba(0,0,0,0.5);
  position:fixed; padding:20px;
  top:0;left:0;
}
.contents {
  width:100%; background: #fff;
  border-radius:8px;
  padding:20px;
  position: relative;
  max-width:700px;
  top:10%;
  margin:0 auto;
}
.contents img {
  width:100%;
}
.close-button {
  position:absolute;
  right:10px;
  top:10px;
  background:none;
  font-size:24px;
  border:0;
  outline:0;
  cursor: pointer;
}

@media screen and (max-width:767px){
  .list-wrap .list {
    width:50%;
    padding:25px 5px;
  }
}
</style>

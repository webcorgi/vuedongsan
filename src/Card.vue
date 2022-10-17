<template>
<div class="list">
    <img :src="room.image" :alt="room.title + '방 이미지'">
    <a href="javascript:;" class="room-title" @click="$emit('openModal')">{{room.title}}</a>
    <p>{{room.price}} 만원</p>
    <button @click="$emit('report')">허위매물신고</button> 
    <span>신고수 : {{room.report}}</span>
</div>
</template>

<script>
export default {
    name:'Card',
    props:{
        room:Array,
    }
}
</script>

<style>
.list {
  width:33.3333%;
  padding:45px 15px;
}.list img {
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


@media screen and (max-width:767px){
  .list {
    width:50%;
    padding:25px 5px;
  }
}
</style>
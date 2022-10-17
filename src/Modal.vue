<template>
  <div class="popup" v-if="isShowPopup==true">
  
    <div class="contents">
      <img :src="rooms[itemId].image" alt="선택한 방 이미지">
      <h4>{{rooms[itemId].title}}</h4>
      <p>{{rooms[itemId].content}}</p>
      <!-- <input type="number" @input="month = $event.target.value"> -->
      <input type="number" v-model="month">
      <p>{{month}}개월 선택함 : {{rooms[itemId].price * month}}만원</p>

      <button class="close-button" @click="closePopup()">X</button>
    </div>
  </div>
</template>

<script>
export default {
    name:'Modal',
    data(){
        return{
            month:1, // 사용자가 input에 입력한 것은 전부 문자자료형
        }
    },
    props:{
        rooms:Array, // array, Object, String, Number,Boolean (형식작성. 틀려도 에러안남. 걍 확인용임)
        itemId:Number,
        isShowPopup:Boolean,
    },
    methods:{
        closePopup(){
            this.$emit('closeModal', false)
        }
    }
}
</script>

<style>


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
</style>
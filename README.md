# vuedongsan

https://webcogy.github.io/vuedongsan/

#### skill list

- vue js
- node js

## Project setup

```
yarn install
```

### Compiles and hot-reloads for development

```
yarn serve
```

### Compiles and minifies for production

```
yarn build
```

### Lints and fixes files

```
yarn lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

### vue 깃페이지 배포방법 참고 (vue-gh-pages)

https://github.com/KieferSivitz/vue-gh-pages

---

## 목차

1. vue cli 설치
1. vue 프로젝트 생성
1. v-for
1. v-if
1. 이벤트 등록 v-on, @
1. {{어쩌구}}, :어쩌구

---

## 1. vue cli 설치

vue 명령어를 사용하려면 필수

```
npm install -g @vue/cli
```

## 2. vue 프로젝트 생성

```
vue create 프로젝트명
```

## 3. v-for

ex) v-for="작명 in 몇번반복 : key="작명"

- '몇번반복' 자리에 array/object 집어넣기 가능.
- 그럼 자료안의 데이터 갯수만큼 반복됨.

```
<a v-for="link in menu" :key="link">{{link}}</a> // 축약사용법
<a v-for="(link,i) in menu" :key="i" href="javascript:;">{{link}}</a>
```

## 4. v-if, v-else, v-else-if

참 일때만 HTML 보여줌. 참이 아닐 때 v-else를 보여줌. v-else-if 다른 조건을 추가.

```
<div v-if="isShowPopup">ㅎㅇ</div>
<div v-else>ㅎㅇ2</div>
<div v-else-if="1 == 3">ㅎㅇ3</div>

```

## 5. v-on, @

이벤트 등록
v-on:click="" or @click=""

```
<button @click="isShowPopup=false">
<button @click="increase(i)">
```

## 6. {{어쩌구}}, :어쩌구

- {{어쩌구}} => html태그안의 '내용' 바인딩 (이거써야 자동 랜더링됨)
- :어쩌구 => html태그안의 '속성' 바인딩

```
// src에 있는거 가져올 땐 ./부터 (웹팩문법) => "./assets/room0.jpg"
<img :src="room.image" :alt="room.title + '방 이미지'">
```

## 7. component 만들어쓰기

0. 컴포넌트.vue 만들기
1. (App.vue에서) vue파일 import해오고
1. 등록하고
1. 쓰기

vue 탬플릿 생성 단축키 =>> ' < 엔터 '

```
<script>
1. 임포트
import Discount from './Discount.vue';
...

2. 등록
export Default{
  components:{
    Discount:Discount,
  }
}
</script>

3. 쓰기
<Discount />
or
<Discount></Discount>
```

## 8. props

- props로 자식에게 데이터 보내는 법

1. 데이터 보내고
2. 등록하고
3. 쓰기

```
<Modal v-bind:데이터이름(작명가능)="데이터이름" />
or
<Modal :데이터이름(작명가능)="데이터이름" />

※ 일반 문자는 v-bind없이도 전달가능함.
ex) <Modal 데이터이름="안녕하세요" />
    작명="문자자료"
    :작명="숫자자료"

```

※ props로 보낸 데이터는 수정금지

## 9. 컴포넌트간 이벤트 전달 \$emit

1. 부모에게 메세지 보낼 땐 >> \$emit('작명', 데이터) // 데이터 실어 보내기 가능
2. 부모가 메세지 수신할 땐 >> @작명="isShowPopup=true"
3. 부모에게 보낸 데이터를 부모가 받을 땐 $event로 받기 가능 >> @작명="isShowPopup=$event"

- 자식이 부모가 갖고 있는 데이터를 직접 변경할 수 없기 때문에, \$emit으로 부모한테 변경해달라고 '요청' 하는 것임.

4. \$emit()을 함수안에서 하고 싶으면

```
<button @click="함수">

export default{
    ...
    methods:{
        함수(){
            this.$emit('작명', this.데이터) // methods에서 상단의 props,data,$변수 모두 this 꼭 붙여야함
        }
    }
}
```

## 10. input, textarea, select에 사용가능한 v-model

1. @input="month = $event.target.value" // 파라미터 e == $event
2. v-model="month" // v-model >> 1번의 약어.
3. checkbox 는 true/false로도 받을 수 있음.

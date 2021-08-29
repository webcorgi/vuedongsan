# vuedongsan

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

---

## 목차

1. vue cli 설치
2. vue 프로젝트 생성
3. v-for
4. v-if
5. 이벤트 등록 v-on, @
6. {{어쩌구}}, :어쩌구

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

## 4. v-if

참 일때만 HTML 보여줌

```
<div v-if="isShowPopup"></div>
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

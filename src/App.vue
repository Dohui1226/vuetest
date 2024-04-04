<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button @click="모달창열렸니 = false">닫기</button>
  </div> 
</div>
<!--UI 만들기 -->
<!--1. UI 현재 상태를 데이터로 저장한다.-->
<!--2. 데이터에 따라 UI가 어떻게 보일지 작성-->


  <div class="menu">
    <a v-for="(xx, i) in 메뉴들" :key="xx">{{xx}}{{ i }}</a>
    <!--vue 반복문은 array/object 집어 넣기가 가능-->
  </div>
  

  <div>
    {{ logo }} <!--자주 변하지 않는 데이터는 보통 이런식으로 랜더링 하지 않음-->
    <div v-for="(a,i) in 3" :key="a">
      <h4>{{ products[i]}}</h4>
    </div>
  </div>


   <div>
    <img src="./assets/room0.jpg">
    <h4 @click="모달창열렸니 = true">{{ products[0] }}</h4>
    <p>50만원</p>
    <button @click="신고수[0]++">허위매물신고</button> <span>신고수 : {{ 신고수[0] }}</span>
   </div>
   <div>
    <img src="./assets/room1.jpg">
    <h4>{{ products[1] }}</h4>
    <p>50만원</p>
    <button @click="신고수[1]++">허위매물신고</button> <span>신고수 : {{ 신고수[1] }}</span>
   </div>

   <div>
    <img :src="원룸들[2].image">
    <h4>{{ 원룸들[2].title}}</h4>
    <p>{{ 원룸들[2].price }}</p>
    <button @click="신고수[2]++">허위매물신고</button> <span>신고수 : {{ 신고수[2] }}</span>
   </div>



</template>

<script>
//리액트가 가장 많이 쓰는데 왜 뷰를 카카오가 씀? 쉬움. 개발할 방법이 정해짐, 리액트보다 랜더링이 더빠름

//데이터 바인딩 하는 이유. 1. 하드코딩시 변경작업이 있을 경우 손이 많이감. 
//                    2. 실시간 자동 렌더링을 쓰기위함 --> 웹앱 

import data from './oneroom.js'

export default {
  name: 'App',
  data(){
    return {
      원룸들 : data,
      모달창열렸니 : false,
      신고수 : [0,0,0],
      price1: 60,
      price2 :70,
      logo : '원룸샵',
      스타일 : 'color blue',
      products : ['역삼동 원룸', '천호동원룸', '마포구원룸' ],
      메뉴들 : ['Home', 'Shop', 'About']
    }
  },
methods : {
  increase(){
    this.신고수 +=1;
  }
},


  components: {
    
  }
}
</script>

<style>
body{
  margin : 0
}

div{
  box-sizing:border-box;
}

.black-bg{
  width : 100%; height:100%;
  background: rgba(0,0, 0, 0.5);
  position : fixed; padding: 20px;

}

.white-bg{
 width : 100%; background: white;
 border-radius: 8px;
 padding: 20px;


}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}


.menu {
  background: darkgoldenrod;
  padding : 15px;
  border-radius: 5px;
}
.menu a{
  color: white;
  padding: 10px;
}

</style>

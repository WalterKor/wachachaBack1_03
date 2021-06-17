<template>

    <div class="menu">
      <a v-for="a in menu" :key="a">{{a}}</a>
    </div>

    <Banner/>

    <div v-for="k in data" :key="k" class="okchanho">
      <h3 @click="OpenModal = true; point = k">{{k.title}}</h3>
      <img :src="k.image" class="foster-size">
      <P @click="openMo == true">{{k.content}}</P>
    </div>



    <!--모달창만들기-->
    <div class="black-bg" v-if="OpenModal = true">
      <div class="white-bg">
          <h4>{{ data[point].title }}</h4>
          <img :src="data[point].image" class="foster">
          <p> {{ data[point].content }}</p>
          <button @click="OpenModal = false">닫기</button>
      </div>
      <button @click="OpenModal = false">닫기</button>
    </div>

    <div v-if= "openMo = true" class="black-bg">
      <div class="white-bg">
        <h4>안녕하세요</h4>
        <button @click="openMo = false">닫기</button>
      </div>
    </div>

</template>

<script>
import data from './assets/Movie.js';
import Banner from './components/Banner.vue';


export default {
  name: 'App',
  data(){
    return{
      point : 0,
      menu : ['MainHome', 'List', 'Login'],
      data : data,
      OpenModal : false,
      openMo : false,
    }
  },
  components: {
    Banner : Banner,
  }
}
</script>

<style>

 div{
  box-sizing: border-box;
}
.menu{
  background: coral;
  padding: 20px;
  border-radius: 10px;
}

.menu a{
  color: white;
  padding: 10px;
  font-weight: bold;
  text-align: center;
}
.foster-size{
  height: 700px;
  width: 450px;
  display: inline-block;
}

.okchanho p{
  cursor: pointer;
}

.black-bg{
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;
}
.white-bg{
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}


</style>

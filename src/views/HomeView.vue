<template>
  <div class="home">
    <Header msg="Welcome to Your Vue.js + TypeScript App"/>
    <div class="background_wrap">
      <h1 class="title">Please search for a station.</h1>
      <div class="background_input_wrap">
        <input type="text" class="search_input" v-model="values"/>
        <router-link to="/Detail" class="search_btn">
          <button class="search_btn_detail" @click="Details">Search</button>

        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
  import { Options, Vue } from 'vue-class-component'
  import Header from '@/components/Header.vue' // @ is an alias to /src

  @Options({
    components: {
      Header
    }
  })

export default class extends Vue {

  Details(){
    alert(this.values);
  }

  fetchTodo() {
    const url1 = 'https://api.odcloud.kr/api/15041096/v1/uddi:e83cfa23-23e6-4d02-a061-cb427648c51e?page=1&perPage=22&serviceKey=suyekkuR7SRO2720g7tgje0Nr1frEuxvzTGqC29kOGrjWzm8b3jdikE0%2Fz4HtHCm3YSdxOp%2FLnAtzPwwATb6lg%3D%3D';
    try {
        fetch(url1).then(response => response.json())
        .then(data =>{
          console.log(data.data[0]);
          // for(let i=0; i<21; i++){
            
          // }
        });
      } catch (error) {
      console.log(error);
    }
  }
  data(){
    return{
      values: '',
    }
  }
}
</script>
<style scoped>
  .background_wrap {
    background-image: url('https://www.bglrt.com/ImagePrint.do?q=200&key=mimg&name=vpr20220622.jpg');
    height:75vh;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  .title {
    font-size:45px;
    margin-top: -200px;
  }
  .search_input {
    margin-top:30px;
    width:400px;
    height:40px;
    border:none;
    border-bottom: 4px solid #2C3E50;
    opacity: 1;
    outline: none;
    text-align: center;
    font-size:34px;
    background-color: transparent;
    font-weight:700;
    color: #2C3E50;
  }

  .search_btn_detail {
    text-decoration: none;
    border-radius: 4px;
    margin-left:10px;
    background-color: #2C3E50;
    border: 2px solid #2C3E50;
    padding: 5px 10px 5px 10px;
    font-size:20px;
    font-weight: 700;
    color:white;
  }
  .search_btn_detail:hover {

    background-color:#445566;
  }
</style>

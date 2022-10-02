<template>
  <div class="home">
    <Header />
    <div class="background_wrap">
      <h1 class="title">Please search for a station.</h1>
      <div class="background_input_wrap">
        <input type="text" class="search_input" v-model="values"/>
          <button class="search_btn_detail" @click="Details">Search</button>
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
    let count = 0;
    const url1 = 'https://api.odcloud.kr/api/15041096/v1/uddi:e83cfa23-23e6-4d02-a061-cb427648c51e?page=1&perPage=22&serviceKey=suyekkuR7SRO2720g7tgje0Nr1frEuxvzTGqC29kOGrjWzm8b3jdikE0%2Fz4HtHCm3YSdxOp%2FLnAtzPwwATb6lg%3D%3D';
    try {
        fetch(url1).then(response => response.json())
        .then(data =>{
          for(let i=0; i<=20; i++){
            if(this.values === data.data[i].역명.slice(0, data.data[i].역명.indexOf('(') === -1 ? 10 : data.data[i].역명.indexOf('('))){
              alert(`
              ${data.data[i].역명}역
              도로명주소 : ${data.data[i].도로명주소} 
              지번주소 : ${data.data[i].지번주소}
              철도운영기관명 : ${data.data[i].역명}
            
              모든 경전철의 세부 정보를 원하신다면 타이틀을 클릭해주세요.`)
            } else {
              count++;
            }
          }
          if(count===21){
            alert('역을 찾을 수 없습니다. 정확하게 입력해주세요.')
          }
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

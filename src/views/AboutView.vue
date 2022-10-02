<template>
  <div class="about">
    <Header />
    <div :key="i" v-for="i in 20" id="trail_box_wrap">
      <div class="trail_wrap">
        <h1 class="station">{{ name.data[i] }}역</h1>
        <h1 class="stations">{{ station.data[i] }}</h1>
        <h1 class="address">도로명주소 : {{ address.data[i]}}</h1>
        <h1 class="location">지번주소 : {{ location.data[i]}}</h1>
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

  data(){
    return {
      name: { data:[] },
      address: { data:[] },
      location: { data:[] },
      station: { data:[] },
    }
  }
  mounted(){
    const url1 = 'https://api.odcloud.kr/api/15041096/v1/uddi:e83cfa23-23e6-4d02-a061-cb427648c51e?page=1&perPage=22&serviceKey=suyekkuR7SRO2720g7tgje0Nr1frEuxvzTGqC29kOGrjWzm8b3jdikE0%2Fz4HtHCm3YSdxOp%2FLnAtzPwwATb6lg%3D%3D';
    try {
        fetch(url1).then(response => response.json())
        .then(data =>{
          console.log(data.data[0])
          for(let i=0; i<=20; i++){
            this.name.data[i] = data.data[i].역명.slice(0, data.data[i].역명.indexOf('(') === -1 ? 10 : data.data[i].역명.indexOf('('));
            this.address.data[i] = data.data[i].도로명주소
            this.location.data[i] = data.data[i].지번주소
            this.station.data[i] = data.data[i].선명
          }
        });
      } catch (error) {
        console.log(error);
      }
  }
}
</script>
<style scoped>
  #trail_box_wrap {
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
  }
  .trail_wrap {
    width:50vw;
    height:90px;
    border-top:2px solid #ccc;
    margin: 20px 0px;
  }

  .station {
    font-size: 30px;
    margin:10px;
  }

  .address {
    font-size: 16px;
  }

  .location {
    font-size: 16px;
  }

  .stations {
    margin-top: -10px;
    font-size: 20px;
  }

  .hidden {
    display: none;
  }
</style>
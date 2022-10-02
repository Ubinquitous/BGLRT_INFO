<template>
    <div class="header_wrap">
      <div class="header_box">
        <router-link to="/"><img src="https://www.bglrt.com/_res/default/img/inc/logo_bgl(k).png" alt="부산김해경전철" class="logo" /></router-link>
      </div>
      <div class="custom_line" />
      <div class="header_box_title">
        <h1><router-link to="/detail" class="title">Busan-Gimhae Light Rail Transit Information</router-link></h1>
      </div>
    </div>
  </template>
  
  <script lang="ts">
  import { Options, Vue } from 'vue-class-component'
  
  @Options({
    props: {
      msg: String
    }
  })
  export default class Header extends Vue {
    msg!: string
  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>

    .header_wrap {
      width:100%;
      height:25vh;
      display: flex;
      justify-content: center;
      flex-direction: column;
      align-items: center;
    }
    .header_box {
      flex-direction: column;
      display: flex;
      justify-content: center;
      align-items: center;
      width:100%;
      height:90px;
    }

    .title {
      color:#2C3E50;
    }

    .custom_line {
      margin-top:20px;
      width:46vw;
      height:2px;
      background-color:#ccc;
    }
    .header_box_title {
      display: flex;
      justify-content: center;
      align-items: center;
      width:100%;
      height:70px;
    }
    .logo {
      margin-top:20px;
      width:150px;
      height:55px;
    }
  </style>
  
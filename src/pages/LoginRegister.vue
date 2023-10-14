<script setup lang="ts">//指定typescript为编程语言

import LoginInputs from "../components/LoginInputs.vue";//报错？？但不影响运行？
import RegisterInputs from "../components/RegisterInputs.vue";

const valid = ref(true)

import {ref, onMounted, onBeforeUnmount} from "vue";
const loginMoveUpIsActive = ref(true)
const loginMoveDownIsActive = ref(false)
const loginHiddenIsActive = ref(false)
const registerMoveUpIsActive = ref(false)
const registerMoveDownIsActive = ref(true)
const registerHiddenIsActive = ref(true)
const guideUpHiddenIsActive = ref(true)

const scroll = (event) => {
  event.preventDefault();//阻止默认行为，这里是页面滚动
  const delta = event.deltaY;
  if (delta < 0) {
    console.debug("滚动1R");
      registerMoveUpIsActive.value=false,
      registerMoveDownIsActive.value=true,
      registerHiddenIsActive.value=true,
          console.debug("滚动1L");
      loginMoveUpIsActive.value=true,
      loginMoveDownIsActive.value=false,
      loginHiddenIsActive.value=false,

      guideUpHiddenIsActive.value=true
  } else if (delta > 0) {
    console.debug("滚动2R");
      registerMoveUpIsActive.value= true,
      registerMoveDownIsActive.value=false,
      registerHiddenIsActive.value=false
       console.debug("滚动2L");
      loginMoveUpIsActive.value= false,
      loginMoveDownIsActive.value=true,
      loginHiddenIsActive.value=true
   
      guideUpHiddenIsActive.value=false
  }
}
</script>

<template>
  <v-form v-model="valid" id="lr">
  <v-container class="scrollPlace"  @wheel="scroll">
  <LoginInputs :loginMoveUpIsActive="loginMoveUpIsActive"
  :loginMoveDownIsActive="loginMoveDownIsActive"
  :loginHiddenIsActive="loginHiddenIsActive"
  ></LoginInputs>
  <RegisterInputs :registerMoveUpIsActive="registerMoveUpIsActive"
  :registerMoveDownIsActive="registerMoveDownIsActive"
  :registerHiddenIsActive="registerHiddenIsActive"
  ></RegisterInputs>
  </v-container>
  </v-form>
  <!---用户引导图片（注册和登录页面）--->
  <v-container>
      <img src="src/img/up1.png" alt="up" id="guideUp" :class="{ 'hidden': guideUpHiddenIsActive}">
      <img src="src/img/down1.png" alt="down" id="guideDown" :class="{ 'hidden': !guideUpHiddenIsActive}">
    </v-container>
</template>

<style src="@/assets/style.css"></style>
<script setup lang="ts">
import {ref} from "vue";
import LoginModal from "../components/LoginModal.vue";

const showAnotherLoginFeishu = ref(false)
const showAnotherLoginWeixin = ref(false)

const showWeixin = () => {
  showAnotherLoginWeixin.value=true
};
const showFeishu = () => {
  showAnotherLoginFeishu.value=true
};
const closeFeishu = () => {
    console.debug('click');
    showAnotherLoginFeishu.value=false
}
const closeWeixin = () => {
    console.debug('click');
    showAnotherLoginWeixin.value=false
}
</script>


<template>
    <v-container>
      <h2 id="anotherlogin">其他登录方式</h2>
      
      <img src="../img/微信logo.png" alt="微信登录" id="weixin" @click="showWeixin">
        <v-container calss="modal">
          <v-container v-show="showAnotherLoginWeixin" class="modal-mask">
            <LoginModal
              :showAnotherLoginWeixin="showAnotherLoginWeixin"
            ></LoginModal>
            <v-btn color="yellow" @click="closeWeixin" v-show="showAnotherLoginWeixin" class="anotherLoginBtn">close</v-btn>
          </v-container>
        </v-container>
      

      <img src="../img/飞书logo.png" alt="飞书登录" id="feishu" @click="showFeishu">
      <v-container v-show="showAnotherLoginFeishu" class="modal-mask">
        <v-container calss="modal">
            <LoginModal
              :showAnotherLoginFeishu="showAnotherLoginFeishu"
            ></LoginModal>
          <v-btn color="pink white--text" @click="closeFeishu" v-show="showAnotherLoginFeishu" class="anotherLoginBtn">close</v-btn>
        </v-container>
      </v-container>
    </v-container>
</template>




<style src="@/assets/style.css"></style>

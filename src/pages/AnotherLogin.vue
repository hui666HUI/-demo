<script setup lang="ts">
import {ref} from "vue";
import LoginModal from "../components/LoginModal.vue";

const showAnotherLoginFeishu = ref(false)

const showFeishu = () => {
  showAnotherLoginFeishu.value=true
};
const closeFeishu = () => {
    console.debug('click');
    showAnotherLoginFeishu.value=false
}
const dialog = ref(false)
</script>


<template>
    <v-container>
      <h2 id="anotherlogin">其他登录方式</h2>
      
      <img src="../img/微信logo.png" alt="微信登录" id="weixin" @click="dialog = true">
      <v-dialog
        v-model="dialog"
        width="auto"
      >
        <v-card>
          <v-card-text>
            微信登录
          </v-card-text>
          <v-card-actions>
            <v-btn color="primary" block @click="dialog = false">Close Dialog</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
      

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

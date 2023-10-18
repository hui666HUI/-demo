<script setup lang="ts">
import {ref, onMounted, onBeforeUnmount} from "vue";
import { defineProps } from 'vue';
import axios from 'axios'


const valid = ref(true)
const email = ref('')
const password = ref('')
const name = ref('虎!')

const verificationCode = ref('')

const emailRulesR = [
  (v: string) => !!v || '必须填写邮箱',
  (v: string) => /.+@.+/.test(v) || '邮箱无效',
]

const passwordRulesR = [
  (v: string) => !!v || '必须填写密码',
  (v: string) => v.length >= 8 || '密码必须大于8位',
]
const verificationCodeRulesR = [
  
]
const nameRulesR = [
    
]
const onClickRegisterR = () => {
  const instance=axios.create({
      baseURL:"https://uzimg.scutbot.icu",//这里填的是前缀，到时候要改
      //timeout: 1000,
      headers:{"Content-Type":"application/json"}
     })

     instance.post("/register",{//这里填的是后缀，到时候要改
        email:email.value,
        passwd:password.value,
        name:name.value
      })
      .then(response =>{
        console.log(response.data);
        alert(response.data.msg);
      })
      .catch(error => {
        alert("注册失败");
        console.log(error);
        console.log(email.value);
        console.log(password);
      })
      .finally(function(){
        console.log("跑一下");
      });
      console.log("润润润");
}
onMounted(() => {
  // 组件挂载完成时的逻辑
})

console.debug("这是一条调试信息R");


const { registerHiddenIsActive, registerMoveUpIsActive, registerMoveDownIsActive } = defineProps({
  registerHiddenIsActive: Boolean,
  registerMoveUpIsActive: Boolean,
  registerMoveDownIsActive: Boolean
});
</script>

<template>
  <!-- <v-form v-model="valid" id="lr"> -->
    <!--<v-container class="scrollPlace"  @wheel="scroll">-->
          <v-container class="loginregister">
            <h2 id="register-heading" :class="{ 'hidden': registerHiddenIsActive}">注册</h2>
          </v-container>
      <form id="register-form" :class="{ 'moveUp':registerMoveUpIsActive ,'moveDown':registerMoveDownIsActive}">
        <!-- <v-container  id="movebox2" class="moveDown" > -->
          <v-container  id="movebox2">
        <v-container  id="register-section" class="contain">
          <v-text-field  v-model="name" :rules="nameRulesR" label="姓名"  required  hide-details ></v-text-field>
          <v-text-field  v-model="email" :rules="emailRulesR" :counter="10" label="邮箱" required hide-details></v-text-field>
          <v-text-field v-model="verificationCode" :rules="verificationCodeRulesR" :counter="6" label="验证码"  required hide-details ></v-text-field>
          <v-text-field v-model="password"  type="password" :rules="passwordRulesR"  label="密码" hide-details required ></v-text-field>
          <v-spacer>
          <v-btn :disabled="!valid" color="primary" @click="onClickRegisterR" id="button" >注册</v-btn>
          </v-spacer>
        </v-container>
        </v-container>
      </form>
    <!--</v-container>-->
  <!-- </v-form> -->
</template>

<style src="@/assets/style.css"></style>
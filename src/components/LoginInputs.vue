<script setup lang="ts">
import {ref, onMounted, onBeforeUnmount} from "vue";
import { defineProps } from 'vue';
import axios from 'axios'

const valid = ref(true)
const email = ref('')
const password = ref('')
const dialog = ref(false)

const emailRulesL = [
  (v: string) => !!v || '必须填写邮箱',
  (v: string) => /.+@.+/.test(v) || '邮箱无效',
]

const passwordRulesL = [
  (v: string) => !!v || '必须填写密码',
  (v: string) => v.length >= 8 || '密码必须大于8位',
]

const onClickLoginL = () => {
  const instance=axios.create({
      baseURL:"https://uzimg.scutbot.icu",//这里填的是前缀，到时候要改
      //timeout: 1000,
      headers:{"Content-Type":"application/json"}
     })

     instance.post("/login",{//这里填的是后缀，到时候要改
        email:email.value,
        passwd:password.value
      })
      .then(response =>{
        console.log(response.data);
        alert(response.data.msg);
      })
      .catch(error => {
        alert("登录失败");
        console.log(error);
        console.log(email);
        console.log(password.value);
      })
      .finally(function(){
        console.log("跑一下");
      });
      console.log("润润润");
}
const onClickForget = () => {
  const instance=axios.create({
      baseURL:"https://uzimg.scutbot.icu",//这里填的是前缀，到时候要改
      //timeout: 1000,
      headers:{"Content-Type":"application/json"}
     })

     instance.post("/ChangePasswd",{//这里填的是后缀，到时候要改
        uuid:email.value,
        passwd:password.value
      })
      .then(response =>{
        console.log(response.data);
        alert(response.data.msg);
      })
      .catch(error => {
        alert("登录失败");
        console.log(error);
        console.log(email);
        console.log(password.value);
      })
      .finally(function(){
        console.log("跑一下");
      });
      console.log("润润润");
}
onMounted(() => {
  // 组件挂载完成时的逻辑
})

console.debug("这是一条调试信息L");


const { loginHiddenIsActive, loginMoveUpIsActive, loginMoveDownIsActive } = defineProps({
  loginHiddenIsActive: Boolean,
  loginMoveUpIsActive: Boolean,
  loginMoveDownIsActive: Boolean
});

</script>

<template>
  <!-- <v-form v-model="valid" id="lr"> -->
    <!--<v-container class="scrollPlace"  @wheel="scroll">-->
          <v-container class="loginregister">
            <h2 id="login-heading" :class="{ 'hidden': loginHiddenIsActive}">登录</h2>
          </v-container>
      <form id="login-form" :class="{ 'moveUp':loginMoveUpIsActive ,'moveDown':loginMoveDownIsActive}">
        <!-- <v-container  id="movebox1" class="moveUp" > -->
        <v-container  id="movebox1">
        <v-container  id="login-section" class="contain">
          <v-text-field v-model="email" :rules="emailRulesL" :counter="10" label="邮箱" required hide-details></v-text-field>
          <v-text-field v-model="password" :rules="passwordRulesL" label="密码" hide-details required type="password"></v-text-field>
          <v-spacer>
          <v-btn :disabled="!valid" color="primary" @click="onClickLoginL" id="button">登录</v-btn>
          </v-spacer>
          


          <v-dialog v-model="dialog" persistent width="1024">
          <template v-slot:activator="{ props }">
            <a href="" id="forget" v-bind="props"  @click.prevent>忘记密码？</a>
          </template>
          <v-card>
            <v-card-title>
              <span class="text-h5">重设密码</span>
            </v-card-title>
          <v-card-text>
          <v-container>
            <v-row>
              <v-col cols="12">
                <v-text-field label="邮箱*" required ></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field label="新密码*" type="password" required ></v-text-field>
              </v-col>
            </v-row>
          </v-container>
            <small>*忘记密码</small>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue-darken-1" variant="text" @click="dialog = false">Close</v-btn>
            <v-btn color="blue-darken-1" variant="text" @click="onClickForget">Save</v-btn>
          </v-card-actions>
          </v-card>
          </v-dialog>


        </v-container>
        </v-container>
      </form>
    <!--</v-container>-->
  <!-- </v-form> -->
</template>

<style src="@/assets/style.css"></style>
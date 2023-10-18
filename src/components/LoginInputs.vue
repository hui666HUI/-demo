<script setup lang="ts">
import {ref, onMounted, onBeforeUnmount} from "vue";
import { defineProps } from 'vue';

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

}
onMounted(() => {
  // 组件挂载完成时的逻辑
})

console.debug("这是一条调试信息L");

// const scroll = (event) => {
//   event.preventDefault();//阻止默认行为，这里是页面滚动
//   const delta = event.deltaY;
//   if (delta < 0) {
      
//       console.debug("滚动1L");
//       loginMoveUpIsActive.value=true,
//       loginMoveDownIsActive.value=false,
//       loginHiddenIsActive.value=false

//   } else if (delta > 0) {

//     console.debug("滚动2L");
//       loginMoveUpIsActive.value= false,
//       loginMoveDownIsActive.value=true,
//       loginHiddenIsActive.value=true
    

//   }
// }

const { loginHiddenIsActive, loginMoveUpIsActive, loginMoveDownIsActive } = defineProps({
  loginHiddenIsActive: Boolean,
  loginMoveUpIsActive: Boolean,
  loginMoveDownIsActive: Boolean
});

// const loginHiddenIsActive = defineProps(['loginHiddenIsActive'])
// const loginMoveUpIsActive = defineProps(['loginMoveUpIsActive'])
// const loginMoveDownIsActive = defineProps(['loginMoveDownIsActive'])
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
          <v-text-field v-model="password" :rules="passwordRulesL" label="密码" hide-details required></v-text-field>
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
            <v-btn color="blue-darken-1" variant="text" @click="dialog = false">Save</v-btn>
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
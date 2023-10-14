<script setup lang="ts">
import {ref, onMounted, onBeforeUnmount} from "vue";
import { defineProps } from 'vue';

const valid = ref(true)
const email = ref('')
const password = ref('')
// const loginMoveUpIsActive = ref(true)
// const loginMoveDownIsActive = ref(false)
// const loginHiddenIsActive = ref(false)

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
          <v-text-field
            v-model="email"
            :rules="emailRulesL"
            :counter="10"
            label="邮箱"
            required
            hide-details
          ></v-text-field>
          <v-text-field
            v-model="password"
            :rules="passwordRulesL"
            label="密码"
            hide-details
            required
          ></v-text-field>
          <v-spacer>
          <v-btn
              :disabled="!valid"
              color="primary"
              @click="onClickLoginL"
              id="button"
          >登录</v-btn>
          </v-spacer>
          <a href="../../forget.html" id="forget">忘记密码？</a>
        </v-container>
        </v-container>
      </form>
    <!--</v-container>-->
  <!-- </v-form> -->
</template>

<style src="@/assets/style.css"></style>
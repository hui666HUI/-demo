<script setup lang="ts">
import {ref, onMounted, onBeforeUnmount} from "vue";
import { defineProps } from 'vue';

const valid = ref(true)
const email = ref('')
const password = ref('')
const name = ref('虎!')

const verificationCode = ref('')
// const registerMoveUpIsActive = ref(false)
// const registerMoveDownIsActive = ref(true)
// const registerHiddenIsActive = ref(true)

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

}
onMounted(() => {
  // 组件挂载完成时的逻辑
})

console.debug("这是一条调试信息R");

// const scroll = (event) => {
//   event.preventDefault();//阻止默认行为，这里是页面滚动
//   const delta = event.deltaY;
//   if (delta < 0) {
//     console.debug("滚动1R");
//       registerMoveUpIsActive.value=false,
//       registerMoveDownIsActive.value=true,
//       registerHiddenIsActive.value=true

//   } else if (delta > 0) {
//     console.debug("滚动2R");
//       registerMoveUpIsActive.value= true,
//       registerMoveDownIsActive.value=false,
//       registerHiddenIsActive.value=false

//   }
// }
const { registerHiddenIsActive, registerMoveUpIsActive, registerMoveDownIsActive } = defineProps({
  registerHiddenIsActive: Boolean,
  registerMoveUpIsActive: Boolean,
  registerMoveDownIsActive: Boolean
});
// const registerHiddenIsActive = defineProps(['registerHiddenIsActive'])
// const registerMoveUpIsActive = defineProps(['registerMoveUpIsActive'])
// const registerMoveDownIsActive = defineProps(['registerMoveDownIsActive'])
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
          <v-text-field
            v-model="name"
            :rules="nameRulesR"
            label="姓名"
            required
            hide-details
          ></v-text-field>
          <v-text-field
            v-model="email"
            :rules="emailRulesR"
            :counter="10"
            label="邮箱"
            required
            hide-details
          ></v-text-field>
          <v-text-field
            v-model="verificationCode"
            :rules="verificationCodeRulesR"
            :counter="6"
            label="验证码"
            required
            hide-details
          ></v-text-field>
          <v-text-field
            v-model="password"
            :rules="passwordRulesR"
            label="密码"
            hide-details
            required
          ></v-text-field>
          <v-spacer>
          <v-btn
              :disabled="!valid"
              color="primary"
              @click="onClickRegisterR"
              id="button"
          >注册</v-btn>
          </v-spacer>
        </v-container>
        </v-container>
      </form>
    <!--</v-container>-->
  <!-- </v-form> -->
</template>

<style src="@/assets/style.css"></style>
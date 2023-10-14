<script setup lang="ts">
import {ref, onMounted, onBeforeUnmount} from "vue";
import { defineProps } from 'vue';

const valid = ref(true)
const email = ref('')
// const loginMoveUpIsActive = ref(true)
// const loginMoveDownIsActive = ref(false)
// const loginHiddenIsActive = ref(false)

const emailRulesL = [
  (v: string) => !!v || '必须填写邮箱',
  (v: string) => /.+@.+/.test(v) || '邮箱无效',
]
onMounted(() => {
  // 组件挂载完成时的逻辑
})
</script>

<template>
  <!-- <v-form v-model="valid" id="lr"> -->
    <!--<v-container class="scrollPlace"  @wheel="scroll">-->
          <v-container class="loginregister">
            <h2 id="login-heading" >忘记密码</h2>
          </v-container>
      <form id="login-form">
        
        <v-container  id="login-section" class="contain">
          <v-text-field
            v-model="email"
            :rules="emailRulesL"
            :counter="10"
            label="邮箱"
            required
            hide-details
          ></v-text-field>
          <v-spacer>
          </v-spacer>
        </v-container>
      </form>
    <!--</v-container>-->
  <!-- </v-form> -->
</template>

<style src="@/assets/style.css"></style>
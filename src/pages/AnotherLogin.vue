<script setup lang="ts">
import {ref} from "vue";
import axios from 'axios'


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
      
      <a href="https://uzimg.scutbot.icu/feishu/oauth">
      <img src="../img/飞书logo.png" alt="飞书登录" id="feishu">
      </a>
    </v-container>
</template>




<style src="@/assets/style.css"></style>

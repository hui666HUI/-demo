<script setup lang="ts">
import {ref} from "vue";
const introduceMoveRightIsActive = ref(false)
const introduceMoveLeftIsActive = ref(true)
const moveRight = () => {
    introduceMoveLeftIsActive.value=false,
    introduceMoveRightIsActive.value=true
};

const moveLeft = () => {
    introduceMoveLeftIsActive.value=true,
    introduceMoveRightIsActive.value=false
};

</script>


<template>
    <v-container id="introduce"  @mouseenter="moveRight" @mouseleave="moveLeft" :class="{ 'moveRight':introduceMoveRightIsActive ,'moveLeft':introduceMoveLeftIsActive}">
        <!-- <img src="@/introduce.png" alt="介绍图片" id="introduceImg" class="moveLeft"> -->
        <img src="../img/introduce.png" alt="介绍图片" id="introduceImg">
        <form>
        <v-container id="introduceText" class="moveLeft">
          <h3 class="introduceSmallText">“华南虎的物资管理系统是我见过最好用</h3>
          <h3 class="introduceSmallText">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;的物资管理系统”</h3>
          <h3 class="introduceSmallText">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;------鲁迅</h3>
          <h3 class="introduceSmallText"></h3>
          <h3 class="introduceSmallText">“华南虎的物资管理系统的网页设计</h3>
          <h3 class="introduceSmallText">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;非常优雅”</h3>
          <h3 class="introduceSmallText">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;------贝聿铭</h3>
        </v-container>
        </form>
    </v-container>
</template>




<style src="@/assets/style.css"></style>

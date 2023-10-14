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
          <h3 class="introduceSmallText">text1text1text1text1text1text1text1text1</h3>
          <h3 class="introduceSmallText">text2text2text2text2text2</h3>
          <h3 class="introduceSmallText">text3text3text3text3text3text3text3text3text3</h3>
          <h3 class="introduceSmallText">text4</h3>
          <h3 class="introduceSmallText">text5text5text5text5</h3>
        </v-container>
        </form>
    </v-container>
</template>




<style src="@/assets/style.css"></style>

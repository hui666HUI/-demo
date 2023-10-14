<script setup lang="ts">
import {ref} from "vue";
import { defineProps } from 'vue';


const { showAnotherLoginFeishu, showAnotherLoginWeixin } = defineProps({
    showAnotherLoginFeishu: Boolean,
    showAnotherLoginWeixin: Boolean
});

</script>


<template>
    <!-- <v-container v-show="showAnotherLoginFeishu"> -->
    
    <v-container :class="{ 'hidden': !showAnotherLoginFeishu}">
        <v-container class="feishuLogin">

        </v-container>
    </v-container>

    <!-- <v-container :class="{ 'hidden': !showAnotherLoginWeixin}" class="modal-mask"> -->
    <v-container :class="{ 'hidden': !showAnotherLoginWeixin}">
        <v-container class="weixinLogin">

        </v-container>
    </v-container>
    <!-- </v-container> -->
</template>




<style src="@/assets/style.css"></style>

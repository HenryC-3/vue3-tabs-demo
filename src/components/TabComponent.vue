<template>
    <button v-for="tab in tabs" :key="tab" @click="currentTab = tab.component">
        {{ tab.name }}
    </button>
    <component :is="currentTab ? currentTab : defaultTab"></component>
</template>

<script setup>
import { markRaw, ref } from "vue";
import tabOne from "./TabOne.vue";
import tabTwo from "./TabTwo.vue";

const tabs = ref([
    { name: "Tab 1", component: markRaw(tabOne) },
    { name: "Tab 2", component: markRaw(tabTwo) },
]);
const currentTab = ref(null);
const defaultTab = tabOne;
</script>

<style scoped></style>

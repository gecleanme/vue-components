<script setup>

import {ref, watch} from "vue";

const showItems = ref(false)

const props = defineProps({
    containerClasses: {type: String, default: ''},
    triggerClasses: {
        type: String,
        default: 'md-trigger'
    },
    listWrapperClasses: {
        type: String,
        default: 'md-list-wrapper'
    },
    buttonName: {type: String, default: 'Dropdown'},
    buttonIcon: String,
    buttonAfterIcon: {type: String, default: 'expand_more'}
})

const closeFromOutside = (event) => {
    if (!event.target.closest('.mindrop')) {
        showItems.value = false;
    }
}

watch(showItems, () => {
    if (showItems.value) {
        document.addEventListener('click', closeFromOutside)
    }
})

</script>
<template>
    <div class="mindrop relative root-container" :class="props.containerClasses">

        <div class="trigger-container md-trigger" @click="showItems=!showItems" :class="props.triggerClasses">
            <i class="material-icons">{{ buttonIcon }}</i>
            <button>{{ props.buttonName }}
            </button>
            <i class="material-icons">{{ buttonAfterIcon }}</i>
        </div>

        <div v-show="showItems" class="list-wrapper-container md-list-wrapper"
             :class="props.listWrapperClasses">
            <slot/>
        </div>

    </div>
</template>

<style scoped>

.md-trigger {
    @apply bg-black rounded px-2 py-3 text-white flex space-x-2 hover:cursor-pointer;
}

.md-list-wrapper{
    @apply bg-black absolute mt-2 px-3 py-2 rounded-md shadow-lg text-white z-10;
}

</style>
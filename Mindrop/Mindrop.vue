<script setup>

import {ref, watch} from "vue";

const showItems = ref(false)

const props = defineProps({
    containerClasses: {type: String, default: ''},
    triggerClasses: {
        type: String,
        default: 'bg-black rounded px-2 py-3 text-white flex space-x-2 hover:cursor-pointer'
    },
    listWrapperClasses: {
        type: String,
        default: 'bg-black absolute mt-2 px-3 py-2 rounded-md shadow-lg text-white z-10'
    },
    buttonName: {type: String, default: 'Dropdown'},
    buttonIcon: String
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

        <div class="trigger-container" @click="showItems=!showItems" :class="props.triggerClasses">
            <i class="material-icons">{{ buttonIcon }}</i>
            <button>{{ props.buttonName }}
            </button>
        </div>

        <div v-show="showItems" class="list-wrapper-container"
             :class="props.listWrapperClasses">
            <slot/>
        </div>

    </div>
</template>

<style scoped>


</style>
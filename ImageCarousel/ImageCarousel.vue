<template>
    <div class="flex items-center md:justify-between">
        <button
            class="hidden lg:block p-4 m-2 bg-white text-gray-400 max-w-5 rounded-full shadow-lg font-bold text-xl"
            @click="prevImage"
        >
            <slot name="prev">&lt;</slot>
        </button>
        <transition name="fade">
            <img
                :src="images[currentIndex]"
                :class="imageClass"
                :key="currentIndex"
                :alt="'Image ' + (currentIndex+1)"
            />
        </transition>
        <button
            class="hidden md:block p-4 m-2 bg-white text-gray-400 max-w-5 rounded-full shadow-lg font-bold text-xl"
            @click="nextImage"
        >
            <slot name="next">&gt;</slot>
        </button>
    </div>


    <div class="mobile-nav flex space-x-2 justify-center lg:hidden">

        <button
            class="p-4 m-2 bg-white text-gray-400 max-w-5 rounded-full shadow-lg font-bold text-xl"
            @click="prevImage"
        >
            <slot name="prev">&lt;</slot>
        </button>

        <button
            class="p-4 m-2 bg-white text-gray-400 max-w-5 rounded-full shadow-lg font-bold text-xl"
            @click="nextImage"
        >
            <slot name="next">&gt;</slot>
        </button>


    </div>


</template>

<script setup>
import {ref, computed, onMounted, onUnmounted} from 'vue'

const props = defineProps({
    images: {
        type: Array,
        required: true
    },
    width: {
        type: String,
        default: '100'
    },
    height: {
        type: String,
        default: '100'
    },

    autoPlay: {
        type: Boolean,
        default: false
    }
})

let currentIndex = ref(0);

const nextImage = () => {
    currentIndex.value = (currentIndex.value + 1) % props.images.length
}

const prevImage = () => {
    currentIndex.value =
        (currentIndex.value - 1 + props.images.length) % props.images.length
}

const autoPlay = () => setInterval(() => {
    currentIndex.value = (currentIndex.value + 1) % props.images.length
}, 3000);

const clearAutoPlay = () => {
    clearInterval(autoPlay());
}

const imageClass = computed(() => `max-w-${props.width} max-h-${props.height} object-contain`)

onMounted(() => {
    // uncomment the next line if you want keyboard interactivity

    // window.addEventListener('keydown', handleKeydown);
    if (props.autoPlay) {
        autoPlay();
    }
})

onUnmounted(() => {
    // uncomment the next line if you want keyboard interactivity

    // window.removeEventListener('keydown', handleKeydown);
    if (props.autoPlay) {
        clearAutoPlay();
    }
})

const handleKeydown = (event) => {
    // add or modify key mappings
    if (event.key === 'ArrowRight') {
        nextImage()
    } else if (event.key === 'ArrowLeft') {
        prevImage()
    }
}
</script>

<style scoped>
.fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
}

.fade-enter, .fade-leave-to {
    opacity: 0;
}
</style>

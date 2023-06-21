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
        default: 'max-w-100'
    },
    height: {
        type: String,
        default: 'max-h-100'
    },

    autoPlay: {
        type: Boolean,
        default: false
    },
    // key bindings can cause conflicts that degrade the user experience

    keyBindings: {
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

const imageClass = computed(() => `${props.width} ${props.height} object-contain`)

onMounted(() => {
    if (props.keyBindings) {
        window.addEventListener('keydown', handleKeydown);
    }
    if (props.autoPlay) {
        autoPlay();
    }
})

onUnmounted(() => {
    if (props.keyBindings) {
        window.removeEventListener('keydown', handleKeydown);
    }
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
        default: 'max-w-100'
    },
    height: {
        type: String,
        default: 'max-h-100'
    },

    autoPlay: {
        type: Boolean,
        default: false
    },
    // key bindings can cause conflicts that degrade the user experience

    keyBindings: {
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

const imageClass = computed(() => `${props.width} ${props.height} object-contain`)

onMounted(() => {
    if (props.keyBindings) {
        window.addEventListener('keydown', handleKeydown);
    }
    if (props.autoPlay) {
        autoPlay();
    }
})

onUnmounted(() => {
    if (props.keyBindings) {
        window.removeEventListener('keydown', handleKeydown);
    }
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
<template>
    <nav aria-label="breadcrumb" :class="props.containerClasses">
        <ol class="breadcrumb flex space-x-2">
            <li v-for="(breadcrumb, index) in breadcrumbs" :key="index" class="breadcrumb-item"
                :class="{ activeClasses: index === breadcrumbs.length - 1 }">
                <Link v-if="index !== props.breadcrumbs.length - 1" :href="breadcrumb.url"
                      :class="props.activeClasses">{{ breadcrumb.label }}
                </Link>
                <span v-else :class="props.inactiveClasses">{{ breadcrumb.label }}</span>
                <span v-if="index !== breadcrumbs.length - 1" :class="props.separatorClasses">/</span>
            </li>
        </ol>
    </nav>
</template>

<script setup>
import {Link} from "@inertiajs/vue3";

const props = defineProps({
    breadcrumbs: {type: Array, required: true},
    containerClasses: {type: String, default: 'text-base p-6 mx-4 my-2 w-3/4 border border-gray-300'},
    itemWrapperClasses: {type: String, default: ''},
    activeClasses: {type: String, default: 'text-blue-500 hover:text-blue-700'},
    inactiveClasses: {type: String, default: 'text-gray-500'},
    separatorClasses: {type: String, default: 'mx-2 text-gray-400'},
});
</script>

<style scoped>
</style>

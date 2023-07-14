# VueComponents
 Custom made, with love

### Properties:
- Vue 3: Composition API Base, using ```script setup``` macro
- Styled with TailwindCSS
- Minimalistic by design


## General Dependencies
- TailwindCSS

## Installation/Usage
- Import Component and use it as shown under the component's section
- Some components have InertiaJS logic embedded in since they were originally designed to work with InertiaJS' Adapters,
feel free to modify the logic to fit your use case. 

## Contribution Guidelines
- WIP

## Contact

Drop me a line at promomegm@gmail.com

## Mindrop

Minimalistic "Context Menu" Component
### Basic Usage (inspect component code for defaults/optional props):
```js
  <Mindrop>
    <!-- Content of the context menu inserted into the default slot -->
    <ul class="w-full">
        <li class="py-2 px-2 hover:bg-gray-500 border-b-2 border-gray-800 cursor-pointer">Menu Item</li>
        <li class="py-2 px-2 hover:bg-gray-500 border-b-2 border-gray-800 cursor-pointer">Menu Item</li>
        <li class="py-2 px-2 hover:bg-gray-500 border-b-2 border-gray-800 cursor-pointer">Menu Item</li>
        <li class="py-2 px-2 hover:bg-gray-500 border-b-2 border-gray-800 cursor-pointer">Menu Item</li>
    </ul>

</Mindrop>
```

### Specific Dependencies:
- Google Material icons (https://github.com/google/material-design-icons)



## Badgerr

SVG Badges made easy

### Basic Usage (inspect component code for defaults/optional props):
```js
// svg path, color, and size (denoted with a Tailwind class)
<Badgerr color="text-green-600" size="w-6"
         path="M1.5 3.25a2.25 2.25 0 1 1 3 2.122v5.256a2.251 2.251 0 1 1-1.5 0V5.372A2.25 2.25 0 0 1 1.5 3.25Zm5.677-.177L9.573.677A.25.25 0 0 1 10 .854V2.5h1A2.5 2.5 0 0 1 13.5 5v5.628a2.251 2.251 0 1 1-1.5 0V5a1 1 0 0 0-1-1h-1v1.646a.25.25 0 0 1-.427.177L7.177 3.427a.25.25 0 0 1 0-.354ZM3.75 2.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm0 9.5a.75.75 0 1 0 0 1.5.75.75 0 0 0 0-1.5Zm8.25.75a.75.75 0 1 0 1.5 0 .75.75 0 0 0-1.5 0Z"/>
```

## ImageCarousel

Flexible Image Carousel Component
### Basic Usage (inspect component code for defaults/optional props):
```html
    <!-- images array is supplied along with flags to activate keyboard bindings and carousel autoplay -->
<ImageCarousel :images="imgs" class="mt-4" :auto-play="true" :key-bindings="true">
    <template #prev> <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
    <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 19.5L8.25 12l7.5-7.5" />
    </svg>
</template>
<template #next> <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
    <path stroke-linecap="round" stroke-linejoin="round" d="M8.25 4.5l7.5 7.5-7.5 7.5" />
    </svg>
</template>
</ImageCarousel>
```

## SimplerConfirm
a minimalistic "Confirmation" Component
### Basic Usage (inspect component code for defaults/optional props):
```html
    <!--Trigger that shows the dialog by setting the "Open" state to true -->
<button @click="showConfirmDialog" class="hidden">Click to Show</button>

    <!-- isOpen: ref flag that determines the "Open" state 
         handleConfirm: function that handle confirmation action
         handleClose: typically inverts the "Open" state
         
    -->
<SimplerConfirm
        :isOpen="isDialogOpen"
        title="Confirmation"
        message="Are you sure you want to proceed?"
        :onConfirm="handleConfirm"
        :onClose="handleClose"
        yesText="Yes"
        noText="Nope"
/>
```

## SlashTrail
Flexible "Breadcrumbs" Component

### Basic Usage (inspect component code for defaults/optional props):

```html
    <!-- Breadcrumbs hashmap containing a "url" and a "label" is passed   -->
    <Breadcrumbs :breadcrumbs="props.breadcrumbs"></Breadcrumbs>

```

## Blinkr
Minimalistic "Flash Message" component
### Basic Usage (inspect component code for defaults/optional props):


```html
    <!-- a message type and text (message) is passed -->
    <Blinkr type="success" message="Operation Succeeded"></Blinkr>

```
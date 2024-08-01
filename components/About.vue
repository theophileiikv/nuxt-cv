<template>
    <div class="pt-5 px-3">
        <div class="max-w-2xl m-auto">
            <h2 class="text-2xl tracking-tight font-bold text-gray-900 mb-4">
                About
            </h2>
            <p class="font-mono text-sm py-1 text-gray-500">{{ resume.about }}</p>
        </div>
    </div>
</template>

<script setup>
const { data: resume } = await useAsyncData('resume', () => queryContent('/data/resume').findOne())
</script>
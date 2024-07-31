<template>
    <div class="bg-gray-50 py-24">
        <div class="max-w-5xl px-4 m-auto sm:px-8">
            <div class="justify-center">
                <h1 class="text-4xl tracking-tight font-extrabold text-gray-900 sm:text-5xl xl:text-5xl text-center mb-6">
                    Hello from header
                </h1>
                {{ resume.name }}
            </div>
        </div>
    </div>
</template>

<script setup>
const { data: resume } = await useAsyncData('resume', () => queryContent('/data/cv').findOne())
</script>
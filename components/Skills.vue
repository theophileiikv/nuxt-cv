<template>
    <div class="pt-5 px-3">
        <div class="max-w-2xl m-auto">
            <h2 class="text-2xl tracking-tight font-bold text-gray-900 mb-4">
                Skills
            </h2>
            <UBadge variant="soft" size="sm" class="text-white font-mono font-semibold bg-gray-600 mr-2" v-for="(skill, index) in resume.skills" :key="index">
                {{ skill }}
            </UBadge>
        </div>
    </div>
</template>

<script setup>
const { data: resume } = await useAsyncData('resume', () => queryContent('/data/resume').findOne())
</script>
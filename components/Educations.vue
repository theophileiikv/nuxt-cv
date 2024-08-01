<template>
    <div class="pt-5 px-3">
        <div class="max-w-2xl m-auto">
            <h2 class="text-2xl tracking-tight font-bold text-gray-900 mb-4">
                Education
            </h2>
            <div v-for="(education, index) in resume.educations" :key="index" class="mb-4 space-y-1">
                <div class="flex items-center justify-between gap-x-2">
                    <h3 class="text-black font-semibold">
                        {{ education.school }}
                    </h3>
                    <p class="font-mono text-sm py-1 text-gray-500">{{ education.date }}</p>

                </div>
                <h4 class="font-mono text-sm text-gray-600">{{ education.degree }}</h4>

                <p class="font-mono text-xs py-1 text-gray-500">{{ education.description }}</p>
            </div>
        </div>
    </div>
</template>

<script setup>
const { data: resume } = await useAsyncData('resume', () => queryContent('/data/resume').findOne())
</script>
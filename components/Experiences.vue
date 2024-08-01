<template>
    <div class="pt-5 px-3">
        <div class="max-w-2xl m-auto">
            <h2 class="text-2xl tracking-tight font-bold text-gray-900 mb-4">
                Work Experience
            </h2>
            <div v-for="(experience, index) in resume.experiences" :key="index" class="mb-4 space-y-1">
                <div class="flex items-center justify-between gap-x-2">
                    <h3 class="text-black font-semibold">
                        <NuxtLink :to="experience.website" target="_blank" class="mr-2 hover:underline">{{ experience.company }}</NuxtLink>
                        <UBadge variant="soft" size="md" class="text-black font-semibold bg-gray-100">{{ experience.location }}</UBadge>
                    </h3>
                    <p class="font-mono text-sm py-1 text-gray-500">{{ experience.date }}</p>
                </div>
                <h4 class="font-mono text-sm text-gray-600">{{ experience.position }}</h4>
                <p v-for="(paragraph, pIndex) in getParagraphs(experience.description)" :key="pIndex" class="font-mono text-xs py-1 text-gray-500">
                    {{ paragraph }}
                </p>
            </div>
        </div>
    </div>
</template>

<script setup>
const { data: resume } = await useAsyncData('resume', () => queryContent('/data/resume').findOne())

const props = defineProps(['experience'])

function getParagraphs(description) {
  return description.split('\n\n').filter(p => p.trim() !== '')
}

</script>
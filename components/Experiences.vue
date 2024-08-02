<template>
    <div class="pt-5 px-3">
        <div class="max-w-2xl m-auto">
            <h2 class="text-2xl tracking-tight font-bold text-gray-900 mb-4">
                Work Experience
            </h2>
            <div v-for="(experience, index) in resume.experiences" :key="index" class="mb-6 space-y-1">
                <div class="flex items-center justify-between gap-x-2">
                    <h3 class="text-black font-semibold">
                        <NuxtLink :to="experience.website" target="_blank" class="mr-2 hover:underline">{{ experience.company }}</NuxtLink>
                        <UIcon name="i-heroicons-map-pin-16-solid" class="w-5 h-5 mr-1 align-top bg-gray-600" /><span class="text-black font-light">{{ experience.location }}</span>
                        <!-- <UBadge variant="soft" size="md" class="text-black font-semibold bg-gray-100">{{ experience.location }}</UBadge> -->
                    </h3>
                    <p class="font-mono text-sm py-1 text-gray-500">{{ experience.date }}</p>
                </div>
                <h4 class="font-mono text-sm text-gray-600">{{ experience.position }}</h4>
                <p v-for="(paragraph, pIndex) in getParagraphs(experience.description)" :key="pIndex" class="font-mono text-xs py-1 text-gray-500">
                    {{ paragraph }}
                </p>
                <span class="block">
                    <UBadge variant="soft" size="sm" class="text-white font-mono font-semibold bg-gray-500 mr-2" v-for="(skill_tech, index_t) in experience.skills_tech" :key="index_t">
                        {{ skill_tech }}
                    </UBadge>
                </span>
                <span class="block">
                    <UBadge variant="soft" size="sm" class="text-black font-mono font-semibold bg-gray-200 mr-2" v-for="(skill_soft, index_s) in experience.skills_soft" :key="index_s">
                        {{ skill_soft }}
                    </UBadge>
                </span>
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
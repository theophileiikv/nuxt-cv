<template>
    <div class="pt-5 px-3">
        <div class="max-w-2xl m-auto">
            <h2 class="text-2xl tracking-tight font-bold text-gray-900 mb-4">
                Projects
            </h2>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-3">
                <div v-for="(project, index) in projects.projects" :key="index" class="rounded-lg border p-3 flex flex-col h-full">
                    <div class="flex flex-col flex-grow">
                        <h3 class="text-black font-semibold text-base">
                            <NuxtLink :to="project.url" target="_blank" class="mr-2 hover:underline">{{ project.name }}</NuxtLink>
                        </h3>
                        <p class="font-mono text-xs py-1 text-gray-500 flex-grow">{{ project.description }}</p>
                        <div class="mt-auto pt-2 flex flex-wrap">
                            <UBadge 
                                v-for="(skill, skillIndex) in project.skills" 
                                :key="skillIndex"
                                variant="soft" 
                                size="xs" 
                                class="text-black font-medium bg-gray-100 mr-1 mb-1"
                            >
                                {{ skill }}
                            </UBadge>
                        </div>
                    </div>
                </div>  
            </div>
        </div>
    </div>
</template>

<script setup>
const { data: projects } = await useAsyncData('projects', () => queryContent('/data/projects').findOne())
</script>
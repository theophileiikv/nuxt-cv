<template>
    <div class="py-16 px-3">
        <div class="max-w-2xl m-auto">
            <div class="flex items-center justify-between">
                <div class="flex-1 space-y-1.5">
                    <h1 class="text-2xl tracking-tight font-bold text-gray-900 mb-6">
                        {{ resume.name }}
                    </h1>
                    <p v-if="resume.bio" class="font-mono text-sm mb-2 text-gray-500">{{ resume.bio }}</p>
                
                    <div v-if="resume.locations" class="font-mono text-xs mb-4 text-gray-500">
                        <ul>
                            <li v-for="(location, index) in resume.locations" :key="index" class="mb-1 underline">
                                <UIcon name="i-heroicons-globe-alt" class="w-3 h-3 mr-1 align-middle" />{{ location }}
                            </li>
                        </ul>
                    </div>
                    <div class="flex space-x-3">
                        <div v-if="resume.contact.email" class="font-mono text-xs text-gray-500">
                            <NuxtLink :to="'mailto:' + resume.contact.email" target="_blank"><UIcon name="i-heroicons-envelope" class="w-6 h-6 mr-1 align-middle" /></NuxtLink>
                        </div>

                        <div v-if="resume.contact.social" class="font-mono text-xs text-gray-500">
                            <NuxtLink 
                                v-for="socialLink in resume.contact.social" 
                                :key="socialLink.name"
                                :to="socialLink.url"
                                target="_blank"
                                class="mr-2"
                            >
                                <UIcon :name="getIconName(socialLink.name)" class="w-6 h-6 align-middle mr-1" />
                            </NuxtLink>
                        </div>
                    </div>
                </div>
                <NuxtImg
                class="rounded-xl"
                src="images/profile.jpeg"
                width="112" height="112"
                />
            </div>
        </div>
    </div>
</template>

<script setup>
const { data: resume } = await useAsyncData('resume', () => queryContent('/data/cv').findOne())

function getIconName(socialName) {
  switch (socialName.toLowerCase()) {
    case 'github':
      return 'i-heroicons-rocket-launch-16-solid'
    case 'linkedin':
      return 'i-heroicons-archive-box-arrow-down-20-solid'
    case 'X':
    case 'twitter':
      return 'i-heroicons-lifebuoy-solid'
    // Add more cases for other social networks
    default:
      return 'i-heroicons-arrow-right-start-on-rectangle-solid'
  }
}

</script>
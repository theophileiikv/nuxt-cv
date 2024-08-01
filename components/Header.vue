<template>
    <div class="pt-16 pb-3 px-3">
        <div class="max-w-2xl m-auto">
            <div class="flex items-center justify-between">
                <div class="flex-1 space-y-1.5 max-w-lg">
                    <h1 class="text-2xl tracking-tight font-bold text-gray-900 mb-4">
                        {{ resume.name }}
                    </h1>
                    <p v-if="resume.bio" class="font-mono text-sm py-1 text-gray-500">{{ resume.bio }}</p>
                
                    <div v-if="resume.locations" class="font-mono text-xs py-1 text-gray-500">
                        <ul>
                            <li v-for="(location, index) in resume.locations" :key="index" class="mb-1 underline">
                                <UIcon name="i-heroicons-globe-alt" class="w-3 h-3 mr-1 align-middle" />{{ location }}
                            </li>
                        </ul>
                    </div>
                    <div class="flex py-1">
                        <div v-if="resume.contact.email" class="font-mono text-xs text-gray-500">
                            <NuxtLink :to="'mailto:' + resume.contact.email" target="_blank" class="mx-1"><UIcon name="i-heroicons-envelope" class="w-6 h-6 align-middle" /></NuxtLink>
                        </div>

                        <div v-if="resume.contact.social" class="font-mono text-xs text-gray-500 m-0">
                            <NuxtLink 
                                v-for="socialLink in resume.contact.social" 
                                :key="socialLink.name"
                                :to="socialLink.url"
                                target="_blank"
                                class="mx-1"
                            >
                                <UIcon :name="getIconName(socialLink.name)" class="w-6 h-6 align-middle" />
                            </NuxtLink>
                        </div>
                    </div>
                </div>
                <NuxtImg
                class="rounded-xl"
                src="images/profile.jpeg"
                width="136" height="136"
                />
            </div>
        </div>
    </div>
</template>

<script setup>
const { data: resume } = await useAsyncData('resume', () => queryContent('/data/resume').findOne())

function getIconName(socialName) {
  switch (socialName.toLowerCase()) {
    case 'github':
      return 'i-fa6-brands-github'
    case 'linkedin':
      return 'i-fa6-brands-linkedin'
    case 'x':
    case 'twitter':
      return 'i-fa6-brands-x-twitter'
    // Add more cases for other social networks
    default:
      return 'i-heroicons-stop-20-solid'
  }
}

</script>
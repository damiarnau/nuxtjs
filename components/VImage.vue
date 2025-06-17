<template>
    <img :src="getStrapiMedia(image.formats.small?.url)" alt="Article Image" />
</template>

<script setup lang="ts">
defineProps<{
    image: {
        formats: {
            small?: {
                url: string
            }
        }
    }
}>()
function getStrapiMedia(path?: string): string | null {
    if (!path) return null
    const config = useRuntimeConfig()

    const strapi = config.public.strapi
    const baseURL = strapi.url.replace(/\/$/, '') // remove trailing slash
    const cleanedPath = path.startsWith('/') ? path : `/${path}`

    return baseURL + cleanedPath
}
</script>
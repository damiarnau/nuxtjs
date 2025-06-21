<template>
    <img :src="getStrapiMedia(image)" alt="Article Image" />
</template>

<script setup lang="ts">
defineProps<{
    image: {
        formats: {
            small?: {
                url: string
            }
            thumbnail?: {
                url: string
            }
            medium?: {
                url: string
            }
            large?: {
                url: string
            }
            original?: {
                url: string
            }
        }
    }
}>()
function getStrapiMedia(path?: any): string | undefined {
    // if (!path) return null
    // const config = useRuntimeConfig()

    // const strapi = config.public.strapi
    // const baseURL = strapi.url.replace(/\/$/, '') // remove trailing slash
    // const cleanedPath = path.startsWith('/') ? path : `/${path}`

    // return baseURL + cleanedPath
    return path?.formats?.small?.url || path?.url
}
</script>
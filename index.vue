<template>
<div v-if='!videosIsLoading'>
    <video-grid :videos="videos" />
</div>
	
</template>

<script>
import VideoGrid from '~/components/videos/VideoGrid.vue'
import { defineComponent } from '@nuxtjs/composition-api'
import { useUser, useData } from '~/lib/compositions'
export default {
	name: 'IndexPage',
	components: { VideoGrid },
}
export default defineComponent({
    setup() {
        const { user, loggedIn } = useUser()
        const { data: videos, isLoading: videosIsLoading } = useData('videos.getVideosFeedOnMain')
        return {
            user,
            videos,
            videosIsLoading
        }
    },
})
</script>

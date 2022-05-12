<template>
    <div class="w-full h-80">
        <div id="pano-v" class="w-full h-full"></div>
    </div>
</template>

<script>
import * as PANOLENS from "panolens"
import {onMounted, onUnmounted} from "vue";

export default {
    name: "PanoVideo",

    props: {
        type: {
            type: String,
            default: 'video'
        },
        source: ''
    },

    setup(props) {
        onMounted(() => {
            const panorama = new PANOLENS.ImagePanorama(props.source);
            let container = document.querySelector('#pano-v');
            container.innerHTML = ''
            const viewer = new PANOLENS.Viewer({
                container: container,
                cameraFov: 100
            });
            viewer.add(panorama);
        })

        onUnmounted(() => {

        })
    }
}
</script>

<style scoped>

</style>

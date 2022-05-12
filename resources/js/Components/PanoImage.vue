<template>
    <div class="w-full h-80">
        <div :id="`pano-i-${number}`" class="w-full h-full"></div>
    </div>
</template>

<script>
import * as PANOLENS from "panolens"
import {onMounted, onUnmounted} from "vue";

export default {
    name: "PanoImage",

    props: {
        type: {
            type: String,
            default: 'image'
        },
        source: '',
        number: 0,
    },

    setup(props) {
        onMounted(() => {
            const panorama = new PANOLENS.ImagePanorama(props.source);
            let container = document.querySelector(`#pano-i-${props.number}`);
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

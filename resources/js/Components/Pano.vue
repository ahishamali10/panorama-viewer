<template>
    <div class="w-full h-80">
        <div id="pano-v" class="w-full h-full"></div>
    </div>
</template>

<script>
import * as PANOLENS from "panolens"
import {onMounted} from "vue";

export default {
    name: "Pano",

    props: {
        type: {
            type: String,
            default: 'image'
        },
        source: ''
    },

    setup(props) {
        onMounted(() => {
            let panorama
            if (props.type === 'video')
                panorama = new PANOLENS.VideoPanorama(props.source);
            else
                panorama = new PANOLENS.ImagePanorama(props.source);
            const viewer = new PANOLENS.Viewer({
                container: document.querySelector('#pano-v'),
                cameraFov: 100
            });
            viewer.add(panorama);
        })
    }
}
</script>

<style scoped>

</style>

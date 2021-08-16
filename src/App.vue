<template>
    <div class="app">
        <img class="wallpaper" src="@/assets/background.jpg" alt="Assel wallpaper" />
        <div class="layer" />

        <div class="invite">
            <video
                id="invite-video"
                class="invite__video"
                width="250"
                height="250"
                autoplay
                preload
                loop
                muted
            >
                <source src="@/assets/video.mp4" type="video/mp4" />
            </video>

            <div class="invite__message">
                <h1>Құрметті, сіздерді Баян мен Асельдің үйлену тойына шақырамыз! Алматы қаласы</h1>
            </div>
        </div>
    </div>
</template>

<script>
import { defineComponent, onMounted } from 'vue'

export default defineComponent({
    setup() {
        const startVideo = () => {
            const video = document.getElementById('invite-video')
            video.play()
        }

        onMounted(startVideo)
    },
})
</script>

<style lang="scss">
@keyframes wallpaper-scale {
    0% {
        transform: scale(1);
    }
    100% {
        transform: scale(1.5);
    }
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.app {
    min-width: 100%;
    min-height: 100vh;
    max-height: 100vh;

    overflow: hidden;

    background: red;

    position: relative;

    & .wallpaper {
        width: 100%;
        height: 100%;

        animation: wallpaper-scale 20s alternate infinite;
    }

    & .layer {
        position: absolute;
        z-index: 1;

        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background-color: rgba(0, 0, 0, 0.8);
    }

    & .invite {
        position: absolute;
        z-index: 2;

        top: 0;
        bottom: 0;
        left: 50%;
        right: 0;

        transform: translateX(-50%);

        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;

        width: 100%;
        max-width: 1000px;

        &__video {
            min-width: 250px;
            min-height: 250px;

            border-radius: 50%;
            object-fit: cover;

            border: 3px solid #df9bff;
            box-shadow: 0px 0px 20px 10px rgba(219, 66, 244, 0.25);
        }

        &__message {
            margin-top: 20px;

            text-align: center;
            color: white;
        }
    }
}
</style>

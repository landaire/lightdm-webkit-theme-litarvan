<template>
    <div class="base">
        <div class="bg" :class="{ blured: isBlured() }">
        </div>

        <transition name="fade">
            <router-view/>
        </transition>
    </div>
</template>

<script>
    export default {
        name: 'base',

        methods: {
            isBlured() {
                let name = this.$router.currentRoute.name;
                return name === 'login' || name === 'select';
            }
        }
    };
</script>

<style lang="scss">
    @import '../theme';

    .bg {
        background-image: $background-image;
        position: fixed;
        left: 0;
        right: 0;

        display: block;
        width: 100%;
        height: 100vh;

        z-index: -1;
        transition: filter 500ms ease-in-out;

        color: $secondary-color;
    }

    .blured {
        filter: blur(10px);
    }
</style>
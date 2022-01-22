<template>
    <div id="app">
        <!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  Pages  ~~~~~~~~~~~~~~~~~ -->
        <Loader />
        <Links />
        <transition name="fade-in" mode="out-in">
            <router-view />
        </transition>
        <!-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  Footer  ~~~~~~~~~~~~~~~~~ -->
        <Footer />
    </div>
</template>
<script>
import Loader from "./views/Loader.vue";
import Links from "./components/HeaderComp.vue";
import Footer from "./views/Footer";

export default {
    name: "App",
    components: {
        Links,
        Footer,
        Loader,
    },
};
</script>

<style scoped lang="scss">
.loader {
    position: fixed;
    inset: 0;
    z-index: 1000;
    transition: opacity 0.5s;
    background: #cfe4e9;
    background: #1c272a;
    display: grid;
    place-items: center;
    div {
        position: relative;
        &::before {
            content: "";
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 10%;
            background: linear-gradient(to top, #1c272a, transparent);
        }
    }
    &.hide {
        opacity: 0;
    }
}

.fade-in-leave-to,
.fade-in-enter-from {
    opacity: 0;
}
.fade-in-leave-active,
.fade-in-enter-active {
    transition: 0.2s ease;
}
</style>

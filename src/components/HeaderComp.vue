<template>
    <header class="header">
        <div class="container">
            <div class="header__box">
                <div class="logo">
                    <a href="#" @click.prevent>
                        <img src="../assets/images/logo.png" alt="Main Logo" />
                    </a>
                </div>
                <nav class="nav">
                    <div
                        v-show="mobileWidth"
                        class="nav__icon"
                        @click="navIcon"
                    >
                        <span></span>
                        <span></span>
                        <span></span>
                    </div>
                    <ul class="nav__ul">
                        <router-link exact tag="li" to="/"
                            ><a class="active" @click="bgMove"
                                >home</a
                            ></router-link
                        >
                        <router-link tag="li" to="/picture"
                            ><a @click="bgMove">picture</a></router-link
                        >
                        <router-link tag="li" to="/icon"
                            ><a @click="bgMove">icon</a></router-link
                        >
                        <router-link tag="li" to="/font"
                            ><a @click="bgMove">font</a></router-link
                        >
                        <router-link tag="li" to="/color"
                            ><a @click="bgMove">color</a></router-link
                        >
                        <li @mouseenter="menuBtnOn" @mouseleave="menuBtnOff">
                            <a href="#" class="menu-btn" @click.prevent
                                >other <i class="fas fa-angle-down"></i
                            ></a>
                            <ul class="nav__menu">
                                <router-link tag="li" to="layout"
                                    ><a
                                        v-on:click="navIcon"
                                        @click="menuBtnOff"
                                    >
                                        layout</a
                                    ></router-link
                                >
                                <router-link tag="li" to="template"
                                    ><a
                                        v-on:click="navIcon"
                                        @click="menuBtnOff"
                                    >
                                        template</a
                                    ></router-link
                                >
                                <router-link tag="li" to="practice"
                                    ><a
                                        v-on:click="navIcon"
                                        @click="menuBtnOff"
                                    >
                                        practice</a
                                    ></router-link
                                >
                                <router-link tag="li" to="problem_solving"
                                    ><a
                                        v-on:click="navIcon"
                                        @click="menuBtnOff"
                                    >
                                        problem solving</a
                                    ></router-link
                                >
                                <router-link tag="li" to="animation"
                                    ><a
                                        v-on:click="navIcon"
                                        @click="menuBtnOff"
                                    >
                                        animation</a
                                    ></router-link
                                >
                                <router-link tag="li" to="reference"
                                    ><a
                                        v-on:click="navIcon"
                                        @click="menuBtnOff"
                                    >
                                        reference</a
                                    ></router-link
                                >
                                <router-link tag="li" to="useful_web"
                                    ><a v-on:click="bgMove" @click="menuBtnOff">
                                        useful web</a
                                    ></router-link
                                >
                                <router-link tag="li" to="web_inspire"
                                    ><a
                                        v-on:click="navIcon"
                                        @click="menuBtnOff"
                                    >
                                        web inspire</a
                                    ></router-link
                                >
                                <router-link tag="li" to="hosting"
                                    ><a
                                        v-on:click="navIcon"
                                        @click="menuBtnOff"
                                    >
                                        hosting</a
                                    ></router-link
                                >
                                <router-link tag="li" to="remote_job"
                                    ><a
                                        v-on:click="navIcon"
                                        @click="menuBtnOff"
                                    >
                                        remote job</a
                                    ></router-link
                                >
                            </ul>
                        </li>
                        <div class="links__bg"></div>
                    </ul>
                </nav>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name: "header",
    data() {
        return {
            mobileWidth: null,
            windowWidth: null,
        };
    },
    // -------------------------------- Links bg & Media icon ------------------
    created() {
        window.addEventListener("DOMContentLoaded", this.resizeLinksBg);
        window.addEventListener("reload", this.resizeLinksBg);
        window.addEventListener("resize", () => {
            this.resizeLinksBg();
            this.checkScreen();
        });
        this.resizeLinksBg();
        this.checkScreen();
    },
    methods: {
        menuBtnOn() {
            document.querySelector(".menu-btn").classList.add("show");
        },
        menuBtnOff() {
            document.querySelector(".menu-btn").classList.remove("show");
        },
        // -------------------------------- Links on click Bg ------------------
        bgMove(e) {
            const links = document.querySelectorAll(".nav__ul > * > a");
            links.forEach((el) => el.classList.remove("active"));
            if (e.target.classList.contains("btn")) {
                links[0].classList.add("active");
                this.navIcon();
                this.bgPos(e);
                return;
            }
            this.navIcon();
            e.target.classList.add("active");
            this.bgPos(e);
        },
        bgPos(e) {
            let element = e.target;
            let menuLinks = [
                ...document.querySelectorAll(".nav__menu > * > *"),
            ];
            if (menuLinks.includes(element)) {
                element = document.querySelector(".menu-btn");
            }

            let w = element.getBoundingClientRect().width;
            let h = element.getBoundingClientRect().height;
            let l = element.offsetLeft;
            let bg = document.querySelector(".links__bg");

            bg.style.width = w + "px";
            bg.style.height = h + "px";
            bg.style.left = l + "px";
        },
        resizeLinksBg() {
            if (document.querySelector(".nav__ul > * > .active")) {
                let el = document.querySelector(".nav__ul > * > .active");
                let w = el.getBoundingClientRect().width;
                let h = el.getBoundingClientRect().height;
                let l = el.offsetLeft;

                let bg = document.querySelector(".links__bg");
                bg.style.width = w + "px";
                bg.style.height = h + "px";
                bg.style.left = l + "px";
            }
        },
        // -------------------------------- Check for mobile screen ------------------
        checkScreen() {
            this.windowWidth = window.innerWidth;
            if (this.windowWidth < 768) {
                this.mobileWidth = true;
                return;
            }
            this.mobileWidth = false;
        },
        navIcon() {
            const links = document.querySelectorAll(".nav__ul > * > a");
            if (window.innerWidth <= 767) {
                document.querySelector(".nav__icon").classList.toggle("show");
            } else {
                links.forEach((el) => el.classList.remove("active"));
                links[links.length - 1].classList.add("active");
                this.resizeLinksBg();
            }
        },
    },
};
</script>

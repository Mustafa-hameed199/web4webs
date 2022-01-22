<template>
    <div class="loader">
        <div>
            <img src="../assets/images/loader.gif" alt="Website Loader" />
        </div>
    </div>
</template>

<script>
export default {
    name: "loader",
    mounted() {
        const loader = document.querySelector(".loader");
        window.addEventListener("load", () => {
            loader.classList.add("hide");
            setTimeout(() => (loader.style.display = "none"), 600);
        });
    },
};
</script>

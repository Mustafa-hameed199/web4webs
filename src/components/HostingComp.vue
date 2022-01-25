<template>
    <section class="hosting" id="hosting">
        <div class="container">
            <h2 class="title">hosting</h2>
            <div class="box">
                <a href="https://github.com/" target="_blank"> github</a>
                <a href="https://www.heroku.com/" target="_blank"> heroku</a>
                <a href="https://www.netlify.com/" target="_blank"> netlify</a>
                <a href="https://firebase.google.com/" target="_blank">
                    firebase</a
                >
                <a href="https://vercel.com/" target="_blank"> vercel</a>
            </div>
            <h2 class="title">domain</h2>
            <div class="box">
                <a href="https://www.namecheap.com/" target="_blank">
                    namecheap</a
                >
                <a href="https://www.name.com/" target="_blank"> name </a>
                <a href="https://www.enom.com/" target="_blank"> enom </a>
                <a
                    href="https://ae.godaddy.com/offers/domains/godaddy-b"
                    target="_blank"
                >
                    godaddy
                </a>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    name: "hosting",
};
</script>

<style lang="scss" scoped>
.box {
    margin-bottom: 2rem;
}
.title {
    font-size: clamp(2rem, 1rem + 3vw, 3rem);
    text-transform: uppercase;
    text-align: center;
    margin-bottom: 2rem;
}
</style>

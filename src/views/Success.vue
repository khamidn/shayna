<template>
	<div class="success">
		<Header />
		<div class="d-flex success-checkout align-items-center justify-content-center">
        <div class="col col-lg-4 text-center">
            <img src="img/success-buy.png" alt="" width="294">
            <h3 class="mt-4">
                Sukses Terbayar!
            </h3>
            <p class="mt-2">
                Silakan tunggu update terbaru dari kami via email yang sudah Anda daftarkan sebelumnya.
            </p>
            <router-link to="/" class="primary-btn pd-cart mt-3">Back to Home</router-link>
        </div>
    </div>
		<Footer />
	</div>
</template>

<script>
	import Header from "@/components/Header.vue";
	import Footer from "@/components/Footer.vue";

	export default {
		name : "Success",
		components : {
			Header,
			Footer

		}
	}
</script>
<template>
  <div class="home">
    <Header />
    <HeroSection />
    <WomenBanner />
    <InstagramPhoto />
    <LogoPartner />
    <Footer />
  </div>
</template>

<script>
// @ is an alias to /src
  import Header from "@/components/Header.vue";
  import HeroSection from "@/components/HeroSection.vue";
  import WomenBanner from "@/components/WomenBanner.vue";
  import InstagramPhoto from "@/components/InstagramPhoto.vue";
  import LogoPartner from "@/components/LogoPartner.vue";
  import Footer from "@/components/Footer.vue";

  export default {
    name: 'Home',
    components: {
      Header,
      HeroSection,
      WomenBanner,
      InstagramPhoto,
      LogoPartner,
      Footer
      
    }
}
</script>

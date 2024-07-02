<template>
  <Header />
  <MainBlock />
  <AboutUs />
  <WorkSection />
  <Gallery />
  <ServiceSection />
  <Contacts />
  <Footer />
</template>

<script>
import Header from "./components/header/Header.vue";
import MainBlock from "./components/main_block/MainBlock.vue";
import AboutUs from "./components/about_us/AboutUs.vue";
import WorkSection from "./components/steps_work/WorkSection.vue";
import Gallery from "./components/gallery/Gallery.vue";
import ServiceSection from "./components/services/ServiceSection.vue";
import Contacts from "./components/contacts/Contacts.vue";
import Footer from "./components/footer/Footer.vue";

export default {
  components: {
    Header,
    MainBlock,
    AboutUs,
    WorkSection,
    Gallery,
    ServiceSection,
    Contacts,
    Footer
  },
};
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  border: none;
  outline: none;
}

html {
  scroll-behavior: smooth;
}

body {
  margin: 0 auto;
}

::-webkit-scrollbar {
  width: 18px;
}

::-webkit-scrollbar-track {
  background-color: #f1f1f1;
}

::-webkit-scrollbar-thumb {
  background-color: #01588b;
  border-radius: 12px;
  border: 3px solid #f1f1f1;
}

a {
  font-family: "Ral", sans-serif;
  text-decoration: none;
}

@media screen and (max-width: 1800px) {
  nav {
    width: 1415px;
  }
}

@media screen and (max-width: 1440px) {
  .container {
    width: 1000px;
  }

  nav {
    width: 1250px;
  }

  nav .requisites {
    flex-direction: column;
    align-items: center;
  }

  .application {
    width: 435px;
  }

  .str {
    width: 333px;
  }

  .point {
    width: 75%;
  }

  /*.head-opis {*/
  /*    width: 47%;*/
  /*}*/
}

@media screen and (max-width: 1200px) {
  .container {
    width: 700px;
  }

  nav {
    width: 900px;
  }

  .nav-sait {
    flex-direction: column;
  }

  .main_head {
    padding-right: 0;
  }

  .requisites,
  .requisites a {
    flex-direction: column;
    gap: 10px;
  }

  .main_block {
    flex-direction: column;
    text-align: center;
  }

  .main_head {
    width: 100%;
    padding-bottom: 50px;
  }

  .main_head .requisites {
    align-items: center;
  }

  .block {
    align-items: center;
  }

  .about_us {
    flex-direction: column;
    align-items: center;
    gap: 33px;
  }

  .head-opis,
  .head-opis p {
    width: 100%;
    align-items: center;
    text-align: center;
  }

  .photo {
    width: 100%;
  }

  .photo img {
    width: 100%;
  }

  .step {
    width: 900px;
  }

  p {
    width: 100%;
  }

  .wave {
    display: none;
  }

  .all_services {
    justify-content: center;
    padding: 60px 0;
  }

  .contacts {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    gap: 60px;
  }
}

@media screen and (max-width: 992px) {
  .container {
    width: 800px;
  }

  nav {
    width: 720px;
  }

  .nav-sait {
    flex-direction: column;
  }

  .photo {
    width: 70%;
  }

  .services {
    flex-direction: column;
    gap: 10px;
  }
}
@media screen and (max-width: 768px) {
  .container {
    width: 600px;
  }

  nav {
    width: 700px;
    flex-direction: column;
    gap: 40px;
  }

  .main_block {
    padding: 70px 0;
  }

  .nav,
  .address {
    width: 140px;
    text-align: center;
  }

  .services {
    flex-direction: column;
  }
}

@media screen and (max-width: 700px) {
  .container {
    width: 450px;
  }

  nav {
    width: 450px;
  }

  .navigation {
    align-items: center;
    flex-direction: column;
    gap: 20px;
  }
}

@media screen and (max-width: 480px) {
  .container {
    width: 400px;
  }

  nav {
    width: 400px;
  }

  .application {
    width: 400px;
  }

  .str {
    width: 350px;
  }

  .head-opis {
    width: 400px;
  }

  .photo img {
    width: 100%;
  }

  .navigation {
    flex-direction: column;
    gap: 20px;
  }

  .logo {
    width: 100%;
  }

  .logo img {
    width: 40%;
  }

  .address {
    align-items: center;
  }
}

@media screen and (max-width: 400px) {
  .container {
    width: 350px;
  }

  nav {
    width: 350px;
  }

  .application {
    width: 350px;
  }

  .str {
    width: 290px;
  }

  .head-opis {
    width: 350px;
  }

  .head_center {
    width: 85%;
  }
}

@media screen and (max-width: 320px) {
  .container {
    width: 290px;
  }

  nav {
    width: 290px;
  }

  .block {
    align-items: flex-start;
    width: 290px;
  }

  .application {
    width: 290px;
  }

  .str {
    width: 250px;
  }

  .head-opis {
    width: 290px;
  }

  .photo img {
    width: 100%;
  }
}
</style>

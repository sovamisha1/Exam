<template>
  <Header />
  <MainContent id="Main" />
  <FaQ id="FaQ" />
  <FeedBack id="FeedBack" />
  <DonateContent id="Donate" />
  <Footer id="footer" />
</template>

<script>
import Header from "./components/Header.vue";
import MainContent from "./components/MainForms/MainContent.vue";
import FaQ from "./components/MainForms/FaQ.vue";
import FeedBack from "./components/MainForms/FeedBack.vue";
import DonateContent from "./components/MainForms/Donate.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    Header,
    MainContent,
    FaQ,
    FeedBack,
    DonateContent,
    Footer,
  },
};
</script>

<style>
Header,
Footer {
  padding: 0.5cm 1cm;
  width: 100%;
  background-color: #b19f9e;
}

Header {
  display: flex;
  justify-content: space-around;
  align-items: center;
}

#FaQ,
#FeedBack,
#Donate {
  display: none;
}
</style>

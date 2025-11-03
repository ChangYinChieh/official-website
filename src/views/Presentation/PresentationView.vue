<script setup>
import { onMounted, onUnmounted } from "vue";
function splitText(text) {
  return text.split(""); // 把字串拆成陣列
}
let observer;
//example components
import NavbarDefault from "../..//examples/navbars/NavbarDefault.vue";
import DefaultFooter from "../../examples/footers/FooterDefault.vue";
import Header from "../../examples/Header.vue";
import FilledInfoCard from "../../examples/cards/infoCards/FilledInfoCard.vue";


// sections
import Announcement from "./Sections/Announcement.vue";


//images
import vueMkHeader from "@/assets/img/banner.jpg";
import UsefulLinks from "./Sections/UsefulLinks.vue";
import History from "./Sections/History.vue";
//import Info from "@/examples/cards/infoCards/InfoSection.vue"
//hooks
const body = document.getElementsByTagName("body")[0];

onMounted(() => {
  observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        entry.target.classList.add("show");
        observer.unobserve(entry.target); // 只觸發一次
      }
    });
  });

  document.querySelectorAll(".text,.content").forEach((el) => observer.observe(el));
});

onUnmounted(() => {
  if (observer) observer.disconnect();
});
</script>

<template>
  <div class="container position-sticky z-index-sticky top-0">
    <div class="row">
      <div class="col-12">
        <NavbarDefault :sticky="true" />
      </div>
    </div>
  </div>
  <Header>
    <div
      class="page-header min-vh-75"
      :style="`
        background: 
          linear-gradient(rgba(255,255,255,0.1), rgba(255,255,255,0.55)), 
          url(${vueMkHeader});
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat; 
        width: 100%;
      `"
      loading="lazy"
    >
      <div class="container">
        <div class="row">
          <div class="col-lg-7 text-center mx-auto position-relative">
            <h1
              class="text-black pt-3 mt-n5 me-2"
              :style="{ display: 'inline-black ' }"
              
            >
              臺北市立大學學生會
            </h1>
            <p class="lead text-black px-5 mt-3" :style="{ fontWeight: '500', color: '#003D79' }">
              我們是一群熱心的學生組成的組織 ❤️<br>為學生謀福利、為學生顧權益 💪
            </p>
          </div>
        </div>
      </div>
    </div>
  </Header>

  <div class="card custom-shadow mx-3 mx-md-4 mt-n5">
    <div class="container mt-1">
      <div class="row">
        <div class="col-md-6 mb-5 mb-md-0">
          <Announcement />
        </div>
        <div class="col-md-6">
          <UsefulLinks />
        </div>
      </div>
      <hr class="my-4" />
      <div class="row">
        <div class="col-md-6 mb-5 mb-md-0">
          <History/>
        </div>
      </div>
    </div>
    <hr class="my-6" />
    <div class="text">
      <span 
        v-for="(char, i) in splitText('簡介')" 
        :key="i" 
        :style="{ transitionDelay: `${i * 0.1}s` }"
      >
        {{ char }}
      </span>
      
      
    
    <hr class="my-5" />
    <p class="content">學生會是北市大最高層級的學生自治團體，分為兩大部門，分別是行政部門（學生會）與立法部門（學生議會），我們致力於維護學生權益，成為同學面對校內問題或想表達意見時最直接、最可靠的窗口。
        我們透過參與校務會議，傳達學生的立場與需求，同時舉辦多元活動，讓同學能投入校園公共事務，建立彼此的連結感。學生會成員來自不同系所與年級，因為對學校的關心與公共事務的熱情而聚在一起，堅信學生的聲音能帶來改變。
    </p>
    <hr class="my-4" />
    <section id ="intro" class="py-5">
      <!-- 資訊公開頁面 -->
     <!-- <Info/> -->
    </section>
  </div>
</div>
  <DefaultFooter />
</template>
<style scoped>
.custom-shadow {
  padding: 2rem;
  box-shadow: 
    0 10px 15px rgba(0, 0, 0, 0.2),
    0 20px 40px rgba(0, 0, 0, 0.3);

  backdrop-filter: blur(10px);
  
  border-radius: 16px;
}
section {
padding: 3rem 1rem;
}

.text {
  font-size: 2rem;
  font-weight: bold;
  color: #333;
  display: inline-block;
  text-align: center;
}

.text span {
  display: inline-block;
  opacity: 0;
  transform: translateY(30px);
  transition: all 0.8s ease-out;
}

.text.show span {
  opacity: 1;
  transform: translateY(0);
}
.text-container {
  position: relative;
  z-index: 1;
}
.content {
  font-size: 1.2rem;
  color: #333;
  opacity: 0;
  transform: translateY(20px);
  transition: all 2s ease-out;
  max-width: 950px;  
  margin: 0 auto;    
  line-height: 1.6;  
  text-align: justify; 
}
.content.show {
  opacity: 1;
  transform: translateY(0);
}
</style>
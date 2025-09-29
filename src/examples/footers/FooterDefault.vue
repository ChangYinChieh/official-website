<script setup>
import logoDark from "@/assets/img/logo.png";
import logoWhite from "@/assets/img/logo2.png";
defineProps({
  brands: {
    type: Array,
    name: String,
    logo: String,
    route: "",
    default: () => [
      {
        name: "臺北市立大學學生會",
        en: "UTSA 12th",
        logo: logoDark,
        route: "/"
      },
      {
        name: "臺北市立大學學生議會",
        en: "UTSP 12th",
        logo: logoWhite,
        route: "/"
      }
    ]
    },
  menus: {
    type: Array,
    name: String,
    items: {
      type: Array,
      name: String,
      href: String
    },
    default: () => [
      {
        name: "",
        items: [
          {
            name: "",
            // href: "utsa@go.utaipei.edu.tw"
          }
        ]
      },
      {
        name: "",
        items: [
          {
            name: "",
            // href: "utsa@go.utaipei.edu.tw"
          }
        ]
      },
      {
        name: "會辦位子",
        items: [
          {
            name: "博愛校區：勤樸樓CB120",
            // href: "utsa@go.utaipei.edu.tw"
          },
          {
            name: "天母校區：鴻坦樓B411",
            // href: "utsa@go.utaipei.edu.tw"
          }
        ]
      },
      
      {
        name: "聯絡我們",
        items: [
          {
            name: "Mail:utsa@go.utaipei.edu.tw",
            // href: "utsa@go.utaipei.edu.tw"
          },
          {
            name: "IG:@utaipei_sa",
            // href: "utsa@go.utaipei.edu.tw"
          }
        ]
      }
    ]
  }
});
</script>
<template>
  <footer class="footer pt-5 mt-5">
    <div class="container">
      <div class="row">
        
        <div
          class="col-md-2 col-sm-6 col-6 mb-4"
          v-for="brand in brands"
          :key="brand.name"
        >
          <a :href="brand.route">
            <img :src="brand.logo" class="mb-2 footer-logo" alt="main_logo" />
          </a>
          <h6 class="font-weight-bolder mb-1">{{ brand.name }}</h6>
          <p class="text-sm">{{ brand.en }}</p>
        </div>

        <div
          class="col-md-2 col-sm-6 col-6 mb-4"
          v-for="{ name, items } of menus"
          :key="name"
        >
          <h6 class="text-sm">{{ name }}</h6>
          <ul class="flex-column ms-n3 nav">
            <li class="nav-item" v-for="item of items" :key="item.name">
              <a class="nav-link" :href="item.href" target="_blank">
                {{ item.name }}
              </a>
            </li>
          </ul>
        </div>

      </div>
    </div>
  </footer>
</template>

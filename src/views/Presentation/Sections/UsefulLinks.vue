<template>
  <div class="container mt-1">
    <div class="activities-wrapper">
      <div class="activity-column announcement">
        <div class="activity-header">
          <span
            style="font-weight: bold; 
                   font-size: 32px;
                   background: -webkit-linear-gradient(transparent 65%,#ffcbff 60%, #ffcbff 100%,transparent 100%);">
            常用連結
          </span>
        </div>
        <div class="header-divider"></div>
        
        <div class="activity-list">
          <div
            class="activity-item"
            v-for="(item,index) in activeLinks"
            :key="index"
          >
            <a :href="item.url" target="_blank" style="font-weight:bold; text-decoration:none;">
              {{ item.name }}
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "UsefulLinks",
  data() {
    return {
      usefulLinks: [
        { name: "勤樸樓B1小舞台借用表單", url: "https://docs.google.com/forms/d/e/1FAIpQLSejrDm3GZMShG0W9Oz7HmFmzpIZpgWy7VSLPd8wQCELu1-6Ow/viewform"},
        { name: "學權申訴表單", url: "https://docs.google.com/forms/d/e/1FAIpQLSerOl43A14UWK23EOhhOYo_TVp1NU3PzSnHWav6oAPyIpZ4Bg/viewform"}
      ],
    };
  },
  computed: {
  activeLinks() {
    return this.usefulLinks;
  }
  } 
};
</script>

<style scoped>
.activities-wrapper {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.activity-header {
  display: flex;
  align-items: center;
  gap: 12px;
  color:#37526d;
}

.header-divider {
  width: 100% ;              
  height: 2px;                
  background-color: #ffdbf0;  
  margin: 8px 0;             
  border-radius: 1px;        
}

.announcement .activity-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.activity-item {
  font-size: 20px;
  color:#37526d;
}
</style>

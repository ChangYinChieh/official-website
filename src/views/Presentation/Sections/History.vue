<template>
  <div class="container mt-1">

    <div class="activities-wrapper">
      <div class="activity-column announcement">
        <div class="activity-header">
          <span style="font-weight: bold; 
             font-size: 32px;
             background: -webkit-linear-gradient(transparent 65%,#ffcbff 60%, #ffcbff 100%,transparent 100%);">
            歷史活動
          </span>
        </div>
        <div class="header-divider"></div>
        
        <div class="activity-list">
          <div
            class="activity-item"
            v-for="(item,index) in activeAnnouncements"
            :key="index"
          >
            <strong>{{ item.title }}</strong> - {{ item.content }} <small style="font-size: 0.8em;color: #BEBEBE;">{{ item.date }}</small>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Announcement",
  data() {
    return {
      hoverIndex: null,
      announcements: [
        { title: "活動1", content: "活動已結束，感謝參與", date: "2025-xx-xx", status: "active" },
        { title: "活動2", content: "活動已結束，感謝參與", date: "2025-xx-xx", status: "active" }
      ]
    }
  },
  computed: {
    activeAnnouncements() {
      return this.announcements.filter(a => a.status === "active");
    }
  }
}
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
}


.activity-header h3 {
  margin: 0;
  font-weight: 600;
  position: relative;
  padding-left: 12px; 
}

.header-divider {
  width: 500px;              
  height: 2px;               
  background-color: #ffdbf0; 
  margin: 8px 0;            
  border-radius: 1px;       
}

.history .activity-list {
  display: flex;
  flex-direction: column;
  gap: 8px;
}


.activity-item {
  font-size: 20px;
}
</style>


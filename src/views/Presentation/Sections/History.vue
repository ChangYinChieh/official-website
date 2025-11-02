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
            @click="openModal(item,$event)"
          >
            <strong>{{ item.date }} {{ item.title }}</strong>
          </div>
        </div>
      </div>
    </div>
  </div>
  <transition name="fade">
    <div v-if="showModal" class="modal-overlay" @click.self="closeModal">
      <div class="modal-box" :style="modalStyles">
        <button class="close-btn" @click="closeModal">×</button>
        <h3>{{ selectedItem.title }}</h3>
        <p style="color:#666;">{{ selectedItem.date }}</p>
        <div class="modal-content-wrapper">
          <p class="modal-content" v-html="formatContent(selectedItem.content)"></p>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: "Announcement",
  data() {
    return {
      hoverIndex: null,
      announcements: [
        { title: "活動1",  date: "2025/xx/xx",content:"我是內文\n我是內文\n我是內文\n我是內文\n我是內文\n我是內文\n我是內文\n我是內文\n我是內文\n我是內文\n", status: "active" },
        { title: "活動2", date: "2025/xx/xx",content:"我是內文\n我是內文\n我是內文\n我是內文\n我是內文\n我是內文\n我是內文\n我是內文\n我是內文\n我是內文\n", status: "active" }
      ],
      showModal: false, 
      selectedItem: {},
      modalPosition: { top: '50%' }
    }
  },
  computed: {
    activeAnnouncements() {
      return this.announcements.filter(a => a.status === "active");
    },
    modalStyles() {
      return {
        top: this.modalPosition.top,
        // transform: 'none'
      };
    }
  },
  methods: {
    openModal(item,event) {
      this.selectedItem = item;
      const mouseY = event.pageY;
      this.modalPosition = {
          top: `${mouseY-500}px`,
          // transform: 'none' 
      };
      this.showModal = true;
    },
    closeModal() {
      this.showModal = false;
      this.modalPosition = { top: '50%'};
    },
    formatContent(text) {
    return text.replace(/\n/g, "<br>");
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
.activity-header span {
  color: #37526d; /* 深藍色，對比更鮮明 */
  font-weight: bold;
}

.header-divider {
  width: 100%;              
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
  color:#37526d;
}

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  display: block;
  align-items: unset; 
  justify-content: unset;
  z-index: 999;
   /* padding-top: 10vh;  */
}


.modal-box {
  position: fixed;
  background: white;
  padding: 24px 30px;
  border-radius: 12px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
  /* max-width: 80%; */
  width: 85%;
  max-height: 75vh;
  text-align: center;
  display: flex;
  flex-direction: column;
  margin: 0 auto;
  left: 50%;
  transform: translateX(-50%);

}
.modal-content-wrapper {
  flex: 1;             
  overflow-y: auto;    
  margin: 12px 0;
}

.modal-content {
  white-space: pre-line;
  line-height: 1.6;
}

.close-btn {
  position: absolute;
  top: 10px;
  right: 12px;
  font-size: 24px;
  background: none;
  border: none;
  color: #777;
  cursor: pointer;
  line-height: 1;
  padding: 2px 6px;
  transition: color 0.2s ease;
}

.close-btn:hover {
  color: #000;
}
</style>


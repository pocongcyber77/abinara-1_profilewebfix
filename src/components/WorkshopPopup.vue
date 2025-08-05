<template>
  <div class="workshop-popup-overlay" @click="closePopup" v-if="isVisible">
    <div class="workshop-popup-card" @click.stop>
      <div class="popup-header">
        <button class="close-button" @click="closePopup">
          <svg class="close-icon" viewBox="0 0 24 24" fill="currentColor">
            <path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/>
          </svg>
        </button>
      </div>
      
      <div class="poster-container">
        <img 
          src="/poster.png" 
          alt="Workshop Poster" 
          class="workshop-poster"
        />
      </div>
      
      <div class="popup-content">
        <h2 class="workshop-title">Advance Abinara</h2>
        <p class="workshop-subtitle">Coding, Creative Education, and Robotic Learning</p>
        <p class="workshop-description">
          Workshop eksklusif untuk mahasiswa ITS yang ingin mendalami dunia coding, 
          pendidikan kreatif, dan pembelajaran robotik bersama tim Abinara-1.
        </p>
        
        <div class="workshop-details">
          <div class="detail-item">
            <span class="detail-label">📅 Tanggal:</span>
            <span class="detail-value">Coming Soon</span>
          </div>
          <div class="detail-item">
            <span class="detail-label">⏰ Waktu:</span>
            <span class="detail-value">09:00 - 17:00 WIB</span>
          </div>
          <div class="detail-item">
            <span class="detail-label">📍 Lokasi:</span>
            <span class="detail-value">ITS Campus</span>
          </div>
        </div>
        
        <router-link to="/advance" class="register-button">
          <span>Register Now!</span>
          <svg class="arrow-icon" viewBox="0 0 24 24" fill="currentColor">
            <path d="M12 4l-1.41 1.41L16.17 11H4v2h12.17l-5.58 5.59L12 20l8-8z"/>
          </svg>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'

const props = defineProps({
  isVisible: {
    type: Boolean,
    default: false
  }
})

const emit = defineEmits(['close'])

const closePopup = () => {
  emit('close')
}
</script>

<style scoped>
.workshop-popup-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
  backdrop-filter: blur(5px);
}

.workshop-popup-card {
  background: white;
  border-radius: 20px;
  max-width: 90vw;
  max-height: 90vh;
  overflow-y: auto;
  position: relative;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
  animation: popupSlideIn 0.3s ease-out;
}

@keyframes popupSlideIn {
  from {
    opacity: 0;
    transform: scale(0.8) translateY(50px);
  }
  to {
    opacity: 1;
    transform: scale(1) translateY(0);
  }
}

.popup-header {
  position: absolute;
  top: 15px;
  right: 15px;
  z-index: 10;
}

.close-button {
  background: rgba(255, 255, 255, 0.9);
  border: none;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

.close-button:hover {
  background: rgba(255, 255, 255, 1);
  transform: scale(1.1);
}

.close-icon {
  width: 20px;
  height: 20px;
  color: #333;
}

.poster-container {
  width: 100%;
  border-radius: 20px 20px 0 0;
  overflow: hidden;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.workshop-poster {
  width: 100%;
  height: auto;
  display: block;
  object-fit: cover;
}

.popup-content {
  padding: 30px;
}

.workshop-title {
  font-size: 2.5rem;
  font-weight: bold;
  color: #e53e3e;
  margin-bottom: 10px;
  text-align: center;
}

.workshop-subtitle {
  font-size: 1.2rem;
  color: #666;
  margin-bottom: 20px;
  text-align: center;
  font-weight: 500;
}

.workshop-description {
  color: #555;
  line-height: 1.6;
  margin-bottom: 25px;
  text-align: center;
}

.workshop-details {
  background: #f8f9fa;
  border-radius: 15px;
  padding: 20px;
  margin-bottom: 30px;
}

.detail-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
  padding: 8px 0;
}

.detail-item:last-child {
  margin-bottom: 0;
}

.detail-label {
  font-weight: 600;
  color: #333;
}

.detail-value {
  color: #666;
  font-weight: 500;
}

.register-button {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  background: linear-gradient(135deg, #e53e3e 0%, #c53030 100%);
  color: white;
  text-decoration: none;
  padding: 15px 30px;
  border-radius: 50px;
  font-weight: bold;
  font-size: 1.1rem;
  transition: all 0.3s ease;
  box-shadow: 0 8px 25px rgba(229, 62, 62, 0.3);
  width: 100%;
}

.register-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 12px 35px rgba(229, 62, 62, 0.4);
  background: linear-gradient(135deg, #c53030 0%, #a52a2a 100%);
}

.arrow-icon {
  width: 20px;
  height: 20px;
  transition: transform 0.3s ease;
}

.register-button:hover .arrow-icon {
  transform: translateX(5px);
}

/* Responsive */
@media (max-width: 768px) {
  .workshop-popup-card {
    max-width: 95vw;
    max-height: 95vh;
    margin: 10px;
  }
  
  .popup-content {
    padding: 20px;
  }
  
  .workshop-title {
    font-size: 2rem;
  }
  
  .workshop-subtitle {
    font-size: 1rem;
  }
}
</style> 
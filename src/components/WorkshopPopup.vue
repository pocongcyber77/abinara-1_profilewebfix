<template>
  <div class="workshop-popup-overlay" @click="closePopup" v-if="isVisible">
    <div class="workshop-popup-card" @click.stop :class="{ 'popup-animated': isAnimated }">
      <div class="popup-header">
        <button class="close-button" @click="closePopup">
          <svg class="close-icon" viewBox="0 0 24 24" fill="currentColor">
            <path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/>
          </svg>
        </button>
      </div>

      <div class="poster-container">
        <div class="poster-background">
          <div class="poster-content">
            <h1 class="arduino-title">ARDUINO 1.0</h1>
            <h2 class="arduino-subtitle">ARDUINO 1.0</h2>

            <div class="speakers-section">
              <div class="speaker">
                <div class="speaker-photo">
                  <img src="/src/assets/images/teams/prog/nabiel.png" alt="Nabiel Nizar Anwari" />
                </div>
                <div class="speaker-info">
                  <h3>Nabiel Nizar Anwari</h3>
                  <p>Programming Division</p>
                </div>
              </div>
              <div class="speaker">
                <div class="speaker-photo">
                  <img src="/src/assets/images/teams/gm/agatha.png" alt="Agatha Samuel Sitompul" />
                </div>
                <div class="speaker-info">
                  <h3>Agatha Samuel Sitompul</h3>
                  <p>General Manager</p>
                </div>
              </div>
            </div>

            <div class="event-banner">
              <h3>Abinara Robotic Education & Innovation 1.0</h3>
            </div>

            <div class="event-details">
              <div class="detail-row">
                <span class="detail-icon">📅</span>
                <span class="detail-text">24-25 Agust 2024</span>
              </div>
              <div class="detail-row">
                <span class="detail-icon">📍</span>
                <span class="detail-text">Online</span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="popup-content">
        <div class="workshop-info">
          <h2 class="workshop-title">🚀 Next-Gen Solutions For Search and Rescue 🚀</h2>

          <div class="materials-section">
            <h3>📚 Materials Covered:</h3>
            <ul>
              <li>First Steps in Coding (Exploring the Basics of C for Beginners)</li>
              <li>Basic Schematic and PCB Layout Design using Kicad Software</li>
            </ul>
          </div>

          <div class="benefits-section">
            <h3>🎁 Benefits:</h3>
            <ul>
              <li>E-Module and Recording</li>
              <li>Get a Big Chance to Join Robotics Team</li>
              <li>E-Certificate</li>
              <li>Ready-to-Use Learning for Your Classes</li>
              <li>Chance to Win a Door Prize</li>
            </ul>
          </div>

          <div class="registration-info">
            <div class="info-item">
              <span class="info-label">💰 Pricing:</span>
              <span class="info-value">25K Bundling / 15K Material</span>
            </div>
            <div class="info-item">
              <span class="info-label">📞 Contact:</span>
              <span class="info-value">+62 812-1660-7839 (Alfa)</span>
            </div>
            <div class="info-item">
              <span class="info-label">⏰ Close Registration:</span>
              <span class="info-value">21 Agust 2024</span>
            </div>
          </div>
        </div>

        <router-link to="/advance" class="register-button">
          <span>Register Now!!</span>
          <svg class="arrow-icon" viewBox="0 0 24 24" fill="currentColor">
            <path d="M12 4l-1.41 1.41L16.17 11H4v2h12.17l-5.58 5.59L12 20l8-8z"/>
          </svg>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits, ref, watch } from 'vue'

const props = defineProps({
  isVisible: {
    type: Boolean,
    default: false
  }
})

const emit = defineEmits(['close'])
const isAnimated = ref(false)

const closePopup = () => {
  emit('close')
}

// Watch for visibility changes to trigger animations
watch(() => props.isVisible, (newValue) => {
  if (newValue) {
    // Start pop animation after a short delay
    setTimeout(() => {
      isAnimated.value = true
    }, 100)
  } else {
    isAnimated.value = false
  }
})
</script>

<style scoped>
.workshop-popup-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
  animation: fadeIn 0.5s ease-out;

}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.workshop-popup-card {
  background: white;
  border-radius: 20px;
  width: 400px;
  max-width: 90vw;
  max-height: 90vh;
  overflow: hidden;
  position: relative;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
  animation: popupSlideIn 0.5s ease-out;
  /* Enhanced glow effect */
  box-shadow:
    0 20px 60px rgba(0, 0, 0, 0.3),
    0 0 30px rgba(229, 62, 62, 0.2),
    0 0 60px rgba(229, 62, 62, 0.1);
  display: flex;
  flex-direction: column;


}

.popup-animated {
  animation:
    popupSlideIn 0.5s ease-out,
    popLoop 2s ease-in-out infinite 0.5s;
}

@keyframes popupSlideIn {
  0% {
    opacity: 0;
    transform: scale(0.3) translateY(100px) rotateX(20deg);
  }
  50% {
    opacity: 0.8;
    transform: scale(1.1) translateY(-10px) rotateX(-5deg);
  }
  100% {
    opacity: 1;
    transform: scale(1) translateY(0) rotateX(0deg);
  }
}

@keyframes popLoop {
  0%, 100% {
    transform: scale(1);
    box-shadow:
      0 20px 60px rgba(0, 0, 0, 0.3),
      0 0 30px rgba(229, 62, 62, 0.2),
      0 0 60px rgba(229, 62, 62, 0.1);
  }
  50% {
    transform: scale(1.05);
    box-shadow:
      0 25px 80px rgba(0, 0, 0, 0.4),
      0 0 50px rgba(229, 62, 62, 0.4),
      0 0 100px rgba(229, 62, 62, 0.2),
      0 0 150px rgba(229, 62, 62, 0.1);
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
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}

.close-button:hover {
  background: rgba(255, 255, 255, 1);
  transform: scale(1.1);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
}

.close-icon {
  width: 20px;
  height: 20px;
  color: #333;
}

.poster-container {
  width: 100%;
  height: 60%;
  min-height: 240px;
  border-radius: 20px 20px 0 0;
  overflow: hidden;
  position: relative;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

.poster-background {
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, #8B0000 0%, #DC143C 50%, #8B0000 100%);
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
}

.poster-content {
  width: 90%;
  height: 90%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  color: white;
  text-align: center;
  position: relative;
}

.poster-container::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(45deg, transparent 30%, rgba(255, 255, 255, 0.1) 50%, transparent 70%);
  animation: shimmer 3s ease-in-out infinite;
  z-index: 1;
}

@keyframes shimmer {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(100%);
  }
}

.arduino-title {
  font-size: 1.4rem;
  font-weight: bold;
  color: white;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  margin: 0;
  letter-spacing: 1px;
}

.arduino-subtitle {
  font-size: 1.1rem;
  font-weight: bold;
  color: rgba(255, 255, 255, 0.8);
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  margin: 0;
  letter-spacing: 1px;
  transform: translateY(-6px);
}

.speakers-section {
  display: flex;
  justify-content: space-around;
  align-items: center;
  margin: 8px 0;
  gap: 12px;
}

.speaker {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
}

.speaker-photo {
  width: 45px;
  height: 45px;
  border-radius: 50%;
  overflow: hidden;
  border: 2px solid white;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.3);
}

.speaker-photo img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.speaker-info h3 {
  font-size: 0.6rem;
  font-weight: bold;
  margin: 0;
  color: white;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
}

.speaker-info p {
  font-size: 0.5rem;
  margin: 0;
  color: rgba(255, 255, 255, 0.9);
}

.event-banner {
  background: linear-gradient(135deg, #000080 0%, #4169E1 100%);
  border-radius: 6px;
  padding: 4px 10px;
  margin: 6px 0;
}

.event-banner h3 {
  font-size: 0.6rem;
  font-weight: bold;
  margin: 0;
  color: white;
}

.event-details {
  display: flex;
  justify-content: space-around;
  align-items: center;
  margin-top: 6px;
}

.detail-row {
  display: flex;
  align-items: center;
  gap: 3px;
}

.detail-icon {
  font-size: 0.7rem;
}

.detail-text {
  font-size: 0.6rem;
  font-weight: bold;
  color: white;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
}

.popup-content {
  padding: 10px;
  overflow-y: auto;
  flex: 1;
}

.workshop-title {
  font-size: 0.9rem;
  font-weight: bold;
  color: #e53e3e;
  margin-bottom: 6px;
  text-align: center;
  text-shadow: 0 2px 10px rgba(229, 62, 62, 0.3);
  animation: titleGlow 2s ease-in-out infinite;
}

@keyframes titleGlow {
  0%, 100% {
    text-shadow: 0 2px 10px rgba(229, 62, 62, 0.3);
  }
  50% {
    text-shadow: 0 2px 20px rgba(229, 62, 62, 0.6), 0 0 30px rgba(229, 62, 62, 0.4);
  }
}

.workshop-info {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.materials-section h3,
.benefits-section h3 {
  font-size: 0.7rem;
  font-weight: bold;
  color: #333;
  margin-bottom: 3px;
}

.materials-section ul,
.benefits-section ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.materials-section li,
.benefits-section li {
  font-size: 0.6rem;
  color: #555;
  margin-bottom: 2px;
  padding-left: 10px;
  position: relative;
}

.materials-section li::before,
.benefits-section li::before {
  content: "•";
  color: #e53e3e;
  font-weight: bold;
  position: absolute;
  left: 0;
}

.registration-info {
  background: #f8f9fa;
  border-radius: 6px;
  padding: 6px;
  border: 2px solid transparent;
  background-clip: padding-box;
  position: relative;
}

.registration-info::before {
  content: '';
  position: absolute;
  top: -2px;
  left: -2px;
  right: -2px;
  bottom: -2px;
  background: linear-gradient(45deg, #e53e3e, #c53030, #e53e3e);
  border-radius: 12px;
  z-index: -1;
  opacity: 0.3;
  animation: borderGlow 3s ease-in-out infinite;
}

.info-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 2px;
  padding: 1px 0;
  font-size: 0.6rem;
}

.info-item:last-child {
  margin-bottom: 0;
}

.info-label {
  font-weight: 600;
  color: #333;
}

.info-value {
  color: #666;
  font-weight: 500;
}

.workshop-details {
  background: #f8f9fa;
  border-radius: 10px;
  padding: 12px;
  margin-bottom: 15px;
  border: 2px solid transparent;
  background-clip: padding-box;
  position: relative;
}

.workshop-details::before {
  content: '';
  position: absolute;
  top: -2px;
  left: -2px;
  right: -2px;
  bottom: -2px;
  background: linear-gradient(45deg, #e53e3e, #c53030, #e53e3e);
  border-radius: 17px;
  z-index: -1;
  opacity: 0.3;
  animation: borderGlow 3s ease-in-out infinite;
}

@keyframes borderGlow {
  0%, 100% {
    opacity: 0.3;
  }
  50% {
    opacity: 0.6;
  }
}

.detail-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 4px;
  padding: 3px 0;
  font-size: 0.8rem;
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
  gap: 4px;
  background: linear-gradient(135deg, #e53e3e 0%, #c53030 100%);
  color: white;
  text-decoration: none;
  padding: 8px 16px;
  border-radius: 50px;
  font-weight: bold;
  font-size: 0.9rem;
  transition: all 0.3s ease;
  box-shadow: 0 8px 25px rgba(229, 62, 62, 0.3);
  width: 100%;
  position: relative;
  overflow: hidden;
  margin-top: 6px;
  flex-shrink: 0;
}

.register-button::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
  transition: left 0.5s;
}

.register-button:hover::before {
  left: 100%;
}

.register-button:hover {
  transform: translateY(-2px);
  box-shadow:
    0 12px 35px rgba(229, 62, 62, 0.4),
    0 0 30px rgba(229, 62, 62, 0.3);
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
    width: 90vw;
    height: 112.5vw;
    max-width: 90vw;
    max-height: 90vh;
    margin: 10px;
  }

  .poster-container {
  height: 260px; /* atau persentase tetap seperti 60% */
  flex-shrink: 0;
}

  .arduino-title {
    font-size: 1.2rem;
  }

  .arduino-subtitle {
    font-size: 1rem;
  }

  .speaker-photo {
    width: 40px;
    height: 40px;
  }

  .speaker-info h3 {
    font-size: 0.5rem;
  }

  .speaker-info p {
    font-size: 0.4rem;
  }

  .popup-content {
    padding: 15px;
  }

  .workshop-title {
    font-size: 0.8rem;
  }

  .materials-section h3,
  .benefits-section h3 {
    font-size: 0.7rem;
  }

  .materials-section li,
  .benefits-section li {
    font-size: 0.6rem;
  }

  .info-item {
    font-size: 0.6rem;
  }

  .register-button {
    padding: 8px 16px;
    font-size: 0.8rem;
  }
}

  </style>




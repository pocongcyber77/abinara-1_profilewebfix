<template>
  <div 
    class="flip-card-container"
    @mouseenter="handleHover"
    @mouseleave="handleHoverLeave"
  >
    <div 
      class="flip-card"
      :class="{ 'flipped': isFlipped }"
    >
      <!-- Front side - Image (no background/card) -->
      <div class="flip-card-front">
        <img
          :src="imageSrc"
          :alt="imageAlt"
          class="flip-card-image"
        />
        <div class="flip-card-overlay">
          <div class="play-button">
            <svg class="play-icon" viewBox="0 0 24 24" fill="currentColor">
              <path d="M8 5v14l11-7z"/>
            </svg>
          </div>
        </div>
      </div>

      <!-- Back side - Video (no frame container) -->
      <div class="flip-card-back">
        <div class="video-container">
          <iframe
            :src="videoUrl"
            title="YouTube video player"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
            allowfullscreen
            class="video-iframe"
          ></iframe>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const props = defineProps({
  imageSrc: {
    type: String,
    required: true
  },
  imageAlt: {
    type: String,
    default: 'Image'
  },
  videoId: {
    type: String,
    required: true
  }
})

const isFlipped = ref(false)
const timeoutId = ref(null)
const hasHovered = ref(false)

// YouTube video URL with autoplay and mute
const videoUrl = `https://www.youtube.com/embed/${props.videoId}?autoplay=1&mute=1&rel=0&modestbranding=1`

const handleHover = () => {
  hasHovered.value = true
  if (timeoutId.value) {
    clearTimeout(timeoutId.value)
    timeoutId.value = null
  }
  isFlipped.value = true
}

const handleHoverLeave = () => {
  // Don't flip back on hover leave if it was triggered by timeout
  if (!hasHovered.value) {
    return
  }
}

const startAutoFlip = () => {
  timeoutId.value = setTimeout(() => {
    if (!hasHovered.value) {
      isFlipped.value = true
    }
  }, 2000) // 2 seconds
}

onMounted(() => {
  startAutoFlip()
})

onUnmounted(() => {
  if (timeoutId.value) {
    clearTimeout(timeoutId.value)
  }
})
</script>

<style scoped>
.flip-card-container {
  perspective: 1000px;
  width: 70%; /* 50% + 40% = 70% (40% lebih besar dari 50%) */
  height: 100%;
  position: relative;
  margin: 0 auto; /* Center the container */
}

.flip-card {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  transform-style: preserve-3d;
  cursor: pointer;
}

.flip-card.flipped {
  transform: rotateY(180deg);
}

.flip-card-front,
.flip-card-back {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
}

/* Front side - Image (maintain original size and position) */
.flip-card-front {
  display: flex;
  align-items: center;
  justify-content: center;
  background: transparent;
}

.flip-card-image {
  width: 100%;
  height: auto;
  max-width: 100%;
  object-fit: contain;
  transition: transform 0.3s ease;
}

.flip-card-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.flip-card-front:hover .flip-card-overlay {
  opacity: 1;
}

.flip-card-front:hover .flip-card-image {
  transform: scale(1.05);
}

.play-button {
  width: 70px; /* 40% lebih besar dari 60px */
  height: 70px;
  background: rgba(255, 255, 255, 0.9);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}

.play-button:hover {
  background: rgba(255, 255, 255, 1);
  transform: scale(1.1);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
}

.play-icon {
  width: 28px; /* 40% lebih besar dari 24px */
  height: 28px;
  color: #e53e3e;
  margin-left: 4px;
}

/* Back side - Video (16:9 aspect ratio, no frame) */
.flip-card-back {
  background: transparent;
  transform: rotateY(180deg);
  display: flex;
  align-items: center;
  justify-content: center;
}

.video-container {
  width: 100%;
  height: 0;
  padding-bottom: 56.25%; /* 16:9 aspect ratio (9/16 = 0.5625) */
  position: relative;
  border-radius: 10px;
  overflow: hidden;
  background: #000;
}

.video-iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border-radius: 10px;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .flip-card-container {
    width: 100%; /* Full width di mobile */
    max-width: 400px; /* Maksimal width untuk mobile */
  }
  
  .play-button {
    width: 60px; /* 40% lebih besar dari 50px */
    height: 60px;
  }
  
  .play-icon {
    width: 24px; /* 40% lebih besar dari 20px */
    height: 24px;
  }
}

/* Animation keyframes for extra flair */
@keyframes pulse {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.05);
  }
  100% {
    transform: scale(1);
  }
}

.flip-card-front:hover .play-button {
  animation: pulse 2s infinite;
}
</style> 
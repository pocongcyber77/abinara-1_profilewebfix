<template>
  <section class="fullscreen">
    <div class="bg-white py-16">
      <div class="mx-auto px-4 lg:ml-10 md:ml-4 ml-2">
        <!-- Mobile: Teks di atas -->
        <div class="block md:hidden mb-8">
          <div class="text-center">
            <h1
              data-aos="fade-down"
              class="text-5xl font-bold gradient-text"
            >
              ABINARA-1
            </h1>
            <p
              data-aos="fade-up"
              class="mt-6 text-lg font-semibold text-gray-800 leading-relaxed text-shadow"
            >
              Abinara-1 is a team that conducts research and competition for
              <span class="highlight"
                >legged autonomous robots with missions to rescue victims.</span
              >
              The team consists of students of Sepuluh Nopember Institute of Technology. one of the
              competitions that is followed is KRSRI (Kontes Robot SAR Indonesia).
            </p>
            
            <!-- Workshop Button Mobile -->
            <button
              @click="openWorkshopPopup"
              class="mt-8 px-8 py-4 bg-gradient-to-r from-red-600 to-red-700 text-white font-bold rounded-full shadow-lg hover:shadow-xl transition-all duration-300 transform hover:scale-105"
            >
              🎓 Join Workshop
            </button>
          </div>
        </div>

        <!-- Desktop: Layout normal -->
        <div class="hidden md:flex flex-row items-center justify-between">
          <!-- Kolom Kiri: Teks -->
          <div class="w-1/2 lg:ml-10">
            <h1
              data-aos="fade-down"
              class="lg:text-7xl font-bold leading-tight md:text-6xl text-5xl gradient-text"
            >
              ABINARA-1
            </h1>
            <p
              data-aos="fade-up"
              class="mt-6 text-lg font-semibold text-gray-800 leading-relaxed text-shadow"
            >
              Abinara-1 is a team that conducts research and competition for
              <span class="highlight"
                >legged autonomous robots with missions to rescue victims.</span
              >
              The team consists of students of Sepuluh Nopember Institute of Technology. one of the
              competitions that is followed is KRSRI (Kontes Robot SAR Indonesia).
            </p>
            
            <!-- Workshop Button Desktop -->
            <button
              @click="openWorkshopPopup"
              class="mt-8 px-8 py-4 bg-gradient-to-r from-red-600 to-red-700 text-white font-bold rounded-full shadow-lg hover:shadow-xl transition-all duration-300 transform hover:scale-105"
            >
              🎓 Join Workshop
            </button>
          </div>

          <!-- Kolom Kanan: Flip Card dengan Video -->
          <div class="w-1/2 flip-card-wrapper">
            <FlipCard
              image-src="/src/assets/images/Gambar-Hero.png"
              image-alt="Anggota Tim Abinara-1"
              video-id="mr9PO-w45q0"
            />
          </div>
        </div>

        <!-- Mobile: Gambar/Video di bawah -->
        <div class="block md:hidden">
          <div class="flip-card-wrapper-mobile">
            <FlipCard
              image-src="/src/assets/images/Gambar-Hero.png"
              image-alt="Anggota Tim Abinara-1"
              video-id="mr9PO-w45q0"
            />
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- parallax disini -->
  <div class="parallax-section mt-10 hidden md:block">
    <div class="parallax-background"></div>
  </div>

  <div data-aos="zoom-in-up" class="py-16 items-center self-center mt-20 md:mt-20">
    <h1
      class="lg:text-7xl font-bold leading-tight md:text-6xl sm:text-6xl md:mt-0 text-5xl gradient-text"
    >
      PROJECTS
    </h1>
  </div>
  <div data-aos="zoom-in-up" class="flex flex-col md:flex-row items-center justify-between">
    <RobotSlider />
    <p
      data-aos="zoom-in-up"
      class="m-10 mt-6 text-md sm:text-xl font-semibold text-gray-800 leading-relaxed text-shadow"
    >
      Abinara-1 is a student research and competition team from Sepuluh Nopember Institute of
      Technology (ITS) that develops legged autonomous robots for search and rescue missions. The
      team focuses on building agile robots capable of navigating complex terrains to detect and
      assist disaster victims. Through innovation and real-world challenges, Abinara-1 aims to
      advance robotic solutions that can support emergency response and save lives in
      critical situations.
    </p>
  </div>

  <Achievements />
  <Gallery />
  <!-- <Alumni /> -->
  
  <!-- Workshop Popup -->
  <WorkshopPopup 
    :is-visible="showWorkshopPopup"
    @close="closeWorkshopPopup"
  />
</template>

<script>
import RobotSlider from './RobotSlider.vue'
import Achievements from './AchievementCard.vue'
import Gallery from '../Gallery.vue'
import FlipCard from '../../FlipCard.vue'
import WorkshopPopup from '../../WorkshopPopup.vue'

export default {
  name: 'HomePage',
  components: {
    RobotSlider,
    Achievements,
    Gallery,
    FlipCard,
    WorkshopPopup,
  },
  data() {
    return {
      showWorkshopPopup: false
    }
  },
  methods: {
    openWorkshopPopup() {
      this.showWorkshopPopup = true
    },
    closeWorkshopPopup() {
      this.showWorkshopPopup = false
    }
  }
}
</script>

<style scoped>
.fullscreen {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.text-shadow {
  text-shadow: 2px 2px 6px rgba(0, 0, 0, 0.5);
}

.highlight {
  color: red;
}

.flip-card-wrapper {
  height: auto;
  padding: 20px;
  transition: transform 0.3s ease-in-out;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  width: 100%;
}

.flip-card-wrapper:hover {
  transform: scale(1.02);
}

/* Mobile responsive adjustments */
@media (max-width: 768px) {
  .fullscreen {
    height: auto;
    min-height: 100vh;
    padding: 20px 0;
  }
  
  .flip-card-wrapper {
    padding: 10px;
    margin-bottom: 20px;
  }
  
  .flip-card-wrapper-mobile {
    width: 100%;
    padding: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 100px; /* Tambah 40px lagi dari 60px = 100px */
  }
}

.parallax-section {
  height: 300px;
  overflow: hidden;
  position: relative;
}

.parallax-background {
  background-image: url('/src/assets/images/teams/full-tim.png');
  filter: brightness(50%);
  height: 100vh;
  width: 100vw;
  position: absolute;
  top: 0;
  left: 0;
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}
</style>

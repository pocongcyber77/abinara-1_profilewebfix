<template>
  <div class="advance-page">
    <div class="container mx-auto px-4 py-16">
             <!-- Header -->
       <div class="workshop-header mb-16">
         <!-- Main Title Section -->
         <div class="title-section">
           <h1 class="main-title">
             <span class="title-advance">Advance 1.0</span>
           </h1>
         </div>
         
                   <!-- Abinara & Subtitle Section -->
          <div class="abinara-subtitle-section">
            <h2 class="abinara-subtitle">
              Abinara Coding, Creative Education, and Robotic Learning
            </h2>
          </div>
         
         <!-- Form Title Section -->
         <div class="form-title-section">
           <div class="form-title-card">
             <h3 class="form-title">Workshop Registration Form</h3>
             <div class="form-title-decoration"></div>
           </div>
         </div>
       </div>

             <!-- Form Container -->
       <div class="max-w-2xl mx-auto">
         <div class="bg-white rounded-2xl form-card-shadow p-8 md:p-12">
          <form @submit.prevent="submitForm" class="space-y-6">
            <!-- Nama -->
            <div class="form-group">
              <label for="nama" class="form-label">Nama Lengkap *</label>
              <input
                id="nama"
                v-model="formData.nama"
                type="text"
                class="form-input"
                placeholder="Masukkan nama lengkap"
                required
              />
            </div>

            <!-- NRP -->
            <div class="form-group">
              <label for="nrp" class="form-label">NRP *</label>
              <input
                id="nrp"
                v-model="formData.nrp"
                type="text"
                class="form-input"
                placeholder="Contoh: 05211940000001"
                required
              />
            </div>

            <!-- Email -->
            <div class="form-group">
              <label for="email" class="form-label">Email *</label>
              <input
                id="email"
                v-model="formData.email"
                type="email"
                class="form-input"
                placeholder="email@student.its.ac.id"
                required
              />
            </div>

            <!-- Nomor Telepon -->
            <div class="form-group">
              <label for="telepon" class="form-label">Nomor Telepon *</label>
              <input
                id="telepon"
                v-model="formData.telepon"
                type="tel"
                class="form-input"
                placeholder="081234567890"
                required
              />
            </div>

            <!-- Fakultas -->
            <div class="form-group">
              <label for="fakultas" class="form-label">Fakultas *</label>
              <select
                id="fakultas"
                v-model="formData.fakultas"
                class="form-select"
                required
              >
                <option value="">Pilih Fakultas</option>
                <option value="FTEIC">FTEIC</option>
                <option value="FTSPK">FTSPK</option>
                <option value="FTIRS">FTIRS</option>
                <option value="FSAD">FSAD</option>
                <option value="FKK">FKK</option>
                <option value="FTK">FTK</option>
                <option value="FDKBD">FDKBD</option>
                <option value="FV">FV</option>
              </select>
            </div>

            <!-- Departemen -->
            <div class="form-group">
              <label for="departemen" class="form-label">Departemen *</label>
              <select
                id="departemen"
                v-model="formData.departemen"
                class="form-select"
                required
              >
                <option value="">Pilih Departemen</option>
                <option v-for="dept in departemenList" :key="dept" :value="dept">
                  {{ dept }}
                </option>
              </select>
            </div>

            <!-- Materi -->
            <div class="form-group">
              <label for="materi" class="form-label">Materi *</label>
              <select
                id="materi"
                v-model="formData.materi"
                class="form-select"
                required
              >
                <option value="">Pilih Materi</option>
                <option value="Ilmu Penghitaman">Ilmu Penghitaman</option>
                <option value="Filsafat Lele">Filsafat Lele</option>
                <option value="Hacking Smart Tolet">Hacking Smart Tolet</option>
                <option value="Astrologi Dukun Cirebon">Astrologi Dukun Cirebon</option>
              </select>
            </div>

            <!-- Paket -->
            <div class="form-group">
              <label for="paket" class="form-label">Paket *</label>
              <select
                id="paket"
                v-model="formData.paket"
                class="form-select"
                required
              >
                <option value="">Pilih Paket</option>
                <option value="Paket Jeroan Kambing">Paket Jeroan Kambing</option>
                <option value="Paket Organ Dukun Cirebon">Paket Organ Dukun Cirebon</option>
                <option value="Paket Rudal Kambing Meksiko">Paket Rudal Kambing Meksiko</option>
              </select>
            </div>

            <!-- Submit Button -->
            <div class="form-group pt-6">
              <button
                type="submit"
                class="submit-button"
                :disabled="isSubmitting"
              >
                <span v-if="!isSubmitting">Daftar Workshop</span>
                <span v-else class="flex items-center gap-2">
                  <svg class="animate-spin h-5 w-5" viewBox="0 0 24 24">
                    <circle
                      class="opacity-25"
                      cx="12"
                      cy="12"
                      r="10"
                      stroke="currentColor"
                      stroke-width="4"
                    ></circle>
                    <path
                      class="opacity-75"
                      fill="currentColor"
                      d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"
                    ></path>
                  </svg>
                  Mendaftar...
                </span>
              </button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

const isSubmitting = ref(false)

const formData = reactive({
  nama: '',
  nrp: '',
  email: '',
  telepon: '',
  fakultas: '',
  departemen: '',
  materi: '',
  paket: ''
})

// 40 dummy departemen dengan nama absurd
const departemenList = [
  'Teknik Skibidi Brainrot',
  'Ilmu Penghitaman Digital',
  'Filsafat Lele Modern',
  'Hacking Smart Toilet',
  'Astrologi Dukun Cirebon',
  'Teknik Rudal Kambing',
  'Ilmu Jeroan Kambing',
  'Fisika Organ Dukun',
  'Matematika Skibidi',
  'Kimia Brainrot',
  'Biologi Lele Terapan',
  'Teknik Toilet Pintar',
  'Ilmu Dukun Digital',
  'Fisika Rudal Meksiko',
  'Matematika Jeroan',
  'Kimia Organ Modern',
  'Biologi Skibidi',
  'Teknik Brainrot',
  'Ilmu Lele Digital',
  'Fisika Toilet Pintar',
  'Matematika Dukun',
  'Kimia Rudal Kambing',
  'Biologi Jeroan',
  'Teknik Organ Dukun',
  'Ilmu Skibidi Modern',
  'Fisika Brainrot',
  'Matematika Lele',
  'Kimia Toilet Pintar',
  'Biologi Dukun Digital',
  'Teknik Rudal Modern',
  'Ilmu Jeroan Pintar',
  'Fisika Organ Skibidi',
  'Matematika Brainrot',
  'Kimia Lele Digital',
  'Biologi Toilet Modern',
  'Teknik Dukun Pintar',
  'Ilmu Rudal Skibidi',
  'Fisika Jeroan Brainrot',
  'Matematika Organ Lele',
  'Kimia Toilet Dukun'
]

const submitForm = async () => {
  isSubmitting.value = true
  
  try {
    // Simulasi pengiriman form
    await new Promise(resolve => setTimeout(resolve, 2000))
    
    // Di sini nantinya akan diintegrasikan dengan Google Docs
    console.log('Form Data:', formData)
    
    // Reset form
    Object.keys(formData).forEach(key => {
      formData[key] = ''
    })
    
    alert('Pendaftaran berhasil! Terima kasih telah mendaftar workshop Advance Abinara.')
    
  } catch (error) {
    console.error('Error submitting form:', error)
    alert('Terjadi kesalahan saat mendaftar. Silakan coba lagi.')
  } finally {
    isSubmitting.value = false
  }
}
</script>

<style scoped>
.advance-page {
  min-height: 100vh;
  background: #ffffff; /* Putih dengan opacity 100% */
  padding: 20px 0;
}

/* Workshop Header Styling */
.workshop-header {
  text-align: center;
  position: relative;
}

/* Main Title Section */
.title-section {
  margin-bottom: 20px;
}

.main-title {
  font-size: 4.5rem;
  font-weight: 900;
  line-height: 1.1;
  margin: 0;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
}

.title-advance {
  background: linear-gradient(135deg, #e53e3e 0%, #c53030 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  font-weight: 900;
  position: relative;
  text-shadow: 0 0 30px rgba(229, 62, 62, 0.3);
}

.title-advance::after {
  content: '';
  position: absolute;
  bottom: -8px;
  left: 50%;
  transform: translateX(-50%);
  width: 80%;
  height: 4px;
  background: linear-gradient(90deg, #e53e3e, #c53030);
  border-radius: 2px;
}

/* Abinara & Subtitle Section */
.abinara-subtitle-section {
  margin-bottom: 40px;
  position: relative;
}

.abinara-subtitle {
  font-size: 2.5rem;
  font-weight: 700;
  line-height: 1.3;
  margin: 0;
  position: relative;
  text-align: center;
  color: #2d3748;
  letter-spacing: 1px;
  background: linear-gradient(135deg, #f7fafc 0%, #edf2f7 100%);
  padding: 20px 30px;
  border-radius: 30px;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
  border: 2px solid rgba(229, 62, 62, 0.1);
  position: relative;
  overflow: hidden;
  display: inline-block;
}

.abinara-subtitle::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(229, 62, 62, 0.05), transparent);
  transition: left 0.6s ease;
}

.abinara-subtitle:hover::before {
  left: 100%;
}

/* Form Title Section */
.form-title-section {
  margin-bottom: 30px;
}

.form-title-card {
  display: inline-block;
  position: relative;
  padding: 20px 40px;
  background: linear-gradient(135deg, #ffffff 0%, #f8f9fa 100%);
  border-radius: 20px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  border: 2px solid rgba(229, 62, 62, 0.1);
  overflow: hidden;
}

.form-title-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
  background: linear-gradient(90deg, #e53e3e, #c53030, #e53e3e);
}

.form-title {
  font-size: 1.75rem;
  font-weight: 700;
  color: #2d3748;
  margin: 0;
  letter-spacing: 1px;
  position: relative;
}

.form-title-decoration {
  position: absolute;
  bottom: -5px;
  left: 50%;
  transform: translateX(-50%);
  width: 50px;
  height: 3px;
  background: linear-gradient(90deg, #e53e3e, #c53030);
  border-radius: 2px;
}

/* Responsive Design */
@media (max-width: 768px) {
  .main-title {
    font-size: 3rem;
  }
  
  .abinara-subtitle {
    font-size: 1.8rem;
    padding: 15px 20px;
  }
  
  .form-title {
    font-size: 1.5rem;
  }
}

.form-card-shadow {
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.15), 
              0 8px 25px rgba(229, 62, 62, 0.1),
              0 0 0 1px rgba(229, 62, 62, 0.05);
  border: 1px solid rgba(229, 62, 62, 0.1);
  backdrop-filter: blur(10px);
}

.form-group {
  display: flex;
  flex-direction: column;
}

.form-label {
  font-weight: 600;
  color: #333;
  margin-bottom: 8px;
  font-size: 1rem;
}

.form-input,
.form-select {
  padding: 12px 16px;
  border: 2px solid #e2e8f0;
  border-radius: 12px;
  font-size: 1rem;
  transition: all 0.3s ease;
  background: white;
}

.form-input:focus,
.form-select:focus {
  outline: none;
  border-color: #e53e3e;
  box-shadow: 0 0 0 3px rgba(229, 62, 62, 0.1);
}

.form-input::placeholder {
  color: #a0aec0;
}

.submit-button {
  width: 100%;
  background: linear-gradient(135deg, #e53e3e 0%, #c53030 100%);
  color: white;
  border: none;
  padding: 16px 32px;
  border-radius: 12px;
  font-size: 1.1rem;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 8px 25px rgba(229, 62, 62, 0.3);
}

.submit-button:hover:not(:disabled) {
  transform: translateY(-2px);
  box-shadow: 0 12px 35px rgba(229, 62, 62, 0.4);
  background: linear-gradient(135deg, #c53030 0%, #a52a2a 100%);
}

.submit-button:disabled {
  opacity: 0.7;
  cursor: not-allowed;
  transform: none;
}

/* Responsive */
@media (max-width: 768px) {
  .advance-page {
    padding: 10px 0;
  }
  
  .container {
    padding: 0 15px;
  }
  
  .bg-white {
    padding: 20px;
  }
}
</style> 
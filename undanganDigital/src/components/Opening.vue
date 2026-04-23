<script setup>
const emit = defineEmits(['open'])
</script>

<template>
  <section class="opening">

    <!-- FOTO LANGSUNG TANPA FRAME -->
    <img 
      src="@/assets/picture/pict6.jpeg" 
      class="photo"
    />

    <!-- TEXT -->
    <div class="text">
      <p class="subtitle">Undangan Pernikahan</p>
      <h1 class="title">Gilang & Maya</h1>

      <button class="btn" @click="emit('open')">
        Buka Undangan
      </button>
    </div>

  </section>
</template>

<style scoped>

/* BACKGROUND */
.opening {
  height: 100vh;
  background: url('../assets/picture/background.png') center/cover no-repeat;
  position: relative;
}

/* FOTO DI-ALIGN KE FRAME BACKGROUND */
.photo {
  position: absolute;

  /* INI YANG HARUS DI-TUNING */
  top: 28%;
  left: 50%;
  transform: translateX(-50%);

  width: 200px;
  height: 260px;

  object-fit: cover;

  /* sedikit radius biar halus */
  border-radius: 100px 100px 20px 20px;
}

/* TEXT */
.text {
  position: absolute;
  bottom: 12%;
  width: 100%;
  text-align: center;
}

.subtitle {
  letter-spacing: 3px;
  font-size: 12px;
  color: #6b6b6b;
}

.title {
  font-family: 'Playfair Display', serif;
  font-size: 28px;
  color: #2c2c2c;
  margin: 10px 0 20px;
}

/* BUTTON */
.btn {
  padding: 12px 28px;
  border-radius: 30px;
  border: none;
  background: linear-gradient(135deg, #c8a96a, #a8864c);
  color: white;
}

/* RESPONSIVE BIAR PRESISI */
@media (max-width: 400px) {
  .photo {
    top: 26%;
    width: 180px;
    height: 240px;
  }
}

</style>
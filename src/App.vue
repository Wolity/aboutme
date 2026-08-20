We now should pull up the original style the chat spoiling<script setup>
import { ref, onMounted } from "vue";
import introVideoSrc from "./assets/intro.mp4";
import jsLogo from "../src/assets/javascript_logo.png";
import tsLogo from "../src/assets/typescript_logo.png";

const isLoaded = ref(false);
const audio = ref(null);
const isPlaying = ref(false);
const current = ref(0);
const duration = ref(0);

const isJsTs = ref(false);
const isTsTs = ref(false);

onMounted(() => {
  setTimeout(() => {
    isLoaded.value = true;
  }, 3000);

  const el = audio.value;
  if (!el) return;

  el.addEventListener("loadedmetadata", () => {
    duration.value = el.duration;
  });

  el.addEventListener("timeupdate", () => {
    current.value = el.currentTime;
  });
});

function togglePlay() {
  const el = audio.value;
  if (!el) return;

  if (!isPlaying.value) {
    el.play()
      .then(() => {
        isPlaying.value = true;
      })
      .catch((err) => console.log("Playback error:", err));
  } else {
    el.pause();
    isPlaying.value = false;
  }
}

function onSeek() {
  const el = audio.value;
  if (el) {
    el.currentTime = current.value;
  }
}
</script>

<template>
  <div class="intro-overlay" :class="{ 'fade-out': isLoaded }">
    <video class="intro-video" autoplay muted playsinline>
      <source :src="introVideoSrc" type="video/mp4" />
    </video>

    <div class="video-noise"></div>
  </div>

  <header class="top-navbar">
    <div class="nav-container">
      <a href="/" class="nav-link home-link">
        HOME
      </a>

      <a href="/" class="logo-link">
        <div class="nordic-cross-icon swedish-flag">
          <div class="cross-box"></div>
          <div class="cross-box"></div>
          <div class="cross-box"></div>
          <div class="cross-box"></div>
        </div>
      </a>

      <a href="/contact" class="nav-link contact-link">
        CONTACT
      </a>
    </div>
  </header>

  <div class="page-wrapper">
    <div class="main">
      <nav class="header anim-block delay-1">
        <h1>Frontend developer</h1>
      </nav>

      <div class="carousel-container anim-block delay-2">
        <div class="icons-group">
          <a
            href="https://vuejs.org/"
            target="_blank"
            class="icon-wrap vue-wrap"
          >
            <img
              src="../src/assets/Bg_vue.png"
              class="tech-icon"
              alt="Vue"
            />
          </a>

          <div
            class="icon-wrap script-toggle-wrap"
            @click="isJsTs = !isJsTs"
          >
            <img
              :src="isJsTs ? tsLogo : jsLogo"
              class="tech-icon toggle-icon"
              alt="JS/TS"
            />
          </div>

          <div
            class="icon-wrap script-toggle-wrap"
            @click="isTsTs = !isTsTs"
          >
            <img
              :src="isTsTs ? jsLogo : tsLogo"
              class="tech-icon toggle-icon"
              alt="TS/JS"
            />
          </div>
        </div>
      </div>

      <div class="projects-section anim-block delay-3">
        <div class="projects-content">
          <h2>My Projects</h2>

          <div class="project-buttons">
            <a
              href=""
              target="_blank"
              class="glass-btn neon-glow"
            >
              <span>Merchandise</span>
              <span class="arrow">↗</span>
            </a>

            <a
              href=""
              target="_blank"
              class="glass-btn neon-glow"
            >
              <span>Healthcare</span>
              <span class="arrow">↗</span>
            </a>

            <a
              href="https://github.com/Wolity/Phasmophobia-Clicker"
              target="_blank"
              class="glass-btn neon-glow"
            >
              <span>Phasmaphobia tool</span>
              <span class="arrow">↗</span>
            </a>
          </div>
        </div>
      </div>

      <div class="music-player anim-block delay-4">
        <img
          src="../src/assets/album.jpeg"
          class="cover"
          alt="Album Cover"
        />

        <div class="track-info">
          <div class="title">OTHERSIDE instrumental</div>

          <input
            type="range"
            min="0"
            :max="duration"
            v-model="current"
            @input="onSeek"
          />
        </div>

        <button class="play-btn" @click="togglePlay">
          {{ isPlaying ? "⏸" : "▶" }}
        </button>

        <audio
          ref="audio"
          src="../src/assets/OTHERSIDE_Beat.mp3"
          preload="metadata"
        ></audio>
      </div>
    </div>

    <footer class="footer-stretched anim-block delay-4">
<<<<<<< HEAD
      <router-link to="/" class="footer-link">
        © 2026 ALEXANDER · ALL RIGHTS RESERVED
      </router-link>
=======
      <a href="/" class="footer-link">
        © 2026 ALEXANDER ASTAPOV · ALL RIGHTS RESERVED
      </a>
>>>>>>> 17e3c90 (navigation_update)
    </footer>
  </div>
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@1,400;1,500;1,600&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Nova+Square&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Oxanium:wght@400;500;600;700&display=swap");
@import url("https://fonts.googleapis.com/css2?family=UnifrakturCook:wght@700&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Electrolize&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.page-wrapper {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background: radial-gradient(circle at top, #1e293b, #0f172a, #020617);
  overflow-x: hidden;
  animation: fogReveal 1.8s cubic-bezier(0.22, 1, 0.36, 1) forwards;
}

.top-navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 60px;
  background: #000000;
  border-bottom: 1px solid rgba(56, 189, 248, 0.2);
  z-index: 100;
  display: flex;
  align-items: center;
  justify-content: center;
}

.nav-container {
  width: 100%;
  max-width: 900px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 30px;
}

.nav-link {
  font-family: "Cormorant Garamond", serif;
  font-style: italic;
  font-size: 20px;
  color: #38bdf8;
  letter-spacing: 2px;
  transition: all 0.3s ease;
  text-shadow: none;
}

.home-link {
  text-decoration: none;

  &:hover {
    text-decoration: underline;
    text-shadow:
      0 0 12px rgba(56, 189, 248, 0.9),
      0 0 25px rgba(56, 189, 248, 0.5);
  }
}

.contact-link {
  text-decoration: none;

  &:hover {
    text-decoration: underline;
    text-shadow:
      0 0 12px rgba(56, 189, 248, 0.9),
      0 0 25px rgba(56, 189, 248, 0.5);
  }
}

.logo-link {
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
}

.nordic-cross-icon.swedish-flag {
  display: grid;
  grid-template-columns: 24px 44px;
  grid-template-rows: 22px 18px;
  gap: 8px;
  padding: 0;
}

.cross-box {
  background: #2563eb;
  border-radius: 0;
  box-shadow: none;
}

.intro-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: 999;
  overflow: hidden;
  background: #000;
  transition:
    opacity 0.8s ease,
    visibility 0.8s ease;

  &.fade-out {
    opacity: 0;
    visibility: hidden;
    pointer-events: none;
  }
}

.intro-video {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.video-noise {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(
    circle,
    transparent 40%,
    rgba(0, 0, 0, 0.7) 100%
  );
  pointer-events: none;
}

@keyframes fogReveal {
  0% {
    filter: blur(25px) brightness(0.2);
    transform: scale(1.05);
  }

  100% {
    filter: blur(0) brightness(1);
    transform: scale(1);
  }
}

@keyframes popIn {
  0% {
    opacity: 0;
    transform: translateY(60px) scale(0.9);
  }

  60% {
    opacity: 1;
    transform: translateY(-10px) scale(1.02);
  }

  100% {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

@keyframes neonPulse {
  0%,
  100% {
    box-shadow:
      0 0 15px rgba(56, 189, 248, 0.4),
      inset 0 0 10px rgba(56, 189, 248, 0.2);
  }

  50% {
    box-shadow:
      0 0 25px rgba(56, 189, 248, 0.8),
      inset 0 0 15px rgba(56, 189, 248, 0.4);
  }
}

.main {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 120px 20px 40px 20px;
  gap: 50px;
  text-align: center;
  font-family: "Oxanium", sans-serif;
  color: #f8fafc;
}

.anim-block {
  opacity: 0;
  animation: popIn 0.8s cubic-bezier(0.34, 1.56, 0.64, 1) forwards;
}

.delay-1 {
  animation-delay: 2.8s;
}

.delay-2 {
  animation-delay: 3s;
}

.delay-3 {
  animation-delay: 3.2s;
}

.delay-4 {
  animation-delay: 3.4s;
}

.header {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 15px;
}

h1 {
  font-family: "Electrolize", sans-serif;
  font-size: 42px;
  font-weight: 400;
  letter-spacing: 0;
  color: #ffffff;
}

.carousel-container {
  width: 100%;
  display: flex;
  justify-content: center;
}

.icons-group {
  display: flex;
  gap: 25px;
  padding: 10px 5px;
}

.tech-icon {
  width: 90px;
  height: 90px;
  border-radius: 18px;
  object-fit: cover;
  flex-shrink: 0;
  transition: all 0.3s ease;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

.vue-wrap {
  display: inline-block;
  cursor: pointer;

  &:hover .tech-icon {
    transform: translateY(-5px) scale(1.05);
    box-shadow:
      0 0 25px rgba(56, 189, 248, 0.8),
      0 0 10px rgba(56, 189, 248, 0.5);
  }
}

.script-toggle-wrap {
  cursor: pointer;
  display: inline-block;

  .toggle-icon {
    transition:
      transform 0.3s ease,
      opacity 0.3s ease,
      box-shadow 0.3s ease;
  }

  &:hover .toggle-icon {
    transform: translateY(-5px) scale(1.05);
    box-shadow:
      0 0 25px rgba(56, 189, 248, 0.8),
      0 0 10px rgba(56, 189, 248, 0.5);
  }
}

.projects-section {
  position: relative;
  width: 100%;
  max-width: 500px;
  border-radius: 24px;
  overflow: hidden;
  min-height: 250px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(
    135deg,
    #090d16 0%,
    #111e38 50%,
    #050b14 100%
  );
  border: 1px solid rgba(56, 189, 248, 0.3);
  box-shadow:
    0 10px 30px rgba(0, 0, 0, 0.5),
    inset 0 0 20px rgba(56, 189, 248, 0.1);
}

.projects-content {
  position: relative;
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  padding: 30px;
  width: 100%;
}

.projects-content h2 {
  font-family: "Electrolize", sans-serif;
  font-style: normal;
  font-size: 28px;
  font-weight: 400;
  color: #38bdf8;
  letter-spacing: 2px;
  text-transform: uppercase;
  text-shadow:
    0 0 12px rgba(56, 189, 248, 0.8),
    0 0 25px rgba(56, 189, 248, 0.4);
}

.project-buttons {
  display: flex;
  flex-direction: column;
  gap: 15px;
  width: 100%;
  max-width: 350px;
}

.glass-btn {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 25px;
  background: rgba(15, 23, 42, 0.7);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border: 1.5px solid #38bdf8;
  border-radius: 16px;
  text-decoration: none;
  font-family: "Oxanium", sans-serif;
  color: #f1f5f9;
  font-size: 16px;
  font-weight: 600;
  letter-spacing: 1px;
  transition: all 0.3s ease;
  animation: neonPulse 3s infinite ease-in-out;

  .arrow {
    font-size: 20px;
    color: #38bdf8;
    transition: transform 0.3s ease;
  }

  &:hover {
    background: rgba(56, 189, 248, 0.25);
    transform: translateY(-3px) scale(1.02);
    box-shadow: 0 0 30px rgba(56, 189, 248, 0.9);

    .arrow {
      transform: translate(3px, -3px);
    }
  }
}

.music-player {
  width: 100%;
  max-width: 500px;
  padding: 20px;
  border-radius: 24px;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 20px;
}

.cover {
  width: 90px;
  height: 90px;
  border-radius: 12px;
  object-fit: cover;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
}

.track-info {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 8px;
  text-align: left;
}

.title {
  font-family: "Electrolize", sans-serif;
  font-style: normal;
  font-size: 24px;
  font-weight: 400;
  color: white;
  letter-spacing: 1px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.track-info input[type="range"] {
  width: 100%;
  cursor: pointer;
  accent-color: #38bdf8;
}

.play-btn {
  background: rgba(255, 255, 255, 0.1);
  color: #fff;
  border: 1px solid rgba(255, 255, 255, 0.2);
  width: 58px;
  height: 58px;
  font-size: 20px;
  border-radius: 16px;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
}

.play-btn:hover {
  background: rgba(255, 255, 255, 0.2);
  transform: scale(1.05);
}

.footer-stretched {
  width: 100%;
  background: #000000;
  border-top: none;
  border-bottom: none;
  text-align: center;
  margin-top: auto;
  padding: 20px 0;
}

.footer-link {
  font-family: "Cormorant Garamond", serif;
  font-style: italic;
  font-size: 18px;
  color: #38bdf8;
  letter-spacing: 4px;
  text-decoration: none;
  text-transform: uppercase;
  text-shadow: none;
  transition: all 0.3s ease;

  &:hover {
    text-decoration: underline;
    text-shadow:
      0 0 12px rgba(56, 189, 248, 0.9),
      0 0 25px rgba(56, 189, 248, 0.5);
  }
}
</style>
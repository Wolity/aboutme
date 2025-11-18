<script setup>
import { ref, onMounted } from "vue";

const audio = ref(null);

const isPlaying = ref(false);
const current = ref(0);
const duration = ref(0);

onMounted(() => {
  const el = audio.value;

  el.addEventListener("loadedmetadata", () => {
    duration.value = el.duration;
  });

  el.addEventListener("timeupdate", () => {
    current.value = el.currentTime;
  });
});

function togglePlay() {
  const el = audio.value;
  if (!isPlaying.value) {
    el.play();
  } else {
    el.pause();
  }
  isPlaying.value = !isPlaying.value;
}

function onSeek() {
  audio.value.currentTime = current.value;
}
</script>

<template>
  <div class="main">
    <nav>
      <h1>Frontend developer</h1>
      <p>you can find me in Telegram:</p>

      <a href="https://t.me/wolity" target="_blank" rel="noopener noreferrer">
        <img src="../src/assets/telegramm.png" class="telegram" />
      </a>
    </nav>

    <div class="technologies">
      <h2>Main technologies:</h2>
      <div class="icons">
        <a href="https://vuejs.org/" target="_blank" rel="noopener noreferrer">
          <img src="../src/assets/Bg_vue.png" class="vue" />
        </a>
        <a
          href="https://en.wikipedia.org/wiki/JavaScript"
          target="_blank"
          rel="noopener noreferrer"
        >
          <img src="../src/assets/javascript_logo.png" class="javascript" />
        </a>
        <a
          href="https://en.wikipedia.org/wiki/TypeScript"
          target="_blank"
          rel="noopener noreferrer"
        >
          <img src="../src/assets/typescript_logo.png" class="typescript" />
        </a>
        <a
          href="https://www.python.org/"
          target="_blank"
          rel="noopener noreferrer"
        >
          <img src="../src/assets/python_icon.jpeg" class="python" />
        </a>
      </div>
    </div>

    <!-- 🎶 -->
    <div class="music-player">
      <img src="../src/assets/album.jpeg" class="cover" />

      <div class="track-info">
        <div class="title">My Track</div>

        <input
          type="range"
          min="0"
          :max="duration"
          v-model="current"
          @input="onSeek"
        />
      </div>

      <button class="play-btn" @click="togglePlay">
        {{ isPlaying ? "⏸ Pause" : "▶ Play" }}
      </button>

      <audio
        ref="audio"
        src="../src/assets/soundcloudaud.com_PARANOIA INTRO.mp3"
      ></audio>
    </div>
  </div>
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

.main {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 80px;
  gap: 40px;
  text-align: center;
  font-family: "Roboto", sans-serif;
  background: linear-gradient(
    to bottom,
    rgb(11, 28, 93),
    #a4c4ff,
    rgb(11, 28, 93)
  );
}

h1,
h2 {
  text-shadow: 2px 2px 5px rgba(21, 21, 21, 0.3);
}

h1 {
  color: #0f2255;
  font-size: 50px;
  margin: 0;
}

p {
  color: #637ac0;
  font-size: 40px;
  font-weight: 600;
}

.telegram {
  width: 100px;
  height: 100px;
  cursor: pointer;
  display: block;
  margin: 0 auto;
  border-radius: 50%;
  padding: 15px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
  transition: transform 0.3s, box-shadow 0.3s;

  &:hover {
    transform: scale(1.1);
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
  }
}

h2 {
  color: #0f2255;
  font-size: 40px;
  margin: 0 0 20px 0;
}

.icons {
  display: flex;
  align-items: flex-end;
  justify-content: center;
  gap: 40px;
}

.vue,
.javascript,
.typescript,
.python {
  cursor: pointer;
  display: block;
  border-radius: 15px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
  transition: transform 0.3s, box-shadow 0.3s;

  width: 100px;

  &:hover {
    transform: scale(1.1);
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
  }
}

/* 🎵 Стили плеера */
.music-player {
  border: 3px solid #a4c4ff,;
  width: 320px;
  padding: 20px;
  border-radius: 20px;
  background: linear-gradient(
    to bottom,
    rgb(11, 28, 93),
    rgba(20, 41, 126, 0.365)
  );
  backdrop-filter: blur(8px);
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.25);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 15px;
}

.cover {
  width: 100%;
  border-radius: 15px;
}

.track-info {
  width: 100%;
  text-align: left;

  .title {
    color: #0f2255;
    font-size: 20px;
    margin-bottom: 8px;
  }

  input[type="range"] {
    width: 100%;
    cursor: pointer;
  }
}

.play-btn {
  background: #0f2255;
  color: white;
  border: none;
  padding: 10px 25px;
  font-size: 18px;
  border-radius: 12px;
  cursor: pointer;
  transition: 0.3s;

  &:hover {
    transform: scale(1.05);
    background: #1b3b8c;
  }
}
</style>

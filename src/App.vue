<script setup></script>

<template>
  <div class="main">
    <nav>
      <h1>About me:</h1>
      <p>
        Frontend future fullstack developer also learning new technologies you
        can find me in:
      </p>

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
        <a href="https://en.wikipedia.org/wiki/JavaScript" target="_blank" rel="noopener noreferrer">
          <img src="../src/assets/javascript_logo.png" class="javascript" />
        </a>
        <a href="https://en.wikipedia.org/wiki/TypeScript" target="_blank" rel="noopener noreferrer">
          <img src="../src/assets/typescript_logo.png" class="typescript" />
        </a>
        <a href="https://www.python.org/" target="_blank" rel="noopener noreferrer">
          <img src="../src/assets/python_icon.jpeg" class="python" />
        </a>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

.main {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 80px;
  gap: 40px;
  text-align: center;
  font-family: 'Roboto', sans-serif;
  background: linear-gradient(to bottom, #6270a9, #56689a, #384267);
  color: #061b6f;
}

h1, h2 {
  text-shadow: 2px 2px 5px rgba(0,0,0,0.3);
}

h1 {
  font-size: 50px;
  margin: 0;
}

p {
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
 background: linear-gradient(to bottom, #6270a9, #56689a, #384267);
  padding: 15px;
  box-shadow: 0 5px 15px rgba(0,0,0,0.3);
  transition: transform 0.3s, box-shadow 0.3s;

  &:hover {
    transform: scale(1.1);
    box-shadow: 0 10px 25px rgba(0,0,0,0.4);
  }


  &:hover {
    transform: scale(1.1);
    box-shadow: 0 10px 25px rgba(0,0,0,0.4);
  }
}

h2 {
  font-size: 40px;
  margin: 0 0 20px 0;
}

.icons {
  display: flex;
  align-items: flex-end;
  justify-content: center;
  gap: 30px;
}

.vue, .javascript, .typescript, .python {
  cursor: pointer;
  display: block;
  border-radius: 15px;
  box-shadow: 0 5px 15px rgba(0,0,0,0.3);
  transition: transform 0.3s, box-shadow 0.3s;
}

.vue { width: 100px; }
.javascript { width: 100px; }
.typescript { width: 100px; }
.python { width: 100px; }

.vue:hover, .javascript:hover, .typescript:hover, .python:hover {
  transform: scale(1.1);
  box-shadow: 0 10px 25px rgba(0,0,0,0.4);
}
</style>

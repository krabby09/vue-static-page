<script lang="ts" setup>
import { ref } from 'vue'

interface Section {
  title: string
  content: string
  show: boolean
}

const sections = ref<Section[]>([
  {
    title: '한가위의 의미',
    content: '한가위는 풍요와 가족 화합을 기념하는 한국의 대표 명절로, 가을의 수확을 감사하고 가족과 함께 시간을 보내는 날입니다.',
    show: false
  },
  {
    title: '전통 음식',
    content: '송편, 한과, 전 등은 한가위에 빠질 수 없는 전통 음식입니다. 송편은 달 모양을 닮아 풍요와 행운을 기원하는 의미를 담고 있습니다.',
    show: false
  },
  {
    title: '전통 놀이',
    content: '윷놀이와 제기차기 등은 가족과 함께 즐기는 대표적인 한가위 놀이입니다. 세대를 넘어 함께 즐기며 웃음과 추억을 쌓을 수 있습니다.',
    show: false
  },
  {
    title: '한가위 스토리',
    content: '옛날 한가위에 달님에게 소원을 빌던 이야기와 풍요를 기원하는 전설이 전해져 내려옵니다. 밝은 달과 함께 행복을 기원하는 날이죠.',
    show: false
  }
])

const toggleSection = (index: number) => {
  sections.value[index].show = !sections.value[index].show
}
</script>

<template>
  <div class="app">
    <header>
      <h1>🌕 풍성한 한가위 웹페이지</h1>
      <p>가족과 함께 즐기는 한가위 이야기</p>
    </header>

    <main>
      <section v-for="(sec, idx) in sections" :key="idx">
        <div class="section-header">
          <h2>{{ sec.title }}</h2>
          <button @click="toggleSection(idx)">
            {{ sec.show ? '숨기기' : '보기' }}
          </button>
        </div>
        <p v-if="sec.show">{{ sec.content }}</p>
      </section>
    </main>
  </div>
</template>

<style scoped>
.app {
  font-family: 'Noto Sans KR', sans-serif;
  color: #333;
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
}

header {
  text-align: center;
  margin-bottom: 3rem;
}

header h1 {
  font-size: 2.5rem;
  margin-bottom: 0.5rem;
}

header p {
  font-size: 1.2rem;
  color: #666;
}

section {
  margin-bottom: 2rem;
  padding: 1rem;
  border-left: 4px solid #f0c987;
  background: #fff8f0;
  border-radius: 8px;
}

.section-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

section h2 {
  font-size: 1.5rem;
  margin: 0;
}

section p {
  font-size: 1rem;
  line-height: 1.5;
  margin-top: 0.5rem;
}

button {
  background-color: #f0c987;
  border: none;
  padding: 0.4rem 0.8rem;
  border-radius: 6px;
  cursor: pointer;
  font-weight: bold;
}

button:hover {
  background-color: #e0b96e;
}
</style>

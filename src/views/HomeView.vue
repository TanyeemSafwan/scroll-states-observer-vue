<script setup>
import { ref, onMounted } from 'vue';
const headers = [
  'Section 1',
  'Section 2',
  'Section 3',
  'Section 4',
  'Section 5',
];

const currentSection = ref('');

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.intersectionRatio > 0) {
        currentSection.value = entry.target.getAttribute('id');
      }
    })
  },
  {
    rootMargin: '0px 0px -90% 0px'
  }
  );

  document.querySelectorAll('article h2').forEach((section) => {
    observer.observe(section);
  });
});
</script>

<template>
  <main>
    <article>
      <h1>My Article</h1>
      <section v-for="(header, index) in headers" :key="header">
      <h2 :id="index">{{ header }}</h2>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Non architecto delectus eaque ullam saepe eos fugiat ex, corporis accusamus maiores. Aliquid unde, corrupti iure earum nisi laborum modi quae est!
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Non architecto delectus eaque ullam saepe eos fugiat ex, corporis accusamus maiores. Aliquid unde, corrupti iure earum nisi laborum modi quae est!
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Non architecto delectus eaque ullam saepe eos fugiat ex, corporis accusamus maiores. Aliquid unde, corrupti iure earum nisi laborum modi quae est!
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Non architecto delectus eaque ullam saepe eos fugiat ex, corporis accusamus maiores. Aliquid unde, corrupti iure earum nisi laborum modi quae est!
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Non architecto delectus eaque ullam saepe eos fugiat ex, corporis accusamus maiores. Aliquid unde, corrupti iure earum nisi laborum modi quae est!
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Non architecto delectus eaque ullam saepe eos fugiat ex, corporis accusamus maiores. Aliquid unde, corrupti iure earum nisi laborum modi quae est!
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Non architecto delectus eaque ullam saepe eos fugiat ex, corporis accusamus maiores. Aliquid unde, corrupti iure earum nisi laborum modi quae est!
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Non architecto delectus eaque ullam saepe eos fugiat ex, corporis accusamus maiores. Aliquid unde, corrupti iure earum nisi laborum modi quae est!
      </p>
      </section> 
    </article>
    <aside>
      <div>
        <a 
        v-for="(header, index) in headers" 
        :key="header" 
        :href="`#${index}`"
        :class="{ active: index == currentSection }"
        >
          {{ header }}
        </a>
      </div>
    </aside>
  </main>
</template>

<style scoped>
main {
  display: flex;
}

article {
  width: 75%;
  margin-bottom: 500px;
}

aside {
  width: 25%;
}

aside > div {
  position: sticky;
  top: 20px;
  padding-left: 2em;
}

aside > div > a {
  display: block;
  color: #2c3e50;
  text-decoration: none;
  border-left: 1px solid #ccc;
  padding-left: 2em;
}

aside a.active {
  font-weight: bold;
  border-color: black;
}
</style>

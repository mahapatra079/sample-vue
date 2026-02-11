<!-- 
  Vue.js Reference Template - Options API
  Component Types: Root, Global, Local
  Structure: <template> + <script> + <style>
-->

<template>
  <div id="app" class="container">
    <!-- 1. CONDITIONAL RENDERING (v-if, v-else, v-show) -->
    <section class="section">
      <h2>Conditional Rendering</h2>
      <button @click="isShow = !isShow" class="btn">Toggle Button</button>
      <button v-if="isShow" class="btn-primary">Visible</button>
      <p v-else class="text-muted">Hidden (v-else)</p>
    </section>

    <!-- 2. LIST RENDERING (v-for) -->
    <section class="section">
      <h2>List Rendering</h2>
      <ul class="list">
        <li v-for="(item, index) in items" :key="index" class="list-item">
          {{ index + 1 }}. {{ item }}
        </li>
      </ul>
    </section>

    <!-- 3. DATA BINDING (One-way & Two-way) -->
    <section class="section">
      <h2>Data Binding</h2>
      <div class="binding-demo">
        <p><strong>One-way:</strong> {{ message }}</p>
        <p><strong>Two-way (v-model):</strong> {{ text }}</p>
        <input v-model="text" type="text" placeholder="Type here..." class="input" />
      </div>
    </section>

    <!-- 4. EVENT HANDLING (@click, v-on) -->
    <section class="section">
      <h2>Event Handling</h2>
      <button @click="toggleEvent" class="btn">{{ openEvent ? 'Hide' : 'Show' }} Content</button>
      <p v-if="openEvent" class="content">Content is visible!</p>
    </section>

    <!-- 5. LIFECYCLE & METHODS -->
    <section class="section">
      <h2>Lifecycle & Methods</h2>
      <p>Count: <strong>{{ count }}</strong></p>
      <button @click="increment" class="btn-success">Increment</button>
    </section>

    <!-- 6. CHILD COMPONENT -->
    <section class="section">
      <h2>Traffic Light</h2>
      <TrafficLight />
    </section>
  </div>
</template>

<script lang="ts">
import TrafficLight from './components/TrafficLight.vue'
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'App',
  
  components: {
    TrafficLight
  },
  
  data() {
    return {
      isShow: false,
      items: ['Apple', 'Banana', 'Orange'],
      message: 'One-way data binding',
      text: 'Edit me',
      openEvent: true,
      count: 0
    }
  },
  
  methods: {
    increment() {
      this.count += 1;
    },
    toggleEvent() {
      this.openEvent = !this.openEvent;
    }
  },
  
  mounted() {
    console.log('Component Mounted')
  },
  
  watch: {
    count(newVal: number, oldVal: number) {
      console.log(`Count updated: ${oldVal} → ${newVal}`)
    }
  },
  
  unmounted() {
    console.log('Component Unmounted')
  }
})
</script>

<style scoped>
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
  font-family: Arial, sans-serif;
}

.section {
  margin-bottom: 2rem;
  padding: 1.5rem;
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  background: #f9f9f9;
}

h2 {
  margin-top: 0;
  color: #42b983;
  font-size: 1.25rem;
}

.btn {
  padding: 0.5rem 1rem;
  margin-right: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  background: #fff;
  cursor: pointer;
  transition: all 0.3s;
}

.btn:hover {
  background: #f0f0f0;
}

.btn-primary {
  padding: 0.5rem 1rem;
  background: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
}

.btn-success {
  padding: 0.5rem 1rem;
  background: #4caf50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.btn-success:hover {
  background: #45a049;
}

.text-muted {
  color: #666;
  font-style: italic;
}

.list {
  list-style: none;
  padding: 0;
}

.list-item {
  padding: 0.5rem;
  margin: 0.25rem 0;
  background: white;
  border-radius: 4px;
}

.binding-demo {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.input {
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 1rem;
}

.content {
  margin-top: 1rem;
  padding: 1rem;
  background: white;
  border-radius: 4px;
}
</style>
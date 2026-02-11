<template>
  <div class="traffic-light">
    <div class="light" :class="{ active: current === 'red' }"></div>
    <div class="light" :class="{ active: current === 'orange' }"></div>
    <div class="light" :class="{ active: current === 'green' }"></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: 'red',
      timer: null
    };
  },
  mounted() {
    this.timer = setInterval(() => {
      if (this.current === 'red') this.current = 'orange';
      else if (this.current === 'orange') this.current = 'green';
      else this.current = 'red';
    }, 1000);
  },
  beforeUnmount() {
    clearInterval(this.timer);
  }
};
</script>

<style scoped>
.traffic-light {
  display: flex;
  flex-direction: column;
  gap: 10px;
  padding: 20px;
  background: #333;
  border-radius: 10px;
  width: fit-content;
  margin-top: 20px;
}
.light {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background: #555;
  transition: 0.3s;
}
.light.active {
  box-shadow: 0 0 20px currentColor;
}
.light:nth-child(1).active {
  background: red;
  color: red;
}
.light:nth-child(2).active {
  background: orange;
  color: orange;
}
.light:nth-child(3).active {
  background: green;
  color: green;
}
</style>

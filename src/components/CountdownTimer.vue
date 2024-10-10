<template>
    <div class="countdown-timer">
      <h1>{{ timeLeft }}</h1>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        targetDate: new Date('2024-12-01T00:00:00'),
        timeLeft: '',
        interval: null,
      };
    },
    methods: {
      calculateTimeLeft() {
        const now = new Date();
        const diff = this.targetDate - now;
  
        if (diff <= 0) {
          this.timeLeft = 'Время вышло!';
          clearInterval(this.interval);
          return;
        }
  
        const days = Math.floor(diff / (1000 * 60 * 60 * 24));
        const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
        const seconds = Math.floor((diff % (1000 * 60)) / 1000);
  
        this.timeLeft = `${days}d ${hours}h ${minutes}m ${seconds}s`;
      },
    },
    mounted() {
      this.calculateTimeLeft();
      this.interval = setInterval(this.calculateTimeLeft, 1000);
    },
    beforeUnmount() {
      clearInterval(this.interval);
    },
  };
  </script>
  
  <style scoped>
  .countdown-timer {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #e0f7fa;
    color: #00796b;
    font-family: 'Arial', sans-serif;
    text-align: center;
    font-size: 2rem;
  }
  
  h1 {
    margin: 0;
  }
  </style>
  
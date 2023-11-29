<template>
  <div class="home-container">
    <div class="home-content">
      <h1 class="home-title">Welcome to IE Bank</h1>
      <p class="home-description">Your Trusted Banking Partner</p>
      <div class="cta-button">
        <router-link to="/Skull">
          <button class="cta-button-primary">Admin</button>
        </router-link>
        <router-link to="/Accounts">
          <button class="cta-button-secondary">User</button>
        </router-link>
      </div>
    </div>
    <div class="home-image" :style="{ backgroundImage: 'url(/Desktop/background.jpeg)' }">
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Home',
  data() {
    return {
      msg: 'Hi! Welcome to IE Bank, your trusted bank',
      environment: '',
      env_var_file_name: '',
    };
  },
  methods: {
    getSkull() {
      const path = `${process.env.VUE_APP_ROOT_URL}/skull`;
      axios
        .get(path)
        .then((response) => {
          this.msg = response.data;
          this.environment = process.env.NODE_ENV;
          this.env_var_file_name = process.env.VUE_APP_ENV_VAR_FILE_NAME;
        })
        .catch((error) => console.log(error));
    },
  },
  created() {
    this.getSkull();
  },
};
</script>

<style scoped>
.home-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 50px;
  background-color: #f7f7f7;
  min-height: 100vh;
}

.home-content {
  flex: 1;
  padding: 20px;
  max-width: 600px;
  text-align: center;
}

.home-title {
  font-size: 48px;
  margin-bottom: 20px;
  color: #007bff;
}

.home-description {
  font-size: 24px;
  margin-bottom: 30px;
  color: #333;
}

.cta-button {
  text-align: center;
}

.cta-button-primary,
.cta-button-secondary {
  background-color: #007bff;
  color: #fff;
  padding: 15px 30px;
  font-size: 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin: 10px;
  transition: background-color 0.3s ease;
}

.cta-button-primary:hover,
.cta-button-secondary:hover {
  background-color: #0056b3;
}

.home-image {
  flex: 1;
  text-align: center;
}

img {
  max-width: 100%;
  height: auto;
  border-radius: 10px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}
</style>
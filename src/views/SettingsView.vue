<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import { useStore } from "../store";

const store = useStore();
const firstName = ref(store.firstName);
const lastName = ref(store.lastName);
const email = ref(store.email);

const router = useRouter();

function handleSave() {
  store.firstName = firstName.value;
  store.lastName = lastName.value;

  alert("Your changes have been saved!");
  router.push("/movies");
}

function goBackToMovies() {
  router.push("/movies");
}
</script>

<template>
  <div class="blockflix-theme">
    <div class="settings-view">
      <h1>User Settings</h1>
      <form @submit.prevent="handleSave">
        <div class="form-group">
          <label for="firstName">First Name:</label>
          <input v-model="firstName" id="firstName" type="text" placeholder="Enter first name" class="input-field" />
        </div>
        <div class="form-group">
          <label for="lastName">Last Name:</label>
          <input v-model="lastName" id="lastName" type="text" placeholder="Enter last name" class="input-field" />
        </div>
        <div class="form-group">
          <label for="email">Email:</label>
          <input :value="email" id="email" type="email" class="input-field" disabled />
        </div>
        <button type="submit" class="button save">Save Changes</button>
        <button type="button" class="button back" @click="goBackToMovies">Back to Movie List</button>
      </form>
    </div>
  </div>
</template>

<style scoped>
.blockflix-theme {
  background-color: #0d0d0d;
  color: #ffffff;
  font-family: 'Poppins', Arial, sans-serif;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
  box-sizing: border-box;
}

.settings-view {
  max-width: 650px;
  width: 100%;
  background-color: #1c1c1c;
  padding: 40px;
  border-radius: 12px;
  box-shadow: 0 6px 15px rgba(0, 0, 0, 0.9);
  border: 3px solid #ff3d3d;
}

h1 {
  text-align: center;
  color: #ff3d3d;
  margin-bottom: 40px;
  font-weight: 800;
  font-size: 2.8rem;
  letter-spacing: 1.5px;
  text-transform: uppercase;
}

.form-group {
  margin-bottom: 30px;
}

label {
  display: block;
  margin-bottom: 10px;
  font-size: 1.1rem;
  color: #f2f2f2;
  font-weight: 500;
}

.input-field {
  width: 100%;
  padding: 14px;
  border: 2px solid #333;
  border-radius: 6px;
  font-size: 1rem;
  color: #ffffff;
  background-color: #262626;
  transition: all 0.3s ease-in-out;
}

.input-field:focus {
  background-color: #121212;
  border: 2px solid #ff3d3d;
  box-shadow: 0 0 10px rgba(255, 61, 61, 0.8);
}

.input-field:disabled {
  background-color: #3a3a3a;
  color: #bbbbbb;
  cursor: not-allowed;
}

.button.save {
  width: 100%;
  padding: 16px;
  background: linear-gradient(90deg, #e50914, #ff3d3d);
  color: #ffffff;
  border: none;
  border-radius: 6px;
  font-size: 1.2rem;
  font-weight: 700;
  cursor: pointer;
  transition: transform 0.2s ease, box-shadow 0.3s ease, background-color 0.3s ease;
}

.button.save:hover {
  background: linear-gradient(90deg, #ff3d3d, #b20710);
  transform: scale(1.08);
  box-shadow: 0 6px 20px rgba(255, 61, 61, 0.6);
}

.button.save:active {
  transform: scale(0.95);
  background-color: #b20710;
}

.button.back {
  margin-top: 15px;
  width: 100%;
  padding: 16px;
  background: #333333;
  color: #ffffff;
  border: none;
  border-radius: 6px;
  font-size: 1.2rem;
  font-weight: 700;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease, box-shadow 0.3s ease;
}

.button.back:hover {
  background-color: #444444;
  transform: scale(1.05);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5);
}

@media (max-width: 768px) {
  .settings-view {
    padding: 25px;
  }

  h1 {
    font-size: 2.2rem;
    letter-spacing: 1px;
  }

  .button.save,
  .button.back {
    font-size: 1rem;
    padding: 14px;
  }
}
</style>

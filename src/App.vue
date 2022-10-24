<template>
  <div class="custom-shape-divider-bottom-1666612813">
    <svg data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 120" preserveAspectRatio="none">
        <path d="M1200 120L0 16.48 0 0 1200 0 1200 120z" class="shape-fill"></path>
    </svg>
</div>
<SignupForm />
</template>

<script>
import SignupForm from './components/SignupForm.vue'

export default {
  name: 'App',
  components: {
   SignupForm
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  margin: 0;
  background: rgb(26, 34, 71);
}
.custom-shape-divider-bottom-1666612813 {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    overflow: hidden;
    line-height: 0;
    transform: rotate(180deg);
}

.custom-shape-divider-bottom-1666612813 svg {
    position: relative;
    display: block;
    width: calc(126% + 1.3px);
    height: 300px;
}

.custom-shape-divider-bottom-1666612813 .shape-fill {
    fill: #FFFFFF;
}
</style>

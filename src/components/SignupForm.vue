<template>
  <form @submit.prevent="handleSubmit">
    <label>Email:</label>
    <input type="email" required v-model="email">
    <label>Password:</label>
    <input type="password" required v-model="password">
    <div v-if="passwordError" class="error">{{ passwordError }}</div>
    <label>Role:</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

    <label>Skills:</label>
    <input type="text" v-model="tempSkill" @keyup.alt="addSkill">
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)">{{ skill }}</span>
    </div>

    <div class="terms">
      <input type="checkbox" v-model="terms" required>
      <label>Accept terms and conditions</label>
    </div>
    
    <!-- <div>
      <input type="checkbox" value="marcelo" v-model="names">
      <label>Marcelo</label>
    </div>
    <div>
      <input type="checkbox" value="daniel" v-model="names">
      <label>Daniel</label>
    </div>
    <div>
      <input type="checkbox" value="jorge" v-model="names">
      <label>Jorge</label>
    </div> -->

    <div class="submit">
      <button class="glow-on-hover">Create an Account</button>
    </div>

  </form>

  <p>email: {{ email }}</p>
  <p>password: {{ password }}</p>
  <p>Role: {{ role }}</p>
  <p>Terms Accepted {{ terms }}</p>
  <!-- <p>Names: {{ names }}</p> -->
  
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      role: 'developer',
      terms: false,
      // names: []
      tempSkill: '',
      skills: [],
      passwordError: ''
    }
  },
  methods: {
    addSkill(e) {
      if (e.key === ','&& this.tempSkill) {
        if(!this.skills.includes(this.tempSkill)) {
        this.skills.push(this.tempSkill)

        }
        this.tempSkill = ''
      }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter((item) => {
        return skill !== item
      })
    },
    handleSubmit() {
     //validate password
      this.passwordError = this.password.length > 5 ? '' : 'Password must be at least 6 chars long'

      if(!this.passwordError) {
        console.log('email: ', this.email)
        console.log('password: ', this.password)
        console.log('role: ', this.role)
        console.log('skills: ', this.skills)
        console.log('terms accepted: ', this.terms)
      }
    }
  }
}
</script>

<style>

  form {
    max-width: 30%;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
  }
  label {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
  }
  input, select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
  }
  input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
  }
  .pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
  }
  button {
    background: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
    cursor: pointer;
    box-shadow: rgba(0, 0, 0, 0.15) 1.95px 1.95px 2.6px;

  }
  .submit {
    text-align: center;
  }
  button:hover {
    background: #0646a7;
    transition: 300ms;
    box-shadow: rgba(0, 0, 0, 0.15) 1.95px 1.95px 2.6px;
    scale: 1.05;
  }


  .glow-on-hover {
    width: 220px;
    height: 50px;
    border: none;
    outline: none;
    color: #fff;
    background: #0646a7;;
    cursor: pointer;
    position: relative;
    z-index: 0;
    border-radius: 10px;
}

.glow-on-hover:before {
    content: '';
    background: linear-gradient(45deg, #ff0000, #ff7300, #fffb00, #48ff00, #00ffd5, #002bff, #7a00ff, #ff00c8, #ff0000);
    position: absolute;
    top: -2px;
    left:-2px;
    background-size: 400%;
    z-index: -1;
    filter: blur(5px);
    width: calc(100% + 4px);
    height: calc(100% + 4px);
    animation: glowing 20s linear infinite;
    opacity: 0;
    transition: opacity .3s ease-in-out;
    border-radius: 10px;
}

.glow-on-hover:active {
    color: #fff
}

.glow-on-hover:active:after {
    scale: 1.05;
}

.glow-on-hover:hover:before {
    opacity: 1;
}

.glow-on-hover:after {
    z-index: -1;
    content: '';
    position: absolute;
    width: 100%;
    height: 100%;
    background: #0646a7;;
    left: 0;
    top: 0;
    border-radius: 10px;
}

@keyframes glowing {
    0% { background-position: 0 0; }
    50% { background-position: 400% 0; }
    100% { background-position: 0 0; }
}
.error {
  color: #ff0062;
  margin-top: 10px;
  font-size: 0.8em;
  font-weight: bold;
}
</style>
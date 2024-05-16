<template>
  <div id="app" role="main">
    <div class="container">
      <img src="/mgm.png" class="logo" alt="Logo">  
      <h4>{{ title }}</h4>
      <form @submit.prevent="submitForm" aria-labelledby="login-heading">
        <div class="email">
          <label for="usernameEmail" class="form-label">Email</label>
          <input v-model="usernameEmail" type="email" id="usernameEmail" required placeholder="Enter your email address" aria-required="true" aria-describedby="wrong email">
          <div v-if="!isValidEmail" id="email-error" class="error-message">Please enter a valid email address</div>
          
          <div class="password-container">
            <label for="password" class="form-label">Password</label>
            <input v-model="password" :type="isPasswordVisible ? 'text' : 'password'" id="password" required placeholder="Enter your password" aria-required="true">
            <div class="password-icon" @click="togglePassword">
              <img v-if="isPasswordVisible" src="/eye-open@2x.png" alt="eye-open">
              <img v-else src="/eye-closed@2x.png" alt="eye-closed">
            </div>
          </div>
          
          <div @click="forgotPassword" class="Forgot-password">
            <p>Forgot password?</p>
          </div>
        </div>
        <div class="keep-me-signed-in">
          <label>
            <input type="checkbox" v-model="rememberMe">
            Keep me signed in for 30 days
          </label>
        </div>
        <button type="submit">SIGN IN</button>
      </form>
      <p  cursor="pointer">
        Read our Terms of Service
        <svg width="16" height="10" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg" @click="showTermsAlert">
<g clip-path="url(#clip0_1_65)">
<path d="M12.7244 8.78859V13.5159C12.7244 13.9338 12.5584 14.3346 12.2629 14.6301C11.9674 14.9256 11.5666 15.0916 11.1487 15.0916H2.48201C2.06409 15.0916 1.66329 14.9256 1.36778 14.6301C1.07227 14.3346 0.90625 13.9338 0.90625 13.5159V4.8492C0.90625 4.43128 1.07227 4.03048 1.36778 3.73497C1.66329 3.43945 2.06409 3.27344 2.48201 3.27344H7.20928" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M10.3672 0.910156H15.0945V5.63743" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M6.42188 9.57682L15.0885 0.910156" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
</g>
<defs>
<clipPath id="clip0_1_65">
<rect width="16" height="16" fill="white"/>
</clipPath>
</defs>
</svg>

      </p>
      <div class="color-bar"></div>
      <div class="platforms">
        <img src="/bottom.png" alt="Platforms that use Indee">
      </div>
    </div>
  </div>
</template>

<script>
import '/src/styles.css';
export default {
  data() {
    return {
      title: 'Sign in',
      usernameEmail: '',
      password: '',
      rememberMe: false,
      isPasswordVisible: false,
      errorMessage: ''
    }
  },
  methods: {
    submitForm() {
      if (!this.usernameEmail) {
        this.errorMessage = 'Please enter your username or email address.';
        return;
      }
      if (!this.isValidEmail(this.usernameEmail)) {
        this.errorMessage = 'Please enter a valid email address.';
        return;
      }
      if (!this.password) {
        this.errorMessage = 'Please enter your password.';
        return;
      }
      alert('You have successfully logged in.');
      this.errorMessage = ''; // Clear error message after successful login
    },
    forgotPassword() {
      const email = prompt('Please enter your email address to reset your password:', this.usernameEmail);
      if (email) {
        alert('A password reset link has been sent to your email address.');
      }
    },
    togglePassword() {
      this.isPasswordVisible = !this.isPasswordVisible; 
    },
    showTermsAlert() {
      alert('Terms and Conditions:\nBy accessing and using this service, you agree to abide by our terms and conditions.\nAny unauthorized use of this service may result in legal action.\n\nBy clicking "OK", you agree to the terms and conditions.');
    },
    isValidEmail(email) {
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return emailRegex.test(email);
    }
  }
}
</script>

<style scoped>

</style>

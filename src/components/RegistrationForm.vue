<template>
  <div class="wrapper">
    <v-container class="reg-container">
      <v-form class="reg-form form" ref="form" v-model="valid" lazy-validation>
        <h1 class="form-title" color="primary">Sign Up for Free</h1>
        <p class="form-description">Welcome, let’s get to know each other!</p>
        <div class="form-items">
          <div class="form-item">
            <h3 class="subtitle">Full Name</h3>
            <v-text-field class="form-row" v-model="form.username" :rules="usernameRules"
              placeholder="Enter your full name" required outlined />
          </div>
          <div class="form-item">
            <h3 class="subtitle">Email</h3>
            <v-text-field class="form-row" v-model="form.email" :rules="emailRules" placeholder="Enter your email"
              required outlined />
          </div>
          <div class="form-item">
            <h3 class="subtitle">Phone number</h3>
            <v-text-field class="form-row" v-model="form.password" :rules="passwordRules"
              placeholder="Enter your phone number" type="number" required outlined />
          </div>
        </div>
        <v-btn-container class="form-buttons">
          <v-btn variant="outlined" class="block-btn btn-continue" @click="submitForm" :disabled="!valid">
            Continue
          </v-btn>
          <v-btn variant="outlined" class="block-btn btn-account" @click="submitForm" :disabled="!valid">
            I have an account
          </v-btn>
        </v-btn-container>

        <p class="form-bottom">By signing up, you agree to the Terms of Service and Privacy Policy</p>
      </v-form>
    </v-container>
  </div>

</template>

<script>
export default {
  name: 'RegistrationForm',

  data() {
    return {
      valid: false,
      form: {
        username: '',
        email: '',
        password: ''
      },
      usernameRules: [
        v => !!v || 'Username is required',
        v => (v && v.length >= 3) || 'Username must be at least 3 characters'
      ],
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+\..+/.test(v) || 'E-mail must be valid'
      ],
      passwordRules: [
        v => !!v || 'Password is required',
        v => (v && v.length >= 6) || 'Password must be at least 6 characters'
      ]
    }
  },
  methods: {
    submitForm() {
      if (this.$refs.form.validate()) {
        alert('Form submitted!');
      }
    }
  }
}
</script>
<style lang="scss">
@import '../assets/styles.scss';

.wrapper {
  width: 100%;
  height: 100%;
  background: linear-gradient(270deg, #1c1c1f 0%, #111113 100%);
  font-family: $mainFont;
}

.reg-container {
  display: grid;
  place-items: center;
  height: 100vh;

  .reg-form {
    width: 600px;
    height: 660px;
    padding: 52px 32px;
    border-radius: 12px;
    text-align: center;
    font-family: $mainFont;
    color: #f5f5f6;

    .form-title {
      font-weight: 500;
      font-size: 32px;
      letter-spacing: 0.01em;
      line-height: 125%;
      margin-bottom: 2px;
    }

    .form-description {
      font-weight: 400;
      line-height: 150%;
      letter-spacing: 0.01em;
    }
  }
}

.reg-form {
  position: relative;
  border-radius: 12px;
  overflow: hidden;

  &:before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border: 2px solid;
    border-image: linear-gradient(to bottom, rgba(138, 123, 123, 0.5), transparent) 1;
  }
}



.form-item {
  margin-bottom: 20px !important;
  height: 80px !important;
  letter-spacing: 0.01em;
  color: #a2a3a9 !important;

  .subtitle {
    font-family: $mainFont;
    font-weight: 400;
    font-size: 16px;
    line-height: 150%;
    letter-spacing: 0.01em;
    color: #f5f5f6;
    display: flex;
    margin-bottom: 2px;
  }

  .v-text-field {
    border-radius: 8px !important;
    height: 48px !important;

  }
}

.block-btn {
  width: 100%;
  height: 52px !important;
  font-weight: 500;
  font-size: 16px;
  border: 1px solid #62646d !important;
  border-radius: 8px !important;
  text-transform: none !important;
  transition: all 300ms ease;
}

.btn-continue {
  background-color: #fff;
  color: #161b26;

  &:hover {
    background: #676262 !important;
    color: #fff;
  }

}

.btn-account {
  margin-top: 20px;
  background: rgba(39, 39, 41, 0.3) !important;
  color: #fff !important;
}

.form-item:not(:last-child) {
  margin-bottom: 20px !important;
}

.form-item:last-child {
  margin-bottom: 32px !important;
}

.form-bottom {
  margin-top: 48px !important;
  font-size: 12px;
  color: #f5f5f6;
}

.form-row .v-input__slot input::placeholder {
  color: #a2a3a9;
  font-size: 14px;
}

.v-input__slot {
  border: 1px solid #333741;
}
</style>
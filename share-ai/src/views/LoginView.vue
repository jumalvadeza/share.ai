<template>
  <div>
    <!-- SVG Background -->
    <svg class="login__blob" viewBox="0 0 566 840" xmlns="http://www.w3.org/2000/svg">
      <mask id="mask0" mask-type="alpha">
        <path
          d="M342.407 73.6315C388.53 56.4007 394.378 17.3643 391.538 0H566V840H0C14.5385 834.991 100.266 804.436 77.2046 707.263C49.6393 591.11 115.306 518.927 176.468 488.873C363.385 397.026 156.98 302.824 167.945 179.32C173.46 117.209 284.755 95.1699 342.407 73.6315Z"
        />
      </mask>
      <g mask="url(#mask0)">
        <path
          d="M342.407 73.6315C388.53 56.4007 394.378 17.3643 391.538 0H566V840H0C14.5385 834.991 100.266 804.436 77.2046 707.263C49.6393 591.11 115.306 518.927 176.468 488.873C363.385 397.026 156.98 302.824 167.945 179.32C173.46 117.209 284.755 95.1699 342.407 73.6315Z"
        />
        <image class="login__img" href="/assets/img/bg-img.jpg" />
      </g>
    </svg>

    <!-- Login/Register Section -->
    <div class="login container grid" :class="{'active': isRegisterFormVisible}" id="loginAccessRegister">
      <!-- Login Form -->
      <div class="login__access">
        <h1 class="login__title">Log in.</h1>
        <div class="login__area">
          <form action="" class="login__form">
            <div class="login__content grid">
              <div class="login__box">
                <input type="email" id="email" v-model="emailLogin" required placeholder=" " class="login__input" />
                <label for="email" class="login__label">Email</label>
                <i class="ri-mail-fill login__icon"></i>
              </div>

              <div class="login__box">
                <input
                  :type="passwordLoginType"
                  id="password"
                  v-model="passwordLogin"
                  required
                  placeholder=" "
                  class="login__input"
                />
                <label for="password" class="login__label">Senha</label>
                <i
                  class="ri-eye-off-fill login__icon login__password"
                  :class="{'ri-eye-fill': passwordLoginType === 'text', 'ri-eye-off-fill': passwordLoginType === 'password'}"
                  @click="togglePasswordVisibility('login')"
                ></i>
              </div>
            </div>
            <a href="#" class="login__forgot">Esqueceu a senha?</a>
            <button type="submit" class="login__button">Login</button>
          </form>
          <div class="login__social">
            <p class="login__social-title">Ou log com</p>
            <div class="login__social-links">
              <a href="#" class="login__social-link"><img src="/assets/img/icon-google.svg" alt="Google" class="login__social-img" /></a>
              <a href="#" class="login__social-link"><img src="/assets/img/icon-facebook.svg" alt="Facebook" class="login__social-img" /></a>
              <a href="#" class="login__social-link"><img src="/assets/img/icon-apple.svg" alt="Apple" class="login__social-img" /></a>
            </div>
          </div>
          <p class="login__switch">
            Não tem uma conta?
            <button @click="toggleFormVisibility">Criar conta</button>
          </p>
        </div>
      </div>

      <!-- Register Form -->
      <div class="login__register">
        <h1 class="login__title">Criar nova conta.</h1>
        <div class="login__area">
          <form action="" class="login__form">
            <div class="login__content grid">
              <div class="login__group grid">
                <div class="login__box">
                  <input type="text" id="names" v-model="firstName" required placeholder=" " class="login__input" />
                  <label for="names" class="login__label">Nome</label>
                  <i class="ri-id-card-fill login__icon"></i>
                </div>
                <div class="login__box">
                  <input type="text" id="surnames" v-model="lastName" required placeholder=" " class="login__input" />
                  <label for="surnames" class="login__label">Sobrenome</label>
                  <i class="ri-id-card-fill login__icon"></i>
                </div>
              </div>

              <div class="login__box">
                <input type="email" id="emailCreate" v-model="emailCreate" required placeholder=" " class="login__input" />
                <label for="emailCreate" class="login__label">Email</label>
                <i class="ri-mail-fill login__icon"></i>
              </div>

              <div class="login__box">
                <input
                  :type="passwordCreateType"
                  id="passwordCreate"
                  v-model="passwordCreate"
                  required
                  placeholder=" "
                  class="login__input"
                />
                <label for="passwordCreate" class="login__label">Senha</label>
                <i
                  class="ri-eye-off-fill login__icon login__password"
                  :class="{'ri-eye-fill': passwordCreateType === 'text', 'ri-eye-off-fill': passwordCreateType === 'password'}"
                  @click="togglePasswordVisibility('create')"
                ></i>
              </div>
            </div>
            <button type="submit" class="login__button">Criar conta</button>
          </form>
          <p class="login__switch">
            Já tem conta?
            <button @click="toggleFormVisibility">Log In</button>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'LoginView',
  data() {
    return {
      emailLogin: '',
      passwordLogin: '',
      passwordLoginType: 'password',
      emailCreate: '',
      passwordCreate: '',
      passwordCreateType: 'password',
      firstName: '',
      lastName: '',
      isRegisterFormVisible: false,
    };
  },
  methods: {
    togglePasswordVisibility(formType) {
      if (formType === 'login') {
        this.passwordLoginType = this.passwordLoginType === 'password' ? 'text' : 'password';
      } else {
        this.passwordCreateType = this.passwordCreateType === 'password' ? 'text' : 'password';
      }
    },
    toggleFormVisibility() {
      this.isRegisterFormVisible = !this.isRegisterFormVisible;
    },
  },
  mounted() {
    // Adiciona o link para o Remixicon
    const link = document.createElement('link');
    link.rel = 'stylesheet';
    link.href = 'https://cdnjs.cloudflare.com/ajax/libs/remixicon/4.2.0/remixicon.css';
    document.head.appendChild(link);
  },
};
</script>

<style scoped>
@import '/public/assets/css/styleslogin.css';
</style>


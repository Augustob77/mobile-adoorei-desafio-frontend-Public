<template>
  <div class="login-container">
    <img src="../assets/logo.png" alt="">
    <b-card
      class="d-flex justify-content-center align-items-center"
      title="Entre na sua conta"
    >
      <b-card-text>
        Para acessar sua conta informe seu e-mail e senha
      </b-card-text>

      <b-row>
        <b-col>
          <b-form>
            <b-form-group label="E-mail">
              <b-form-input
                id="email"
                type="email"
                class="my-4"
                placeholder="Seu e-mail"
                size="lg"
                v-model="form.email"
              />
            </b-form-group>

            <b-form-group label="Senha">
              <b-form-input
                id="password"
                type="password"
                class="my-1"
                placeholder="Sua senha"
                size="lg"
                v-model="form.password"
              />

              <div align="right">
                <a> Esqueci minha senha </a>
              </div>
            </b-form-group>

            <b-button
              class="my-3 border-0"
              type="button"
              block
              @click="login"
            >
              FAZER LOGIN
            </b-button>
          </b-form>
        </b-col>
      </b-row>
    </b-card>

    <b-row class="my-4">
      <b-col>
        <div align="center">
          <span> Ainda não tem conta? </span>
          <a class="register-text" href="/planes"> Cadastre-se </a>
        </div>
      </b-col>
    </b-row>
  </div>  
</template>
<script>

export default {
  data() {
    return {
      form: {
        email: '',
        password: ''
      }
    }
  },
  
  methods: {
    login() {
      // Implementado apenas na versão desktop
    },
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  text-decoration: none;
}

.login-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #f5f5f5 !important;
}

img {
  width: 250px;
  padding: 2.5rem;
}

a {
  font-size: 1.13rem !important;
  color: #737373 !important;
}

span {
  font-size: 1.3rem !important;
}

.card-body {
  width: 100% !important;
  padding: 1.8rem !important;
}

.card-title {
  font-size: 1.75rem;
  font-weight: bold;
}

.card-text {
  font-size: 1.2rem;
  margin-top: -0.25rem;
  color: rgb(68, 68, 68);
}

.register-text {
  font-size: 1.3rem !important;
  color: #F30C6A !important; 
}

input {
  border-radius: 0.3rem !important;
  height: 5rem !important;
  font-size: 1rem !important;
  border-color: #a3a3a3 !important;
}

button {
  border-radius: 0.3rem !important;
  border: none;
  height: 5rem;
  width: 100%;
  font-size: 1.2rem !important;
  background-color: #F30C6A !important; 
  color: white;
}

</style>
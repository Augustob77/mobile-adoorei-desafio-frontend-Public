<template>
  <div class="card-container">
    <b-row>
      <b-col cols="12" align="center">
        <img src="../assets/logo.png" alt="">
        <p class="text-one"> Você está muito próximo de mudar a forma de </p>
        <p class="text-two"> hospedar seu site </p>
      </b-col>
      <b-col
        cols="12"
        class="my-5"
      >
        <card-plane
          :plane-item="planeItem"
          :is-edition="true"
        />
      </b-col>
      <b-col cols=12>
        <b-card
          title="Dados Pessoais" 
          class="my-5"
        >
          <b-card-text>
            Informe seus dados pessoais para acesso à sua conta
          </b-card-text>

          <b-form>
            <b-form-group label="Nome completo">
              <b-form-input
                id="name"
                type="text"
                class="my-4"
                placeholder="informe seu nome completo"
                size="lg"
                v-model="form.name"
              />
            </b-form-group>

            <b-form-group label="Celular">
              <b-form-input
                id="cell"
                type="text"
                class="my-4"
                placeholder="(99) 99999-0000"
                size="lg"
                v-model="form.cell"
                v-mask="'(##) #####-####'"
              />
            </b-form-group>

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
                size="lg"
                v-model="form.password"
              />

              <div class="my-2">
                <span> No mínimo 8 caracteres</span>
              </div>
            </b-form-group>

            <b-form-group label="Confirme sua senha">
              <b-form-input
                id="passwordConfirm"
                type="password"
                class="my-2"
                size="lg"
                v-model="form.passwordConfirm"
              />
            </b-form-group>

            <hr class="invoice-spacing">
            <b-card-text class="title-text">
              Dados do seu site
            </b-card-text>

            <b-form-group label="Nome do seu site">
              <b-form-input
                id="siteName"
                type="text"
                placeholder="Meu site"
                size="lg"
                v-model="form.siteName"
              />

              <div class="my-2">
                <span> Exatamente igual o título do seu site</span>
              </div>
            </b-form-group>
            <hr class="invoice-spacing">

            <b-form-checkbox
                id="checkbox"
                name="checkbox"
                class="checkbox-item"
                v-model="form.checkbox"
                :value="true"
                :unchecked-value="false"
            >
            <p class="text-check"> Ao concluir com seu cadastro você concorda com nossos termos de uso e políticas de privacidade. </p>
            </b-form-checkbox>

            <b-button
                class="my-3 border-0"
                type="button"
                block
                @click="register()"
            >
                CRIAR CONTA
            </b-button>
          </b-form>
        </b-card>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import CardPlane from '@/components/CardPlane.vue'
import planesList from '@/mixins/planesList'
import axios from 'axios'

export default {
    components: {
      CardPlane,
    },

    mixins: [planesList],

    data() {
      return {
        planeItem: null,
        form: {
          name: '',
          cell: '',
          email: '',
          password: '',
          passwordConfirm: '',
          siteName: '',
          checkbox: false
        }
      }
    },
  
    mounted() {
      const { id } = this.$router.currentRoute.params
      this.planeItem = planesList.find(item => item.id === id)

      this.planeItem ? this.planeItem : this.planeItem = planesList[0]
    },

    methods: {
      register() {
         // Implementado apenas na versão desktop
      }
    }
}
</script>

<style scoped>
.card-container {
  display: flex;
  height: 100%;
  justify-content: center;
  padding: 9rem;
  margin-top: -5rem !important;
  background-color: #f5f5f5 !important;
}

img {
  width: 200px;
}

span {
  font-size: 0.9rem !important;
  color: #737373 !important;
}

button {
  border-radius: 0.3rem !important;
  border: none;
  height: 4rem !important;
  width: 100%;
  font-size: 1.2rem !important;
  background-color: #F30C6A !important; 
  color: white;
}
.text-one {
  margin-top: 2rem !important;
  font-weight: bold !important;
  font-size: 1.7rem !important;
}
.text-two {
  color: #F30C6A !important;
  text-decoration: underline;
  font-size: 1.7rem !important;
  font-weight: bold !important;
  margin-top: -1.5rem !important;
}
.text-three {
  font-weight: normal;
  font-size: 1rem !important;
}
.title-text{
  font-weight: bold;
  font-size: 1.8rem !important;
  color: rgb(29, 29, 29) !important;
}
.card-body {
  padding: 2rem !important;
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

input {
  border-radius: 0.3rem !important;
  height: 4rem !important;
  font-size: 1rem !important;
  border-color: #a3a3a3 !important;
}
.text-check {
  margin-left: 1.2rem !important;
  margin-top: -1.65rem;
}

</style>
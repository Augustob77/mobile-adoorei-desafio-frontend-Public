<template>
  <div>
    <div class="header">
      <img src="../assets/logo.png" alt="">
      <img src="../assets/avatar.png" class="avatar" align="right" alt="">
    </div>
    <div class="card-container">
        <b-row>
        <b-col cols="12">
            <h1> {{ 'Olá' + ' ' + userName + ','}} </h1>
            <p> Seja bem vindo a sua conta de hospedagem</p>
            
            <div align="center">
              <iframe src="https://www.youtube.com/embed/-5PlzQXQymk" frameborder="0" width="900" height="600"></iframe>
            </div>
            
            <p> Caso tenha alguma dúvida, visite nossa central de ajuda</p>
        </b-col>
        </b-row>
    </div>
  </div>
</template>

<script>
export default {
    data() {
      return {
        userName: '',
      }
    },

    mounted() {
      const { userName } = this.$router.currentRoute.params
      userName ? this.userName = userName : this.userName = 'Usuário'
    }
}
</script>

<style scoped>
.card-container {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  padding: 19rem;
  background-color: #f5f5f5 !important;
}
.header {
  background-color: #f5f5f5 !important;
  padding: 2rem;
  margin-top: -12rem;
}

img {
  width: 150px;
  margin-top: 12rem !important;
}
.avatar {
  width: 50px;
  margin-top: 12rem !important;
}

h1 {
  font-size: 1.8rem;
  font-weight: bold;
  margin-top: 4rem !important;
}
</style>
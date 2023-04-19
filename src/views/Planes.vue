<template>
  <div class="card-container">
    <b-row>
      <b-col cols="12" align="center">
        <img src="../assets/logo.png" alt="">
        <p class="text-one"> Você está muito próximo de mudar a forma de </p>
        <p class="text-two"> hospedar seu site </p>
        <p class="text-three"> Escolha o seu plano </p>
      </b-col>
      <b-col
        v-for="planeItem in planes"
        :key="planeItem.id"
        class="my-5"
      >
        <card-plane
          :plane-item="planeItem"
          :is-edition="false"
        />
      </b-col>
    </b-row> 
  </div>
</template>
  
<script>
import CardPlane from '@/components/CardPlane.vue'
import planesList from '@/mixins/planesList'

export default {
  components: {
    CardPlane,
  },
  
  mixins: [planesList],

  data() {
    return {
      planes: planesList,
    }
  },
};
</script>

<style scoped>
.card-container {
  display: flex;
  height: 100%;
  justify-content: center;
  padding: 6rem;
  margin-top: -3rem !important;
  background-color: #f5f5f5 !important;
}

img {
  width: 200px;
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


</style>
  
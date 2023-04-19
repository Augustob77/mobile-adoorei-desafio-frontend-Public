<template>
  <div>
    <b-card
      class="d-flex justify-content-center align-items-center border-0"
      :title="planeItem.name"
      :header="moreUsed()"
    >
      <b-card-text class="price-text" align="center">
        {{ planeItem.price  }}
      </b-card-text>

      <b-card-text class="payment-desc-text" align="center">
        {{ planeItem.monthlyPaymentDescription  }}
      </b-card-text>
      
      <hr class="invoice-spacing">
      <b-card-text class="desc-text" align="center">
        {{ planeItem.description  }}
      </b-card-text>
      <hr class="invoice-spacing">

      <b-button
        v-if="!isEdition"
        class="my-3 border-0"
        type="button"
        block
        @click="selectPlane(planeItem)"
      >
        ESCOLHER ESSE PLANO
      </b-button>

      <b-card-text class="server-desc-text" v-if="!isEdition">
        {{ planeItem.serverDescription  }}
      </b-card-text>

      <div v-if="!isEdition">
        <div 
          v-for="(item, index) in planeItem.listOne"
          :key="index"
          align="left"
        >
          <b-card-text class="v-for-item-text">
            {{ '✔' + item }}
          </b-card-text>
        </div>
      </div>

      <b-card-text class="generic-bold-text" v-if="!isEdition">
        {{ planeItem.support  }}
      </b-card-text>

      <b-card-text class="generic-bold-text" v-if="!isEdition">
        {{ planeItem.apps  }}
      </b-card-text>

      <div v-if="!isEdition">
        <div 
          v-for="(item, index) in planeItem.listTwo"
          :key="index"
          align="left"
        >
          <b-card-text class="v-for-item-text">
            {{ '✔' + item }}
          </b-card-text>
        </div>
      </div>

      <b-card-text
        v-if="planeItem.migrationFree && !isEdition"
        class="generic-bold-text"
        align="left"
      >
        {{ planeItem.migrationFree }}
      </b-card-text>

      <b-card-text
        v-if="planeItem.migrationFreeText && !isEdition"
        align="left"
      >
        {{ '✔' + planeItem.migrationFreeText }}
      </b-card-text>

      <b-card-text class="generic-bold-text" v-if="!isEdition">
        {{ planeItem.youHave  }}
      </b-card-text>

      <div v-if="!isEdition">
        <div 
          v-for="(item, index) in planeItem.listTree"
          :key="index"
          align="left"
        >
          <b-card-text class="v-for-item-text">
            {{ '✔' + item }}
          </b-card-text>
        </div>
      </div>

      <b-button
        v-if="isEdition"
        class="my-3 btn-switch"
        type="button"
        block
        @click="switchPlane()"
      >
        Trocar plano
      </b-button>
    </b-card>
  </div>
</template>

<script>
export default {
  props: {
    planeItem: {
      type: Object,
      default: () => {},
    },
    isEdition: {
      type: Boolean,
      default: false,
    }
  },

  data() {
    return {

    }
  },

  mounted() {
    this.moreUsed()
  },

  methods: {
    selectPlane(planeItem) {
      this.$router.push({
        name: 'register',
        params: { id: planeItem.id },
      })
    },
    switchPlane() {
      this.$router.push({
        name: 'planes',
      })
    },
    moreUsed() {
      if (this.planeItem.id === '002' && !this.isEdition) {
        return 'MAIS USADO'
      } else if (this.isEdition) {
        return 'PLANO ESCOLHIDO'
      }
    }
  }
}
</script>

<style scoped>
.card-body {
  width: 21rem !important;
  padding: 3rem !important;
}

.card-title {
  font-size: 1.7rem;
  font-weight: bold;
  margin-left: 1.6rem;
  color: #545454;
}
.card-header {
  background-color: #10C300;
  color: white;
  border-radius: 0.7rem;
  margin-top: -2.55rem;
}
/* .card-header {
  background-color: #000000;
  color: white;
  border-radius: 0.7rem;
  margin-top: -2.55rem;
} */
.price-text {
  color: #F30C6A !important;
  font-size: 1.8rem;
  font-weight: bold;
  margin-top: 1rem;
}

.payment-desc-text {
  color: #7c7c7c !important;
  font-size: 1rem;
}

.desc-text {
  color: #545454 !important;
  font-size: 1.26rem;
}

.server-desc-text {
  color: #545454;
  margin-top: 0.6rem;
  font-weight: bold;
  font-size: 1.1rem;
  text-decoration: underline
}

.generic-bold-text {
  color: #545454;
  margin-top: 1rem;
  font-weight: bold;
  font-size: 1.1rem;
}

.v-for-item-text {
  margin-top: 0.3rem;
}

button {
  border-radius: 0.3rem !important;
  border: none;
  height: 4rem !important;
  width: 100%;
  font-size: 1.2rem !important;
  background-color: #F30C6A; 
  color: white;
}

.btn-switch {
  border-radius: 0.3rem !important;
  height: 4rem !important;
  width: 100%;
  background-color: black; 
  font-size: 1.2rem !important;
}
</style>
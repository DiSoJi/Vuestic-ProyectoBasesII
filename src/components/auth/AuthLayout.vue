<template>
<div class="auth-layout row align-content--center">
  <div class="flex xs12 pa-3 flex-center">
    <router-link class="py-5 flex-center" to="/">
      <va-icon-vuestic />
    </router-link>
  </div>

  <div class="flex xs12 pa-3">
    <div class="d-flex justify--center">
      <va-card class="auth-layout__card">
        <va-tabs
          v-model="tabIndex"
          center
        >
          <va-tab>{{ $t('auth.login') }}</va-tab>
          <va-tab>{{ $t('auth.createNewAccount') }}</va-tab>
        </va-tabs>

        <va-separator/>

        <div class="pa-3">
          <router-view/>
        </div>
      </va-card>
    </div>
  </div>
</div>
</template>

<script>
import VaIconVuestic from 'vuestic-ui/src/components/vuestic-components/va-icon/va-iconset/VaIconVuestic'

const tabs = [
  'login',
  'signup',
]

export default {
  name: 'AuthLayout',
  components: { VaIconVuestic },
  data () {
    return {
      selectedTabIndex: 0,
      tabTitles: ['login', 'createNewAccount'], // Nombre identificador para los dos tabs.
    }
  },
  computed: {
    tabIndex: {
      set (tabIndex) {
        this.$router.push({ name: tabs[tabIndex] }) // Esto setea el valor del tab seleccionado. 1 o 0 en este caso
      },
      get () {
        return tabs.indexOf(this.$route.name)
      },
    },
  },
}
</script>

<style lang="scss">
.auth-layout {
  min-height: 100vh;
  background-image: linear-gradient(to right, #0e4ac4, #002c85);

  &__card {
    width: 100%;
    max-width: 600px; //Cambia el tamaño de la carta de loggeo en auth/login
  }

  &__options {
    @include media-breakpoint-down(xs) {
      flex-direction: column;
    }
  }
}
</style>

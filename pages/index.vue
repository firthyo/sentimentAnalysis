<template>
  <div>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6">
        <div class="text-center">
          <p class="display-1">Sentiment Analytic</p>
        </div>

      </v-col>
    </v-row>

    <v-row>
      <v-col cols="6" class="d-flex justify-center">
        <v-row>
          <v-col cols="12">
            <template>
              <v-file-input
                label="File input"
                outlined
                dense
                v-model="fileInput"
              ></v-file-input>
              <div>
                <div class="text-center">
                  <v-progress-circular
                    v-if="loading"
                    :active="loading"
                    :indeterminate="loading"
                    :size="70"
                    :width="7"
                    color="purple"
                  ></v-progress-circular>
                </div>
              </div>
            </template>
            <div>
              <v-scale-transition>
                <div
                  v-if="!loading"
                  class="text-center"
                >
                  <v-btn
                    color="primary"
                    @click="loading = true"
                  >
                    submit
                  </v-btn>
                </div>
              </v-scale-transition>
            </div>
          </v-col>
        </v-row>

      </v-col>
      <v-col cols="6" class="d-flex justify-center">
        <div class="text-center">
          <h3 class="mb-2">OUTPUT</h3>
          <img src="~/static/happy.png" alt="happy" width="30%" v-if="!isshowsentiment">
          <img src="~/static/happy.png" alt="happy" width="30%" v-if="isshowsentiment">
          <div class="text-center pt-5">
            <v-btn @click="refresh">Refresh</v-btn>
          </div>
        </div>
      </v-col>
    </v-row>
  </div>


</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  components: {
    Logo,
    VuetifyLogo
  },
  data: () => ({
    loading: false,
    fileInput: null,
    isshowsentiment:false
  }),
  methods: {
    submit() {
      loading: true
      this.fileInput = null
      console.log('js')
    },
    refresh(){
      this.isshowsentiment = false
    }

  },
  watch: {
    loading(val) {
      if (!val) return
      setTimeout(() => (this.loading = false), 3000)
      setTimeout(() => (this.fileInput = null), 3000)
    },
  },
}
</script>

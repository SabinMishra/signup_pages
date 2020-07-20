<template>
  <div>
    <v-content>
      <v-container class="fill-height" fluid>
        <v-row align="center" justify="center">
          <v-col cols="12" sm="8" md="8">
            <v-card class="elevation-12">
              <v-row>
                <v-col cols="12" md="6">
                  <v-card-text class="mt-12">
                    <h1
                      class="text-center display-w font-weight-light text--accent-3"
                    >
                      Sign Up
                    </h1>

                    <!-- Another code copied here-->

                    <v-form lazy-validation>
                      <v-text-field
                        label="Email"
                        class="mt-11 font-weight-black inputs"
                        :rules="emailRules"
                        v-model.lazy="email"
                        prepend-icon="email"
                      ></v-text-field>

                      <v-text-field
                        :append-icon="show ? 'mdi-eye' : 'mdi-eye-off'"
                        :type="show ? 'text' : 'password'"
                        name="passwordInput"
                        label="Password"
                        class="mt-10 "
                        v-model.lazy="p1"
                        prepend-icon="fas fa-lock "
                        @click:append="show = !show"
                      >
                      </v-text-field>

                      <v-text-field
                        :append-icon="show ? 'mdi-eye' : 'mdi-eye-off'"
                        :type="show ? 'text' : 'password'"
                        name="passwordInput"
                        label="Confirm Password"
                        :rules="[emailRules, passwordCompare]"
                        v-model.lazy="p2"
                        prepend-icon="fas fa-lock "
                        @click:append="show = !show"
                        class="mt-10 "
                      >
                      </v-text-field>

                      <div class="text-center">
                        <v-btn
                          text
                          class="mt-6 "
                          @click="submit"
                          >Submit</v-btn
                        >
                      </div>
                    </v-form>
                  </v-card-text>
                </v-col>

                <v-col cols="12" md="6" sm="6" class="d-sm-none d-md-flex">
                  <v-img src="../assets/background1.jpg" class="my-n3">
                    <div class="mt-10">
                      <svg
                      v-show="shows"
                      class="checkmark"
                      xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 52 52"
                    >
                      <circle
                        class="checkmark__circle"
                        cx="26"
                        cy="26"
                        r="25"
                        fill="none"
                      />
                      <path
                        class="checkmark__check"
                        fill="none"
                        d="M14.1 27.2l7.1 7.2 16.7-16.8"
                      />
                    </svg>
                    </div>
                    
                  </v-img>
                </v-col>
              </v-row>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </div>
</template>

<script>
export default {
  data() {
    return {
      shows: false,
      email: "",
      p1: "",
      p2: "",
      emailRules: [
        (v) => !!v || "Email is reqiured",
        (v) => /.+@.+\..+/.test(v) || "Email must be valid",
      ],
      show:false
    };
  },
  methods: {
    submit() {
      this.shows = true;
    },
  },
  watch: {
    //  if(this.email.length>1){
    //    this.status = 'ok'
    //  }
  },
  computed: {
    passwordCompare() {
      return () => this.p1 === this.p2;
    },
  },
};
</script>

<style scoped>
.checkmark__circle {
  stroke-dasharray: 166;
  stroke-dashoffset: 166;
  stroke-width: 2;
  stroke-miterlimit: 10;
  stroke: #7ac142;
  fill: none;
  animation: stroke 0.6s cubic-bezier(0.65, 0, 0.45, 1) forwards;
}

.checkmark {
  width: 56px;
  height: 56px;
  border-radius: 50%;
  display: block;
  stroke-width: 2;
  stroke: #fff;
  stroke-miterlimit: 10;
  margin: 10% auto;
  box-shadow: inset 0px 0px 0px #7ac142;
  animation: fill 0.4s ease-in-out 0.4s forwards,
    scale 0.3s ease-in-out 0.9s both;
}

.checkmark__check {
  transform-origin: 50% 50%;
  stroke-dasharray: 48;
  stroke-dashoffset: 48;
  animation: stroke 0.3s cubic-bezier(0.65, 0, 0.45, 1) 0.8s forwards;
}

@keyframes stroke {
  100% {
    stroke-dashoffset: 0;
  }
}
@keyframes scale {
  0%,
  100% {
    transform: none;
  }
  50% {
    transform: scale3d(1.1, 1.1, 1);
  }
}
@keyframes fill {
  100% {
    box-shadow: inset 0px 0px 0px 30px #7ac142;
  }
}
</style>

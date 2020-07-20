<template>
  <div>

    <v-content>
      
      <v-container class="fill-height" fluid>
       
        <v-row align="center" justify="center" >
          <v-col cols="12" md="4" sm="6">
            
            <v-card class="elevation-12 ">
            <v-img src="../assets/background1.jpg" class="height">
              

              <v-card-text>
                <h1 class="text-center mt-6">Sign Up</h1>
                <v-form>
                  <v-text-field label="Email" class="mt-11 font-weight-black inputs" :rules="emailRules"  prepend-icon="email"></v-text-field>
                
          
                      
          <v-text-field
          :append-icon="show? 'mdi-eye' : 'mdi-eye-off'"
          :type="show? 'text' : 'password'"
          name="passwordInput"
          label="Password"
          class="mt-10 font-weight-black "
          v-model="p1"
          prepend-icon="fas fa-lock "
          @click:append="show = !show"
          >

          </v-text-field>

          <v-text-field
          :append-icon="show? 'mdi-eye' : 'mdi-eye-off'"
          :type="show? 'text' : 'password'"
          name="passwordInput"
          label="Confirm Password"
          :rules="[emailRules,passwordCompare]"
          v-model="p2"
          prepend-icon="fas fa-lock "
          @click:append="show = !show"
          class="mt-10 font-weight-black"
          >

          </v-text-field>

          <div class="text-center">
            <v-btn text class="mt-6 font-weight-black" >Submit</v-btn>
          </div>
                </v-form>
              </v-card-text>
           </v-img>
            </v-card>
            
            
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </div>
</template>

<script>
  export default {
   data(){
     return{
       show:false,
       p1:'',
       p2:'',
       
        emailRules:[
           v=>!!v || 'Email is reqiured',
           v=>/.+@.+\..+/.test(v) || 'Email must be valid'
         ]
         }   
        },
        computed:{
          passwordCompare(){
            return ()=>(this.p1 === this.p2)
          }
        }
   } 
  
</script>

<style  scoped>
.back{
opacity:0.5
}
.height{
  height:600px;
}

.inputs{
  color: red;
}



</style>
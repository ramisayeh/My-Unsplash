<template>
  <div class="topnav">
  <img class="header__logo" src="../assets/logo.png" />
  
    
 <v-dialog
    v-model="dialog"
    persistent
    max-width="600px"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          v-bind="attrs"
          v-on="on"
          class="btn"
        >
          add a photo 
        </v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span class="headline">Add a new photo</span>
        </v-card-title>
        <v-card-text>
          
          <v-container>
            <v-row>
              
              <v-col cols="12">
                <form @submit.prevent="savePhoto" >
                <v-text-field
                  label="Label"
                  required
                  v-model="label"
                >
                
                </v-text-field>
                </form>
              </v-col>
              <v-col cols="12">
                <v-text-field
                  label="Photo URL"
                  type="text"
                  required
                  v-model="url"
                ></v-text-field>
              </v-col>
            </v-row>
          </v-container>
          <small>Please enter a valid image URL.</small>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            text
          >
            Cancel
          </v-btn>
          <v-btn
          type="submit"
            text
          
          >
            Submit
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
</div>
  
</template>

<script>


import db from '../firebaseInit'
  export default {
     
          navbarOptions: {
            name: 'Mainnavbar',
            elementId: "main-navbar",
            isUsingVueRouter: true,
            mobileBreakpoint: 99
            },
     data() {
        return {
          label: null,
          url: null,
           dialog: false, 
            imagees: [],
            search: ''
                }
        
            },
            methods: {
              savePhoto(){
                db.collection('imagees').add(
                   console.log(this.label),
                  {
                  label : this.label,
                  url: this.url
                })
              }},
              computed: {
                filteredImages: function () {
                  return this.imagees.filter((image) => {
                    console.log(this.data.search)
                    return image.label.match(this.search)
                  })
                }
              }
             
            
            
            
  }
</script>

<style lang="css">
.theme--light.v-btn.v-btn--has-bg {
   background-color: #3db46d;
}
  .topnav {

  background-color: #ffffff;
}
@media screen and (min-width: 768px){
.header__logo {
    width: 140px;
    margin-right: 14px;
}}
.header__logo {
  float: left;
  height: 30px;
  width: 110px;
  margin-top: 12px;
}

.btn {
float: right;
background-color: #3db46d;
border-color: #3db46d;
border-style: solid;
box-shadow:
#000000 0px 1px 6px 0px;
text-align: center;
font-size: 14px;
line-height: 19px;
border: none;
padding: 14px 22px;
border-radius: 24px;
font-weight: 700;
transition: all .25s;
height: 50px;

}

.btn:hover {
background-color:#37a06d;
color: rgb(255, 255, 255);
}


  
</style>
<template>
  <div class="topnav">
  <img class="header__logo" src="../assets/logo.png" />
  <div class="search-container">
    <form >
      <input type="text" placeholder="Search by name" name="search">
    </form>
  </div>
 <v-dialog
      v-model="dialog"
      persistent
      max-width="600px"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          v-bind="attrs"
          v-on="on"
        >
          add a photo 
        </v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span class="headline">User Profile</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Legal first name*"
                  required
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Legal middle name"
                  hint="example of helper text only on focus"
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
                md="4"
              >
                <v-text-field
                  label="Legal last name*"
                  hint="example of persistent helper text"
                  persistent-hint
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field
                  label="Email*"
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field
                  label="Password*"
                  type="password"
                  required
                ></v-text-field>
              </v-col>
              <v-col
                cols="12"
                sm="6"
              >
                <v-select
                  :items="['0-17', '18-29', '30-54', '54+']"
                  label="Age*"
                  required
                ></v-select>
              </v-col>
              <v-col
                cols="12"
                sm="6"
              >
                <v-autocomplete
                  :items="['Skiing', 'Ice hockey', 'Soccer', 'Basketball', 'Hockey', 'Reading', 'Writing', 'Coding', 'Basejump']"
                  label="Interests"
                  multiple
                ></v-autocomplete>
              </v-col>
            </v-row>
          </v-container>
          <small>*indicates required field</small>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="blue darken-1"
            text
            @click="dialog = false"
          >
            Close
          </v-btn>
          <v-btn
            color="blue darken-1"
            text
            @click="dialog = false"
          >
            Save
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
</div>
  
</template>

<script>



  export default {
    
      data() {
        return {
          dialog: false,
          navbarOptions: {
            name: 'Mainnavbar',
            elementId: "main-navbar",
            isUsingVueRouter: true,
            mobileBreakpoint: 99,
           
                    }
                }
            }
  }
</script>

<style lang="css">
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

.topnav .v-btn {
  float: right;
background-color:
#3db46d;

border-color:
#3db46d;
border-style:
solid;
box-shadow:
#000000 0px 1px 6px 0px;
color:
#ffffff;
text-align:
center;
    font-size: 14px;
    line-height: 19px;
    border: none;
    padding: 14px 22px;
    border-radius: 24px;
    font-weight: 700;
    transition: all .25s;
    height: 50px;

}

.topnav .v-btn:hover {
  background-color:#37a06d;
  color: rgb(255, 255, 255);
}

.topnav .search-container {
  float: left;
}

.topnav input[type=text] {
  padding: 6px;
  margin-top: 8px;
  font-size: 17px;

}



.topnav .search-container button:hover {
  background: #ccc;
}

@media screen and (max-width: 600px) {
  .topnav .search-container {
    float: right;
  }
  .topnav .search-container {
    float: right ;
  }

   .topnav input[type=text], .topnav .search-container button {
    float: right ;
    text-align: left;
    width: 100%;
    margin: 0;
    padding: 14px;

  }
  
}
.topnav input[type=text] {
    border: 1px solid rgb(10, 10, 10);  
    border-radius: 24px;
  }
  
</style>
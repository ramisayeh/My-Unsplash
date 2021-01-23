<template>

  <div class="hello">
     <div class="search-container">
    <form >
      <input  id='call' v-model="search" type="text" placeholder="Search by name"  >
    </form>
  </div>
    <div class="row">
      <div class="column">
        <div
          v-for="image in filteredImages" v-bind:key="image"
          class="imgs">
       
          <img  v-bind:src='image.url'/>
          <div class="overlay">
             <v-dialog
              v-model="dialog"
              persistent
              max-width="600px">
      <template v-slot:activator="{ on, attrs }">
               <button class="dbutton"  v-bind="attrs"
          v-on="on"  >Delete</button>
          </template>
      <v-card>
        <v-card-title>
          <span class="headline">photo delete verification</span>
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
            </v-row>
          </v-container>
          <small>Please enter the images label .</small>
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
            <label class='label'>{{image.label}}</label>
            </div>
        </div>
      </div>
     <div class="column">
        <div
          v-for="image in list2" v-bind:key="image"
          class="imgs">
       
          <img  v-bind:src='image.url'  />
          <div class="overlay">
             <v-dialog
            v-model="dialog"
            persistent
            max-width="600px"
    >
      <template v-slot:activator="{ on, attrs }">
               <button class='dbutton' v-bind="attrs"
          v-on="on"  >Delete</button>
          </template>
      <v-card>
        <v-card-title>
          <span class="headline">photo delete verification</span>
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
            </v-row>
          </v-container>
          <small>Please enter the images label .</small>
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
            <label class='label'>{{image.label}}</label>
            </div>
        </div>
      </div>
      <div class="column">
        <div
          v-for="image in list1" v-bind:key="image"
          class="imgs">
       
          <img  v-bind:src='image.url'  />
          <div class="overlay">
             <v-dialog
            v-model="dialog"
            persistent
            max-width="600px"
    >
      <template v-slot:activator="{ on, attrs }">
               <button  v-bind="attrs"
          v-on="on" class='dbutton' >Delete</button>
          </template>
      <v-card>
        <v-card-title>
          <span class="headline">photo delete verification</span>
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
            </v-row>
          </v-container>
          <small>Please enter the images label .</small>
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
            <label class='label'>{{image.label}}</label>
            </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import db from '../firebaseInit';
import search from './nav'

export default {
  name: "Photos",

  data() {
    return {
           label: null,
          url: null,
           dialog: false, 
        imagees: [],
        list1: [],
        list2: [],
        search: ''
        

    }
    
    },
    created () {
        db.collection("list1").get()
        .then(querySnapshot => {
     querySnapshot.forEach(doc => {
                console.log( doc.data())
                const data ={
                    'id': doc.id,
                    'label': doc.data().label,
                    'url': doc.data().url
                }
                this.list1.push(data)
            })
        }),
        db.collection("imagees").get()
        .then(querySnapshot => {
     querySnapshot.forEach(doc => {
                console.log( doc.data())
                const data ={
                    'id': doc.id,
                    'label': doc.data().label,
                    'url': doc.data().url
                }
                this.imagees.push(data)
            })
        }),
         db.collection("list2").get()
        .then(querySnapshot => {
     querySnapshot.forEach(doc => {
                console.log( doc.data())
                const data ={
                    'id': doc.id,
                    'label': doc.data().label,
                    'url': doc.data().url
                }
                this.list2.push(data)
            })
        })
        
    },
    
    computed: {
                filteredImages: function () {
                  return this.imagees.filter((image) => {
                    return image.label.match(search)
                  })
                }
              },
    methods: {
                deletephoto (){
                if(confirm('Are you sure')){
                    db.collection('imagees').get()
                    .then(querySnapshot => {
                        querySnapshot.forEach(doc => {
                            doc.ref.delete();
                        })
                    })
                }
                }
            }

    
    }
</script>

<style lang='css'>

.imgs:hover .overlay {
  bottom: 0;
  height: 100%;
}
.overlay {
  position: absolute;
  bottom: 100%;
  left: 0;
  right: 0;
  background-color: #0b0d0e7c;
  overflow: hidden;
  width: 100%;
  height:0;
  transition: .5s ease;
  border-radius: 24px;
   margin-top: 8px;

}
form{
display:flex;
justify-content:center;
}
.row {
  display: flex;
  flex-wrap: wrap;
  padding: 0 4px;
  margin:14px;
  justify-content: center;
}
.label {
  color : #ffff;
   position: absolute;
  -webkit-transform: translate(50%, 50%);
  -ms-transform: translate(50%, 50%);
  transform: translate(50%, 50%);
  
}
.column {
  flex: 30%;
  max-width: 30%;
  padding: 0 4px;
  justify-content:
space-between;
}
.column img {
  margin-top: 8px;
  vertical-align: middle;
  width: 100%;
  border-radius: 24px;
}
.imgs {
  position: relative;
}

.dbutton {
  border: 1px solid #d43b3b;
  border-radius: 12px;
  font-style: normal;
  font-weight: 400;
  font-size: 20px;
  line-height: 15px;
  color:  #d43b3b;
  text-transform: lowercase;
  background-color: #f5f5f500;
  position: absolute;
  cursor: pointer;
  top: 20px;
  right: 16px;
  font-size: 18px;
  padding: 7px;
  position: absolute;
  z-index: 2;
   }
p {
  font-style: normal;
  font-weight: 500;
  font-size: 18px;
  line-height: 22px;
  color: #ffffff;
  position: relative;
  margin-top: -40px;
  padding-left: 20px;
  z-index: 3;
  opacity: 0;
}
.topnav .search-container {
  float: left;
}

.topnav input[type=text] {
  padding: 6px;
  margin-top: 8px;
  font-size: 17px;

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
#call{
    border: 1px solid rgb(10, 10, 10);  
    border-radius: 24px;
  }

</style>
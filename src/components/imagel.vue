<template>
  <div class="hello">
    <div class="row">
      <div class="column">
        <div
          v-for="image in images[0]" v-bind:key="image"
          class="imgs">
          <img  v-bind:src='image'  />
          <div class="overlay">
            <button @click="deletes(item)">Delete</button>
            <label class='label'>label</label>
            </div>
        </div>
      </div>
      <div class="column">
        <div
          v-for="image in t" v-bind:key="image"
          class="imgs"
        >
          <img  v-bind:src='image'  />
         <div class="overlay">
            <button @click="deletes(item)">Delete</button>
            <label class='label'>label</label>
            </div>
        </div>
      </div>
      <div class="column">
        <div
          v-for="image in g" v-bind:key="image"
          class="imgs"
        >
          <img  v-bind:src='image'  />
         <div class="overlay">
            <button @click="deletes(item)">Delete</button>
            <label class='label'>label</label>
            </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Photos",
  methods: {
    deletes(item) {
      console.log(item);
      this.$emit('delete:item', item)
    },
  },
  data() {
    return { images :[[ 'https://media.senscritique.com/media/000017453094/150_200/Sarra_Hannachi.jpg',
        'https://i.pinimg.com/474x/8d/35/07/8d35077e43cff3cafe7843926c9567d8.jpg'],            
        ],
        t:['https://www.jeuneafrique.com/medias/2012/03/13/012032012175333000000P.jpg',
              'https://www.baya.tn/wp-content/uploads/2014/02/mis1.png'],
             g: ['https://i.pinimg.com/originals/c5/1d/6b/c51d6b511edd41a278667b951baedcad.jpg',
                  'https://i0.wp.com/arjazia.com/wp-content/uploads/2020/12/t-shirt-tunisie-femme-made-in-tunisia.jpg?fit=800%2C800&ssl=1&resize=400%2C400',
                    'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR8TPOLm2ayfQIuXBM9g51x72SCO0ul5NbDcA&usqp=CAU']
                     }}
};
</script>

<style scoped>
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
.row {
  display: flex;
  flex-wrap: wrap;
  padding: 0 4px;
  justify-content: center;
}
.label {
  color : #ffff;
   position: absolute;
  -webkit-transform: translate(50%, 50%);
  -ms-transform: translate(50%, 50%);
  transform: translate(50%, 2500%);
  
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

button {
  border: 1px solid #eb5757;
  border-radius: 12px;
  background: none;
  font-style: normal;
  font-weight: 400;
  font-size: 10px;
  line-height: 15px;
  text-transform: lowercase;
  color: #eb5757;
  position: absolute;
  cursor: pointer;
  top: 20px;
  right: 16px;
  font-size: 18px;
  opacity: 0;
  padding: 7px;
   position: absolute;
  -webkit-transform: translate(-50%, -50%);
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  text-align: center;
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

</style>
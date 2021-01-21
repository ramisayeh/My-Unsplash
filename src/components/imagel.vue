<template>
  <div class="hello">
    <div class="row">
      <div class="column">
        <div
          v-for="image in images" v-bind:key="image"
          class="imgs"
        >
          <img  v-bind:src='image'  />
          <button @click="deletes(item)">Delete</button>
        </div>
      </div>
      <div class="column">
        <div
          v-for="image in images" v-bind:key="image"
          class="imgs"
        >
          <img  v-bind:src='image'  />
          <button @click="deletes(item)">Delete</button>
        </div>
      </div>
      <div class="column">
        <div
          v-for="image in images" v-bind:key="image"
          class="imgs"
        >
          <img  v-bind:src='image'  />
          <button @click="deletes(item)">Delete</button>
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
    return { images :[
        'https://media.senscritique.com/media/000017453094/150_200/Sarra_Hannachi.jpg',
        'https://i.pinimg.com/474x/8d/35/07/8d35077e43cff3cafe7843926c9567d8.jpg',
            'https://www.jeuneafrique.com/medias/2012/03/13/012032012175333000000P.jpg',
              'https://www.baya.tn/wp-content/uploads/2014/02/mis1.png',
                'https://i.pinimg.com/originals/c5/1d/6b/c51d6b511edd41a278667b951baedcad.jpg',
                  'https://i0.wp.com/arjazia.com/wp-content/uploads/2020/12/t-shirt-tunisie-femme-made-in-tunisia.jpg?fit=800%2C800&ssl=1&resize=400%2C400',
                    'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR8TPOLm2ayfQIuXBM9g51x72SCO0ul5NbDcA&usqp=CAU'
       
                    
        ] }}
};
</script>

<style scoped>
.row {
  display: flex;
  flex-wrap: wrap;
  padding: 0 4px;
  justify-content: center;
}
.column {
  flex: 30%;
  max-width: 30%;
  padding: 0 4px;
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
  z-index: 3;
  position: absolute;
  cursor: pointer;
  top: 20px;
  right: 16px;
  font-size: 18px;
  opacity: 0;
  padding: 7px;
}
button:hover {
  opacity: 1;
  border: 1px solid #cc4b4b;
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
img:hover {
  filter: linear-gradient(rgba(0, 0, 0, 0.6),rgba(0,0,0,0.4));
}
img:hover ~ button {
  opacity: 1;
}
img:hover ~ p {
  opacity: 1;
}
</style>
<script>
  import Skeleton from './components/Skeleton.vue'
  import Found from './components/Found.vue'

  export default {
    components: {
      Skeleton,
      Found,
    },
    data() {
      return {
        listItems: [],
        count: 1,
        category: '',
        categoryman: '', 
        loading: true
      }
    },
    methods: {
      async increment(){
        if(this.count >= 20){
          this.count = 1
        }else{
          this.count += 1
        }
        this.getData()
      },
      async getData() {
        this.loading = true
        this.category = false
        fetch(`https://fakestoreapi.com/products/${this.count}`)
        .then(res => res.json())
        .then((data) => {
          if(data.category == `women's clothing` || data.category == `men's clothing`){
            this.category = true
            this.listItems = data

            if(data.category == `men's clothing`){
              this.categoryman = true
            }else{
              this.categoryman = false
            }
          }
        })
        .catch((err) => {
          console.log(err)
        })
        .finally(() => {
          this.loading = false
        })

      }
    },
    mounted() {
      this.getData()
    }
  }
</script>

<template>
  <!-- loading -->
  <div v-if="loading">
    <Skeleton/>
  </div>

  <!-- content -->
  <div v-else>
    <!-- category available -->
    <div v-if="category">
        <div class="container">
          <div v-bind:class="`${categoryman? 'rectangle' : 'rectangle-woman'}`">
            <img class="aksesoris" src="./assets/bg-aksesoris.svg"/>
          </div>
          <div class="card">
            <div class="areaImg">
              <img class="img" :src="listItems.image"/>
            </div>
            <div>
              <div>
                <h1 v-bind:class="`${categoryman? 'title' : 'title-woman'}`">{{ listItems.title }}</h1>
              </div>
              <div class="areaRating">
                <p>{{ listItems.category }}</p>
                <div class="containerRate">
                  {{ listItems.rating?.rate }}/5
                  <div class="ratingcontainer">
                    <div v-if="categoryman" v-for="item in 5" v-bind:class="`${listItems?.rating?.rate <= item? 'rating border': 'rating full'}`"></div>
                    <div v-else v-for="item in 5" v-bind:class="`${listItems?.rating?.rate <= item? 'rating border-woman': 'rating full-woman'}`"></div>
                  </div>
                </div>
              </div>
              <div class="body">
                <p>{{ listItems.description }}</p>
              </div>
              <div>
                <h3 v-bind:class="`${categoryman? 'price' : 'price-woman'}`">${{ listItems.price }}</h3>
                <div class="areabtn">
                  <button v-bind:class="`${categoryman? 'btn' : 'btn-woman'}`">Buy Now</button>
                  <button @click="increment()" v-bind:class="`${categoryman? 'btnNext' : 'btnNext-woman'}`">Next Product</button>
                </div>
              </div>
            </div>
          </div>
        </div>
    </div>

    <!-- category not available -->
    <div v-else>
      <div class="container">
          <Found @sendCount="increment"/>
        </div>
    </div>
  </div>
</template>

<style scoped>
  .areaImg{
    padding: 0 80px;
    display: flex;
    align-items: center;
  }

  .areaRating{
    display: flex;
    justify-content: space-between;
    margin: 20px 0;
  }

  .ratingcontainer{
    display: flex;
    align-items: center;
    margin-left: 16px;
  }

  .containerRate{
    display: flex;
  }

  .areabtn{
    display: flex;
    justify-content: space-between;
  }

  .btn{
    background-color: var(--btn-man);
    color: var(--background-default);
    padding: 10px 0px;
    cursor: pointer;
    width: 48%;
  }
  
  .btnNext{
    border:2px solid var(--btn-man);
    outline: none;
    background-color: transparent;
    color: var(--btn-man);
    width: 48%;
    padding: 10px 0px;
    cursor: pointer;
  }

  .btn-woman{
    background-color: var(--btn-woman);
    color: var(--background-default);
    padding: 10px 0px;
    cursor: pointer;
    width: 48%;
  }
  
  .btnNext-woman{
    border:2px solid var(--btn-woman);
    outline: none;
    background-color: transparent;
    color: var(--btn-woman);
    width: 48%;
    padding: 10px 0px;
    cursor: pointer;
  }

  .body{
    border-top: 2px solid rgba(0, 0, 0, 0.2);
    border-bottom: 2px solid rgba(0, 0, 0, 0.2);
    padding: 20px 0 40px 0;
  }

  .price{
    padding: 20px 0;
    color: var(--btn-man);
  }

  .price-woman{
    padding: 20px 0;
    color: var(--btn-woman);
  }

  .title{
    color: var(--btn-man);
  }

  .title-woman{
    color: var(--btn-woman);
  }

  .aksesoris{
    width: 100%;
  }
  
</style>

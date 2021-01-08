<template>
  <Carousel v-model="value1" loop>

    <CarouselItem v-for="row in rows" :key="'slider_'+row.id">
      <div class="rel">

        <template v-if="row.link">
          <a :href="row.link">
            <img :src="$images(row.image , 'org')"  style="width: 100%;max-height: 500px">
            <h3 class="sliderTitle">{{row.name}}</h3>

          </a>
        </template>
        <template v-else>
          <img :src="$images(row.image , 'org')"  style="width: 100%;max-height: 500px">
          <h3 class="sliderTitle">{{row.name}}</h3>

        </template>

      </div>

    </CarouselItem>

  </Carousel>
</template>
<script>
export default {
  data () {
    return {
      rows:[],
      loading:true,
      value1:0
    }
  },
  mounted() {
    this.fetchData()
  },
  methods: {
    fetchData() {
      this.loading=true;
      let url = process.env.MODULE_URL+'sliders';

      this.$axios.$get(url).then((res) => {
        this.rows = res.payload.data;
        this.loading = false;
      })


    }
  }
}
</script>
<style>
.rel{
  position: relative;
}
.sliderTitle{
  position: absolute;
  z-index: 10;
  top: 40%;
  left: 10%;
  font-size: 50px;
  color: #d7dde4;
  background:dimgray;
  opacity: .8;
  padding: 5px;
  text-transform: uppercase;

}
</style>

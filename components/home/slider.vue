<template>
  <Carousel v-model="value1" loop>
    <CarouselItem v-for="row in rows" :key="'slider_'+row.id">
      <img :src="$images(row.image , 'org')"  style="width: 100%;max-height: 500px">
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

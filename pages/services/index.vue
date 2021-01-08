<template>
  <div class="container">
    <div>

      <h1>Services({{total}})</h1>


      <loading v-if="loading"/>
      <Row v-else>
        <Col  span="8" v-for="row in rows">

          <Card style="margin: 28px" >
            <p slot="title"><nuxtLink :to="'/services/'+row.id">{{row.name}} </nuxtLink></p>
            <nuxtLink :to="'/services/'+row.id">
            <img :src="$images(row.image)" >
            </nuxtLink>
          </Card>
        </Col>
      </Row>
      <template v-if = 'currentPage !== lastPage'>
        <Button type="primary" :loading="loading" @click="fetchData">
          <span v-if="!loading">Click me!</span>
          <span v-else>Loading...</span>
        </Button>
      </template>


    </div>
  </div>
</template>

<script>
import loading from "@/components/loading";
export default {
  head(){
    return{
      title : 'Services'
    }
  },
  comments:{
    loading
  },
  data() {
    return {
      rows: [],
      loading:false,
      lastPage:'',
      nextUrl:'',
      currentPage:'',
      total:0,
    }
  },
  mounted() {
    this.fetchData()
  },
  methods: {
    fetchData() {
      this.loading=true;
      let url = process.env.MODULE_URL+'services';
      if (this.nextUrl !== '' && this.nextUrl != null){
        url = this.nextUrl
      }
      this.$axios.$get(url).then((res) => {
        if (this.rows.length > 0){
          this.rows = [...this.rows , ...res.payload.data]
        }else {
          this.rows = res.payload.data;
        }

        this.loading = false;
        this.nextUrl = res.payload.next_page_url;
        this.lastPage = res.payload.last_page;
        this.currentPage = res.payload.current_page;
        this.total = res.payload.total;

      })


    }
  }


}

</script>



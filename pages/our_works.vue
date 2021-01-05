<template>
  <div class="container">
    <div>

      <h1>Clients({{total}})</h1>


      <loading v-if="loading"/>
      <Row v-else>

          <List item-layout="vertical">
            <ListItem v-for="row in rows" :key="row.id">
              <ListItemMeta  :title="row.name" />
              {{ row.description }}
              <template slot="action">
                <li v-if="row.link">
                 <nuxtLink :to="row.link">
                   <Icon type="md-link" />
                   Visit
                 </nuxtLink>
                </li>
                <li>
                  <Icon type="md-calendar" />
                  {{row.created_at}}
                </li>

              </template>
              <template slot="extra">
                <img :src="$images(row.image)"></template>
            </ListItem>
          </List>

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
      let url = process.env.MODULE_URL+'our_works';
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



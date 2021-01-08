
<template>
  <div class="layout">
    <Layout>
      <Header>
        <Menu mode="horizontal" theme="dark" active-name="1">
          <div class="layout-logo">
            <img src="logo.png"  width="100" style="margin-bottom: 20px">
          </div>
          <div class="layout-nav" >
            <MenuItem name="1">
              <nuxtLink to="/" class="font_color">
                <Icon type="ios-navigate"></Icon>
                Home
              </nuxtLink>
            </MenuItem>
            <MenuItem name="2">
              <nuxtLink to="/services" class="font_color">
                <Icon type="ios-navigate"></Icon>
                Services
              </nuxtLink>
            </MenuItem>
            <MenuItem name="3">
              <nuxtLink to="/teams" class="font_color">
                <Icon type="ios-navigate"></Icon>
                Teams
              </nuxtLink>
            </MenuItem>
            <MenuItem name="4">
              <nuxtLink to="/our_works" class="font_color">
                <Icon type="ios-navigate"></Icon>
               Our Works
              </nuxtLink>
            </MenuItem>
            <MenuItem name="5">
              <nuxtLink to="/clients" class="font_color">
                <Icon type="ios-navigate"></Icon>
                Clients
              </nuxtLink>
            </MenuItem>
            <MenuItem name="5">
              <nuxtLink to="/pages/5" class="font_color">
                <Icon type="ios-navigate"></Icon>
                About Us
              </nuxtLink>
            </MenuItem>
            <MenuItem name="5">
              <nuxtLink to="/pages/6" class="font_color">
                <Icon type="ios-navigate"></Icon>
                Privacy
              </nuxtLink>
            </MenuItem>
            <MenuItem name="5">
              <nuxtLink to="/pages/7" class="font_color">
                <Icon type="ios-navigate"></Icon>
                Terms And Conditions
              </nuxtLink>
            </MenuItem>
          </div>
        </Menu>
      </Header>
      <Content style="padding: 0 50px ; margin-top: 20px">

        <Card>
          <div style="min-height: 200px;">
           <nuxt />
          </div>
        </Card>
      </Content>
      <Footer class="layout-footer-center">2011-2016 &copy; TalkingData</Footer>
    </Layout>
  </div>
</template>
<script>
export default {
  head(){
    return{
      title : 'Home'
    }
  },
}
</script>
<style scoped>
.layout{
  background: #f5f7f9;
  position: relative;
  overflow: hidden;
}
.layout-logo{
  width: 100px;
  height: 30px;
  background: #5b6270;
  border-radius: 3px;
  float: left;
  position: relative;
  top: 15px;
  left: 20px;
}
.layout-nav{

  margin: 0 auto;
  margin-right: 20px;
}
.layout-footer-center{
  text-align: center;
}
.font_color{
  color: #eeeeee;
}
</style>

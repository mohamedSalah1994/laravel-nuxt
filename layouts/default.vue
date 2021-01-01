
<template>
  <div class="layout">
    <Layout>
      <Header>
        <Menu mode="horizontal" theme="dark" active-name="1">
          <div class="layout-logo"></div>
          <div class="layout-nav">
            <MenuItem name="1">
              <nuxtLink to="/">
                <Icon type="ios-navigate"></Icon>
                Home
              </nuxtLink>
            </MenuItem>
            <MenuItem name="2">
              <nuxtLink to="/services">
                <Icon type="ios-navigate"></Icon>
                Services
              </nuxtLink>
            </MenuItem>
            <MenuItem name="3">
              <nuxtLink to="/teams">
                <Icon type="ios-navigate"></Icon>
                Teams
              </nuxtLink>
            </MenuItem>
            <MenuItem name="4">
              <nuxtLink to="/our_works">
                <Icon type="ios-navigate"></Icon>
               Our Works
              </nuxtLink>
            </MenuItem>
            <MenuItem name="5">
              <nuxtLink to="/clients">
                <Icon type="ios-navigate"></Icon>
                Clients
              </nuxtLink>
            </MenuItem>
            <MenuItem name="5">
              <nuxtLink to="/pages">
                <Icon type="ios-navigate"></Icon>
                About Us
              </nuxtLink>
            </MenuItem>
            <MenuItem name="5">
              <nuxtLink to="/pages">
                <Icon type="ios-navigate"></Icon>
                Privacy
              </nuxtLink>
            </MenuItem>
            <MenuItem name="5">
              <nuxtLink to="/pages">
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

}
</script>
<style scoped>
.layout{
  border: 1px solid #d7dde4;
  background: #f5f7f9;
  position: relative;
  border-radius: 4px;
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
</style>

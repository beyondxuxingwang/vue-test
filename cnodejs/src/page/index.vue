<template>
<div>
 <Header></Header>
  <div>index page 列表</div>
  <div class="list">
    <ul>
      <li v-for="(i,value) in list">
        <time v-text="i.create_at"></time>&nbsp;&nbsp;&nbsp;&nbsp;
        <router-link :to="'/content/'+i.id">
          {{i.title}}
        </router-link>
      </li>
    </ul>
  </div>
  <Footer></Footer>
</div>

</template>

<script>
import Header from "../components/header.vue";
import Footer from "../components/footer.vue";
export default {
  components: {
    Header,
    Footer
  },
  data() {
    return {
      list: []
    };
  },
  created() {
    this.getData();
  },
  methods: {
    getData() {
      this.$api.get("topics", null, res => {
        console.log(res);
        this.list = res.data;
      });
    }
  }
};
</script>
<style>
  li{
    list-style: none;
    height: 50px;
    line-height: 50px;
    border-bottom: 1px solid #ccc;
  }
</style>

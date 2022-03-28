<template>
  <div>
    <!-- <GreetingUser id="greeting" name="suncheol" /> -->
    <!-- <ProductList :products="products" /> -->
    <h2>Hello Event Component</h2>
    <h3>{{ username }}</h3>
    <!-- Event -->
    <button @click="displayDetail = true">show detail</button>
    <DetailView
      v-if="displayDetail"
      @closeDetail="close"
      @sendData="showData"
    />
    <!-- Provide && Inject -->
    <CompLevel1 />
    <!-- multiComponent -->
    <div>
      <button @click="activeTab = 'Menu1'">Menu1</button>
      <button @click="activeTab = 'Menu2'">Menu2</button>
      <button @click="activeTab = 'Menu3'">Menu3</button>
    </div>
    <keep-alive>
      <component :is="activeTab"></component>
    </keep-alive>
  </div>
  <!-- Slot -->
  <CardView>
    <template v-slot:header>
      <h1>h1</h1>
    </template>
    <template v-slot:body>
      <h2>h2</h2>
    </template>
    <template v-slot:footer>
      <h3>h3</h3>
    </template>
  </CardView>
  <TodoList />
  <ParentComp />
  <ProductStatus />
  <FeeStatus />
  <SavingStatus />
  <TestComponent />
</template>

<script>
import TestComponent from "./components/composition/TestComponent.vue";
import SavingStatus from "./components/mixins/SavingStatus.vue";
import FeeStatus from "./components/mixins/FeeStatus.vue";
import ProductStatus from "./components/mixins/ProductStatus.vue";
import ParentComp from "./components/lifecycle/ParentComp.vue";
import TodoList from "./components/http/TodoList.vue";
import CardView from "./components/slot/CardView.vue";
import Menu1 from "./components/tabitems/Menu1.vue";
import Menu2 from "./components/tabitems/Menu2.vue";
import Menu3 from "./components/tabitems/Menu3.vue";
import CompLevel1 from "./components/provide-inject/CompLevel1.vue";
import DetailView from "./components/DetailView.vue";
// import GreetingUser from "./components/GreetingUser.vue";
// import ProductList from "./components/ProductList.vue";
export default {
  name: "App",
  data() {
    return {
      activeTab: "Menu1",
      username: "sunchoel",
      // products: [
      //   { id: 0, name: "TV", price: 500000, company: "LG" },
      //   { id: 1, name: "전자렌지", price: 400000, company: "삼성" },
      //   { id: 2, name: "가스오븐", price: 300000, company: "한화" },
      //   { id: 3, name: "냉장고", price: 200000, company: "대우" },
      //   { id: 4, name: "에어컨", price: 100000, company: "해태" },
      // ],
      displayDetail: false,
    };
  },
  provide() {
    return {
      name: this.username,
    };
  },
  components: {
    // ProductList,
    // GreetingUser,
    DetailView,
    CompLevel1,
    Menu1,
    Menu2,
    Menu3,
    CardView,
    TodoList,
    ParentComp,
    ProductStatus,
    FeeStatus,
    SavingStatus,
    TestComponent,
  },
  computed: {},
  watch: {},
  methods: {
    close() {
      this.displayDetail = false;
    },
    showData(data) {
      this.username = `${data}`;
    },
  },
  directives: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

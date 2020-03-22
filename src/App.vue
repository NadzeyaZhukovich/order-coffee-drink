<template>
  <div id="app">
    <Header></Header>
    <section class="row">
      <CoffeeList/>
      <Basket/>
    </section>
    <Footer></Footer>
  </div>
</template>

<script>
  import CoffeeList from '@/components/CoffeeList';
  import Basket from '@/components/Basket';
  import Header from '@/components/Header';
  import Footer from '@/components/Footer';

  export default {
  name: 'App',
  components: {
    CoffeeList,
    Basket,
    Header,
    Footer,
  },

  data() {
    return {
      coffeeDescription: [
        {name: 'latte', price: 4, icon: 'link to icon'},
        {name: 'cappuccino', price: 4, icon: 'link to icon'},
        {name: 'coffee', price: 4, icon: 'link to icon'},
        {name: 'mokachino', price: 4, icon: 'link to icon'},
      ]
    }
  }
}
</script>

<style>
  .row {
    width: 1200px;
    margin: 70px auto 0;
    display: flex;
    padding-top: 10px;
  }
</style>

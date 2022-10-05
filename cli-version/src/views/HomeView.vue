<template>
  <div id="app" class="app">
    <h1>{{ disneyName }}</h1>
    <p class="description">
      Bienvenue sur le {{ disneyName }}<br />Livraison GRATUITE dès 60,00€
      d’achats | Livraison standard 4,90€ | Livraison point relais 3,90€ .
    </p>

    <!-- boucle pour lui dire d'afficher chaque items dans le
			tab disneyEars -->
    <section class="disney">
      <h2>Disney ears</h2>
      <DisneyItem
        v-for="item in disneyEars"
        @add-items-to-cart = "addToShoppingCart"
        :name="item.name"
        :image="item.image"
        :quantity="item.quantity"
        :inStock="item.inStock"
        :key="item.name"
      />
    </section>

    <aside class="shopping-cart">
      <h2>Panier d'achat : {{ shoppingCart }} articles</h2>
    </aside>

    <footer class="footer">
      <p>{{ copyright }}</p>
    </footer>
  </div>
</template>

<script>
import DisneyItem from "../components/DisneyItem.vue";

export default {
  name: "App",
  components: {
    DisneyItem,
  },
  //mes données
  data() {
    return {
      disneyName: "Shop Disney",
      shoppingCart: 0,
      //ici tab disneyEars dans ma data avec sa clé + sa valeur correspondante
      disneyEars: [
        {
          name: "Disney ears doré",
          image: {
            source: "/images/disneyears1.jpeg",
            alt: "Disney ears Gold",
          },
          inStock: true,
          quantity: 1,
        },
        {
          name: "disney ears Encanto",
          image: {
            source: "/images/disneyears2.jpg",
            alt: "Disney ears Encanto",
          },
          inStock: true,
          quantity: 1,
        },
        {
          name: "Disney ears Minnie",
          image: {
            source: "/images/disneyears3.jpg",
            alt: "Disney ears Minnie",
          },
          inStock: false,
          quantity: 1,
        },
      ],
    };
  },
  //propriété computed pour afficher l'année
  computed: {
    copyright() {
      const currentYear = new Date().getFullYear();

      return `Copyright ${this.disneyName} ${currentYear}`;
    },
  },
  ////méthode qui permet de rajouter des produits dans le panier
  methods: {
    addToShoppingCart(amount) {
      this.shoppingCart += amount;
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.description {
  max-width: 960px;
  font-size: 1.2rem;
  margin: 0 auto;
}

.footer {
  text-align: center;
  font-style: italic;
}

.disney {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.shopping-cart {
  position: absolute;
  right: 30px;
  top: 0;
}
</style>

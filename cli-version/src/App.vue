<template>
  <div id="app" class="app">
    <h1>{{ disneyName }}</h1>
    <p class="description">
      Bienvenue sur le {{ disneyName }}<br/>Livraison GRATUITE dès 60,00€ d’achats |
      Livraison standard 4,90€ | Livraison point relais 3,90€ .
    </p>

    <!-- boucle pour lui dire d'afficher chaque items dans le
			tab disneyEars -->
    <section class="disney">
      <h2>Disney ears</h2>
      <DisneyItem
        v-for="item in disneyEars"
        :addToShoppingCart="addToShoppingCart"
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

    <h2>Contactez nous</h2>
    <p>Adresse : {{ address }}</p>
    <p>Téléphone : {{ phone }}</p>
    <p>Email : {{ email }}</p>
    <p>Horaires :</p>
    <ul>
      <li>L-V: 06:00 à 16:00</li>
      <li>Samedi: 07:00 à 14:00</li>
      <li>Dimanche: 07:00 à 12:00</li>
    </ul>
    <footer class="footer">
      <p>{{ copyright }}</p>
    </footer>
  </div>
</template>

<script>
import DisneyItem from "./components/DisneyItem";

export default {
  name: "App",
  components: {
    DisneyItem,
  },
  //mes données
  data() {
    return {
      address: "Disneyland Paris, Marne-la-vallée, France",
      email: "contact@disneyshop.com",
      phone: "01 88 88 88 88",
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
</style>

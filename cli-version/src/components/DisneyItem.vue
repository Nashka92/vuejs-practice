<script>
	//ici j'exporte mon component que je vais appeler DisneyItem
	// avec ses propriétés
export default {
	name: "DisneyItem",
	//faire en typescript
	props: ["addToShoppingCart", "image", "inStock", "name", "quantity"]
}
</script>

<!-- Le template sera l'affichage de mon component -->
<template>
	<div class="disney-item">
		<img class="disney-item__image" :src="image.source" :alt="image.alt" />
		<div>
			<h3>{{ name }}</h3>
			<!-- Condition s'il est en stock afficher "en stock",
				sinon afficher "rupture" -->
			<p v-if="inStock">En stock</p>
			<p v-else>En rupture de stock</p>
			<div>
				<label for="add-item-quantity">Quantité : {{ quantity }}</label>
				<!-- Ici c'est ce qui permet de mettre à jour la quantité que l'user
				va mettre dans son panier, j'utilise propriété "model" pour mettre à jour -->
				<input v-model.number="quantity" id="add-item-quantity" type="number" />
				<!-- propriété v-on (@click) pour augmenter le total du panier -->
				
				<button @click="addToShoppingCart(quantity)">
					Ajouter au panier
				</button>
			</div>
		</div>
	</div>
</template>

<style></style>

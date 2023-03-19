L'app consite à faire afficher 10 cocktails aléatoirement avec un refresh qui maj ces 10 coktails. En cliquant sur un coktail on a la possibilitée de voir son detail (recette, photo etc...) et de l'ajouter aux favoris. La page favoris est accessible sur l'écran d'acceuil et contient une liste des cocktails favoris sur lesquels on peut cliquer et aussi faire afficher le detail, on peut supprimer un cocktail de sa liste de favoris.

L'app est codée en javascript avec le framwork react nativ, voir config node, la rubrique react nativ pour les infos sur la configuration. 

# API

Le principe est d'utiliser une API, ce lien genère aléatoirement un cocktail www.thecocktaildb.com/api/json/v1/1/random.php (Cliquer mon voir un exepemple du retour de l'API).

# React navigation


## App.js

#### Import 

```js
import { NavigationContainer } from '@react-navigation/native';
```

#### bottom tab navigator

```js
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';

const Tab = createBottomTabNavigator();
```

#### Wrap
Le principe est de wrapper mon app dans 3 pages dans la default fonction App()

```js
<NavigationContainer>
	<Tab.Navigator>
		<Tab.Screen name="Home" component={HomeScreen} />
		<Tab.Screen name="Favorites" component={FavoritesScreen} />
		<Tab.Screen name="Detail" component={DetailScreen} />
	</Tab.Navigator>
</NavigationContainer>
```

Ensuite chaque page est contenu dans une fonction au dessus de la fonction App(), par exemple pour la page HomeScreen qui contient la liste des coktails (composant List.js)

```js
const HomeScreen = () => {
	return (
		<ListCocktail></ListCocktail>
	);
}
```

Pour la fonction `DetailScreen` c'est plus subtil car elle est appelée lorsqu'on appui sur un cocktail de la liste, elle prend donc en paramètre `route` pour pouvoir accéder à l'id du cocktail. Lorsqu'un écran est ajouté à une pile de navigation, React Navigation crée un objet `route` qui va contenir en params ce que je lui passe en parametre lorsque je créé ma route vers DetailScreen dans List.js (`navigation.navigate('Detail', { id: item.id, name: item.name})`). 

```js
const DetailScreen = ({ route }) => {
	if (route.params !== undefined) {
		const { id } = route.params;
		return (
			<DetailCocktail id={id}></DetailCocktail>
		);
	}
	return (
		<DetailCocktail id={11007}></DetailCocktail>
	);
}
```

*Idée : Faire passer l'objet entier par la route au lieu de refetch par id dans le detail. 

## Composants

### List.js

List est la page d'accueil de mon app, elle affiche 10 cocktails aléatoirement qui changent à chaque refresh. Elle contient le fetch de l'API bouclé * 10. Le resultat de la requête est push dans un tableau cocktail en json -> `res.json()`.

```js
useEffect(() => {
	const fetchData = async () => {
		const cocktails = [];
		for (let i=0; i < 10; i++) {
		cocktails.push(fetch('https://lien').then(res => res.json()));
	}
		const data = await Promise.all(cocktails)
		setCocktails(data.map(cocktail => ({
			id: cocktail.drinks[0].idDrink,
			name: cocktail.drinks[0].strDrink,
			photo: cocktail.drinks[0].strDrinkThumb,
		})))
	}
	fetchData()
}, []);
```

`Promise.all` prend en entrée une itération de promesse et retourne une promesse seule.

La fonction `renderItem` prend l'`item` en etrée (l'objet qui contient l'`id`, le `name` et la `photo` du cocktail) pour faire afficher une liste de cocktail dans une `flatlist`. Chaque composant de la liste est un bouton qui envoi vers la page `detail` grace à `react navigation`. Dans la `route` je transmet l'`id` pour pouvoir `fetch` by id le cocktail que je souhaite dans `detail`. 

```js
import { useNavigation } from '@react-navigation/native';

const navigation = useNavigation();

const renderItem = ({ item }) => (
	<Pressable id={item.id} onPress={() => navigation.navigate('Detail', { id: item.id })}>
		<View>
			<Image source={{ uri: item.photo }} />
			<Text>{item.name}</Text>
		</View>
	</Pressable>
);
```

À noter que je pourrai faire passer l'objet entier drinks du retour de l'API pour faire afficher mon cocktail dans `detail` mais je préfère pour cet exercice faire comme ça.

### Detail.js


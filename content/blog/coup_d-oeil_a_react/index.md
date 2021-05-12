---
title: Un coup d'oeil à Reactjs
date: "2021-04-30"
description: "Un premier coup d'oeil à Reactjs "
---

Dans le cadre de ma formation OpenClassrooms j'ai un dernier projet: coder un réseau social d'entreprise. Il s'agit  d'un projet full-stack avec le back end en nodejs avec une base de donnée en sql et le front end au choix. 

J'ai choisi d'utiliser le framework React pour mon front end étant donné qu'il est encore très populaire et également très demandé par les employeurs.

###Librairie ou framework?

La première chose que j'ai rencontré est une question qui reviens souvent: 
Est-ce une librairie ou un framework?
Et moi qui croyait apprendre le framework javaScript le plus populaire... 

En regardant le site [reactjs.org](http://reactjs.org) la réponse vient rapidement: "React - A JavaScript library for building user interfaces" autrement dit une librairie JavaScript pour créer des interfaces utilisateurs.

Le mystère étant résolu intéressons nous plutôt à React en lui-même.

###jsx

Le premier élément est le jsx, il s'agit tout simplement d'html ( a peu près, il y a quelques exceptions ). Cela va nous permettre d'intégrer ensemble le code html et des expressions javascript dans le même fichier

```jsx
const name = 'Nicolas'
const element = <div>Bonjour {name}</div>

ReactDOM.render(element, document.getElementById('root'))
```

Le code ci dessus illustre l'intégration de html et javascript, la dernière ligne permet d'afficher l'élément dans un fichier html classique, plus précisément dans un élément ayant pour id 'root'.

Il faut toute fois prendre garde: même si cela ressemble beaucoup à de l'html, il s'agit quand même de javascript, dans un fichier .js et donc certains mots clés peuvent porter à confusion.

Par exemple: 

```jsx
const element = <div class="contenu">Bonjour cher lecteur</div> 
```

cela semble plutôt innocent mais "class" se trouve être également un mot clé javascript, cela va porter à confusion lors de l'exécution du code.

Pour éviter cela on utilisera une variante 

```jsx
const element = <div className="contenu">Bonjour cher lecteur</div> 
```

Jsx remplace le mot clé class par className (noter l'utilisation de camel case pour le nom ) de sorte que le code soit correctement interprété par les navigateurs.

Jsx n'est pas à proprement parler nécessaire pour utiliser React,il est effectivement possible d'imbriguer plusieurs méthodes ReactDOM.render() les unes dans les autres mais cela se révèle rapidement ingérable. Au final, le jsx simplifie tellement les choses qu'il en est presque indispensable.

###Composants

 Les pièces de base d’un projet React sont les composants ( ou components en anglais). Il s’agit tout simplement d’un bout de code réutilisable représentant une partie de votre interface, ça peut être un entête de page, un formulaire ou une galerie d’images par exemple.

On peux aussi imbriquer les composants les uns dans les autres: des containers individuels à l'intérieur d'un container lui-même dans un autre container.

Il y a 2 type de composant:

- les composants de classe ES6, qui sont des classes
- les composants fonctionnels, qui sont des fonctions

Composant ES6:

```jsx
class Hello extends React.Component {
	render() {
		return (
			<div>
				<h1>Hello there</h1>
			</div>
		)
	}
}
```

Composant fonctionnel:

```jsx
function Hello() {
    return (
        <div>
            <h1>Hello there</h1>
        </div>
    )
}
const Hello = () => {
	return (
		<div>
			<h1>Hello there</h1>
		</div>
	)
}
```
Voici trois façon d'écrire un composant qui renvoie toute la même chose: un simple div avec un titre h1 à l'intérieur.

###Comment choisir le type de composant?

Voila une question qui m'a fait me gratter la tête pendant un petit moment. 
Traditionnellement, les composants fonctionnels étaient qualifiés de "stateless" sans état, pour simplifier il s'agissait de composant statiques. 
Depuis l'introduction de react hook il est désormais possible d'utiliser les états dans les composants fonctionnels, les différences sont de plus en plus mince. De plus, parce qu'ils sont légers et plus simple à écrire, l'équipe Facebook recomande d'utiliser des composants fonctionnels dans la mesure du possible.

Je réalise que je n'ai pas encore parler de rendu de contenu ou des states mais ça devra attendre une prochaine fois, quand j'aurais eu le temps de comprendre exactement comment ça marche et pourquoi.

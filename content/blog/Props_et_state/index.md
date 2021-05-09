---
title: Props et states
date: "2021-05-09"
description: "les props et state dans Reactjs"
---

Jusqu'à présent, React est très utile pour créer des interfaces utilisateurs à base de blocs réutilisable en utilisant des composants soit de classe ES6 soit fonctionnels, cependant ce n'est pas très dynamique tout ça et on ne sait pas encore comment faire passer des donées d'un composent à un autre.

##Les props 

Les props (diminutif de properties ou propriétées) sont un bon moyen de faire passer des données d'un composant parent à un composant enfant, elles fonctionnent comme un peu comme les attributs en html: 

```jsx
const ParentComponent = () => {
    return(
        <div>
            <ChildComponent title="Hello there" />
        </div>
    )
} 
```

Ici la prop est "title" et contient la chaine de caractère "Hello there" on y accède dans le composant enfant de cette façon:

```jsx
const ChildComponent = (props) => {
    return (
        <div>
            <h1>{props.title}</h1>
        </div>
    )
}
```
(On utilise les accolades dans du code jsx pour executer du code javascript au milieu du pseudo html)

On voit ici que l'on appelle "props" en argument du composant, on peut l'appeler autrement mais par convention il est pratique d'appeler les props... props. 
Donc 'props' contient touts les props passées au composant, props.title va donc contenir la chaine "Hello there", on aurait pu utiliser d'autres attributs pour passer d'autres données.
Pour faire simple, on peut utiliser un attribut dans le code jsx pour faire des données vers un composant enfant ou on l'utilisera comme un argument dans une fonction, et ça s'appelle une props...

Dans l'exemple au dessus j'ai utilisé une chaine de caractère en tant que props mais on peut bien sur utiliser des nombres, des booléens ou des variables. Il faut cependant savoir une chose: ces données appartiennent au composant parent, il est donc impossible au composant enfant des les modifier une fois reçus.

##les states

Contrairement aux props, les données state sont locales et spécifique au composant auquel elles appartiennent. Elles ne sont donc accessible depuis un autre composant si l'on décide des les faire passer en props à un composant enfant.
Basiquement, chaque composant a un objet state ou l'on va stocker les valeurs des propriétés du composant. Lorsque l'objet state change, le composant est  re-rendu.

dans un composant de type class ES6, on déclare l'objet state dans dans une méthode constructor et on y accède avec la syntaxe this.state.propriétée.

```jsx
class Voiture extends React.Composent {
    constructor(props) {
        super(props)
        this.state = {
            marque: "citroen",
            type: "c4";
            color: "grise",
            année= 2010
        }

    }
    render() {
        return(
            <div>
                <h1>Ma {this.state.marque} </h1>
                <p>
                    C'est une {this.state.type} {this.state.color} de {this.state.année}
                </p>
            </div>
        )
    }
}
```
Pour changer la valeur d'une ou plusieurs propriétées, il faut utiliser la méthode setState() afin de s'assurer que le composant appelle bien la méthode render().

```jsx
class Voiture extends React.Composent {
    constructor(props) {
        super(props)
        this.state = {
            marque: "citroen",
            type: "c4";
            color: "grise",
            année= 2010
        }

    }
    changeColor () => {
        this.setState({ color: "bleue" })
    }
    render() {
        return(
            <div>
                <h1>Ma {this.state.marque} </h1>
                <p>
                    C'est une {this.state.type} {this.state.color} de {this.state.année}
                </p>
                <button
                    type="button"
                    onClick= {this.changeColor}
                    >Changer la couleur</button>
            </div>
        )
    }
}
```
Jusqu'à l'introduction des hooks dans react 16.8 il était nécessaire d'utiliser des composants de classe ES6 pour bénéficier des variables states. Jusque la les composants fonctionnels étaient qualifiés au miux de "stateless" ( sans état) au pire de "dumb" parce qu'ils étaient forcément statique du fait de l'absence de variables state.
On verra dans un prochain article comment utiliser les hooks notament pour les states.


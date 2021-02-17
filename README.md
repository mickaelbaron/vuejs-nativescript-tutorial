# Tutoriel Vue.js: savoir développer des applications mobiles avec NativeScript

L'objectif de cette série d'exercices est d'apprendre à développer une application mobile avec le framework [Vue.js](https://vuejs.org/) et en utilisant une approche hybride via le framework [NativeScript](https://nativescript.org/). 

[NativeScript](https://nativescript.org/) est une solution opensource qui existe depuis 2015 et qui permet de développer une application mobile sous [Android](https://www.android.com) et [iOS](https://www.apple.com/ios) en utilisant le langage JavaScript ou tout langage qui se transpile à JavaScript, comme TypeScript. [NativeScript](https://nativescript.org/) gère aussi les frameworks web orientés composants comme [Angular](https://angular.io/) et [Vue.js](https://vuejs.org/). La version pour [Vue.js](https://vuejs.org/) s'appelle [NativeScript-Vue](https://nativescript-vue.org/). Les composants graphiques utilisés dans le code HTML de l'application développée sont spécifiques à [NativeScript](https://nativescript.org/). Il n'est pas possible d'utiliser les composants classiques HTML d'une application web comme `<p>`, `<div>`, `<form>`, etc. En effet, [NativeScript](https://nativescript.org/) va traduire ces composants d'abstraction afin d'invoquer les composants natifs du dispositif mobile. Les applications ainsi développées seront ainsi plus proches des applications natives. Cela permet aussi d'utiliser des composants (dit plugin sous [NativeScript](https://nativescript.org/)) pour accéder aux API natives du téléphone (accéléromètre, géolocalisation, caméra...). 

Les exercices proposés dans ce tutoriel se proposent de vous donner les bases du développement d'applications mobiles avec [NativeScript](https://nativescript.org/), sans entrer dans les détails. Ne vous attendez pas à devenir un expert de [NativeScript](https://nativescript.org/) à la fin, ce n'est pas l'objectif. Je détaille ci-dessous le contenu de chaque exercice :

* [préparer son environnement de test via la ligne de commande 💪🏼](/vuejs-nativescript-tutorial-exercice0) ;
* [créer et exécuter son premier projet NativeScript](/vuejs-nativescript-tutorial-exercice1) ;
* [utiliser les API natives d'un dispositif mobile](/vuejs-nativescript-tutorial-exercice2) ;
* [invoquer et visualiser les données d'un service web](/vuejs-nativescript-tutorial-exercice3).

**Buts pédagogiques** : configurer son environnement de test, créer un émulateur Android et iOS, créer un projet avec NativeScript-Vue, débogguer son application avec VueDevTools, naviguer entre des composants, communiquer avec les API natives d'un dispositif, invoquer un service web, afficher les données JSON.

> Ce dépôt est utilisé dans le cadre d'un cours sur le développement d'applications web que je dispense  en français à l'[ISAE-ENSMA](https://www.ensma.fr) pour les étudiants en dernière année du cycle d'ingénieur qui suivent l'option informatique. Tous les supports de cours et tutoriaux sont disponibles sur ma page Developpez.com : [https://mbaron.developpez.com](https://mbaron.developpez.com/#page_web) et sur ma page personnelle : [https://mickael-baron.fr/](https://mickael-baron.fr/).

## Prérequis logiciels

* Éditeur de code [Visual Studio Code](https://code.visualstudio.com/) ;
* Le gestionnaire de paquet [npm](https://www.npmjs.com/) ; 
* SDK [Android](https://www.android.com) ou Xcode [iOS](https://www.apple.com/ios) ;
* Java 8.

L'installation du SDK de [Android](https://www.android.com) et [iOS](https://www.apple.com/ios) sont expliquées dans un exercice spécial : [préparer son environnement de test via la ligne de commande 💪🏼](/vuejs-nativescript-tutorial-exercice0). Si vous disposer déjà d'une installation faite avec [Android Studio](https://developer.android.com/studio) pour [Android](https://www.android.com) ou XCode pour [iOS](https://www.apple.com/ios), vous pouvez directement passer à l'exerice 1. Assurez-vous toutefois de disposer d'un émulateur fonctionnel avant de commencer les exercices.

## Ressources

Retrouver les autres tutoriels :

* [Tutoriel sur l'intégration de la bibilothèque Vue.js dans un site web existant](https://github.com/mickaelbaron/vuejs-form-tutorial) ;
* [Tutoriel sur le développement d'une application SPA (Single-Page Application) avec Vue.js](https://github.com/mickaelbaron/vuejs-spa-tutorial) ;
* [Article sur les généralités des frameworks web JavaScript et sur la présentation de Vue.js](https://mickael-baron.fr/web/vuejs-generalites-part1) ;
* [Article sur la mise en œuvre des concepts de Vue.js](https://mickael-baron.fr/web/vuejs-miseenoeuvre-part2) ;
* [Article sur le déploiement d'une application web développée avec Vue.js](https://mickael-baron.fr/web/vuejs-deploiement-part3).

Pour aller plus loin, vous pouvez consulter les ressources suivantes :

* [Introduction au développement web avec des composants](https://mickael-baron.fr/web/intro-developpement-web-composant) ;
* [Introduction au développement Web avec Vue.js](https://mickael-baron.fr/web/intro-vuejs).
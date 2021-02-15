# Exercice 1 : Utiliser les API natives d'un dispositif mobile avec NativeScript-Vue

Cet exercice s'intéresse à l'utilisation des API natives des dispositifs mobiles afin d'accéder aux données liées à l'accéléromètre, la géolocalisation et la caméra en utilisant [NativeScript-Vue](https://nativescript-vue.org/). Nous montrons également comment gérer les permissions pour autoriser l'accès à ces API natives sans explicitement le coder dans le projet [Vue.js](https://vuejs.org/). Ainsi, votre code pourra fonctionner sans problème sur [Android](https://www.android.com) et [iOS](https://www.apple.com/ios).

Dans la suite de l'exercice, nous utiliserons un dispositif mobile virtuel [Android](https://www.android.com). Si vous souhaitez utiliser un dispositif physique ou basé sur [iOS](https://www.apple.com/ios) la démarche sera la même.

## But

* Accéder aux données de l'accéléromètre, la géolocalisation et la caméra.
* Donner des permissions pour accéder aux API natives.

## Étapes à suivre

* Ouvrir un terminal et exécuter la ligne de commande suivante qui permet de créer un projet [NativeScript-Vue](https://nativescript-vue.org/) à partir d'un template. Le nom du projet à renseigner est `ns-exercice2`. Des questions vous seront posées, pour plus de simplicité, laisser les valeurs par défaut.

```console
$ vue init nativescript-vue/vue-cli-template ns-exercice2
```

* Éditer le fichier _src/components/App.vue_ et remplacer par le code donné ci-dessous.

```javascript
<template>
  <Page>
    <ActionBar title="Welcome to NativeScript-Vue!" />
    <StackLayout>
      <TabView>
          <TabViewItem title="Accéléromètre">
          <!-- <AccelerometerComponent /> -->
          <Label text="TODO: AccelerometerComponent" />
        </TabViewItem>
        <TabViewItem title="Géolocalisation">
          <!-- <LocationComponent /> -->
          <Label text="TODO: LocationComponent" />
        </TabViewItem>
        <TabViewItem title="Caméra">
          <!-- <CameraComponent /> -->
          <Label text="TODO: CameraComponent" />
        </TabViewItem>
      </TabView>
    </StackLayout>
  </Page>
</template>

<script >
// import AccelerometerComponent from "@/components/AccelerometerComponent";
// import LocationComponent from "@/components/LocationComponent";
// import CameraComponent from "@/components/CameraComponent";

export default {
  components: {
    // AccelerometerComponent,
    // LocationComponent,
    // CameraComponent,
  },
};
</script>

<style scoped>
ActionBar {
  background-color: #53ba82;
  color: #ffffff;
}
</style>
```

Il s'agit du composant principal qui contiendra les trois composants développés pour manipuler respectivement l'accéléromètre, la géolocalisation et la caméra. Au fur et à mesure de l'avancé de cet exercice, nous déclarerons un composant développé comme élément du composant `TabView`. Il faudra décommenter au fur et à mesure chaque composant.

Nous commençons par l'accès aux données transmises par l'accéléromètre. Cette API native ne requiert pas de permission spécifique. L'accéléromètre retourne les accélérations linéaires selon trois axes orthogonaux (x, y et z).  

* Créer un nouveau fichier _src/components/AccelerometerComponent.vue_ qui servira à afficher les données de l'accéléromètre. Compléter ce fichier par le code ci-dessous.

```javascript
<template>
  <StackLayout>
    <Label v-bind:text="accelerometerValues.x"></Label>
    <Label v-bind:text="accelerometerValues.y"></Label>
    <Label v-bind:text="accelerometerValues.z"></Label>
  </StackLayout>
</template>

<script>
var accelerometer = require("nativescript-accelerometer");

export default {
  data() {
    return {
      accelerometerValues: {
        x: null,
        y: null,
        z: null,
      },
    };
  },
  mounted() {
    accelerometer.startAccelerometerUpdates(
      (data) => {
        this.accelerometerValues = data;
      },
      {
        sensorDelay: "ui",
      }
    );
  },
};
</script>
```

Les informations de l'accéléromètre sont transmise par la fonction `startAccelerometerUpdates` qui retourne des nouvelles valeurs selon une fréquence de rafraichissement. Cette fréquence `sensorDelay` peut recevoir les valeurs suivantes : `normal` (0.2 second), `ui` (0.06 second), `game` (0.02 second) et `fastest` (aussi vite que possible). Bien entendu, plus la valeur de `sensorDelay` est basse, plus votre système transmet des informations récentes avec le problème d'une surconsommation de ressource. Le choix de la valeur de `sensorDelay` doit être réaliste.

* Depuis la ligne de commande, ajouter le plugin `nativescript-accelerometer` au projet (le fichier _package.json_ sera impacté).

```console
$ ns plugin add nativescript-accelerometer
```

* Modifier le fichier _src/components/App.vue_ de façon à décommenter tout ce qui concerne le composant *AccelerometerComponent*.

* Démarrer l'émulateur [Android](https://www.android.com) si ce n'est pas déjà fait (voir [exercice 0](../vuejs-nativescript-tutorial-exercice0/README.md) pour démarrer l'émulateur créé pour cette série d'exercices).

```console
$ emulator @pixel_xl_30
```

* Pour exécuter le projet [NativeScript-Vue](https://nativescript-vue.org/) et tester la récupération des données de l'accéléromètre, il ne vous reste plus qu'à exécuter la ligne de commande suivante.

```console
$ ns run android
```

![Composant AccelerometerComponent qui permet d'afficher dans trois composants textes les accélérations linéaires selon trois axes orthogonaux](images/accelerometer.png)

Sur l'émulateur il est assez difficile de vérifier le fonctionnement de l'accéléromètre. Vous pouvez toutefois changer l'orientation du téléphone et vous constaterez que les valeurs changent.



ns plugin add nativescript-geolocation

https://market.nativescript.org/plugins/@nativescript/camera/
https://github.com/NativeScript/plugins

 emulator -webcam-list
 emulator  -camera-back webcam0 @pixel_xl_30

https://github.com/nstudio/nativescript-camera-plus

## Aller plus loin

* Implémenter le mouvement d'agitation de votre téléphone (https://nativescript.org/blog/detecting-shakes-in-nativescript/)

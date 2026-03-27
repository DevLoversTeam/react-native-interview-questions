**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  React Native <img src="./assets/reactnative.svg" width="40" height="40" />
</h1>

<h2>Les questions et réponses d’entretien React Native les plus populaires</h2>

<details>
<summary>1. Qu’est-ce que React Native et en quoi est-il différent de React ?</summary>

#### React Native

React Native est un framework open source pour créer des applications mobiles
avec JavaScript/TypeScript et React.

Différence clé :

1. **React (React.js)** : construit des interfaces web rendues dans le DOM du
   navigateur (`div`, `span`, etc.).
2. **React Native** : construit des applications iOS/Android rendues avec des
   composants natifs de la plateforme (`View`, `Text`, `Image`, etc.).

Les deux partagent le même modèle de composants, props/state et hooks, mais
ciblent des plateformes et des couches de rendu différentes.

**En bref**

React Native cible le mobile avec des composants UI natifs, tandis que React
cible le DOM web.

</details>

<details>
<summary>2. Explique le concept de JSX dans React Native.</summary>

#### React Native

JSX (JavaScript XML) est une extension de syntaxe qui permet d’écrire la
structure de l’UI de manière déclarative, dans un style proche du HTML, à
l’intérieur de JavaScript.

Dans React Native, JSX s’utilise avec des composants natifs :

```jsx
function Greeting() {
  return <Text>Hello, React Native!</Text>;
}
```

Notes :

1. JSX n’est pas du HTML. Babel le transforme en appels JavaScript.
2. Tu peux insérer des expressions JavaScript dans `{}`.
3. En React Native, JSX utilise des composants natifs (`View`, `Text`) plutôt
   que des balises navigateur (`div`, `p`).

**En bref**

JSX est un sucre syntaxique pour décrire l’UI, puis React Native le mappe vers
les composants natifs.

</details>

<details>
<summary>3. Comment créer un composant fonctionnel en React Native ?</summary>

#### React Native

Un composant fonctionnel est une fonction JavaScript qui retourne du JSX.

```jsx
import React from 'react';
import { View, Text } from 'react-native';

function ProfileCard() {
  return (
    <View>
      <Text>Profile</Text>
    </View>
  );
}

export default ProfileCard;
```

Tu peux aussi utiliser la syntaxe fonction fléchée :

```jsx
const ProfileCard = () => (
  <View>
    <Text>Profile</Text>
  </View>
);
```

**En bref**

C’est une fonction qui retourne du JSX, généralement combinée à des hooks pour
l’état et les effets.

</details>

<details>
<summary>4. Quels sont les composants core en React Native (View, Text, Image, etc.) ?</summary>

#### React Native

Les composants core sont des primitives UI intégrées fournies par React Native
pour créer des interfaces mobiles.

Composants core courants :

1. **View** : conteneur de base pour la mise en page et le style.
2. **Text** : affiche du contenu texte.
3. **Image** : rend des images locales ou distantes.
4. **TextInput** : champ de saisie texte.
5. **ScrollView** : conteneur défilable.
6. **FlatList / SectionList** : rendu efficace de listes volumineuses.
7. **Pressable / TouchableOpacity** : gestion des interactions tactiles.
8. **SafeAreaView** : respecte les zones sûres de l’écran (encoches, coins
   arrondis).

Ces composants sont mappés vers des éléments UI natifs sur iOS et Android.

**En bref**

Ce sont les briques de base de RN ; cite 2-3 composants que tu utilises tous
les jours.

</details>

<details>
<summary>5. Que sont les props en React Native et comment les utilise-t-on ?</summary>

#### React Native

Les props (properties) sont des entrées en lecture seule transmises d’un
composant parent à un composant enfant.

Elles servent à :

1. Passer des données (texte, nombres, objets, tableaux).
2. Passer du comportement (fonctions callback).
3. Configurer des composants réutilisables.

Exemple :

```jsx
import { View, Text } from 'react-native';

function WelcomeMessage({ name }) {
  return (
    <View>
      <Text>Welcome, {name}!</Text>
    </View>
  );
}

function App() {
  return <WelcomeMessage name="Alex" />;
}
```

Ici, `name` est une prop envoyée de `App` vers `WelcomeMessage`.

**En bref**

Les props sont des entrées immuables parent -> enfant, utilisées pour la
configuration et le flux de données.

</details>

<details>
<summary>6. Qu’est-ce que le state en React Native et comment est-il géré avec les hooks ?</summary>

#### React Native

Le state est une donnée propre au composant qui peut évoluer dans le temps et
déclencher des mises à jour de l’UI.

Dans les composants fonctionnels, le state est généralement géré avec le hook
`useState` :

```jsx
import React, { useState } from 'react';
import { View, Text, Button } from 'react-native';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <View>
      <Text>Count: {count}</Text>
      <Button title="Increment" onPress={() => setCount(count + 1)} />
    </View>
  );
}
```

Pour une logique plus complexe, tu peux utiliser `useReducer`.

**En bref**

Le state est une donnée locale mutable ; avec les hooks, on la met à jour et on déclenche des rerenders de façon prévisible.

</details>

<details>
<summary>7. Quelle est la différence entre state et props ?</summary>

#### React Native

`state` et `props` stockent tous deux des données pour le rendu, mais leurs
rôles sont différents :

1. **Props** : entrées en lecture seule passées du parent vers l’enfant.
2. **State** : données internes, mutables, gérées par le composant lui-même.

Comparaison rapide :

1. **Qui possède la donnée ?** Props : composant parent. State : composant
   courant.
2. **Peut-elle changer localement ?** Props : non. State : oui, via des hooks
   comme `useState`.
3. **Cas d’usage :** Props : configuration et flux de données entre composants.
   State : comportement dynamique de l’UI dans un composant.

**En bref**

Les props sont des entrées immuables parent -> enfant ; le state modélise la donnée interne qui change.

</details>

<details>
<summary>8. Comment gères-tu les entrées utilisateur en React Native ?</summary>

#### React Native

Les entrées utilisateur sont généralement gérées via des composants contrôlés,
le plus souvent `TextInput`, combinés avec le state.

```jsx
import React, { useState } from 'react';
import { View, TextInput, Text } from 'react-native';

function NameForm() {
  const [name, setName] = useState('');

  return (
    <View>
      <TextInput
        value={name}
        onChangeText={setName}
        placeholder="Enter your name"
      />
      <Text>Hello, {name}</Text>
    </View>
  );
}
```

Événements/handlers clés :

1. `onChangeText` : met à jour le state du texte.
2. `onPress` : gère les actions bouton/tactiles.
3. `onSubmitEditing` : réagit à la validation clavier sur `TextInput`.

**En bref**

Utilise des inputs contrôlés : la valeur vit dans le state et se met à jour via des handlers.

</details>

<details>
<summary>9. Comment styles-tu des composants en React Native ?</summary>

#### React Native

React Native utilise des objets JavaScript pour les styles au lieu de fichiers CSS.

Tu peux styler les composants de trois façons courantes :

1. **Styles inline** (rapides, locaux) :

```jsx
<Text style={{ color: 'blue', fontSize: 18 }}>Hello</Text>
```

2. **`StyleSheet.create`** (recommandé dans la plupart des cas) :

```jsx
const styles = StyleSheet.create({
  title: { color: 'blue', fontSize: 18 },
});
```

3. **Tableaux de styles** (conditionnels/composés) :

```jsx
<Text style={[styles.title, isActive && styles.active]}>Hello</Text>
```

Les styles RN ressemblent à CSS, mais avec des propriétés en camelCase (par
exemple `backgroundColor`, `fontSize`).

**En bref**

Le styling RN se fait avec des objets JS, souvent centralisés pour cohérence et réutilisation.

</details>

<details>
<summary>10. Qu’est-ce que StyleSheet et quand l’utiliser ?</summary>

#### React Native

`StyleSheet` est un utilitaire React Native pour définir et organiser les styles
de manière structurée.

Exemple :

```jsx
import { StyleSheet, View, Text } from 'react-native';

const styles = StyleSheet.create({
  container: {
    padding: 16,
    backgroundColor: '#fff',
  },
  title: {
    fontSize: 20,
    fontWeight: '600',
  },
});

function Card() {
  return (
    <View style={styles.container}>
      <Text style={styles.title}>Card title</Text>
    </View>
  );
}
```

Quand l’utiliser :

1. Quand les styles sont réutilisés sur plusieurs éléments.
2. Quand tu veux un code composant plus propre et maintenable.
3. Quand tu veux une approche de style cohérente et scalable sur des écrans/apps plus grands.

**En bref**

Utilise StyleSheet pour des styles réutilisables, plus propres et plus faciles à maintenir.

</details>

<details>
<summary>11. Explique Flexbox et son rôle dans le layout.</summary>

#### React Native

Flexbox est le système principal de layout dans React Native. Il contrôle
comment les composants sont dimensionnés, alignés et distribués dans un
conteneur.

Dans React Native, les valeurs par défaut de Flexbox diffèrent légèrement du CSS web :

1. `flexDirection` vaut `column` par défaut.
2. `alignContent` vaut `flex-start` par défaut.
3. `flexShrink` vaut `0` par défaut.

Propriétés courantes :

1. `flex` : définit l’espace pris par un élément par rapport aux autres.
2. `flexDirection` : disposition en ligne ou en colonne.
3. `justifyContent` : alignement sur l’axe principal.
4. `alignItems` : alignement sur l’axe secondaire.
5. `gap` (versions RN modernes) : espacement entre enfants.

Exemple :

```jsx
<View
  style={{ flex: 1, flexDirection: 'row', justifyContent: 'space-between' }}
>
  <View style={{ width: 50, height: 50, backgroundColor: 'red' }} />
  <View style={{ width: 50, height: 50, backgroundColor: 'blue' }} />
</View>
```

**En bref**

Pense en axes (principal vs secondaire), puis ajuste `justifyContent` et `alignItems`.

</details>

<details>
<summary>12. Comment gères-tu le responsive design en React Native ?</summary>

#### React Native

Le responsive design en React Native se gère en combinant des layouts flexibles
avec des APIs adaptées au device.

Approches courantes :

1. Utiliser Flexbox (`flex`, `%`, alignement) au lieu de tailles fixes.
2. Utiliser `Dimensions` ou `useWindowDimensions()` pour la taille d’écran.
3. Utiliser `Platform` pour les ajustements spécifiques à la plateforme.
4. Utiliser `SafeAreaView` pour respecter encoche et UI système.
5. Échelonner typographie/espacements via des constantes partagées.

Exemple :

```jsx
import { useWindowDimensions, View } from 'react-native';

function ResponsiveCard() {
  const { width } = useWindowDimensions();
  const isTablet = width >= 768;

  return <View style={{ padding: isTablet ? 24 : 16 }} />;
}
```

**En bref**

Combine layout flexible, dimensions d’écran et gestion des safe areas.

</details>

<details>
<summary>13. Comment déboguer une application React Native ?</summary>

#### React Native

Le debugging en React Native se fait généralement avec un mix d’outils intégrés
et externes.

Options principales :

1. **Logs Metro** : `console.log`, warnings, erreurs dans la sortie terminal.
2. **React Native Dev Menu** : recharger l’app, inspecter l’UI, activer des outils de debug.
3. **React DevTools** : inspecter l’arbre de composants, props et état des hooks.
4. **Flipper** : inspection réseau, logs, layout et plugins de performance.
5. **Tooling natif** : Xcode (iOS) et Android Studio (Android) pour crashes/logs natifs.

Bonne pratique : reproduire avec des étapes claires, isoler le composant fautif,
et vérifier sur iOS et Android si nécessaire.

**En bref**

Réponds avec la stack d’outils : logs, DevTools/Flipper et logs natifs selon la plateforme.

</details>

<details>
<summary>14. Qu’est-ce que Fast Refresh et comment cela fonctionne ?</summary>

#### React Native

Fast Refresh est une fonctionnalité de développement qui met à jour l’app
immédiatement après un changement de code, tout en essayant de conserver l’état
des composants.

Fonctionnement :

1. Tu sauvegardes un fichier.
2. Metro reconstruit uniquement les modules impactés.
3. React Native injecte le code mis à jour dans l’app en cours d’exécution.
4. L’UI se met à jour instantanément sans redémarrage complet dans la plupart des cas.

Notes :

1. L’état local est généralement conservé pour les composants fonctionnels.
2. Si les modifications touchent l’initialisation de module ou des exports
   non-composants, RN peut faire un rechargement plus large.
3. C’est une feature de dev uniquement, pas un comportement de production.

**En bref**

Fast Refresh met à jour les modules modifiés en dev et conserve souvent l’état local.

</details>

<details>
<summary>15. Que sont les composants Touchable et comment fonctionnent-ils ?</summary>

#### React Native

Les composants Touchable sont des wrappers interactifs qui réagissent aux taps/
press. Ils permettent de déclencher des actions (ouvrir un écran, soumettre un
formulaire, sélectionner un élément).

Options courantes :

1. `Pressable` (moderne, flexible, recommandé dans beaucoup de cas).
2. `TouchableOpacity` (réduit l’opacité au press).
3. `TouchableHighlight` (affiche un surlignage sous l’enfant).
4. `TouchableWithoutFeedback` (sans feedback visuel).

Exemple :

```jsx
import { Pressable, Text } from 'react-native';

function SaveButton({ onSave }) {
  return (
    <Pressable onPress={onSave}>
      <Text>Save</Text>
    </Pressable>
  );
}
```

Ils exposent des événements comme `onPress`, `onPressIn`, `onPressOut` et
`onLongPress`.

**En bref**

Ils ajoutent des interactions de press à l’UI ; `Pressable` est généralement le meilleur choix moderne.

</details>

<details>
<summary>16. Comment gères-tu la navigation en React Native (React Navigation) ?</summary>

#### React Native

La navigation est généralement gérée avec `@react-navigation/*`.

Setup typique :

1. Installer le core React Navigation et les navigateurs nécessaires.
2. Envelopper l’app avec `NavigationContainer`.
3. Définir stacks/tabs/drawers.
4. Naviguer avec `navigation.navigate('ScreenName')`.

Dans la plupart des apps, combine Stack + Tab et garde des noms de routes typés.

**En bref**

Utilise la composition de navigateurs (stack/tab/drawer) avec une structure de routes explicite.

</details>

<details>
<summary>17. Quel est le rôle de NavigationContainer ?</summary>

#### React Native

`NavigationContainer` est le provider racine qui gère l’état de navigation et
relie les navigateurs à l’environnement de l’app.

Il est responsable de :

1. Maintenir l’état actuel de l’arbre de navigation.
2. Gérer le linking/deep links.
3. Fournir le contexte de navigation à tous les écrans.

Sans lui, React Navigation ne peut pas fonctionner.

**En bref**

C’est le conteneur racine de contexte et d’état de navigation pour toute l’application.

</details>

<details>
<summary>18. Comment passes-tu des paramètres entre écrans ?</summary>

#### React Native

On passe les params via les méthodes de navigation.

Exemple :

```jsx
navigation.navigate('Profile', { userId: '42' });
```

Lecture des params dans l’écran cible :

```jsx
const { userId } = route.params;
```

Utilise les params pour un petit contexte de route, pas pour un state global
volumineux.

**En bref**

Envoie de petits paramètres via `navigate` et récupère-les via `route.params`.

</details>

<details>
<summary>19. Qu’est-ce que le deep linking et comment l’implémenter ?</summary>

#### React Native

Le deep linking permet d’ouvrir un écran précis de l’app depuis une URL.

Implémentation avec React Navigation :

1. Définir URL scheme/universal links dans les configs natives.
2. Configurer l’objet `linking` dans `NavigationContainer`.
3. Mapper les chemins URL vers les noms d’écrans.

Cela permet des flux comme `myapp://product/123` ouvrant l’écran produit.

**En bref**

Mappe les URLs vers les écrans pour que les liens externes ouvrent la route exacte.

</details>

<details>
<summary>20. Que sont les keys dans les listes et pourquoi sont-elles importantes ?</summary>

#### React Native

`key` identifie chaque élément de liste de manière unique pour la reconciliation
React.

Pourquoi c’est important :

1. Aide React à mettre à jour uniquement les lignes modifiées.
2. Évite la réutilisation incorrecte d’éléments et les bugs d’état.
3. Améliore performance et prévisibilité du rendu.

Utilise toujours des IDs stables et uniques, pas l’index du tableau (sauf liste statique).

**En bref**

Des keys stables et uniques évitent les bugs de rendu de liste et améliorent les updates.

</details>

<details>
<summary>21. Comment rendre des listes efficacement (FlatList, SectionList) ?</summary>

#### React Native

Pour un rendu efficace des listes en React Native, privilégie `FlatList` et
`SectionList` plutôt que de mapper de grands tableaux dans `ScrollView`.

Pourquoi c’est efficace :

1. Rendu lazy des items (lignes visibles + buffer).
2. Recyclage des vues d’items avec moins d’usage mémoire.
3. Optimisations intégrées de pagination et de scroll.

Cas d’usage :

1. `FlatList` : liste unidimensionnelle d’éléments similaires.
2. `SectionList` : liste groupée avec en-têtes de section.

Exemple simple `FlatList` :

```jsx
import { FlatList, Text, View } from 'react-native';

function UsersList({ users }) {
  return (
    <FlatList
      data={users}
      keyExtractor={item => item.id}
      renderItem={({ item }) => (
        <View>
          <Text>{item.name}</Text>
        </View>
      )}
    />
  );
}
```

**En bref**

Préfère les listes virtualisées pour les gros volumes afin de maîtriser mémoire et performance de scroll.

</details>

<details>
<summary>22. Qu’est-ce que VirtualizedList et quand l’utiliser ?</summary>

#### React Native

`VirtualizedList` est le moteur de base derrière `FlatList` et `SectionList`.
Il gère le rendu par fenêtre pour de grands datasets.

Quand l’utiliser directement :

1. Quand la source de données n’est pas un simple tableau.
2. Quand tu as besoin d’un contrôle total sur `getItem` et `getItemCount`.
3. Quand les abstractions `FlatList`/`SectionList` sont trop limitées.

Dans la plupart des apps, commence par `FlatList` ou `SectionList`, plus simples
et suffisantes pour les cas courants.

**En bref**

Utilise-le directement seulement pour des besoins avancés d’accès aux données ; sinon FlatList/SectionList suffit.

</details>

<details>
<summary>23. Comment récupérer des données en React Native (fetch, axios) ?</summary>

#### React Native

Tu peux récupérer des données avec l’API native `fetch` ou avec `axios`.

Exemple `fetch` :

```jsx
async function loadPosts() {
  const response = await fetch('https://api.example.com/posts');
  if (!response.ok) throw new Error('Request failed');
  return response.json();
}
```

Exemple `axios` :

```jsx
import axios from 'axios';

async function loadPosts() {
  const { data } = await axios.get('https://api.example.com/posts');
  return data;
}
```

Flux typique dans un composant :

1. Démarrer l’état de chargement.
2. Exécuter la requête asynchrone.
3. Sauvegarder résultat ou erreur dans le state.
4. Arrêter le chargement et rendre en conséquence.

**En bref**

Explique clairement le cycle de requête : loading, success, failure et gestion d’annulation.

</details>

<details>
<summary>24. Quelles sont les bonnes pratiques pour les appels API et la gestion d’erreurs ?</summary>

#### React Native

Bonnes pratiques API / erreurs :

1. Centraliser la logique API dans une couche service.
2. Gérer systématiquement les états loading, success et error.
3. Définir des timeouts et une stratégie de retry pour les pannes transitoires.
4. Valider la structure de réponse avant d’utiliser les données.
5. Afficher des messages d’erreur compréhensibles (pas des erreurs serveur brutes).
6. Utiliser l’annulation (`AbortController`) pour éviter de mettre à jour des écrans démontés.
7. Gérer le refresh des tokens auth à un seul endroit (interceptors/middleware).

Pattern court :

1. `try` de la requête.
2. `catch` des erreurs réseau/serveur.
3. Mapping vers des messages métier.
4. Log des détails techniques pour debug/monitoring.

**En bref**

Mets l’accent sur une couche API centralisée, un mapping d’erreurs cohérent et une stratégie retry/cancel.

</details>

<details>
<summary>25. Comment gérer le stockage asynchrone (package communautaire AsyncStorage) ?</summary>

#### React Native

`AsyncStorage` est une solution de stockage clé-valeur persistante pour des
données légères (préférences utilisateur, flags, cache simple).

Usage de base :

```jsx
import AsyncStorage from '@react-native-async-storage/async-storage';

async function saveTheme(theme) {
  await AsyncStorage.setItem('theme', theme);
}

async function loadTheme() {
  return AsyncStorage.getItem('theme');
}
```

Bonnes pratiques :

1. Sérialiser les objets avec `JSON.stringify` / `JSON.parse`.
2. Envelopper les appels dans `try/catch`.
3. Garder des payloads petits ; ne pas l’utiliser comme base de données.
4. Namespacer les clés (ex. `app:user:token`).
5. Pour des données sensibles, préférer un stockage sécurisé (Keychain/Keystore).

**En bref**

Utilise-le pour une persistance légère, pas pour les secrets ; sérialise les données et gère les erreurs.

</details>

<details>
<summary>26. Quelles sont les solutions modernes de gestion d’état (Context, Zustand, Redux Toolkit) ?</summary>

#### React Native

Les options modernes dépendent de la complexité de l’app :

1. **Context API** : données globales simples, peu de boilerplate.
2. **Zustand** : store léger, API simple, très peu de cérémonie.
3. **Redux Toolkit** : patterns robustes, middleware, devtools, et bonne montée en charge équipe.

Choisis l’outil le plus petit qui couvre réellement la complexité du projet.

**En bref**

Choisis selon la complexité : Context pour le simple, Zustand/RTK pour des domaines d’état plus larges.

</details>

<details>
<summary>27. Comment gérer un état global sans Redux ?</summary>

#### React Native

Tu peux utiliser Context + hooks ou des stores légers comme Zustand/Jotai.

Pattern courant :

1. Créer un provider pour l’état partagé par domaine.
2. Encapsuler les updates dans des custom hooks.
3. Garder l’état serveur séparé (React Query/Apollo).

Cela évite le boilerplate Redux tout en restant scalable pour beaucoup d’apps.

**En bref**

Combine Context ou stores légers avec des custom hooks et des frontières claires.

</details>

<details>
<summary>28. Que sont les hooks React et lesquels sont les plus utilisés ?</summary>

#### React Native

Les hooks sont des fonctions qui permettent aux composants fonctionnels
d’utiliser state, effets et autres capacités de React.

Hooks courants :

1. `useState`
2. `useEffect`
3. `useMemo`
4. `useCallback`
5. `useRef`
6. `useContext`
7. `useReducer`

Ils permettent aussi de réutiliser de la logique via des custom hooks.

**En bref**

Les hooks apportent la logique stateful aux fonctions et facilitent la réutilisation.

</details>

<details>
<summary>29. Qu’est-ce que useEffect et comment remplace-t-il les méthodes de cycle de vie ?</summary>

#### React Native

`useEffect` exécute les effets secondaires après le rendu et peut aussi les
nettoyer.

Mapping lifecycle (classe -> hooks) :

1. `componentDidMount` -> `useEffect(..., [])`
2. `componentDidUpdate` -> `useEffect(..., [deps])`
3. `componentWillUnmount` -> fonction de cleanup retournée par `useEffect`

Il unifie le comportement de cycle de vie dans les composants fonctionnels.

**En bref**

Utilise-le pour effets + cleanup ; raisonne en dépendances, pas en noms de lifecycle de classe.

</details>

<details>
<summary>30. Que sont useMemo et useCallback, et quand les utiliser ?</summary>

#### React Native

`useMemo` mémoïse des valeurs calculées. `useCallback` mémoïse des références de
fonctions.

À utiliser quand :

1. Le calcul est coûteux.
2. Des références stables sont nécessaires pour éviter des rerenders enfants.
3. Valeurs/callbacks servent de dépendances à d’autres hooks.

Ne pas en abuser ; applique-les là où le profiling montre un vrai gain.

**En bref**

Applique-les de manière ciblée pour stabiliser valeurs/callbacks coûteux quand le gain est mesuré.

</details>

<details>
<summary>31. Que sont les refs et quand les utiliser ?</summary>

#### React Native

Les refs sont des références mutables vers des instances de composants ou des
éléments natifs. Elles permettent d’accéder à des APIs impératives sans
déclencher de re-renders.

Cas d’usage typiques :

1. Donner/retirer le focus à un `TextInput`.
2. Déclencher des méthodes de scroll (`scrollToOffset`, `scrollToEnd`).
3. Mesurer le layout (`measure`, `measureInWindow`).
4. Stocker des valeurs mutables qui ne doivent pas mettre à jour l’UI.

Exemple :

```jsx
import React, { useRef } from 'react';
import { View, TextInput, Button } from 'react-native';

function LoginForm() {
  const inputRef = useRef(null);

  return (
    <View>
      <TextInput ref={inputRef} placeholder="Email" />
      <Button title="Focus input" onPress={() => inputRef.current?.focus()} />
    </View>
  );
}
```

Utilise les refs pour des actions impératives, pas pour remplacer le flux normal
state/props.

**En bref**

Les refs servent à l’accès impératif (focus/scroll/mesure), pas au flux de données classique.

</details>

<details>
<summary>32. Comment créer des custom hooks ?</summary>

#### React Native

Un custom hook est une fonction réutilisable qui commence par `use` et combine
des hooks React (`useState`, `useEffect`, etc.) en logique partagée.

Règles :

1. Le nom du hook doit commencer par `use`.
2. Appeler les hooks uniquement au niveau supérieur du custom hook.
3. Retourner les valeurs/fonctions nécessaires aux composants.

Exemple :

```jsx
import { useEffect, useState } from 'react';

function useOnlineStatus() {
  const [isOnline, setIsOnline] = useState(true);

  useEffect(() => {
    // S’abonner aux changements réseau ici
    return () => {
      // Se désabonner ici
    };
  }, []);

  return isOnline;
}
```

Les custom hooks améliorent la réutilisation, la lisibilité et la séparation
des responsabilités.

**En bref**

Extrais la logique stateful répétée dans des fonctions `use*` pour garder des composants clairs.

</details>

<details>
<summary>33. Qu’est-ce que l’optimisation de performance en React Native ?</summary>

#### React Native

Optimiser la performance en React Native consiste à réduire le coût de rendu,
JavaScript et layout pour garder des interactions fluides (surtout sur appareils
moyens/faibles).

Zones d’optimisation courantes :

1. Rendu : éviter les re-renders inutiles.
2. Listes : utiliser `FlatList`/`SectionList` avec un tuning adapté.
3. Travail JavaScript : sortir les calculs lourds des chemins critiques de rendu.
4. Images : compresser, mettre en cache et dimensionner correctement.
5. Communication Native/JS : minimiser les opérations coûteuses entre couches.

Objectif typique : 60 FPS stables, démarrage plus rapide et bonne réactivité tactile.

**En bref**

Profile d’abord, puis optimise rendu, listes, images et hotspots de charge JS.

</details>

<details>
<summary>34. Comment éviter les re-renders inutiles ?</summary>

#### React Native

On évite les re-renders inutiles en stabilisant les props et en limitant les
mises à jour de state à ce qui est nécessaire.

Techniques pratiques :

1. Utiliser `React.memo` pour les composants fonctionnels purs.
2. Utiliser `useMemo` pour les valeurs dérivées coûteuses.
3. Utiliser `useCallback` pour des références de callbacks stables.
4. Garder le state aussi local que possible.
5. Éviter de créer des objets/fonctions inline passés loin dans l’arbre.
6. Diviser les gros composants en sous-composants plus ciblés.
7. Utiliser des keys stables dans les listes.

Et surtout profiler d’abord (React DevTools/Flipper) puis optimiser les vrais
bottlenecks.

**En bref**

Props stables, state local et mémoïsation ciblée réduisent le coût réel de rendu.

</details>

<details>
<summary>35. Qu’est-ce que la memoization en React Native ?</summary>

#### React Native

La memoization est une technique qui met en cache des résultats calculés ou des
sorties de composants, puis les réutilise quand les entrées n’ont pas changé.

Outils de memoization courants en React Native :

1. `React.memo` : mémoïse le rendu du composant via comparaison de props.
2. `useMemo` : mémoïse des valeurs calculées.
3. `useCallback` : mémoïse des références de fonctions.

Exemple :

```jsx
import React, { useMemo } from 'react';

function Total({ items }) {
  const sum = useMemo(() => {
    return items.reduce((acc, item) => acc + item.price, 0);
  }, [items]);

  return <Text>{sum}</Text>;
}
```

Utilise la memoization de façon sélective ; en abuser peut ajouter de la
complexité sans gain mesurable.

**En bref**

La memoization évite de recalculer du travail inchangé en cachant valeurs, fonctions ou rendus.

</details>

<details>
<summary>36. Qu’est-ce que le moteur Hermes et pourquoi est-il important ?</summary>

#### React Native

Hermes est un moteur JavaScript optimisé pour React Native.

Pourquoi il est important :

1. Démarrage d’app plus rapide.
2. Consommation mémoire plus faible sur de nombreux appareils.
3. Performance plus prévisible sur Android/iOS.
4. Bonne intégration avec le tooling RN.

Hermes est un choix par défaut fréquent pour des apps RN en production.

**En bref**

Hermes améliore surtout le démarrage et le profil mémoire de nombreuses apps RN.

</details>

<details>
<summary>37. Qu’est-ce que la nouvelle architecture React Native ?</summary>

#### React Native

La New Architecture modernise les internals de RN autour de :

1. Fabric renderer.
2. TurboModules.
3. JSI (JavaScript Interface).
4. Direction Bridgeless.

Objectifs : réduire la latence JS/native, mieux gérer la concurrence et
améliorer la performance.

**En bref**

On peut la résumer à Fabric + TurboModules + JSI pour moins d’overhead et une meilleure scalabilité.

</details>

<details>
<summary>38. Que sont Fabric et TurboModules ?</summary>

#### React Native

`Fabric` est le nouveau système de rendu. `TurboModules` est le nouveau système
de modules natifs.

Ensemble, ils apportent :

1. Des updates UI plus efficaces.
2. Un accès plus rapide aux modules.
3. Une meilleure intégration native typée via codegen.
4. De meilleures performances au démarrage et à l’exécution.

**En bref**

Fabric modernise le rendu ; TurboModules modernise l’accès et le chargement des modules natifs.

</details>

<details>
<summary>39. Qu’est-ce que JSI et comment remplace-t-il l’ancien bridge ?</summary>

#### React Native

JSI (JavaScript Interface) est une API C++ qui permet une interaction plus
directe entre JS et native.

Comparé à l’ancien bridge :

1. Réduit la messagerie asynchrone JSON coûteuse.
2. Permet des appels avec moins d’overhead et des intégrations runtime partagées.
3. Supporte des features de nouvelle architecture comme TurboModules/Fabric.

Cela réduit fortement les goulots d’étranglement de communication.

**En bref**

JSI réduit l’overhead du bridge legacy grâce à une interaction JS-native plus directe.

</details>

<details>
<summary>40. Qu’est-ce que le mode Bridgeless en React Native ?</summary>

#### React Native

Le mode Bridgeless est une direction d’architecture où RN fonctionne sans le
chemin runtime du bridge legacy.

Avantages :

1. Moins d’overhead de communication.
2. Modèle runtime plus propre et moderne.
3. Meilleur alignement avec Fabric, TurboModules et JSI.

Il fait partie de l’évolution long terme de RN vers plus de performance et de
maintenabilité.

**En bref**

Bridgeless retire la dépendance à l’ancien bridge pour un runtime plus propre et performant.

</details>

<details>
<summary>41. Comment React Native atteint-il des performances proches du natif ?</summary>

#### React Native

React Native atteint des performances proches du natif en rendant de vrais
composants UI natifs et en optimisant le travail entre couches JavaScript et
native.

Raisons clés :

1. L’UI est rendue avec des vues natives (`UIView`, `android.view`) plutôt que
   dans une web view.
2. Les updates déclaratifs de React réduisent le travail UI inutile.
3. Hermes peut améliorer le temps de démarrage et l’usage mémoire.
4. La New Architecture (Fabric, TurboModules, JSI) réduit l’overhead du bridge.
5. Les composants de listes optimisés (`FlatList`, `SectionList`) supportent la virtualisation.

La performance dépend aussi du design de l’app : JS lourd, rendus non optimisés
et grosses images peuvent ralentir l’expérience.

**En bref**

RN paraît natif quand les chemins de rendu sont optimisés et la charge JS maîtrisée.

</details>

<details>
<summary>42. Que sont les Native Modules et quand faut-il les utiliser ?</summary>

#### React Native

Les Native Modules sont des modules spécifiques plateforme (iOS/Android)
exposant des fonctionnalités natives à JavaScript.

À utiliser quand :

1. Tu as besoin d’APIs absentes du core/community React Native.
2. Tu dois accéder plus profondément aux capacités device/plateforme.
3. Tu veux de meilleures performances pour une logique qui doit tourner côté natif.

Exemples :

1. Fonctions avancées caméra ou Bluetooth.
2. Intégration de SDKs propriétaires (paiements, biométrie, analytics).
3. Services background spécifiques OS.

S’il existe un package communautaire maintenu, préfère-le d’abord. Écris un
module custom quand les besoins sont vraiment spécifiques.

**En bref**

Utilise des modules natifs quand les APIs de plateforme ne sont pas couvertes par les solutions standard.

</details>

<details>
<summary>43. Comment écrire du code natif pour React Native (Swift/Kotlin) ?</summary>

#### React Native

Tu écris du code natif en créant un module iOS (Swift/Objective-C) et/ou
Android (Kotlin/Java), puis en exposant méthodes/événements à JavaScript.

Flux global :

1. Créer une classe de module natif sur chaque plateforme.
2. Exporter méthodes/constantes/événements vers React Native.
3. Enregistrer le module dans le projet natif.
4. Appeler le module depuis JavaScript/TypeScript.

Exemple minimal côté JS :

```jsx
import { NativeModules } from 'react-native';

const { DeviceInfoModule } = NativeModules;

async function loadDeviceName() {
  const name = await DeviceInfoModule.getDeviceName();
  return name;
}
```

En RN moderne, privilégie les patterns TurboModules/Codegen pour la
compatibilité long terme.

**En bref**

Expose des capacités natives via des modules, puis appelle-les depuis JS avec des interfaces claires.

</details>

<details>
<summary>44. Comment intégrer React Native dans une app native existante ?</summary>

#### React Native

Tu peux embarquer React Native comme une feature dans une app iOS/Android
existante, au lieu de réécrire toute l’application.

Approche typique :

1. Ajouter les dépendances React Native aux projets natifs.
2. Configurer le bundle et le runtime RN.
3. Lancer une root view/un écran RN depuis la navigation native.
4. Échanger des données entre native et RN via props, events ou modules.

Cas d’usage courants :

1. Construire un module cross-platform (ex. settings/profil) dans une app sinon native.
2. Migrer des écrans legacy de manière incrémentale.

Cette stratégie réduit le risque de migration et permet une adoption progressive
de RN.

**En bref**

Intègre RN écran par écran pour moderniser progressivement sans réécriture totale.

</details>

<details>
<summary>45. Comment gérer du code spécifique plateforme (Platform API) ?</summary>

#### React Native

Le comportement spécifique plateforme se gère avec l’API `Platform` et les
extensions de fichiers par plateforme.

Techniques principales :

1. Checks runtime avec `Platform.OS` (`ios`, `android`).
2. Sélecteurs plateforme via `Platform.select(...)`.
3. Fichiers séparés par extension : `Component.ios.tsx` et
   `Component.android.tsx`.

Exemple :

```jsx
import { Platform, Text } from 'react-native';

const label = Platform.select({
  ios: 'Hello iOS',
  android: 'Hello Android',
  default: 'Hello',
});

function Screen() {
  return <Text>{label}</Text>;
}
```

L’idéal est de partager le plus possible la logique et d’isoler seulement les
différences nécessaires.

**En bref**

Gère les écarts via `Platform` ou fichiers dédiés, tout en gardant un maximum de logique partagée.

</details>

<details>
<summary>46. Comment construire des composants pour les différences iOS/Android ?</summary>

#### React Native

Construis une logique cœur partagée et isole l’UI/comportement spécifique
plateforme uniquement là où c’est nécessaire.

Techniques :

1. `Platform.OS` / `Platform.select`.
2. Fichiers `Component.ios.tsx` et `Component.android.tsx`.
3. Tokens de design system avec overrides par plateforme.

Garde la divergence minimale pour réduire le coût de maintenance.

**En bref**

Garde un contrat de composant commun et isole seulement le comportement spécifique plateforme.

</details>

<details>
<summary>47. Comment gères-tu les gestes en React Native ?</summary>

#### React Native

Utilise des librairies orientées gestes pour des interactions fiables et
performantes.

Approche courante :

1. `react-native-gesture-handler` pour la reconnaissance des gestes.
2. `react-native-reanimated` pour des animations fluides pilotées par geste.
3. Composer handlers tap, pan, fling et pinch selon les besoins de l’écran.

Évite le travail JS lourd dans les callbacks de gestes actifs.

**En bref**

Associe Gesture Handler et Reanimated pour une UX gestuelle fluide de niveau production.

</details>

<details>
<summary>48. Qu’est-ce que PanResponder et quand l’utiliser ?</summary>

#### React Native

`PanResponder` est le gestionnaire de gestes intégré à RN pour traiter les
mouvements tactiles.

À utiliser quand :

1. Les besoins de gestes sont simples.
2. Tu veux zéro dépendance supplémentaire.

Pour des gestes complexes et très performants, préfère souvent Gesture Handler + Reanimated.

**En bref**

PanResponder convient aux gestes simples ; pour des interactions complexes, le stack moderne est préférable.

</details>

<details>
<summary>49. Quelles librairies utiliser pour les gestes (Gesture Handler, Reanimated) ?</summary>

#### React Native

Stack de gestes le plus courant :

1. `react-native-gesture-handler` pour une reconnaissance robuste.
2. `react-native-reanimated` pour des animations performantes et les worklets.

Elles sont souvent utilisées ensemble pour une UX gestuelle de qualité
production.

**En bref**

Gesture Handler détecte les gestes de façon robuste, Reanimated les anime de façon fluide.

</details>

<details>
<summary>50. Qu’est-ce que Reanimated et pourquoi l’utiliser ?</summary>

#### React Native

Reanimated est une librairie d’animation haute performance pour RN.

Pourquoi l’utiliser :

1. Animations plus fluides avec moins de jank.
2. Transitions pilotées par gestes.
3. Exécution efficace de la logique d’animation (worklets/modèle proche UI thread).
4. Très utile pour des interactions complexes (bottom sheets, shared transitions, etc.).

**En bref**

Reanimated est le choix standard pour des animations avancées et performantes en RN moderne.

</details>

<details>
<summary>51. Qu’est-ce que l’API Animated et comment fonctionne-t-elle ?</summary>

#### React Native

`Animated` est le système d’animation intégré de React Native pour créer des
transitions UI fluides en animant des valeurs dans le temps.

Fonctionnement :

1. Créer une valeur animée (`new Animated.Value(0)`).
2. Lier cette valeur à des propriétés de style (`opacity`, `transform`, etc.).
3. Démarrer des animations avec `Animated.timing`, `spring` ou `decay`.

Exemple :

```jsx
import React, { useRef } from 'react';
import { Animated, Button } from 'react-native';

function FadeInBox() {
  const opacity = useRef(new Animated.Value(0)).current;

  const start = () => {
    Animated.timing(opacity, {
      toValue: 1,
      duration: 400,
      useNativeDriver: true,
    }).start();
  };

  return (
    <>
      <Animated.View
        style={{ opacity, width: 120, height: 120, backgroundColor: 'tomato' }}
      />
      <Button title="Fade in" onPress={start} />
    </>
  );
}
```

**En bref**

Animated gère les transitions basées sur des valeurs ; utilise le native driver quand il est supporté.

</details>

<details>
<summary>52. Quelle est la différence entre animations déclaratives et impératives ?</summary>

#### React Native

La différence tient à la façon de décrire et contrôler le comportement de
l’animation.

1. **Animations déclaratives** : on définit l’état UI cible et les transitions
   à haut niveau ; le framework gère l’exécution.

2. **Animations impératives** : on contrôle manuellement le cycle d’animation
   étape par étape (start, stop, update).

En React Native :

1. `LayoutAnimation` et de nombreux patterns Reanimated sont plus déclaratifs.
2. `Animated.Value` avec orchestration directe via `.start()` est plus impératif.

Les approches déclaratives sont souvent plus maintenables ; l’impératif donne un
contrôle fin pour des séquences complexes.

**En bref**

Le déclaratif décrit le résultat visé ; l’impératif pilote manuellement chaque étape.

</details>

<details>
<summary>53. Comment implémenter des animations fluides ?</summary>

#### React Native

Pour garder des animations fluides, réduis le travail sur le thread principal et
évite les rerenders coûteux pendant le mouvement.

Bonnes pratiques :

1. Préférer `useNativeDriver: true` quand c’est supporté.
2. Favoriser `transform` et `opacity` plutôt que des propriétés de layout lourdes.
3. Isoler/mémoïser les composants animés quand c’est pertinent.
4. Éviter les calculs lourds pendant gestes/animations.
5. Utiliser `react-native-reanimated` pour des interactions avancées performantes.
6. Optimiser les grosses listes/images animées à l’écran.

Teste toujours sur des appareils réels milieu de gamme, pas seulement en
émulateur/simulateur.

**En bref**

Priorise `transform`/`opacity` et limite la charge JS pendant les interactions actives.

</details>

<details>
<summary>54. Qu’est-ce que LayoutAnimation et quand l’utiliser ?</summary>

#### React Native

`LayoutAnimation` anime les changements globaux de layout (position/taille) lors
de l’ajout, suppression ou redimensionnement de vues.

Quand l’utiliser :

1. Sections qui s’ouvrent/se ferment.
2. Insertion/suppression de lignes de liste avec transitions simples.
3. Updates UI où tu veux une interpolation automatique du layout.

Exemple :

```jsx
import { LayoutAnimation, UIManager, Platform } from 'react-native';

if (
  Platform.OS === 'android' &&
  UIManager.setLayoutAnimationEnabledExperimental
) {
  UIManager.setLayoutAnimationEnabledExperimental(true);
}

LayoutAnimation.configureNext(LayoutAnimation.Presets.easeInEaseOut);
setExpanded(prev => !prev);
```

Utilise-le pour des transitions de layout simples ; pour des animations
complexes pilotées par gestes, Reanimated est souvent plus adapté.

**En bref**

Parfait pour des changements de layout simples (expand/collapse), pas pour des chorégraphies avancées.

</details>

<details>
<summary>55. Comment gérer les safe areas (SafeAreaView) ?</summary>

#### React Native

Les safe areas empêchent le contenu de chevaucher encoches, coins arrondis et
barres système.

Approche recommandée :

1. Utiliser `react-native-safe-area-context`.
2. Envelopper la racine de l’app avec `SafeAreaProvider`.
3. Utiliser `SafeAreaView` ou `useSafeAreaInsets()` dans les écrans/composants.

Exemple :

```jsx
import { SafeAreaProvider, SafeAreaView } from 'react-native-safe-area-context';

function App() {
  return (
    <SafeAreaProvider>
      <SafeAreaView style={{ flex: 1 }}>{/* screen content */}</SafeAreaView>
    </SafeAreaProvider>
  );
}
```

Cela garantit un espacement cohérent entre appareils iOS et Android.

**En bref**

Utilise safe-area context pour garder le contenu visible autour de l’encoche et de l’UI système.

</details>

<details>
<summary>56. Comment gérer les changements d’orientation du device ?</summary>

#### React Native

On gère l’orientation en écoutant les changements de dimensions/orientation et
en adaptant le layout en conséquence.

Options :

1. `useWindowDimensions()` pour recalcul responsive.
2. Librairies d’orientation pour lock/listen explicites.
3. Config native plateforme si la rotation doit être restreinte.

Teste toujours les transitions portrait/landscape sur appareils réels.

**En bref**

Réagis aux changements dimension/orientation et adapte le layout sans dégrader l’usage.

</details>

<details>
<summary>57. Qu’est-ce que PixelRatio et quand est-ce utile ?</summary>

#### React Native

`PixelRatio` fournit des utilitaires liés à la densité de pixels du device.

Utile pour :

1. Scaler les assets UI sur écrans haute densité.
2. Arrondir les tailles de layout pour éviter le flou.
3. Charger des images à la bonne taille.

Cela aide à obtenir des visuels plus nets et cohérents entre appareils.

**En bref**

Utilise PixelRatio pour des visuels nets et des choix de taille/image adaptés à la densité.

</details>

<details>
<summary>58. Comment implémenter des polices personnalisées ?</summary>

#### React Native

Les polices custom s’ajoutent comme assets de l’app puis se référencent via
`fontFamily`.

Étapes typiques :

1. Ajouter les fichiers de police (`.ttf`/`.otf`) aux assets.
2. Configurer le linking (RN CLI ou config Expo).
3. Utiliser les noms de police dans les styles.
4. Sous Expo, charger les polices avant rendu avec `expo-font`.

Garde une échelle typographique et une stratégie fallback pour la cohérence.

**En bref**

Charge les polices comme assets et applique un système typographique cohérent sur tous les écrans.

</details>

<details>
<summary>59. Comment gérer l’accessibilité en React Native ?</summary>

#### React Native

L’accessibilité doit être intégrée dès le départ dans les composants.

Pratiques clés :

1. Ajouter des labels/hints accessibles.
2. Utiliser des rôles/états sémantiques.
3. Garantir un contraste suffisant et des zones tactiles adaptées.
4. Supporter l’agrandissement dynamique du texte.
5. Tester avec VoiceOver (iOS) et TalkBack (Android).

L’accessibilité améliore l’UX pour tous les utilisateurs, pas seulement ceux
qui utilisent des aides techniques.

**En bref**

Traite l’accessibilité comme une qualité de base : labels, rôles, état, contraste et tests lecteurs d’écran.

</details>

<details>
<summary>60. Que sont AccessibilityRole et AccessibilityState ?</summary>

#### React Native

`accessibilityRole` décrit ce qu’est un élément (button, header, link, etc.).
`accessibilityState` décrit son état actuel (disabled, selected, checked, busy,
expanded).

Ils aident les lecteurs d’écran à annoncer un contexte pertinent pour les
éléments interactifs.

Exemple :

```jsx
<Pressable
  accessibilityRole="button"
  accessibilityState={{ disabled: isDisabled }}
>
  <Text>Submit</Text>
</Pressable>
```

**En bref**

`Role` décrit le type d’élément, `State` décrit son état interactif courant.

</details>

<details>
<summary>61. Comment gérer les push notifications ?</summary>

#### React Native

Les push notifications s’implémentent en général avec des services plateforme
plus une librairie RN.

Setup courant :

1. Choisir le provider : Firebase Cloud Messaging (FCM), APNs (iOS), ou un
   service comme OneSignal.
2. Configurer permissions et tokens natifs (token APNs / token FCM).
3. Enregistrer des listeners pour notifications foreground, background et ouvertes.
4. Gérer deep links/navigation quand l’utilisateur touche la notification.

Librairies typiques :

1. `@react-native-firebase/messaging` pour FCM.
2. `notifee` pour un handling local/distant plus riche.

Bonne pratique : payloads petits, endpoints sécurisés et gestion du refresh token.

**En bref**

Couvre inscription des tokens, flow des permissions, gestion foreground/background et navigation au tap.

</details>

<details>
<summary>62. Comment implémenter des tâches en background ?</summary>

#### React Native

Les tâches en background dépendent des limites plateforme et du type de tâche
(sync, location, uploads, notifications).

Approches :

1. Utiliser des APIs background natives via des librairies.
2. Planifier des jobs périodiques pour du travail léger.
3. Utiliser des headless tasks sur Android quand l’app est terminée/en arrière-plan.

Outils courants :

1. `react-native-background-fetch` pour des fetchs périodiques.
2. Handlers background de `@react-native-firebase/messaging` pour du travail déclenché par push.
3. Services/workers natifs pour des scénarios avancés.

Important : iOS et Android appliquent des politiques batterie strictes ; le
background n’est jamais garanti à un timing exact.

**En bref**

Le background est contraint par la plateforme : vise la fiabilité plutôt qu’un timing précis.

</details>

<details>
<summary>63. Comment gérer le mode offline et la synchronisation des données ?</summary>

#### React Native

Le mode offline repose sur des données local-first puis une synchro quand la
connectivité revient.

Stratégie cœur :

1. Persister les données localement (AsyncStorage, SQLite, Realm, etc.).
2. Mettre en file les opérations d’écriture hors ligne.
3. Détecter les changements de connectivité.
4. Rejouer la file et résoudre les conflits à la reconnexion.

Pratiques recommandées :

1. Concevoir des opérations API idempotentes quand possible.
2. Utiliser timestamps/versioning pour la résolution de conflits.
3. Afficher un statut UI clair : offline, syncing, failed, synced.
4. Garder une politique retry/backoff pour éviter les tempêtes de requêtes.

**En bref**

Utilise une approche local-first avec file d’écriture et synchro avec gestion des conflits.

</details>

<details>
<summary>64. Comment implémenter des stratégies de cache ?</summary>

#### React Native

Le cache réduit la latence, l’usage réseau et les recalculs.

Couches de cache courantes :

1. **Cache de réponse API** : mémoire + persistant.
2. **Cache image** : librairies optimisées ou headers HTTP de cache.
3. **Cache de données calculées** : memoization (`useMemo`) pour valeurs coûteuses.
4. **Cache de requêtes** : librairies type React Query/Apollo avec cache normalisé.

Règles pratiques :

1. Définir TTL/règles d’invalidation par ressource.
2. Utiliser stale-while-revalidate pour une UI réactive.
3. Vider le cache au logout ou changement de contexte auth.
4. Éviter une croissance illimitée du cache.

**En bref**

Définis périmètre et invalidation du cache ; stale-while-revalidate donne souvent le meilleur compromis UX.

</details>

<details>
<summary>65. Qu’est-ce que GraphQL et comment l’utiliser en React Native ?</summary>

#### React Native

GraphQL est un langage de requête et un runtime pour API qui permet aux clients
de demander exactement les données nécessaires via un endpoint unique.

Pourquoi c’est utile en React Native :

1. Réduit over-fetching/under-fetching.
2. S’aligne bien avec les besoins de données par écran.
3. Fonctionne avec de bons patterns de cache côté client.

Comment l’utiliser :

1. Définir queries/mutations/subscriptions GraphQL.
2. Utiliser une librairie cliente (le plus souvent Apollo Client).
3. Exécuter les opérations dans hooks/composants.
4. Gérer loading, erreurs et mises à jour de cache.

Petit exemple de shape :

```graphql
query GetUser($id: ID!) {
  user(id: $id) {
    id
    name
    avatar
  }
}
```

**En bref**

GraphQL permet de demander exactement les champs utiles sur mobile, en limitant l’over-fetching.

</details>

<details>
<summary>66. Qu’est-ce qu’Apollo Client et quand faut-il l’utiliser ?</summary>

#### React Native

Apollo Client est un client GraphQL populaire pour exécuter queries/mutations/
subscriptions et gérer un cache normalisé.

À utiliser quand :

1. L’app repose fortement sur des APIs GraphQL.
2. Tu as besoin de fonctionnalités de cache solides et d’outils d’update.
3. Tu veux des patterns GraphQL cohérents entre écrans.

Pour des apps majoritairement REST, des alternatives plus légères peuvent être
plus simples.

**En bref**

Utilise Apollo quand cache GraphQL et état client normalisé sont des besoins centraux.

</details>

<details>
<summary>67. Qu’est-ce que NetInfo et comment l’utiliser ?</summary>

#### React Native

`@react-native-community/netinfo` fournit l’état de connectivité réseau.

Cas d’usage :

1. Détecter les transitions offline/online.
2. Désactiver ou mettre en file les actions réseau hors ligne.
3. Déclencher sync/retry quand la connexion revient.

C’est une brique essentielle pour une UX offline-first robuste.

**En bref**

NetInfo suit la connectivité pour piloter les requêtes et relancer intelligemment.

</details>

<details>
<summary>68. Comment gérer les mises à jour temps réel (WebSockets, subscriptions) ?</summary>

#### React Native

Les mises à jour temps réel se gèrent généralement via WebSockets ou
subscriptions GraphQL.

Pattern :

1. Ouvrir une connexion persistante.
2. S’abonner à des canaux/événements spécifiques.
3. Fusionner les événements entrants dans le state local/global.
4. Reconnecter avec backoff en cas de coupure.

Gère aussi lifecycle app et changements réseau pour éviter des sockets obsolètes.

**En bref**

Maintiens des canaux persistants, réconcilie les événements dans le state, et gère reconnect/backoff.

</details>

<details>
<summary>69. Quels sont les outils de test courants (Jest, Detox) ?</summary>

#### React Native

Stack de test courant :

1. **Jest** : tests unitaires et d’intégration.
2. **React Native Testing Library** : tests d’interaction de composants.
3. **Detox** : tests UI end-to-end sur émulateur/simulateur/device.
4. **ESLint/TypeScript en CI** : checks statiques de correction.

Combiner ces couches donne une couverture plus fiable.

**En bref**

Adopte un testing en couches : Jest pour logique/composants, Detox pour flux end-to-end complets.

</details>

<details>
<summary>70. Comment écrire des tests unitaires en React Native ?</summary>

#### React Native

Les tests unitaires se font généralement avec Jest (+ Testing Library pour les
composants).

Étapes générales :

1. Arrange : préparer entrées composant/fonction.
2. Act : exécuter rendu ou comportement.
3. Assert : vérifier sorties/état/callbacks attendus.

De bons tests unitaires sont isolés, déterministes et rapides.

**En bref**

De bons tests unitaires sont rapides et déterministes, et valident le comportement plutôt que l’implémentation.

</details>

<details>
<summary>71. Comment réaliser des tests end-to-end ?</summary>

#### React Native

Les tests end-to-end (E2E) valident des parcours utilisateur complets dans un
environnement réel ou simulé, incluant UI, navigation et intégration backend.

Processus typique :

1. Lancer l’app en mode test.
2. Interagir avec l’UI comme un utilisateur (tap, saisie, scroll).
3. Vérifier les résultats visibles et l’état de navigation.
4. Exécuter les tests en CI sur plusieurs devices/configurations.

L’outil E2E RN le plus courant est **Detox**.

Bonnes pratiques :

1. Ajouter des `testID` stables sur les éléments importants.
2. Garder les tests déterministes (contrôler réseau/données si possible).
3. Prioriser d’abord les user journeys critiques (auth, checkout, core flows).

**En bref**

Les tests E2E valident les parcours critiques à travers navigation et intégrations réelles.

</details>

<details>
<summary>72. Quels outils de debugging sont disponibles (Flipper) ?</summary>

#### React Native

Le debugging React Native combine généralement logs runtime, inspection de
composants et diagnostics natifs.

Outils courants :

1. **Flipper** : plugins logs, réseau, inspecteur layout et performance.
2. **React DevTools** : inspection arbre de composants, props, state, hooks.
3. **Logs Metro** : sortie console et warnings/erreurs runtime.
4. **Xcode / Android Studio** : crash logs natifs, logs device, breakpoints.
5. **Support debug Hermes** : profiling/inspection spécifique moteur JS.

Flipper est particulièrement utile comme hub desktop central pour le debugging
JS + natif.

**En bref**

Réponds avec la stack : logs, DevTools/Flipper, et logs natifs pour les problèmes plateforme.

</details>

<details>
<summary>73. Comment profiler la performance en React Native ?</summary>

#### React Native

Le profiling performance permet d’identifier les vrais bottlenecks côté rendu,
exécution JS et charge UI thread.

Méthodes clés :

1. Utiliser React DevTools Profiler pour repérer les rendus coûteux.
2. Utiliser les plugins Flipper pour timings performance/réseau.
3. Mesurer temps de démarrage et latence de transitions sur devices réels.
4. Inspecter le rendu des listes (`FlatList` configs, dropped frames).
5. Profiler la partie native avec Xcode Instruments / Android Profiler.

Points à surveiller :

1. Rerenders inutiles fréquents.
2. Tâches JS longues qui bloquent l’interaction.
3. Travail image/layout lourd sur écrans critiques.

Profile toujours sur des builds proches de la production, pas seulement en debug.

**En bref**

Le profiling sur builds proches prod révèle les vrais bottlenecks à optimiser.

</details>

<details>
<summary>74. Qu’est-ce qu’Expo et quand l’utiliser ?</summary>

#### React Native

Expo est une plateforme et toolchain autour de React Native qui simplifie le
développement, les builds et les updates.

Utilise Expo quand :

1. Tu veux un setup plus rapide et une meilleure productivité.
2. Tu as besoin de features natives courantes via Expo SDK (caméra, notifications, etc.).
3. Tu préfères des workflows build cloud/local simplifiés (EAS).

Expo inclut :

1. Dev tools et runtime.
2. Modules Expo SDK.
3. Tooling de build et submission.
4. Support OTA via les services Expo.

C’est un excellent défaut pour beaucoup d’apps, sauf si tu as besoin de contrôle
natif profond dès le départ.

**En bref**

Expo est idéal pour livrer plus vite avec moins de surcharge de setup natif.

</details>

<details>
<summary>75. Quelle est la différence entre Expo managed workflow et bare workflow ?</summary>

#### React Native

La différence porte sur le niveau de contrôle natif du projet.

1. **Managed workflow** : Expo gère la configuration native. Tu travailles
   surtout en JS/TS et config Expo. Développement plus rapide, moins de maintenance native.

2. **Bare workflow** : tu as des projets natifs iOS/Android complets (proche RN
   “plain”). Plus de contrôle, mais plus de complexité setup/maintenance.

Choisis managed quand vitesse/simplicité priment. Choisis bare quand tu as
besoin de code natif custom ou d’intégration low-level avancée.

**En bref**

Managed favorise la vitesse ; bare favorise le contrôle natif total et la personnalisation.

</details>

<details>
<summary>76. Quels sont les avantages et inconvénients d’Expo ?</summary>

#### React Native

Avantages :

1. Setup de projet rapide et itérations courtes.
2. SDK riche pour des features natives courantes.
3. Pipeline build/update simple avec EAS.
4. Bonne DX pour petites/moyennes équipes.

Inconvénients :

1. Moins de contrôle natif direct en managed workflow.
2. Certains edge cases natifs exigent bare/eject.
3. Dépendance aux choix/outils de l’écosystème Expo.

Expo est excellent pour la productivité, avec des compromis en flexibilité low-level.

**En bref**

Expo améliore DX et vitesse de release, mais une personnalisation native poussée peut nécessiter bare.

</details>

<details>
<summary>77. Comment gérer les builds et le déploiement d’une app ?</summary>

#### React Native

Le pipeline build/deploy inclut généralement :

1. Versioning et changelog.
2. Build CI pour Android/iOS.
3. Tests automatisés et quality gates.
4. Signing et génération d’artefacts.
5. Submission store (Play Console / App Store Connect).
6. Monitoring post-release et plan de rollback.

Les apps Expo utilisent souvent EAS Build/Submit ; les apps bare utilisent
souvent Fastlane/scripts CI.

**En bref**

Traite les releases comme un pipeline : versioning, checks CI, signing, submission, monitoring.

</details>

<details>
<summary>78. Qu’est-ce que le code signing et pourquoi est-ce important ?</summary>

#### React Native

Le code signing vérifie cryptographiquement l’identité et l’intégrité de l’app.

Pourquoi c’est important :

1. Confirme l’authenticité du publisher.
2. Empêche de faire confiance à des binaires altérés.
3. Obligatoire pour la distribution via les stores.

iOS utilise certificats/profils ; Android utilise des keystores.

**En bref**

Le code signing prouve l’authenticité de l’app et reste indispensable pour une distribution fiable.

</details>

<details>
<summary>79. Comment gérer les environnements (dev/staging/prod) ?</summary>

#### React Native

Utilise une configuration d’environnement explicite par cible de build.

Setup courant :

1. Endpoints API et feature flags séparés.
2. Variants/flavors de build (Android) et schemes (iOS).
3. Secrets spécifiques via variables CI sécurisées.
4. Nommage clair des release channels.

Garde la sélection d’environnement déterministe et visible dans le diagnostic app.

**En bref**

Sépare les configs par environnement et garde secrets/configuration hors code source.

</details>

<details>
<summary>80. Qu’est-ce que CodePush / OTA updates et quand l’utiliser ?</summary>

#### React Native

Les OTA updates livrent JavaScript/assets sans release complet en store.

Utile pour :

1. Bugfixes rapides dans la couche JS.
2. Petites mises à jour de contenu/logique.

Limites :

1. Impossible d’updater le code binaire natif.
2. Obligation de respecter les politiques stores.

Utilise l’OTA pour des updates JS incrémentaux et sûrs, pas en remplacement des
releases binaires.

**En bref**

OTA est idéal pour corriger vite du JS ; les changements natifs demandent toujours un binaire store.

</details>

<details>
<summary>81. Quelles sont les bonnes pratiques pour structurer une grande codebase ?</summary>

#### React Native

Pour de gros projets React Native, la structure doit optimiser la
navigabilité, l’ownership par feature et le refactoring long terme.

Approche courante : organisation feature-first :

1. Grouper par domaine/feature (`features/auth`, `features/profile`, etc.).
2. Garder l’UI partagée dans `components/` et les hooks génériques dans `hooks/`.
3. Séparer la couche API/data (`services/`, `api/`, `store/`).
4. Centraliser config/constantes globales (`config/`, `theme/`, `env/`).
5. Définir des frontières claires et des entry points publics par feature.

Il faut aussi imposer la cohérence via linting, formatting, TypeScript et des
conventions d’architecture documentées.

**En bref**

Organise par frontières de features pour garder ownership, réutilisation et refactor gérables.

</details>

<details>
<summary>82. Comment assurer la scalabilité et la maintenabilité ?</summary>

#### React Native

Scalabilité et maintenabilité viennent d’une bonne architecture plus une vraie
discipline de process d’ingénierie.

Pratiques clés :

1. Utiliser des frontières modulaires par feature et des primitives réutilisables.
2. Garder la logique métier hors des composants UI.
3. Utiliser TypeScript pour des refactors plus sûrs.
4. Ajouter des tests automatisés (unit/integration/E2E).
5. Faire respecter la qualité avec ESLint, Prettier, checks CI et code review.
6. Suivre en continu les régressions perf et crash analytics.
7. Documenter les patterns (state, navigation, networking, gestion d’erreurs).

Une codebase scalable est prévisible : les nouvelles features suivent les mêmes
patterns avec peu d’exceptions.

**En bref**

La scalabilité repose sur architecture cohérente, automatisation et standards techniques appliqués.

</details>

<details>
<summary>83. Quelles sont les bonnes pratiques pour gérer des données sensibles ?</summary>

#### React Native

Les données sensibles (tokens, secrets, PII) doivent être protégées en
stockage, transit et logs.

Bonnes pratiques :

1. Ne jamais hardcoder des secrets ni embarquer de clés privées dans l’app.
2. Utiliser un stockage sécurisé (wrappers iOS Keychain / Android Keystore).
3. Utiliser HTTPS/TLS pour tout le trafic API.
4. Minimiser les données sensibles stockées et leur durée de rétention.
5. Masquer les champs sensibles dans logs, analytics et crash reports.
6. Faire rotation des tokens/keys et implémenter la révocation.
7. Ajouter détection jailbreak/root et tamper si le threat model l’exige.

`AsyncStorage` n’est pas adapté aux secrets hautement sensibles.

**En bref**

Stocke les secrets de façon sécurisée, limite leur exposition et évite le stockage non protégé.

</details>

<details>
<summary>84. Comment gérer l’authentification (biométrie, tokens) ?</summary>

#### React Native

L’authentification en React Native combine souvent gestion sécurisée des tokens
et déverrouillage biométrique optionnel pour le confort.

Flux typique :

1. L’utilisateur se connecte (credentials/OAuth/social).
2. Le backend renvoie access + refresh tokens.
3. Stocker les tokens en stockage sécurisé (pas AsyncStorage en clair).
4. Joindre l’access token aux requêtes API.
5. Rafraîchir le token quand l’access token expire.
6. Nettoyer tokens et état de session au logout.

Usage biométrique :

1. Utiliser Face ID / Touch ID / biométrie Android pour réauth locale.
2. Garder un modèle auth serveur basé tokens ; la biométrie protège l’accès local.

Centraliser l’état auth et les interceptors évite la duplication de logique.

**En bref**

Combine un cycle de vie token sécurisé avec biométrie optionnelle pour la réauth locale.

</details>

<details>
<summary>85. Qu’est-ce que react-native-webview et quand l’utiliser ?</summary>

#### React Native

`react-native-webview` est un composant qui rend du contenu web à l’intérieur de
l’app mobile.

Cas d’usage :

1. Afficher des pages web externes ou internes.
2. Intégrer des flows web existants (help center, pages de paiement, docs).
3. Intégrer des modules hybrides quand une réécriture native complète n’est pas nécessaire.

Exemple :

```jsx
import { WebView } from 'react-native-webview';

function DocsScreen() {
  return <WebView source={{ uri: 'https://example.com/docs' }} />;
}
```

À utiliser avec prudence sur les flows critiques : UX, performance, sécurité et
intégration native sont souvent meilleures avec des écrans full native/RN.

**En bref**

WebView convient pour des flows web circonscrits ; pour les parcours cœur, privilégie souvent du natif/RN.

</details>

<details>
<summary>86. Qu’est-ce que react-native-svg et pourquoi est-ce utile ?</summary>

#### React Native

`react-native-svg` fournit des primitives de rendu SVG dans RN.

Pourquoi c’est utile :

1. Graphiques vectoriels indépendants de la résolution.
2. Excellent pour icônes, charts et illustrations.
3. Plus flexible que des assets PNG statiques.

C’est une dépendance standard dans de nombreuses apps orientées design.

**En bref**

Le support SVG permet des icônes/graphismes nets et scalables sur toutes les densités d’écran.

</details>

<details>
<summary>87. Comment implémenter une navigation drawer ?</summary>

#### React Native

On l’implémente généralement avec `@react-navigation/drawer`.

Flux de base :

1. Installer les dépendances du drawer navigator.
2. Créer un `Drawer.Navigator` avec les écrans.
3. Personnaliser le contenu du drawer si besoin.
4. Combiner avec des navigateurs stack/tab.

Garde les routes principales dans le drawer et évite un nesting excessif.

**En bref**

Le drawer est utile pour les sections top-level ; garde une hiérarchie simple et prévisible.

</details>

<details>
<summary>88. Qu’est-ce que la navigation gestuelle ?</summary>

#### React Native

La navigation gestuelle signifie que l’utilisateur navigue via des swipes et
patterns tactiles (back swipe, tab swipe, drawer drag).

Dans RN, elle est généralement portée par React Navigation + Gesture Handler.

Avantages :

1. Interactions avec un ressenti plus natif.
2. Navigation à une main plus rapide dans de nombreux flows.

**En bref**

La navigation gestuelle améliore l’UX mobile quand elle respecte les conventions plateforme.

</details>

<details>
<summary>89. Comment implémenter des shared element transitions ?</summary>

#### React Native

Les shared element transitions animent un élément UI commun entre deux écrans.

Implémentation typique :

1. Utiliser une librairie qui supporte les shared transitions.
2. Assigner des IDs partagés identiques sur source/cible.
3. Configurer le comportement de transition de navigation.

Cela améliore la continuité visuelle des flows liste/détail.

**En bref**

Les shared transitions préservent le contexte visuel entre écran liste et écran détail.

</details>

<details>
<summary>90. Qu’est-ce que le renderer Fabric et quelle différence ?</summary>

#### React Native

Fabric est le nouveau renderer RN dans la New Architecture.

Différences avec le renderer legacy :

1. Meilleure intégration avec les patterns React concurrents.
2. Pipeline de rendu plus efficace.
3. Collaboration étroite avec JSI/TurboModules.
4. Latence plus faible pour certains updates UI.

C’est une pièce centrale de la modernisation de RN.

**En bref**

Fabric améliore l’efficacité du rendu et s’intègre au modèle runtime moderne de RN.

</details>

<details>
<summary>91. Quel est l’avantage de l’architecture TurboModules ?</summary>

#### React Native

Les TurboModules font partie de la New Architecture de React Native et améliorent
la manière dont les modules natifs sont chargés et appelés depuis JavaScript.

Principaux avantages :

1. **Chargement paresseux :** les modules sont initialisés uniquement si nécessaire.
2. **Meilleures performances :** moins de coût au démarrage et moins d’overhead lié au bridge.
3. **Sûreté de typage via codegen :** contrats plus solides entre JS et natif.
4. **Maintenabilité accrue :** interfaces de modules plus claires et intégration native modernisée.

Les TurboModules sont particulièrement utiles dans les grandes apps avec de nombreuses dépendances natives.

**En bref**

Les TurboModules optimisent le démarrage et l’accès natif grâce au lazy loading et à des interfaces typées.

</details>

<details>
<summary>92. Comment gérer les error boundaries dans React Native ?</summary>

#### React Native

Les Error Boundaries capturent les erreurs de rendu dans l’arbre des composants
enfants et évitent que toute l’UI de l’app ne plante.

Dans React Native, elles sont implémentées comme des composants de classe avec :

1. `static getDerivedStateFromError(error)`
2. `componentDidCatch(error, info)`

Exemple :

```jsx
import React from 'react';
import { Text, View } from 'react-native';

class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError() {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    // Envoyer l’erreur vers un service de monitoring
  }

  render() {
    if (this.state.hasError) {
      return (
        <View>
          <Text>Une erreur est survenue.</Text>
        </View>
      );
    }

    return this.props.children;
  }
}
```

Entoure les arbres d’écrans critiques avec des boundaries et remonte les erreurs
vers des outils de monitoring.

**En bref**

Les error boundaries isolent les crashs de rendu et affichent un fallback UI au lieu de casser toute l’app.

</details>

<details>
<summary>93. Comment gérer les erreurs globales ?</summary>

#### React Native

La gestion globale des erreurs couvre les exceptions JS non interceptées, les
rejets de promesses et les crashs natifs.

Stratégie courante :

1. Configurer un gestionnaire global d’erreurs JS.
2. Capturer les rejets de promesses non gérés.
3. Intégrer un outil de crash/error monitoring (par exemple Sentry, Bugsnag).
4. Journaliser le contexte (utilisateur/session/écran) de manière sûre.
5. Afficher un fallback UI si possible et récupérer proprement.

Il faut aussi suivre séparément les crashs natifs via les outils plateforme et les SDK de monitoring.

**En bref**

Capte les échecs JS/natifs non gérés de façon centralisée et remonte assez de contexte pour le debug.

</details>

<details>
<summary>94. Qu’est-ce que AppState et comment l’utiliser ?</summary>

#### React Native

`AppState` permet de détecter si l’app est active, en arrière-plan, ou inactive.

États typiques :

1. `active` : app au premier plan et interactive.
2. `background` : app en exécution en arrière-plan.
3. `inactive` (surtout iOS, état transitoire).

Cas d’usage :

1. Mettre en pause/reprendre timers, vidéo, ou polling.
2. Rafraîchir certaines données au retour au premier plan.
3. Réduire le travail en background pour économiser la batterie.

On s’abonne aux changements d’état via des listeners.

**En bref**

AppState t’aide à adapter le comportement de l’app entre foreground et background.

</details>

<details>
<summary>95. Comment gérer le bouton Retour Android (BackHandler) ?</summary>

#### React Native

Sur Android, `BackHandler` permet d’intercepter l’appui sur le bouton matériel Retour.

Approche typique :

1. Écouter l’événement `hardwareBackPress`.
2. Gérer un comportement custom (fermer modal, revenir dans un flow, demander confirmation de sortie).
3. Retourner `true` pour indiquer que l’événement est géré, `false` pour laisser le comportement par défaut.

Exemple :

```jsx
import { BackHandler } from 'react-native';
import { useEffect } from 'react';

useEffect(() => {
  const sub = BackHandler.addEventListener('hardwareBackPress', () => {
    // custom logic
    return true;
  });

  return () => sub.remove();
}, []);
```

Avec React Navigation, vérifie que la logique custom ne casse pas le comportement de retour attendu.

**En bref**

BackHandler permet de personnaliser l’action du bouton Retour Android tout en gardant une navigation cohérente.

</details>

<details>
<summary>96. Comment optimiser la taille du bundle ?</summary>

#### React Native

L’optimisation du bundle vise à réduire le volume de JS/assets livrés.

Étapes pratiques :

1. Supprimer les dépendances inutilisées.
2. Importer uniquement les modules nécessaires.
3. Compresser/redimensionner les images et médias.
4. Activer la minification et les optimisations de build de production.
5. Isoler les fonctionnalités lourdes quand l’architecture le permet.

Des bundles plus petits améliorent le démarrage et la vitesse de livraison des mises à jour.

**En bref**

Un bundle plus léger accélère le lancement et les updates en réduisant le JS et les assets embarqués.

</details>

<details>
<summary>97. Comment gérer les upgrades de version et les migrations ?</summary>

#### React Native

Les upgrades doivent être progressifs et validés automatiquement.

Processus recommandé :

1. Mettre à niveau par petites étapes.
2. Lire les release notes RN et les breaking changes.
3. Utiliser les helpers/diffs d’upgrade React Native.
4. Exécuter les tests complets sur iOS et Android.
5. Livrer avec monitoring actif et plan de rollback.

Évite les sauts de plusieurs versions d’un coup quand c’est possible.

**En bref**

Fais des upgrades incrémentaux, vérifie les changements cassants, puis valide sur toutes les plateformes.

</details>

<details>
<summary>98. Quelles sont les limites de React Native ?</summary>

#### React Native

Limites fréquentes :

1. Certaines API natives avancées exigent du code natif personnalisé.
2. La qualité des packages de l’écosystème peut varier.
3. Les performances se dégradent avec une mauvaise architecture ou une charge JS trop lourde.
4. Les upgrades et l’outillage natif peuvent être complexes.

Malgré cela, RN reste très efficace pour de nombreuses applications cross-platform.

**En bref**

React Native est productif, mais les cas avancés demandent parfois du natif et une optimisation rigoureuse.

</details>

<details>
<summary>99. Comment implémenter la synchronisation en temps réel ?</summary>

#### React Native

La synchro temps réel combine transport live et mises à jour locales robustes face aux conflits.

Stratégie type :

1. Recevoir les événements via WebSocket/subscriptions.
2. Appliquer des mises à jour optimistes pour les actions utilisateur.
3. Persister l’état local pour la continuité hors ligne.
4. Réconcilier la vérité serveur avec les changements locaux au reconnect.
5. Utiliser du versioning et des règles de résolution de conflits.

Cette approche maintient des données fraîches sans sacrifier la cohérence.

**En bref**

La synchro temps réel repose sur des flux d’événements, une réconciliation fiable et une bonne résilience offline.

</details>

<details>
<summary>100. Comment concevoir une architecture mobile scalable ?</summary>

#### React Native

Une architecture mobile scalable repose sur des frontières claires et des flux prévisibles.

Principes clés :

1. Structure modulaire orientée fonctionnalités.
2. Séparation entre UI, logique métier et couche data.
3. Stratégie d’état explicite (local/global/server state).
4. Patterns cohérents pour navigation, erreurs et réseau.
5. Garde-fous qualité automatisés (tests, lint, CI, monitoring).

L’architecture doit privilégier la vitesse d’évolution long terme, pas seulement la rapidité initiale.

**En bref**

Pense modules, flux de données clairs et conventions techniques applicables à l’échelle de l’équipe.

</details>

**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  React Native <img src="./assets/reactnative.svg" width="40" height="40" />
</h1>

<h2>Die beliebtesten React Native Interviewfragen und Antworten</h2>

<details>
<summary>1. Was ist React Native und worin unterscheidet es sich von React?</summary>

#### React Native

React Native ist ein Open-Source-Framework zur Entwicklung mobiler Anwendungen
mit JavaScript/TypeScript und React.

Wichtigster Unterschied:

1. **React (React.js):** erstellt Web-UIs, die in das Browser-DOM (`div`,
   `span` usw.) gerendert werden.
2. **React Native:** erstellt iOS/Android-Apps, die in native Plattform-
   Komponenten (`View`, `Text`, `Image` usw.) gerendert werden.

Beide nutzen dasselbe Komponentenmodell, props/state und Hooks, zielen aber auf
unterschiedliche Plattformen und Rendering-Layer.

**Kurz gesagt**

React Native ist für mobile Apps mit nativen UI-Komponenten, React für Web-UIs im
DOM.

</details>

<details>
<summary>2. Erkläre das Konzept von JSX in React Native.</summary>

#### React Native

JSX (JavaScript XML) ist eine Syntax-Erweiterung, mit der du UI-Strukturen
innerhalb von JavaScript deklarativ in einem HTML-ähnlichen Stil schreiben kannst.

In React Native wird JSX mit nativen Komponenten verwendet:

```jsx
function Greeting() {
  return <Text>Hello, React Native!</Text>;
}
```

Hinweise:

1. JSX ist kein HTML. Es wird von Babel in JavaScript-Aufrufe umgewandelt.
2. JavaScript-Ausdrücke können in `{}` eingebettet werden.
3. In React Native nutzt JSX native Komponenten (`View`, `Text`) statt Browser-
   Tags (`div`, `p`).

**Kurz gesagt**

JSX ist eine bequeme Schreibweise zur UI-Beschreibung, die React Native auf
native Komponenten abbildet.

</details>

<details>
<summary>3. Wie erstellt man eine funktionale Komponente in React Native?</summary>

#### React Native

Eine funktionale Komponente ist eine JavaScript-Funktion, die JSX zurückgibt.

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

Du kannst auch die Arrow-Function-Syntax verwenden:

```jsx
const ProfileCard = () => (
  <View>
    <Text>Profile</Text>
  </View>
);
```

**Kurz gesagt**

Es ist eine normale Funktion, die JSX zurückgibt, häufig kombiniert mit Hooks
für State und Effekte.

</details>

<details>
<summary>4. Was sind Core Components in React Native (View, Text, Image usw.)?</summary>

#### React Native

Core Components sind eingebaute UI-Bausteine von React Native zum Aufbau mobiler
Oberflächen.

Häufige Core Components:

1. **View:** grundlegender Container für Layout und Styling.
2. **Text:** zeigt Textinhalte an.
3. **Image:** rendert Bilder aus lokalen Assets oder von URLs.
4. **TextInput:** Eingabefeld für Text.
5. **ScrollView:** scrollbarer Container.
6. **FlatList / SectionList:** effizientes Rendering großer Listen.
7. **Pressable / TouchableOpacity:** verarbeitet Touch-Interaktionen.
8. **SafeAreaView:** berücksichtigt sichere Bildschirmbereiche (Notches,
   abgerundete Ecken).

Diese Komponenten werden auf native UI-Elemente unter iOS und Android gemappt.

**Kurz gesagt**

Das sind die zentralen Bausteine von React Native, aus denen die Oberfläche
zusammengesetzt wird.

</details>

<details>
<summary>5. Was sind Props in React Native und wie werden sie verwendet?</summary>

#### React Native

Props (Properties) sind schreibgeschützte Eingabewerte, die von einer
Elternkomponente an eine Kindkomponente übergeben werden.

Sie werden verwendet, um:

1. Daten zu übergeben (Text, Zahlen, Objekte, Arrays).
2. Verhalten zu übergeben (Callback-Funktionen).
3. Wiederverwendbare Komponenten zu konfigurieren.

Beispiel:

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

Hier ist `name` ein Prop, das von `App` an `WelcomeMessage` übergeben wird.

**Kurz gesagt**

Props sind unveränderliche Eingaben, um Daten und Verhalten von oben nach unten
im Komponentenbaum weiterzugeben.

</details>

<details>
<summary>6. Was ist State in React Native und wie wird er mit Hooks verwaltet?</summary>

#### React Native

State sind komponenteneigene Daten, die sich im Laufe der Zeit ändern können und
UI-Updates auslösen.

In funktionalen Komponenten wird State meist mit dem `useState`-Hook verwaltet:

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

Für komplexere Logik kannst du `useReducer` verwenden.

**Kurz gesagt**

State sind veränderliche lokale Daten; mit Hooks aktualisierst du sie
vorhersehbar und löst gezielt Re-Renders aus.

</details>

<details>
<summary>7. Was ist der Unterschied zwischen State und Props?</summary>

#### React Native

`state` und `props` speichern beide Daten für das Rendering, haben aber
unterschiedliche Rollen:

1. **Props:** schreibgeschützte Eingaben, die von Eltern- an Kindkomponenten
   übergeben werden.
2. **State:** interne, veränderliche Daten, die von der Komponente selbst
   verwaltet werden.

Schnellvergleich:

1. **Wem gehören die Daten?** Props: Elternkomponente. State: aktuelle
   Komponente.
2. **Lokal veränderbar?** Props: nein. State: ja, z. B. über `useState`.
3. **Einsatzzweck:** Props: Konfiguration und Datenfluss zwischen Komponenten.
   State: dynamisches UI-Verhalten innerhalb einer Komponente.

**Kurz gesagt**

Der Kernunterschied ist Ownership: Props kommen von außen, State gehört der
Komponente.

</details>

<details>
<summary>8. Wie verarbeitet man Benutzereingaben in React Native?</summary>

#### React Native

Benutzereingaben werden meist über kontrollierte Komponenten verarbeitet,
häufig mit `TextInput` in Kombination mit State.

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

Wichtige Events/Handler:

1. `onChangeText`: aktualisiert den Text im State.
2. `onPress`: verarbeitet Button-/Touch-Aktionen.
3. `onSubmitEditing`: reagiert auf das Absenden über die Tastatur im
   `TextInput`.

**Kurz gesagt**

Bei kontrollierten Inputs liegt der Wert im State und wird über Handler
aktualisiert.

</details>

<details>
<summary>9. Wie stylt man Komponenten in React Native?</summary>

#### React Native

React Native verwendet JavaScript-Objekte für Styles statt CSS-Dateien.

Du kannst Komponenten auf drei gängige Arten stylen:

1. **Inline-Styles** (schnell, lokal):

```jsx
<Text style={{ color: 'blue', fontSize: 18 }}>Hello</Text>
```

2. **`StyleSheet.create`** (für die meisten Fälle empfohlen):

```jsx
const styles = StyleSheet.create({
  title: { color: 'blue', fontSize: 18 },
});
```

3. **Style-Arrays** (bedingt/komponiert):

```jsx
<Text style={[styles.title, isActive && styles.active]}>Hello</Text>
```

Die Syntax ist CSS-ähnlich, aber mit camelCase-Eigenschaften (z. B.
`backgroundColor`, `fontSize`).

**Kurz gesagt**

RN-Styles sind JS-Objekte; zentral definierte Styles verbessern Konsistenz und
Wiederverwendbarkeit.

</details>

<details>
<summary>10. Was ist StyleSheet und wann sollte man es verwenden?</summary>

#### React Native

`StyleSheet` ist ein React-Native-Utility, um Styles strukturiert zu definieren
und zu organisieren.

Beispiel:

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

Wann verwenden:

1. Wenn Styles in mehreren Elementen wiederverwendet werden.
2. Wenn du saubereren, wartbaren Komponentencode willst.
3. Wenn du einen konsistenten, skalierbaren Styling-Ansatz für größere Screens/
   Apps brauchst.

**Kurz gesagt**

StyleSheet ist sinnvoll für saubere, wiederverwendbare Styles und bessere
Wartbarkeit.

</details>

<details>
<summary>11. Erkläre Flexbox und seine Rolle im Layout.</summary>

#### React Native

Flexbox ist das primäre Layout-System in React Native. Es steuert, wie
Komponenten in einem Container dimensioniert, ausgerichtet und verteilt werden.

In React Native unterscheiden sich einige Flexbox-Defaults leicht von Web-CSS:

1. `flexDirection` ist standardmäßig `column`.
2. `alignContent` ist standardmäßig `flex-start`.
3. `flexShrink` ist standardmäßig `0`.

Häufige Eigenschaften:

1. `flex`: legt fest, wie viel Platz ein Element relativ zu Geschwistern
   einnimmt.
2. `flexDirection`: Layout in Zeile oder Spalte.
3. `justifyContent`: Ausrichtung auf der Hauptachse.
4. `alignItems`: Ausrichtung auf der Querachse.
5. `gap` (in modernen RN-Versionen): Abstand zwischen Kind-Elementen.

Beispiel:

```jsx
<View
  style={{ flex: 1, flexDirection: 'row', justifyContent: 'space-between' }}
>
  <View style={{ width: 50, height: 50, backgroundColor: 'red' }} />
  <View style={{ width: 50, height: 50, backgroundColor: 'blue' }} />
</View>
```

**Kurz gesagt**

Flexbox basiert auf Achsenlogik: Hauptachse vs. Querachse plus korrektes
`justify/align`.

</details>

<details>
<summary>12. Wie setzt man Responsive Design in React Native um?</summary>

#### React Native

Responsive Design in React Native entsteht durch die Kombination aus flexiblen
Layouts und gerätebewussten APIs.

Gängige Ansätze:

1. Flexbox (`flex`, `%`, Ausrichtung) statt fester Größen verwenden.
2. `Dimensions` oder `useWindowDimensions()` für Bildschirmgrößen nutzen.
3. `Platform` für plattformspezifische Anpassungen einsetzen.
4. `SafeAreaView` nutzen, um Notches und System-UI zu berücksichtigen.
5. Typografie/Abstände über gemeinsame Konstanten skalieren.

Beispiel:

```jsx
import { useWindowDimensions, View } from 'react-native';

function ResponsiveCard() {
  const { width } = useWindowDimensions();
  const isTablet = width >= 768;

  return <View style={{ padding: isTablet ? 24 : 16 }} />;
}
```

**Kurz gesagt**

In RN bedeutet Responsiveness meist: flexible Layouts + Bildschirmmaße +
Safe-Area-Berücksichtigung.

</details>

<details>
<summary>13. Wie debuggt man eine React-Native-Anwendung?</summary>

#### React Native

Debugging in React Native erfolgt typischerweise mit einer Kombination aus
integrierten und externen Tools.

Wichtige Optionen:

1. **Metro-Logs:** `console.log`, Warnungen und Fehler im Terminal/Output.
2. **React Native Dev Menu:** App neu laden, UI inspizieren, Debug-Tools
   aktivieren.
3. **React DevTools:** Komponentenbaum, Props und Hook-State inspizieren.
4. **Flipper:** Netzwerk-Inspektion, Logs, Layout-Inspektion,
   Performance-Plugins.
5. **Native Tooling:** Xcode (iOS) und Android Studio (Android) für native
   Crashes und Logs.

Best Practice: Probleme mit klaren Schritten reproduzieren, die fehlerhafte
Komponente isolieren und auf iOS und Android verifizieren.

**Kurz gesagt**

Am zuverlässigsten ist ein Tool-Stack aus Logs, DevTools/Flipper und nativen
Logs für plattformspezifische Fehler.

</details>

<details>
<summary>14. Was ist Fast Refresh und wie funktioniert es?</summary>

#### React Native

Fast Refresh ist eine Entwicklungsfunktion, die die App nach Code-Änderungen
sofort aktualisiert und dabei möglichst den Komponenten-State erhält.

So funktioniert es:

1. Du speicherst eine Datei.
2. Metro baut nur betroffene Module neu.
3. React Native injiziert den aktualisierten Code in die laufende App.
4. Die UI aktualisiert sich in den meisten Fällen ohne vollständigen Neustart.

Hinweise:

1. Lokaler State bleibt bei funktionalen Komponenten oft erhalten.
2. Wenn Änderungen die Modulinitialisierung oder Nicht-Komponenten-Exporte
   betreffen, kann React Native breiter neu laden.
3. Es ist ein reines Dev-Feature und kein Produktionsverhalten.

**Kurz gesagt**

Fast Refresh bringt Änderungen schnell ins laufende Build und behält häufig den
lokalen State.

</details>

<details>
<summary>15. Was sind Touchable-Komponenten und wie funktionieren sie?</summary>

#### React Native

Touchable-Komponenten sind interaktive Wrapper, die auf Taps/Presses reagieren.
Damit können Nutzer Aktionen wie Screen-Wechsel, Formular-Submit oder Auswahl
von Elementen auslösen.

Häufige Optionen:

1. `Pressable` (modern und flexibel, in vielen Fällen empfohlen).
2. `TouchableOpacity` (ändert die Opazität beim Drücken).
3. `TouchableHighlight` (zeigt eine Hervorhebung unter dem Kind-Element).
4. `TouchableWithoutFeedback` (ohne visuelles Feedback).

Beispiel:

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

Sie bieten Events wie `onPress`, `onPressIn`, `onPressOut` und `onLongPress`.

**Kurz gesagt**

Das sind UI-Wrapper für Press-Interaktionen; in modernen Projekten ist
`Pressable` oft der Standard.

</details>

<details>
<summary>16. Wie handhabt man Navigation in React Native (React Navigation)?</summary>

#### React Native

Navigation wird in React Native üblicherweise mit `@react-navigation/*`
umgesetzt.

Typisches Setup:

1. React-Navigation-Core und benötigte Navigatoren installieren.
2. Die App mit `NavigationContainer` umschließen.
3. Stack-/Tab-/Drawer-Navigatoren definieren.
4. Mit `navigation.navigate('ScreenName')` navigieren.

Für die meisten Apps ist eine Kombination aus Stack + Tab sinnvoll, mit klar
getypten Routen.

**Kurz gesagt**

Nutze die Komposition aus Stack/Tab/Drawer und halte die Routenstruktur explizit.

</details>

<details>
<summary>17. Welche Rolle hat NavigationContainer?</summary>

#### React Native

`NavigationContainer` ist der Root-Provider, der den Navigationszustand verwaltet
und Navigatoren mit der App-Umgebung verbindet.

Er ist zuständig für:

1. Das Halten des aktuellen Navigationsbaum-Zustands.
2. Die Verarbeitung von Linking/Deep Links.
3. Das Bereitstellen des Navigationskontexts für alle Screens.

Ohne ihn funktioniert React Navigation nicht.

**Kurz gesagt**

Er ist der zentrale Navigationskontext und State-Holder der gesamten App.

</details>

<details>
<summary>18. Wie übergibt man Parameter zwischen Screens?</summary>

#### React Native

Parameter werden über Navigationsmethoden übergeben.

Beispiel:

```jsx
navigation.navigate('Profile', { userId: '42' });
```

Parameter im Ziel-Screen auslesen:

```jsx
const { userId } = route.params;
```

Nutze Params für kleinen Routen-Kontext, nicht für großen/globalen App-State.

**Kurz gesagt**

Übergib kleine Routenparameter via `navigate` und lies sie über `route.params`
aus.

</details>

<details>
<summary>19. Was ist Deep Linking und wie implementiert man es?</summary>

#### React Native

Deep Linking ermöglicht, einen bestimmten App-Screen über eine URL zu öffnen.

Implementierung mit React Navigation:

1. URL-Scheme/Universal Links in nativen Konfigurationen definieren.
2. Das `linking`-Objekt im `NavigationContainer` konfigurieren.
3. URL-Pfade auf Screen-Namen mappen.

So lassen sich z. B. Links wie `myapp://product/123` direkt auf den
Produktscreen öffnen.

**Kurz gesagt**

Deep Linking mappt URLs auf Screens, damit externe Links direkt die passende
Route öffnen.

</details>

<details>
<summary>20. Was sind Keys in Listen und warum sind sie wichtig?</summary>

#### React Native

`key` identifiziert Listenelemente eindeutig für React Reconciliation.

Warum wichtig:

1. React kann gezielt nur geänderte Zeilen aktualisieren.
2. Verhindert fehlerhafte Wiederverwendung von Elementen/State-Bugs.
3. Verbessert Rendering-Performance und Vorhersagbarkeit.

Verwende stabile, eindeutige IDs statt des Array-Index (außer bei statischen
Listen).

**Kurz gesagt**

Stabile, eindeutige Keys vermeiden Listen-Bugs und verbessern die Effizienz beim
UI-Update.

</details>

<details>
<summary>21. Wie rendert man Listen effizient (FlatList, SectionList)?</summary>

#### React Native

Für effizientes Listen-Rendering in React Native solltest du `FlatList` und
`SectionList` bevorzugen, statt große Arrays innerhalb von `ScrollView` zu
mappen.

Warum sie effizient sind:

1. Sie rendern Elemente lazy (nur sichtbare Zeilen + Puffer).
2. Sie recyceln Item-Views und reduzieren den Speicherverbrauch.
3. Sie bieten eingebaute Pagination- und Scroll-Optimierungen.

Einsatzfälle:

1. `FlatList`: eindimensionale Liste ähnlicher Elemente.
2. `SectionList`: gruppierte Liste mit Abschnittsüberschriften.

Einfaches `FlatList`-Beispiel:

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

**Kurz gesagt**

Für große Datenmengen sind virtualisierte Listen die beste Wahl für Speicher-
und Scroll-Performance.

</details>

<details>
<summary>22. Was ist VirtualizedList und wann sollte man sie verwenden?</summary>

#### React Native

`VirtualizedList` ist die Basis-Engine hinter `FlatList` und `SectionList`.
Sie übernimmt windowed rendering für große Datensätze.

Direkter Einsatz ist sinnvoll, wenn:

1. deine Datenquelle kein einfaches Array ist,
2. du volle Kontrolle über `getItem` und `getItemCount` brauchst,
3. `FlatList`/`SectionList`-Abstraktionen nicht ausreichen.

In den meisten Apps sind `FlatList` oder `SectionList` der bessere Start,
weil sie einfacher sind und typische Szenarien abdecken.

**Kurz gesagt**

VirtualizedList direkt nur bei Spezialfällen nutzen; sonst reichen FlatList/
SectionList meist aus.

</details>

<details>
<summary>23. Wie lädt man Daten in React Native (fetch, axios)?</summary>

#### React Native

Daten kannst du mit dem eingebauten `fetch`-API oder mit `axios` laden.

`fetch`-Beispiel:

```jsx
async function loadPosts() {
  const response = await fetch('https://api.example.com/posts');
  if (!response.ok) throw new Error('Request failed');
  return response.json();
}
```

`axios`-Beispiel:

```jsx
import axios from 'axios';

async function loadPosts() {
  const { data } = await axios.get('https://api.example.com/posts');
  return data;
}
```

Typischer Ablauf in einer Komponente:

1. Loading-State starten.
2. Asynchronen Request ausführen.
3. Ergebnis oder Fehler im State speichern.
4. Loading beenden und entsprechend rendern.

**Kurz gesagt**

Wichtig ist ein klarer Request-Lifecycle: loading, success, error und saubere
Fehlerbehandlung.

</details>

<details>
<summary>24. Was sind Best Practices für API-Calls und Error Handling?</summary>

#### React Native

Best Practices für API und Fehlerbehandlung:

1. API-Logik in einer Service-Schicht zentralisieren.
2. Immer Loading-, Success- und Error-States behandeln.
3. Timeouts und Retry-Strategie für temporäre Fehler festlegen.
4. Response-Shape vor Nutzung validieren.
5. Nutzerfreundliche Fehlermeldungen anzeigen (keine rohen Serverfehler).
6. Cancellation (`AbortController`) nutzen, um unmounted Screens nicht zu
   aktualisieren.
7. Auth-Token-Refresh zentral an einer Stelle halten
   (Interceptors/Middleware).

Kurzes Muster:

1. `try` Request.
2. `catch` Netzwerk-/Serverfehler.
3. Auf domänenspezifische Fehler mappen.
4. Technische Details für Debugging/Monitoring loggen.

**Kurz gesagt**

Zentralisierte API-Schicht, konsistentes Error-Mapping und klare Retry/Cancel-
Strategie sind entscheidend.

</details>

<details>
<summary>25. Wie geht man mit Async Storage um (AsyncStorage Community-Paket)?</summary>

#### React Native

`AsyncStorage` ist eine persistente Key-Value-Lösung für leichte Daten wie
Benutzereinstellungen, Flags und einfache Caches.

Grundlegende Nutzung:

```jsx
import AsyncStorage from '@react-native-async-storage/async-storage';

async function saveTheme(theme) {
  await AsyncStorage.setItem('theme', theme);
}

async function loadTheme() {
  return AsyncStorage.getItem('theme');
}
```

Best Practices:

1. Objekte mit `JSON.stringify` / `JSON.parse` serialisieren.
2. Aufrufe in `try/catch` kapseln.
3. Payloads klein halten; nicht als Datenbank verwenden.
4. Schlüssel mit Namespace versehen (z. B. `app:user:token`).
5. Für sensible Daten sichere Speicherlösungen nutzen
   (Keychain/Keystore).

**Kurz gesagt**

AsyncStorage ist gut für leichte Persistenz, aber nicht für Secrets; Daten
serialisieren und Fehler sauber behandeln.

</details>

<details>
<summary>26. Was sind moderne State-Management-Lösungen (Context, Zustand, Redux Toolkit)?</summary>

#### React Native

Die passende Lösung hängt vor allem vom Umfang der App und vom Team ab:

1. **Context API:** geeignet für einfache globale Daten mit wenig Boilerplate.
2. **Zustand:** leichtgewichtig, schnell einzurichten, gute Ergonomie.
3. **Redux Toolkit:** strukturierter Ansatz mit Middleware, DevTools und klaren Mustern für größere Projekte.

Wähle das kleinste Tool, das die tatsächliche Komplexität zuverlässig abdeckt.

**Kurz gesagt**

Bei kleinen Anforderungen reicht Context oft aus, bei wachsender Domänenlogik sind Zustand oder RTK meist die bessere Wahl.

</details>

<details>
<summary>27. Wie verwaltet man globalen State ohne Redux?</summary>

#### React Native

Globaler State lässt sich gut mit Context + Hooks oder mit schlanken Stores wie Zustand/Jotai lösen.

Ein verbreitetes Vorgehen:

1. Provider pro Domäne definieren.
2. Updates in Custom Hooks kapseln.
3. Server-State getrennt halten (z. B. React Query/Apollo).

So bleibt die Architektur klar, ohne den Overhead einer vollständigen Redux-Umgebung.

**Kurz gesagt**

Nutze Context oder leichte Stores plus saubere Hook-Abstraktionen, wenn Redux für dein Szenario zu schwer ist.

</details>

<details>
<summary>28. Was sind React Hooks und welche werden häufig verwendet?</summary>

#### React Native

Hooks sind Funktionen, mit denen Funktionskomponenten State, Side Effects und weitere React-Features verwenden können.

Häufige Hooks:

1. `useState`
2. `useEffect`
3. `useMemo`
4. `useCallback`
5. `useRef`
6. `useContext`
7. `useReducer`

Durch eigene Hooks lässt sich wiederverwendbare Logik sauber aus Komponenten auslagern.

**Kurz gesagt**

Hooks bringen zustandsbehaftete Logik in Funktionskomponenten und fördern Wiederverwendung über Custom Hooks.

</details>

<details>
<summary>29. Was ist useEffect und wie ersetzt es Lifecycle-Methoden?</summary>

#### React Native

`useEffect` führt Side Effects nach dem Rendern aus und kann bei Bedarf Aufräumlogik zurückgeben.

Typische Zuordnung von Klassen-Lifecycle zu Hooks:

1. `componentDidMount` -> `useEffect(..., [])`
2. `componentDidUpdate` -> `useEffect(..., [deps])`
3. `componentWillUnmount` -> Cleanup-Funktion aus `useEffect`

Damit wird Lifecycle-Verhalten in Funktionskomponenten einheitlich abgebildet.

**Kurz gesagt**

Mit `useEffect` steuerst du Effekte und Cleanup über Abhängigkeiten statt über separate Klassenmethoden.

</details>

<details>
<summary>30. Was sind useMemo und useCallback und wann sollte man sie einsetzen?</summary>

#### React Native

`useMemo` zwischenspeichert berechnete Werte, `useCallback` stabilisiert Funktionsreferenzen.

Sinnvoller Einsatz, wenn:

1. Berechnungen teuer sind.
2. stabile Referenzen Child-Re-Renders reduzieren.
3. Werte/Funktionen als Dependencies in anderen Hooks genutzt werden.

Wichtig: nicht pauschal einsetzen, sondern dort, wo Profiling einen echten Nutzen zeigt.

**Kurz gesagt**

`useMemo` und `useCallback` gezielt zur Stabilisierung verwenden, wenn messbare Performancegewinne nötig sind.

</details>

<details>
<summary>31. Was sind Refs und wann sollte man sie verwenden?</summary>

#### React Native

Refs sind veränderbare Referenzen auf Komponenteninstanzen oder native Elemente. Damit kannst du imperative APIs nutzen, ohne Re-Renders auszulösen.

Typische Anwendungsfälle:

1. `TextInput` fokussieren oder Fokus entfernen.
2. Scroll-Methoden auslösen (`scrollToOffset`, `scrollToEnd`).
3. Layout messen (`measure`, `measureInWindow`).
4. Mutable Werte speichern, die keine UI-Aktualisierung triggern sollen.

Beispiel:

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

Nutze Refs für imperative Aktionen, nicht als Ersatz für normalen State/Props-Flow.

**Kurz gesagt**

Refs sind für direkten imperativen Zugriff gedacht (Fokus/Scroll/Messung), nicht für regulären Datenfluss.

</details>

<details>
<summary>32. Wie erstellt man Custom Hooks?</summary>

#### React Native

Ein Custom Hook ist eine wiederverwendbare Funktion mit Präfix `use`, die React Hooks (`useState`, `useEffect` usw.) zu gemeinsamer Logik bündelt.

Regeln:

1. Der Name muss mit `use` beginnen.
2. Hooks nur auf oberster Ebene des Custom Hooks aufrufen.
3. Nur die Werte/Funktionen zurückgeben, die Komponenten brauchen.

Beispiel:

```jsx
import { useEffect, useState } from 'react';

function useOnlineStatus() {
  const [isOnline, setIsOnline] = useState(true);

  useEffect(() => {
    // Hier Netzwerkänderungen abonnieren
    return () => {
      // Hier Abo aufräumen
    };
  }, []);

  return isOnline;
}
```

Custom Hooks verbessern Wiederverwendung, Lesbarkeit und Trennung von Verantwortlichkeiten.

**Kurz gesagt**

Lagere wiederkehrende zustandsbehaftete Logik in `use*`-Funktionen aus, damit Komponenten schlank bleiben.

</details>

<details>
<summary>33. Was bedeutet Performance-Optimierung in React Native?</summary>

#### React Native

Performance-Optimierung heißt in React Native, Render-, JavaScript- und Layout-Overhead zu reduzieren, damit Interaktionen flüssig bleiben (auch auf schwächeren Geräten).

Wichtige Bereiche:

1. Rendering: unnötige Re-Renders vermeiden.
2. Listen: `FlatList`/`SectionList` richtig konfigurieren.
3. JavaScript-Workload: teure Berechnungen aus kritischen Render-Pfaden nehmen.
4. Bilder: korrekt skalieren, komprimieren und cachen.
5. JS-Native-Kommunikation: kostenintensive Cross-Layer-Operationen minimieren.

Ziele sind typischerweise stabile 60 FPS, schneller Start und reaktionsschnelle Touch-Interaktionen.

**Kurz gesagt**

Erst messen, dann gezielt Renderpfade, Listen, Bilder und JS-Hotspots optimieren.

</details>

<details>
<summary>34. Wie vermeidet man unnötige Re-Renders?</summary>

#### React Native

Unnötige Re-Renders vermeidest du, indem Props stabil bleiben und State nur dann aktualisiert wird, wenn es wirklich nötig ist.

Praktische Techniken:

1. `React.memo` für reine Funktionskomponenten nutzen.
2. `useMemo` für teure abgeleitete Werte einsetzen.
3. `useCallback` für stabile Callback-Referenzen verwenden.
4. State möglichst lokal halten.
5. Keine neuen Objekte/Funktionen inline erzeugen, wenn sie tief als Props weitergereicht werden.
6. Große Komponenten in kleinere, fokussierte Teile aufspalten.
7. In Listen stabile Keys verwenden.

Zusätzlich immer profilen (React DevTools/Flipper) und nur echte Bottlenecks optimieren.

**Kurz gesagt**

Stabile Props, lokaler State und selektive Memoisierung senken unnötige Renderkosten effektiv.

</details>

<details>
<summary>35. Was ist Memoization in React Native?</summary>

#### React Native

Memoization ist eine Technik, bei der berechnete Ergebnisse oder Render-Ausgaben zwischengespeichert und wiederverwendet werden, solange sich die Eingaben nicht ändern.

Typische Werkzeuge in React Native:

1. `React.memo`: memoisiert Komponenten-Rendering per Props-Vergleich.
2. `useMemo`: memoisiert berechnete Werte.
3. `useCallback`: memoisiert Funktionsreferenzen.

Beispiel:

```jsx
import React, { useMemo } from 'react';

function Total({ items }) {
  const sum = useMemo(() => {
    return items.reduce((acc, item) => acc + item.price, 0);
  }, [items]);

  return <Text>{sum}</Text>;
}
```

Memoization gezielt einsetzen; übermäßige Nutzung erhöht Komplexität ohne garantierten Nutzen.

**Kurz gesagt**

Memoization verhindert unnötige Neuberechnungen und Re-Renders, wenn Inputs unverändert bleiben.

</details>

<details>
<summary>36. Was ist die Hermes-Engine und warum ist sie wichtig?</summary>

#### React Native

Hermes ist eine JavaScript-Engine, die speziell für React Native optimiert wurde.

Warum sie wichtig ist:

1. Schnellere App-Startzeit.
2. Geringerer Speicherverbrauch auf vielen Geräten.
3. Stabilere und besser vorhersagbare Performance auf Android/iOS.
4. Gute Integration in das RN-Tooling.

Hermes ist in vielen produktiven React-Native-Apps die Standardwahl.

**Kurz gesagt**

Hermes verbessert in vielen RN-Apps vor allem Startverhalten und Speichernutzung.

</details>

<details>
<summary>37. Was ist die neue React-Native-Architektur?</summary>

#### React Native

Die New Architecture modernisiert die internen RN-Mechanismen und basiert auf:

1. Fabric Renderer.
2. TurboModules.
3. JSI (JavaScript Interface).
4. Bridgeless-Ausrichtung.

Ziele sind niedrigere Latenz zwischen JS und Native, bessere Concurrency-Unterstützung und höhere Gesamtperformance.

**Kurz gesagt**

Die neue Architektur kombiniert Fabric, TurboModules und JSI, um Overhead zu senken und besser zu skalieren.

</details>

<details>
<summary>38. Was sind Fabric und TurboModules?</summary>

#### React Native

`Fabric` ist das neue Rendering-System, `TurboModules` sind das moderne Modul-System für native Funktionen.

Gemeinsam ermöglichen sie:

1. Effizientere UI-Aktualisierungen.
2. Schnelleren Zugriff auf native Module.
3. Bessere Typsicherheit durch Codegen.
4. Verbesserte Start- und Laufzeitperformance.

**Kurz gesagt**

Fabric modernisiert das UI-Rendering, TurboModules modernisieren den Zugriff auf native APIs.

</details>

<details>
<summary>39. Was ist JSI und wie ersetzt es die alte Bridge?</summary>

#### React Native

JSI (JavaScript Interface) ist eine C++-Schnittstelle, über die JavaScript und Native deutlich direkter miteinander kommunizieren.

Im Vergleich zur alten Bridge:

1. Weniger schwergewichtiges asynchrones JSON-Messaging.
2. Niedrigerer Overhead bei Aufrufen und Runtime-Integrationen.
3. Grundlage für Features der neuen Architektur wie TurboModules/Fabric.

Dadurch werden Kommunikationsengpässe zwischen den Schichten spürbar reduziert.

**Kurz gesagt**

JSI ersetzt den Bridge-Overhead durch direktere JS-Native-Kommunikation.

</details>

<details>
<summary>40. Was ist der Bridgeless-Modus in React Native?</summary>

#### React Native

Der Bridgeless-Modus ist eine Architektur-Richtung, bei der React Native ohne den Legacy-Bridge-Laufzeitpfad arbeitet.

Vorteile:

1. Weniger Kommunikations-Overhead.
2. Klareres, moderneres Runtime-Modell.
3. Bessere Abstimmung mit Fabric, TurboModules und JSI.

Er ist Teil der langfristigen Entwicklung von RN in Richtung mehr Performance und Wartbarkeit.

**Kurz gesagt**

Bridgeless reduziert die Abhängigkeit von der alten Bridge und verbessert so die moderne Runtime-Basis.

</details>

<details>
<summary>41. Wie erreicht React Native eine nahezu native Performance?</summary>

#### React Native

React Native erreicht eine nahezu native Performance, indem echte native UI-Komponenten gerendert und die Arbeit zwischen JavaScript- und Native-Schicht gezielt optimiert wird.

Wesentliche Gründe:

1. Die UI wird mit nativen Views (`UIView`, `android.view`) statt in einer WebView dargestellt.
2. Das deklarative Update-Modell von React reduziert unnötige UI-Arbeit.
3. Hermes kann Startzeit und Speichernutzung verbessern.
4. Die New Architecture (Fabric, TurboModules, JSI) senkt Bridge-Overhead.
5. Optimierte Listenkomponenten (`FlatList`, `SectionList`) nutzen Virtualisierung.

Die tatsächliche Performance hängt trotzdem vom App-Design ab: schwere JS-Tasks, unoptimierte Re-Renders und große Bilder können die App ausbremsen.

**Kurz gesagt**

React Native wirkt nativ, wenn Renderpfade sauber optimiert und JavaScript-Last kontrolliert werden.

</details>

<details>
<summary>42. Was sind Native Modules und wann sollte man sie verwenden?</summary>

#### React Native

Native Modules sind plattformspezifische iOS/Android-Module, die native Funktionen für JavaScript verfügbar machen.

Du nutzt sie, wenn:

1. benötigte APIs weder im RN-Core noch in Community-Paketen vorhanden sind,
2. tieferer Zugriff auf Geräte-/OS-Funktionen nötig ist,
3. bestimmte Logik aus Performancegründen nativ laufen soll.

Beispiele:

1. Erweiterte Kamera- oder Bluetooth-Features.
2. Integration proprietärer SDKs (Payments, Biometrics, Analytics).
3. Betriebssystemspezifische Hintergrunddienste.

Wenn es ein gepflegtes Community-Paket gibt, ist das meist die bessere erste Option. Eigene Native Modules lohnen sich bei speziellen Anforderungen.

**Kurz gesagt**

Native Modules sind sinnvoll, wenn dir für wichtige Plattformfunktionen keine passende Standardlösung reicht.

</details>

<details>
<summary>43. Wie schreibt man nativen Code für React Native (Swift/Kotlin)?</summary>

#### React Native

Du schreibst nativen Code, indem du auf iOS (Swift/Objective-C) und/oder Android (Kotlin/Java) ein Modul erstellst und Methoden/Events nach JavaScript exponierst.

Typischer Ablauf:

1. Native Modulklasse pro Plattform anlegen.
2. Methoden, Konstanten und Events für React Native exportieren.
3. Modul im nativen Projekt registrieren.
4. Modul aus JavaScript/TypeScript aufrufen.

Minimales JS-Beispiel:

```jsx
import { NativeModules } from 'react-native';

const { DeviceInfoModule } = NativeModules;

async function loadDeviceName() {
  const name = await DeviceInfoModule.getDeviceName();
  return name;
}
```

In modernen RN-Projekten sind TurboModules/Codegen-Patterns für langfristige Kompatibilität meist vorzuziehen.

**Kurz gesagt**

Native Funktionen als Module bereitstellen und dann über klar definierte JS-Schnittstellen nutzen.

</details>

<details>
<summary>44. Wie integriert man React Native in eine bestehende native App?</summary>

#### React Native

React Native kann als einzelnes Feature in eine vorhandene iOS/Android-App eingebettet werden, statt die gesamte Anwendung neu zu schreiben.

Üblicher Ansatz:

1. React-Native-Abhängigkeiten in die nativen Projekte aufnehmen.
2. Bundle und Runtime-Setup für RN einrichten.
3. Einen RN-Root-Screen aus der nativen Navigation starten.
4. Daten über Props, Events oder Module zwischen Native und RN austauschen.

Typische Einsatzfälle:

1. Ein plattformübergreifendes Modul (z. B. Einstellungen/Profil) in einer sonst nativen App.
2. Schrittweise Migration älterer Screens.

So lässt sich das Risiko bei der Modernisierung senken und die Einführung von RN inkrementell steuern.

**Kurz gesagt**

RN lässt sich screenweise integrieren, damit Migration und Modernisierung kontrolliert und schrittweise erfolgen.

</details>

<details>
<summary>45. Wie geht man mit plattformspezifischem Code um (Platform API)?</summary>

#### React Native

Plattformspezifisches Verhalten wird mit der `Platform`-API und plattformspezifischen Dateiendungen umgesetzt.

Haupttechniken:

1. Laufzeitprüfungen mit `Platform.OS` (`ios`, `android`).
2. Plattformauswahl mit `Platform.select(...)`.
3. Dateisplitting über Endungen wie `Component.ios.tsx` und `Component.android.tsx`.

Beispiel:

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

Der beste Weg ist, möglichst viel Logik gemeinsam zu halten und nur notwendige Unterschiede zu isolieren.

**Kurz gesagt**

Nutze Platform-Checks oder plattformspezifische Dateien, aber halte den gemeinsamen Codeanteil so groß wie möglich.

</details>

<details>
<summary>46. Wie baut man Komponenten für Unterschiede zwischen iOS und Android?</summary>

#### React Native

Baue eine gemeinsame Kernlogik und trenne nur die Stellen, an denen sich UI oder Verhalten plattformspezifisch unterscheiden müssen.

Typische Techniken:

1. `Platform.OS` bzw. `Platform.select` verwenden.
2. Dateien nach Plattform aufteilen (`Component.ios.tsx`, `Component.android.tsx`).
3. Design-System-Tokens mit plattformspezifischen Overrides einsetzen.

Halte die Divergenz bewusst klein, damit Wartung und Weiterentwicklung nicht unnötig teuer werden.

**Kurz gesagt**

Ein gemeinsamer Komponentenvertrag plus gezielte Plattform-Overrides ist der robusteste Ansatz.

</details>

<details>
<summary>47. Wie geht man mit Gesten in React Native um?</summary>

#### React Native

Für zuverlässige und performante Interaktionen nutzt man in der Praxis spezialisierte Gesture-Libraries.

Gängiger Stack:

1. `react-native-gesture-handler` für Gestenerkennung.
2. `react-native-reanimated` für flüssige, gestengesteuerte Animationen.
3. Kombination aus Tap-, Pan-, Fling- und Pinch-Handlern je nach Screen-Anforderung.

Wichtig ist, schwere JS-Arbeit während aktiver Gesten zu vermeiden.

**Kurz gesagt**

Für produktionsreife Gesture-UX: Gesture Handler für Erkennung, Reanimated für flüssige Reaktion.

</details>

<details>
<summary>48. Was ist PanResponder und wann sollte man ihn verwenden?</summary>

#### React Native

`PanResponder` ist der eingebaute Gesture-Responder von React Native für Touch-Bewegungen.

Sinnvoll, wenn:

1. Gestenanforderungen einfach sind,
2. möglichst keine zusätzliche Abhängigkeit gewünscht ist.

Für komplexe oder besonders performanzkritische Gesten ist meist die Kombination aus Gesture Handler und Reanimated besser geeignet.

**Kurz gesagt**

PanResponder passt für einfache Fälle; bei anspruchsvollen Gesten ist der moderne Library-Stack meist überlegen.

</details>

<details>
<summary>49. Welche Libraries nutzt man für Gesten (Gesture Handler, Reanimated)?</summary>

#### React Native

Der häufigste Produktions-Stack für Gesten besteht aus:

1. `react-native-gesture-handler` für robuste Gesture-Recognition.
2. `react-native-reanimated` für performante Animationen und Worklets.

Beide werden meist gemeinsam eingesetzt, wenn Interaktionen flüssig und präzise sein müssen.

**Kurz gesagt**

Gesture Handler erkennt Gesten stabil, Reanimated setzt sie performant in Animationen um.

</details>

<details>
<summary>50. Was ist Reanimated und warum wird es verwendet?</summary>

#### React Native

Reanimated ist eine Hochleistungs-Animationsbibliothek für React Native.

Warum sie häufig eingesetzt wird:

1. Flüssigere Animationen mit weniger Ruckeln.
2. Sehr gute Unterstützung für gesture-getriebene Übergänge.
3. Effizientes Ausführen der Animationslogik (Worklets, UI-thread-nahe Verarbeitung).
4. Gut geeignet für komplexe Interaktionen wie Bottom Sheets oder Shared Transitions.

**Kurz gesagt**

Reanimated ist die Standardwahl für anspruchsvolle, performante Animationen in modernen RN-Apps.

</details>

<details>
<summary>51. Was ist die Animated API und wie funktioniert sie?</summary>

#### React Native

`Animated` ist das eingebaute Animationssystem von React Native, mit dem UI-Übergänge über animierte Werte umgesetzt werden.

Funktionsprinzip:

1. Einen animierten Wert erstellen (`new Animated.Value(0)`).
2. Diesen Wert an Style-Properties binden (`opacity`, `transform` usw.).
3. Animationen mit APIs wie `Animated.timing`, `spring` oder `decay` starten.

Beispiel:

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

**Kurz gesagt**

`Animated` arbeitet wertbasiert; mit `useNativeDriver` laufen unterstützte Animationen meist deutlich flüssiger.

</details>

<details>
<summary>52. Was ist der Unterschied zwischen deklarativen und imperativen Animationen?</summary>

#### React Native

Der Unterschied liegt darin, wie die Animation beschrieben und gesteuert wird.

1. **Deklarativ:** Zielzustand und Übergang werden auf höherer Ebene definiert; das Framework übernimmt die Ausführung.
2. **Imperativ:** Der Ablauf wird Schritt für Schritt manuell gesteuert (starten, stoppen, Werte aktualisieren).

In React Native gilt oft:

1. `LayoutAnimation` und viele Reanimated-Muster wirken deklarativ.
2. `Animated.Value` mit explizitem `.start()`-Orchestrieren wirkt eher imperativ.

Deklarative Ansätze sind meist wartbarer, imperative bieten mehr Feinkontrolle für komplexe Sequenzen.

**Kurz gesagt**

Deklarativ beschreibt das gewünschte Ergebnis, imperativ steuert den Ablauf explizit.

</details>

<details>
<summary>53. Wie implementiert man flüssige Animationen?</summary>

#### React Native

Für flüssige Animationen muss Arbeit auf dem Hauptthread reduziert und teure Re-Renders während der Bewegung vermieden werden.

Best Practices:

1. Wenn möglich `useNativeDriver: true` nutzen.
2. `transform` und `opacity` bevorzugen statt layoutlastiger Properties.
3. Animierte Komponenten isolieren und bei Bedarf memoizen.
4. Schwere Berechnungen während Gesten/Animationen vermeiden.
5. Für anspruchsvolle Interaktionen `react-native-reanimated` einsetzen.
6. Große Listen/Bilder optimieren, wenn sie mitanimiert werden.

Immer auf echten Mid-Range-Geräten testen, nicht nur im Emulator/Simulator.

**Kurz gesagt**

Setze auf `transform`/`opacity` und halte JS-Last während aktiver Animation minimal.

</details>

<details>
<summary>54. Was ist LayoutAnimation und wann sollte man es verwenden?</summary>

#### React Native

`LayoutAnimation` animiert globale Layout-Änderungen (Position/Größe), wenn Views eingefügt, entfernt oder in ihrer Größe verändert werden.

Sinnvolle Anwendungsfälle:

1. Bereiche ein- und ausklappen.
2. Listeneinträge mit einfachen Übergängen hinzufügen/entfernen.
3. UI-Updates mit automatischer Layout-Interpolation.

Beispiel:

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

Für einfache Layout-Transitions ist es sehr praktisch; bei komplexen, gesture-getriebenen Abläufen ist Reanimated häufig die bessere Wahl.

**Kurz gesagt**

`LayoutAnimation` eignet sich für einfache Layout-Übergänge, nicht für komplexe Interaktions-Choreografien.

</details>

<details>
<summary>55. Wie geht man mit Safe Areas um (SafeAreaView)?</summary>

#### React Native

Safe Areas verhindern, dass Inhalte mit Notches, abgerundeten Ecken oder Systemleisten überlappen.

Empfohlener Ansatz:

1. `react-native-safe-area-context` verwenden.
2. App-Root mit `SafeAreaProvider` umschließen.
3. In Screens/Komponenten `SafeAreaView` oder `useSafeAreaInsets()` nutzen.

Beispiel:

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

So bleibt das Spacing auf iOS und Android konsistent und Inhalte bleiben sichtbar.

**Kurz gesagt**

Mit Safe-Area-Context stellst du sicher, dass UI-Inhalte nicht von Notches oder System-UI verdeckt werden.

</details>

<details>
<summary>56. Wie geht man mit Änderungen der Geräteausrichtung um?</summary>

#### React Native

Ausrichtungswechsel verarbeitet man, indem man auf Dimensions-/Orientation-Änderungen hört und das Layout dynamisch anpasst.

Optionen:

1. `useWindowDimensions()` für responsive Neuberechnung.
2. Orientation-Libraries zum expliziten Sperren/Abonnieren.
3. Native Plattformkonfiguration, wenn Rotation eingeschränkt werden muss.

Portrait-/Landscape-Übergänge sollten immer auf echten Geräten getestet werden.

**Kurz gesagt**

Reagiere auf Größen- und Ausrichtungsänderungen und passe das Layout ohne UX-Brüche an.

</details>

<details>
<summary>57. Was ist PixelRatio und wann ist es nützlich?</summary>

#### React Native

`PixelRatio` liefert Hilfsfunktionen zur Pixeldichte des Geräts.

Nützlich für:

1. Skalierung von UI-Assets auf hochauflösenden Displays.
2. Runden von Layoutgrößen, um Unschärfe zu vermeiden.
3. Laden passender Bildgrößen je nach Dichte.

Damit werden Darstellungen über verschiedene Geräte hinweg schärfer und konsistenter.

**Kurz gesagt**

`PixelRatio` hilft bei dichtebewusster Skalierung, damit UI und Bilder auf allen Screens klar bleiben.

</details>

<details>
<summary>58. Wie implementiert man benutzerdefinierte Schriftarten?</summary>

#### React Native

Custom Fonts werden als App-Assets eingebunden und anschließend über `fontFamily` verwendet.

Typischer Ablauf:

1. Font-Dateien (`.ttf`/`.otf`) in Assets ablegen.
2. Linking konfigurieren (RN CLI oder Expo-Config).
3. Font-Namen in Styles referenzieren.
4. In Expo Fonts vor dem Rendern mit `expo-font` laden.

Eine konsistente Typografie-Skala plus Fallback-Strategie sorgt für stabile Darstellung.

**Kurz gesagt**

Schriften als Assets einbinden, korrekt laden und konsequent über ein Typografie-System einsetzen.

</details>

<details>
<summary>59. Wie berücksichtigt man Accessibility in React Native?</summary>

#### React Native

Barrierefreiheit sollte von Anfang an Teil der Komponentenentwicklung sein.

Wichtige Maßnahmen:

1. Verständliche Labels und Hinweise setzen.
2. Semantische Rollen und Zustände definieren.
3. Ausreichenden Kontrast und Touch-Zielgrößen sicherstellen.
4. Dynamische Textskalierung unterstützen.
5. Mit VoiceOver (iOS) und TalkBack (Android) testen.

Accessibility verbessert die UX insgesamt, nicht nur für Nutzer mit Assistive Tech.

**Kurz gesagt**

Accessibility ist Basisqualität: klare Labels, korrekte Rollen/Zustände, guter Kontrast und Screen-Reader-Tests.

</details>

<details>
<summary>60. Was sind AccessibilityRole und AccessibilityState?</summary>

#### React Native

`accessibilityRole` beschreibt, was ein Element ist (z. B. Button, Header, Link).
`accessibilityState` beschreibt seinen aktuellen Zustand (z. B. disabled, selected, checked, busy, expanded).

Dadurch können Screen Reader interaktive Elemente mit relevantem Kontext ansagen.

Beispiel:

```jsx
<Pressable
  accessibilityRole="button"
  accessibilityState={{ disabled: isDisabled }}
>
  <Text>Submit</Text>
</Pressable>
```

**Kurz gesagt**

`Role` beschreibt den Elementtyp, `State` den aktuellen Interaktionszustand.

</details>

<details>
<summary>61. Wie handhabt man Push-Benachrichtigungen?</summary>

#### React Native

Push-Notifications werden üblicherweise über Plattformdienste plus RN-Library umgesetzt.

Typisches Setup:

1. Provider wählen: Firebase Cloud Messaging (FCM), APNs (iOS) oder Dienste wie OneSignal.
2. Native Berechtigungen und Tokens konfigurieren (APNs-Token / FCM-Token).
3. Listener für Foreground-, Background- und Opened-Events registrieren.
4. Deep Links/Navigation beim Tippen auf eine Notification verarbeiten.

Häufige Libraries:

1. `@react-native-firebase/messaging` für FCM.
2. `notifee` für erweiterte lokale/remote Notification-Handling-Szenarien.

Best Practice: kleine Payloads, abgesicherte Endpunkte und sauberes Token-Refresh-Handling.

**Kurz gesagt**

Wichtig sind saubere Token-Registrierung, Permission-Flow sowie Foreground/Background- und Tap-Navigation-Handling.

</details>

<details>
<summary>62. Wie implementiert man Background-Tasks?</summary>

#### React Native

Background-Tasks hängen von Plattformgrenzen und Aufgabentyp ab (Sync, Location, Uploads, Notifications).

Ansätze:

1. Native Background-APIs über Libraries nutzen.
2. Periodische Jobs für leichte Aufgaben planen.
3. Auf Android Headless Tasks verwenden, wenn die App beendet/im Hintergrund ist.

Gängige Tools:

1. `react-native-background-fetch` für periodische Fetch-Tasks.
2. `@react-native-firebase/messaging`-Background-Handler für Push-getriggerte Arbeit.
3. Native Services/Worker für komplexere Fälle.

Wichtig: iOS und Android haben strikte Batterie-/Scheduling-Regeln, daher ist exaktes Timing nicht garantiert.

**Kurz gesagt**

Background-Verarbeitung ist plattformbeschränkt; plane auf Zuverlässigkeit statt auf sekundengenaue Ausführung.

</details>

<details>
<summary>63. Wie geht man mit Offline-Modus und Datensynchronisierung um?</summary>

#### React Native

Offline-Fähigkeit basiert auf einem Local-First-Ansatz plus Synchronisierung bei wiederhergestellter Verbindung.

Kernstrategie:

1. Daten lokal persistieren (AsyncStorage, SQLite, Realm usw.).
2. Schreiboperationen im Offline-Zustand in eine Queue legen.
3. Konnektivitätsänderungen erkennen.
4. Queue beim Reconnect erneut ausführen und Konflikte auflösen.

Empfohlene Praktiken:

1. API-Operationen möglichst idempotent gestalten.
2. Timestamps/Versionierung für Conflict Resolution verwenden.
3. Klaren UI-Status anzeigen: offline, syncing, failed, synced.
4. Retry-/Backoff-Policy gegen Request-Stürme einsetzen.

**Kurz gesagt**

Local-First-Speicherung plus Write-Queue und konfliktbewusster Sync macht Offline-UX robust.

</details>

<details>
<summary>64. Wie implementiert man Caching-Strategien?</summary>

#### React Native

Caching reduziert Latenz, Netzwerklast und unnötige Neuberechnungen.

Typische Cache-Ebenen:

1. **API-Response-Cache:** In-Memory plus persistenter Cache.
2. **Image-Cache:** optimierte Image-Libraries oder HTTP-Cache-Header.
3. **Computed-Data-Cache:** Memoization (`useMemo`) für teure Ableitungen.
4. **Request-Cache:** z. B. React Query/Apollo mit normalisierten Caches.

Praktische Regeln:

1. TTL-/Invalidierungsregeln pro Ressource definieren.
2. Stale-while-revalidate-Muster für responsive UI nutzen.
3. Cache bei Logout oder Auth-Kontextwechsel bereinigen.
4. Unbegrenztes Cache-Wachstum vermeiden.

**Kurz gesagt**

Wirksames Caching braucht klare Scopes und Invalidierung; stale-while-revalidate liefert oft die beste UX-Balance.

</details>

<details>
<summary>65. Was ist GraphQL und wie nutzt man es in React Native?</summary>

#### React Native

GraphQL ist eine Query-Sprache plus Runtime für APIs, bei der Clients exakt die Datenfelder anfragen, die sie benötigen.

Warum nützlich in React Native:

1. Reduziert Over-Fetching und Under-Fetching.
2. Passt gut zu screenbasierten Datenanforderungen.
3. Arbeitet gut mit starken Client-Caching-Strategien.

Typische Nutzung:

1. Queries/Mutations/Subscriptions definieren.
2. Client-Library verwenden (meist Apollo Client).
3. Operationen in Hooks/Komponenten ausführen.
4. Loading-, Error- und Cache-Updates behandeln.

Kleines Beispielschema:

```graphql
query GetUser($id: ID!) {
  user(id: $id) {
    id
    name
    avatar
  }
}
```

**Kurz gesagt**

Mit GraphQL fordert der Screen nur benötigte Felder an und minimiert unnötigen Datenverkehr.

</details>

<details>
<summary>66. Was ist Apollo Client und wann sollte man ihn verwenden?</summary>

#### React Native

Apollo Client ist ein verbreiteter GraphQL-Client für Queries, Mutations, Subscriptions und normalisiertes Caching.

Sinnvoll, wenn:

1. die App stark auf GraphQL-APIs aufbaut,
2. leistungsfähige Cache-Mechanismen und Update-Tools benötigt werden,
3. ein einheitliches GraphQL-Muster über viele Screens gewünscht ist.

Für REST-lastige Apps können leichtere Alternativen einfacher sein.

**Kurz gesagt**

Apollo ist ideal, wenn GraphQL plus starker Client-Cache ein zentraler Architekturbaustein ist.

</details>

<details>
<summary>67. Was ist NetInfo und wie verwendet man es?</summary>

#### React Native

`@react-native-community/netinfo` liefert den aktuellen Netzwerkstatus der App.

Typische Einsatzfälle:

1. Offline/Online-Wechsel erkennen.
2. Netzwerkaktionen offline deaktivieren oder in Queue legen.
3. Bei wiederhergestellter Verbindung Sync/Retry auslösen.

NetInfo ist ein zentrales Fundament für zuverlässige Offline-First-UX.

**Kurz gesagt**

NetInfo zeigt Konnektivität an, damit Requests intelligent gesteuert und Wiederholungen gezielt ausgelöst werden können.

</details>

<details>
<summary>68. Wie geht man mit Echtzeit-Updates um (WebSockets, Subscriptions)?</summary>

#### React Native

Echtzeit-Updates werden in der Regel mit WebSockets oder GraphQL-Subscriptions umgesetzt.

Muster:

1. Persistente Verbindung aufbauen.
2. Relevante Channels/Events abonnieren.
3. Eingehende Events in lokalen/globalen State mergen.
4. Bei Verbindungsabbruch mit Backoff reconnecten.

App-Lifecycle und Netzwerkwechsel sollten mitbehandelt werden, damit keine veralteten Sockets bestehen bleiben.

**Kurz gesagt**

Dauerhafte Verbindung halten, Events sauber in State integrieren und Reconnect/Backoff zuverlässig managen.

</details>

<details>
<summary>69. Was sind gängige Test-Tools (Jest, Detox)?</summary>

#### React Native

Ein typischer RN-Teststack besteht aus mehreren Ebenen:

1. **Jest:** Unit- und Integrations-Tests.
2. **React Native Testing Library:** komponentennahe Interaktionstests.
3. **Detox:** End-to-End-Tests auf Emulator/Simulator/Gerät.
4. **ESLint/TypeScript in CI:** statische Qualitäts- und Korrektheitsprüfungen.

Die Kombination dieser Ebenen ergibt eine belastbare Testabdeckung.

**Kurz gesagt**

Beste Abdeckung entsteht schichtweise: Jest für Logik/Komponenten, Detox für reale End-to-End-Flows.

</details>

<details>
<summary>70. Wie schreibt man Unit-Tests in React Native?</summary>

#### React Native

Unit-Tests werden meist mit Jest geschrieben, oft ergänzt durch Testing Library für Komponenten.

Grundablauf:

1. Inputs/Initialzustand vorbereiten (Arrange).
2. Verhalten ausführen (Act).
3. Ergebnis, State oder Callbacks prüfen (Assert).

Gute Unit-Tests sind isoliert, deterministisch und schnell.

**Kurz gesagt**

Fokus auf reproduzierbares Verhalten statt Implementierungsdetails sorgt für stabile Unit-Tests.

</details>

<details>
<summary>71. Wie führt man End-to-End-Tests durch?</summary>

#### React Native

End-to-End-Tests (E2E) prüfen komplette User-Flows in einer realen oder simulierten App-Umgebung inklusive UI, Navigation und Backend-Integration.

Typischer Ablauf:

1. App im Testmodus starten.
2. UI wie ein Nutzer bedienen (tippen, tippen/eingeben, scrollen).
3. Sichtbare Ergebnisse und Navigationszustände validieren.
4. Tests in CI auf mehreren Geräten/Konfigurationen ausführen.

Das gängigste E2E-Tool im RN-Umfeld ist **Detox**.

Best Practices:

1. Stabile `testID`s für wichtige Elemente vergeben.
2. Tests deterministisch halten (Netzwerk/Daten möglichst kontrollieren).
3. Zuerst kritische Journeys absichern (Auth, Checkout, Core-Flows).

**Kurz gesagt**

E2E-Tests validieren geschäftskritische Nutzerpfade über echte Navigations- und Integrationsgrenzen hinweg.

</details>

<details>
<summary>72. Welche Debugging-Tools gibt es (Flipper)?</summary>

#### React Native

Beim React-Native-Debugging kombiniert man typischerweise Runtime-Logs, Komponenteninspektion und native Diagnostik.

Häufige Tools:

1. **Flipper:** Plugins für Logs, Network, Layout-Inspector und Performance.
2. **React DevTools:** Komponentenbaum, Props, State und Hooks inspizieren.
3. **Metro-Logs:** Console-Ausgaben sowie Runtime-Warnungen/Fehler.
4. **Xcode / Android Studio:** native Crash-Logs, Device-Logs, Breakpoints.
5. **Hermes-Debug-Support:** JS-Engine-spezifische Profiling-/Inspection-Funktionen.

Flipper ist besonders hilfreich als zentraler Desktop-Hub für JS- und Native-Debugging.

**Kurz gesagt**

Effektives Debugging kombiniert Flipper/DevTools mit nativen Logs aus Xcode und Android Studio.

</details>

<details>
<summary>73. Wie profiliert man Performance in React Native?</summary>

#### React Native

Performance-Profiling identifiziert reale Bottlenecks bei Rendering, JS-Ausführung und UI-Thread-Last.

Wichtige Methoden:

1. React DevTools Profiler für teure Re-Renders verwenden.
2. Flipper-Plugins für Performance- und Netzwerk-Timings nutzen.
3. Startup-Zeit und Screen-Transition-Latenz auf echten Geräten messen.
4. Listenverhalten analysieren (`FlatList`-Konfiguration, dropped frames).
5. Native Seite mit Xcode Instruments / Android Profiler untersuchen.

Worauf achten:

1. Häufige unnötige Re-Renders.
2. Lange JS-Tasks, die Interaktionen blockieren.
3. Hohe Bild-/Layout-Last auf kritischen Screens.

Immer möglichst release-nahe Builds profilieren, nicht nur Debug-Builds.

**Kurz gesagt**

Nur Profiling auf realistischen Builds zeigt die echten Performance-Probleme, die optimiert werden sollten.

</details>

<details>
<summary>74. Was ist Expo und wann sollte man es verwenden?</summary>

#### React Native

Expo ist eine Plattform samt Toolchain rund um React Native, die Entwicklung, Builds und Updates deutlich vereinfacht.

Sinnvoll, wenn:

1. schnelleres Setup und hohe Entwicklerproduktivität gewünscht sind,
2. häufige Native-Features über Expo SDK benötigt werden (Kamera, Notifications usw.),
3. vereinfachte Cloud-/Local-Build-Workflows (EAS) bevorzugt werden.

Expo umfasst:

1. Dev-Tools und Runtime.
2. Expo-SDK-Module.
3. Build- und Submission-Tooling.
4. OTA-Update-Support über Expo-Services.

Für viele Apps ist Expo ein starker Standard, sofern nicht von Anfang an tiefe Native-Kontrolle nötig ist.

**Kurz gesagt**

Expo ist ideal, wenn du schneller liefern und den nativen Setup-Aufwand minimieren willst.

</details>

<details>
<summary>75. Was ist der Unterschied zwischen Expo Managed und Bare Workflow?</summary>

#### React Native

Der Kernunterschied liegt im Grad der nativen Kontrolle.

1. **Managed Workflow:** Expo verwaltet die native Konfiguration. Du arbeitest primär in JS/TS plus Expo-Config. Schnellere Entwicklung, weniger native Wartung.
2. **Bare Workflow:** Volle iOS/Android-Projekte unter eigener Kontrolle (ähnlich zu plain RN). Mehr Flexibilität, aber auch mehr Setup- und Wartungsaufwand.

Managed passt, wenn Geschwindigkeit und Einfachheit priorisiert werden. Bare ist richtig, wenn eigene Native-Module oder tiefe Low-Level-Integrationen nötig sind.

**Kurz gesagt**

Managed maximiert Geschwindigkeit, Bare maximiert native Kontrolle und Anpassbarkeit.

</details>

<details>
<summary>76. Was sind Vor- und Nachteile von Expo?</summary>

#### React Native

Vorteile:

1. Schnelles Projekt-Setup und kurze Iterationszyklen.
2. Umfangreiches SDK für häufige Native-Features.
3. Einfache Build-/Update-Pipeline mit EAS.
4. Gute Developer Experience für kleine und mittlere Teams.

Nachteile:

1. Weniger direkte Native-Kontrolle im Managed Workflow.
2. Manche Native-Edge-Cases erfordern Bare/Eject.
3. Abhängigkeit von Entscheidungen und Tools im Expo-Ökosystem.

Expo ist sehr produktiv, bringt aber Trade-offs bei tiefer Low-Level-Flexibilität.

**Kurz gesagt**

Expo beschleunigt Entwicklung und Releases, kann bei sehr spezifischer Native-Anpassung jedoch einschränken.

</details>

<details>
<summary>77. Wie handhabt man App-Builds und Deployment?</summary>

#### React Native

Eine typische Build-/Release-Pipeline umfasst:

1. Versionierung und Changelog.
2. CI-Builds für Android/iOS.
3. Automatisierte Tests und Quality Gates.
4. Signing und Artefakt-Erzeugung.
5. Store-Submission (Play Console / App Store Connect).
6. Post-Release-Monitoring und Rollback-Plan.

Expo-Apps nutzen häufig EAS Build/Submit, Bare-Apps oft Fastlane oder CI-Skripte.

**Kurz gesagt**

Releases sollten als klarer Pipeline-Prozess laufen: Versionierung, CI-Checks, Signing, Submission, Monitoring.

</details>

<details>
<summary>78. Was ist Code Signing und warum ist es wichtig?</summary>

#### React Native

Code Signing verifiziert kryptografisch Identität und Integrität einer App.

Warum wichtig:

1. Bestätigt die Echtheit des Publishers.
2. Verhindert, dass manipulierte Binaries als vertrauenswürdig gelten.
3. Ist für die Store-Distribution verpflichtend.

iOS arbeitet mit Zertifikaten/Provisioning-Profilen, Android mit Keystores.

**Kurz gesagt**

Code Signing ist der Nachweis für Authentizität und eine Pflichtvoraussetzung für vertrauenswürdige Verteilung.

</details>

<details>
<summary>79. Wie verwaltet man Umgebungen (dev/staging/prod)?</summary>

#### React Native

Setze je Build-Ziel eine explizite Environment-Konfiguration auf.

Gängiges Setup:

1. Getrennte API-Endpunkte und Feature-Flags.
2. Build-Varianten/Flavors (Android) und Schemes (iOS).
3. Environment-spezifische Secrets über sichere CI-Variablen.
4. Klare Release-Channel-Benennung.

Die Auswahl der Umgebung sollte deterministisch sein und in der App-Diagnostik sichtbar bleiben.

**Kurz gesagt**

Trenne Konfigurationen sauber pro Umgebung und halte Secrets konsequent außerhalb des Quellcodes.

</details>

<details>
<summary>80. Was ist CodePush / OTA-Updates und wann sollte man es nutzen?</summary>

#### React Native

OTA-Updates liefern JavaScript/Assets ohne vollständiges Store-Release aus.

Sinnvoll für:

1. Schnelle Bugfixes in der JS-Schicht.
2. Kleine Inhalts- und Logik-Updates.

Grenzen:

1. Native Binärcode kann damit nicht aktualisiert werden.
2. Store-Richtlinien müssen eingehalten werden.

OTA sollte für sichere inkrementelle JS-Updates genutzt werden, nicht als Ersatz für Binary-Releases.

**Kurz gesagt**

OTA ist ideal für schnelle JS-Korrekturen, während Native-Änderungen weiterhin ein Store-Binary erfordern.

</details>

<details>
<summary>81. Was sind Best Practices für die Strukturierung einer großen Codebase?</summary>

#### React Native

Bei großen React-Native-Projekten sollte die Struktur Auffindbarkeit, Feature-Ownership und langfristiges Refactoring unterstützen.

Ein verbreiteter Ansatz ist feature-first:

1. Nach Domänen/Features gruppieren (`features/auth`, `features/profile` usw.).
2. Gemeinsame UI in `components/`, generische Hooks in `hooks/` halten.
3. API-/Datenebene trennen (`services/`, `api/`, `store/`).
4. App-weite Konfiguration/Konstanten zentralisieren (`config/`, `theme/`, `env/`).
5. Klare Grenzen und öffentliche Entry-Points je Feature definieren.

Zusätzlich sollte Konsistenz per Linting, Formatting, TypeScript und dokumentierten Architekturregeln abgesichert werden.

**Kurz gesagt**

Feature-Grenzen als primäre Struktur machen Ownership, Wiederverwendung und Refactoring deutlich beherrschbarer.

</details>

<details>
<summary>82. Wie stellt man Skalierbarkeit und Wartbarkeit sicher?</summary>

#### React Native

Skalierbarkeit und Wartbarkeit entstehen aus sauberer Architektur plus disziplinierten Engineering-Prozessen.

Wichtige Praktiken:

1. Modulare Feature-Grenzen und wiederverwendbare Primitives nutzen.
2. Business-Logik außerhalb von UI-Komponenten halten.
3. TypeScript für sichere Refactorings einsetzen.
4. Automatisierte Tests auf Unit/Integration/E2E-Ebene einführen.
5. Codequalität mit ESLint, Prettier, CI-Checks und Code-Review durchsetzen.
6. Performance-Regressions und Crash-Analytics kontinuierlich verfolgen.
7. Muster für State, Navigation, Networking und Error Handling dokumentieren.

Eine skalierbare Codebase ist vorhersagbar: neue Features folgen denselben Konventionen mit minimalen Ausnahmen.

**Kurz gesagt**

Skalierung gelingt mit konsistenter Architektur, automatisierten Qualitätsbarrieren und klaren Team-Standards.

</details>

<details>
<summary>83. Was sind Best Practices für den Umgang mit sensiblen Daten?</summary>

#### React Native

Sensible Daten (Tokens, Secrets, PII) müssen in Speicherung, Übertragung und Logs geschützt werden.

Best Practices:

1. Secrets nie im Quellcode hardcoden und keine privaten Keys in der App ausliefern.
2. Sicheren Storage nutzen (iOS Keychain / Android Keystore-Wrapper).
3. Für alle API-Aufrufe HTTPS/TLS verwenden.
4. Gespeicherte sensible Daten und Aufbewahrungsdauer minimieren.
5. Sensitive Felder in Logs, Analytics und Crash-Reports maskieren.
6. Token/Keys rotieren und Widerruf (Revocation) unterstützen.
7. Bei entsprechendem Threat Model Jailbreak/Root- und Tamper-Detection ergänzen.

`AsyncStorage` ist für hochsensible Geheimnisse nicht geeignet.

**Kurz gesagt**

Secrets gehören in sichere Speicherpfade mit minimaler Exposition, niemals in ungeschützte Standardablagen.

</details>

<details>
<summary>84. Wie handhabt man Authentifizierung (Biometrie, Tokens)?</summary>

#### React Native

Authentifizierung kombiniert in RN meist einen sicheren Token-Lifecycle mit optionalem biometrischem Re-Auth für Komfort.

Typischer Ablauf:

1. Nutzer meldet sich an (Credentials/OAuth/Social).
2. Backend liefert Access- und Refresh-Token.
3. Tokens sicher speichern (nicht in plain AsyncStorage).
4. Access-Token an API-Requests anhängen.
5. Bei Ablauf Access-Token über Refresh-Token erneuern.
6. Bei Logout Tokens und Session-State vollständig löschen.

Biometrie-Nutzung:

1. Face ID / Touch ID / Android-Biometrie für lokale Re-Authentifizierung nutzen.
2. Server-Authentifizierung tokenbasiert halten; Biometrie schützt lokalen Zugriff.

Zentraler Auth-State und Request-Interceptor vermeiden doppelte Logik.

**Kurz gesagt**

Ein robuster Auth-Flow braucht sicheren Token-Umgang und optionale Biometrie als lokale Komfortschicht.

</details>

<details>
<summary>85. Was ist react-native-webview und wann sollte man es verwenden?</summary>

#### React Native

`react-native-webview` ist eine Komponente, die Web-Inhalte innerhalb der mobilen App rendert.

Einsatzfälle:

1. Externe oder interne Webseiten anzeigen.
2. Bestehende Web-Flows einbetten (Help Center, Zahlungsseiten, Doku).
3. Hybride Module integrieren, wenn ein kompletter Native-Rewrite nicht nötig ist.

Beispiel:

```jsx
import { WebView } from 'react-native-webview';

function DocsScreen() {
  return <WebView source={{ uri: 'https://example.com/docs' }} />;
}
```

Für kritische Kernflows mit Bedacht nutzen: UX, Performance, Sicherheit und tiefe Native-Integration sind oft mit vollwertigen RN/Native Screens besser.

**Kurz gesagt**

WebView eignet sich für abgegrenzte Web-Inhalte, Kernfunktionen der App sollten meist nativ/RN umgesetzt werden.

</details>

<details>
<summary>86. Was ist react-native-svg und warum ist es nützlich?</summary>

#### React Native

`react-native-svg` stellt in React Native grundlegende SVG-Render-Primitives bereit.

Warum nützlich:

1. Auflösungsunabhängige Vektorgrafiken.
2. Ideal für Icons, Charts und Illustrationen.
3. Flexibler als statische PNG-Assets.

Für viele designintensive Apps ist es eine Standardabhängigkeit.

**Kurz gesagt**

SVG-Support sorgt für scharfe, skalierbare Grafiken über unterschiedliche Displaydichten hinweg.

</details>

<details>
<summary>87. Wie implementiert man eine Drawer-Navigation?</summary>

#### React Native

Dafür wird üblicherweise `@react-navigation/drawer` verwendet.

Grundablauf:

1. Abhängigkeiten für den Drawer Navigator installieren.
2. `Drawer.Navigator` mit den Screens anlegen.
3. Optional den Drawer-Content anpassen.
4. Bei Bedarf mit Stack-/Tab-Navigation kombinieren.

Primäre Routen gehören in den Drawer; übermäßige Verschachtelung sollte vermieden werden.

**Kurz gesagt**

Drawer-Navigation eignet sich für Top-Level-Bereiche, solange die Hierarchie klar und flach bleibt.

</details>

<details>
<summary>88. Was ist gesture-basierte Navigation?</summary>

#### React Native

Gesture-basierte Navigation bedeutet, dass Nutzer per Wisch- und Touch-Mustern zwischen Screens navigieren (Back-Swipe, Tab-Swipe, Drawer-Drag).

In React Native wird das typischerweise durch React Navigation plus Gesture Handler unterstützt.

Vorteile:

1. Natürlichere, native wirkende Interaktionen.
2. Schnellere Einhand-Navigation in vielen Flows.

**Kurz gesagt**

Gesten-Navigation verbessert mobile UX deutlich, wenn sie an Plattformkonventionen angepasst ist.

</details>

<details>
<summary>89. Wie implementiert man Shared-Element-Transitions?</summary>

#### React Native

Shared-Element-Transitions animieren ein gemeinsames UI-Element zwischen zwei Screens.

Typische Umsetzung:

1. Eine Library mit Shared-Transition-Support einsetzen.
2. Quell- und Ziel-Elementen identische Shared-IDs geben.
3. Navigations-Transition passend konfigurieren.

Das verbessert die visuelle Kontinuität in List/Detail-Flows.

**Kurz gesagt**

Shared-Transitions halten den visuellen Kontext beim Wechsel zwischen Liste und Detailansicht stabil.

</details>

<details>
<summary>90. Was ist der Fabric-Renderer und was ist der Unterschied?</summary>

#### React Native

Fabric ist der neue Renderer von React Native innerhalb der New Architecture.

Unterschiede zum Legacy-Renderer:

1. Bessere Integration mit Concurrent-React-Patterns.
2. Effizientere Rendering-Pipeline.
3. Engere Zusammenarbeit mit JSI/TurboModules.
4. Geringere Latenz bei bestimmten UI-Updates.

Fabric ist ein zentraler Bestandteil der RN-Modernisierung.

**Kurz gesagt**

Fabric steigert Rendering-Effizienz und passt in das moderne Runtime-Modell von React Native.

</details>

<details>
<summary>91. Was ist der Vorteil der TurboModules-Architektur?</summary>

#### React Native

TurboModules sind Teil der New Architecture von React Native und verbessern, wie native Module aus JavaScript geladen und aufgerufen werden.

Hauptvorteile:

1. **Lazy Loading:** Module werden nur bei Bedarf initialisiert.
2. **Bessere Performance:** weniger Startup-Overhead und geringere Bridge-Kosten.
3. **Typsicherheit via Codegen:** robustere Verträge zwischen JS und Native.
4. **Höhere Wartbarkeit:** klarere Modul-Schnittstellen und modernisierte Native-Integration.

TurboModules sind besonders wertvoll in großen Apps mit vielen nativen Abhängigkeiten.

**Kurz gesagt**

TurboModules verbessern Startzeit und Native-Zugriff durch bedarfsgeladenes, typisiertes Modul-Handling.

</details>

<details>
<summary>92. Wie geht man mit Error Boundaries in React Native um?</summary>

#### React Native

Error Boundaries fangen Render-Fehler in Kind-Komponentenbäumen ab und verhindern, dass die gesamte UI abstürzt.

In React Native werden sie als Klassenkomponenten umgesetzt mit:

1. `static getDerivedStateFromError(error)`
2. `componentDidCatch(error, info)`

Beispiel:

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
    // Fehler an Monitoring senden
  }

  render() {
    if (this.state.hasError) {
      return (
        <View>
          <Text>Something went wrong.</Text>
        </View>
      );
    }

    return this.props.children;
  }
}
```

Kritische Screen-Bereiche sollten mit Boundaries umschlossen und an Monitoring-Tools angebunden werden.

**Kurz gesagt**

Error Boundaries isolieren Render-Crashes und zeigen Fallback-UI statt die gesamte App zu brechen.

</details>

<details>
<summary>93. Wie handhabt man globale Fehler?</summary>

#### React Native

Globales Error Handling umfasst unbehandelte JS-Exceptions, Promise-Rejections und native Crashes.

Gängige Strategie:

1. Globalen JS-Error-Handler konfigurieren.
2. Unhandled Promise Rejections erfassen.
3. Crash-/Error-Monitoring integrieren (z. B. Sentry, Bugsnag).
4. Kontext (User/Session/Screen) sicher mitloggen.
5. Wenn möglich Fallback-UI zeigen und kontrolliert recovern.

Native Crashes sollten zusätzlich über Plattform-Tooling und Monitoring-SDKs erfasst werden.

**Kurz gesagt**

Ungefangene JS- und Native-Fehler zentral sammeln und mit ausreichend Kontext reporten.

</details>

<details>
<summary>94. Was ist AppState und wie wird es verwendet?</summary>

#### React Native

`AppState` zeigt an, ob die App aktiv, im Hintergrund oder inaktiv ist.

Typische Zustände:

1. `active`: App ist im Vordergrund und interaktiv.
2. `background`: App läuft im Hintergrund.
3. `inactive`: Übergangszustand (vor allem iOS).

Einsatzfälle:

1. Timer, Video oder Polling pausieren/fortsetzen.
2. Sensible Daten beim Rückkehr in den Vordergrund aktualisieren.
3. Analytics-/Session-Lifecycle-Events auslösen.

Beispiel:

```jsx
import { AppState } from 'react-native';

const subscription = AppState.addEventListener('change', nextState => {
  // State-Wechsel behandeln
});

// Später:
subscription.remove();
```

**Kurz gesagt**

Mit AppState steuerst du sauber, welche Arbeit im Vordergrund läuft und was im Hintergrund pausiert.

</details>

<details>
<summary>95. Wie handhabt man den Android-Back-Button (BackHandler)?</summary>

#### React Native

Unter Android lässt sich der Hardware-Back-Button über `BackHandler` gezielt steuern.

Muster:

1. Auf `hardwareBackPress` subscriben.
2. `true` zurückgeben, um das Event selbst zu konsumieren.
3. `false` zurückgeben, damit Standardverhalten greift (z. B. Navigation zurück).

Beispiel:

```jsx
import { BackHandler } from 'react-native';
import { useEffect } from 'react';

useEffect(() => {
  const sub = BackHandler.addEventListener('hardwareBackPress', () => {
    // Eigene Logik
    return false;
  });

  return () => sub.remove();
}, []);
```

Bei React Navigation zuerst deren Back-Handling-APIs nutzen und `BackHandler` für Spezialfälle einsetzen.

**Kurz gesagt**

Back-Events bewusst behandeln und mit Navigation konsistent integrieren.

</details>

<details>
<summary>96. Wie optimiert man die Bundle-Größe?</summary>

#### React Native

Bundle-Optimierung fokussiert sich darauf, ausgeliefertes JS und Assets zu reduzieren.

Praktische Schritte:

1. Ungenutzte Abhängigkeiten entfernen.
2. Nur benötigte Module importieren.
3. Bilder und Medien komprimieren bzw. korrekt skalieren.
4. Minifizierung und Produktionsoptimierungen aktivieren.
5. Schwere Features dort aufteilen, wo die Architektur es erlaubt.

Kleinere Bundles verbessern Startzeit und Update-Auslieferung.

**Kurz gesagt**

Weniger ausgeliefertes JS/Asset-Volumen bedeutet schnelleren Start und effizientere Updates.

</details>

<details>
<summary>97. Wie handhabt man Versions-Upgrades und Migrationen?</summary>

#### React Native

Upgrades sollten schrittweise und mit automatisierter Validierung erfolgen.

Empfohlener Ablauf:

1. In kleinen Schritten upgraden.
2. RN-Release-Notes und Breaking Changes prüfen.
3. Upgrade-Helper/Diffs für React Native nutzen.
4. Vollständige Tests auf iOS und Android durchführen.
5. Mit Monitoring und Rollback-Bereitschaft ausrollen.

Große Mehrversionssprünge möglichst vermeiden.

**Kurz gesagt**

Inkrementelle Upgrades plus Release-Note-Checks und vollständige Regressionstests minimieren Migrationsrisiko.

</details>

<details>
<summary>98. Was sind die Grenzen von React Native?</summary>

#### React Native

Typische Einschränkungen:

1. Manche fortgeschrittenen Native-APIs erfordern eigenes Native-Development.
2. Die Qualität von Ecosystem-Paketen variiert.
3. Bei schwacher Architektur oder hoher JS-Last kann Performance leiden.
4. Upgrades und Native-Tooling sind teils komplex.

Trotzdem ist RN für viele Cross-Platform-Apps sehr effektiv.

**Kurz gesagt**

React Native ist produktiv, aber anspruchsvolle Spezialfälle brauchen oft natives Know-how und sorgfältiges Tuning.

</details>

<details>
<summary>99. Wie implementiert man Echtzeit-Synchronisierung?</summary>

#### React Native

Echtzeit-Sync kombiniert Live-Transport mit konfliktresistenter lokaler Datenpflege.

Typische Strategie:

1. Live-Events via WebSocket/Subscriptions empfangen.
2. Optimistische Updates für User-Aktionen anwenden.
3. Lokalen State für Offline-Kontinuität persistieren.
4. Beim Reconnect Server-Truth mit lokalen Änderungen abgleichen.
5. Versionierung und Conflict-Resolution-Regeln nutzen.

So bleiben Daten aktuell, ohne Konsistenz zu verlieren.

**Kurz gesagt**

Robuster Echtzeit-Sync braucht Event-Streams, Offline-Persistenz und klare Konfliktauflösung.

</details>

<details>
<summary>100. Wie entwirft man eine skalierbare Mobile-Architektur?</summary>

#### React Native

Skalierbare Mobile-Architektur setzt auf klare Grenzen und vorhersagbare Abläufe.

Kernprinzipien:

1. Feature-basierte modulare Struktur.
2. Trennung von UI, Domain-Logik und Datenebene.
3. Explizite State-Strategie (lokal/global/server-state).
4. Konsistente Muster für Navigation, Fehlerbehandlung und Networking.
5. Automatisierte Quality Gates (Tests, Lint, CI, Monitoring).

Architektur sollte auf langfristige Änderbarkeit optimiert sein, nicht nur auf schnellen Start.

**Kurz gesagt**

Skalierbarkeit entsteht durch modulare Grenzen, klaren Datenfluss und konsequent durchgesetzte Team-Konventionen.

</details>

**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  React Native <img src="./assets/reactnative.svg" width="40" height="40" />
</h1>

<h2>Najpopularniejsze pytania i odpowiedzi na rozmowie React Native</h2>

<details>
<summary>1. Czym jest React Native i czym różni się od Reacta?</summary>

#### React Native

React Native to framework open source do budowania aplikacji mobilnych przy
użyciu JavaScript/TypeScript i Reacta.

Kluczowa różnica:

1. **React (React.js):** tworzy interfejs webowy renderowany do DOM przeglądarki (`div`, `span` itp.).
2. **React Native:** tworzy aplikacje iOS/Android renderowane do natywnych komponentów platformy (`View`, `Text`, `Image` itd.).

Oba podejścia używają tego samego modelu komponentów, props/state oraz hooków,
ale celują w inne platformy i warstwy renderowania.

**Krótko**

React Native jest dla mobile i natywnego UI, a React dla webu i DOM.

</details>

<details>
<summary>2. Wyjaśnij koncepcję JSX w React Native.</summary>

#### React Native

JSX (JavaScript XML) to rozszerzenie składni, które pozwala deklaratywnie
opisywać strukturę UI w stylu zbliżonym do HTML bezpośrednio w JavaScript.

W React Native JSX działa z natywnymi komponentami:

```jsx
function Greeting() {
  return <Text>Hello, React Native!</Text>;
}
```

Uwagi:

1. JSX to nie HTML. Babel zamienia go na wywołania JavaScript.
2. Wyrażenia JavaScript można osadzać w `{}`.
3. W RN używasz komponentów natywnych (`View`, `Text`), a nie tagów przeglądarkowych (`div`, `p`).

**Krótko**

JSX to wygodna składnia opisu interfejsu, którą React Native mapuje na komponenty natywne.

</details>

<details>
<summary>3. Jak utworzyć komponent funkcyjny w React Native?</summary>

#### React Native

Komponent funkcyjny to funkcja JavaScript, która zwraca JSX.

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

Możesz też użyć składni funkcji strzałkowej:

```jsx
const ProfileCard = () => (
  <View>
    <Text>Profile</Text>
  </View>
);
```

**Krótko**

To zwykła funkcja zwracająca JSX, często łączona z hookami do stanu i efektów.

</details>

<details>
<summary>4. Czym są core components w React Native (View, Text, Image itd.)?</summary>

#### React Native

Core components to wbudowane prymitywy UI dostarczane przez React Native do
budowania interfejsów mobilnych.

Najczęściej używane:

1. **View:** podstawowy kontener do layoutu i stylowania.
2. **Text:** wyświetlanie tekstu.
3. **Image:** renderowanie obrazów z assetów lokalnych lub URL.
4. **TextInput:** pole wprowadzania tekstu.
5. **ScrollView:** przewijalny kontener na treść.
6. **FlatList / SectionList:** wydajne listy dla większych zbiorów danych.
7. **Pressable / TouchableOpacity:** obsługa interakcji dotykowych.
8. **SafeAreaView:** uwzględnia bezpieczne obszary ekranu (notch, zaokrąglenia).

Te komponenty mapują się do natywnych elementów UI na iOS i Androidzie.

**Krótko**

To podstawowe klocki RN do budowy interfejsu, np. `View`, `Text`, `Image`.

</details>

<details>
<summary>5. Czym są propsy w React Native i jak się ich używa?</summary>

#### React Native

Props (properties) to wejściowe, tylko-do-odczytu dane przekazywane z
komponentu rodzica do komponentu dziecka.

Służą do:

1. Przekazywania danych (tekst, liczby, obiekty, tablice).
2. Przekazywania zachowania (funkcje callback).
3. Konfigurowania komponentów wielokrotnego użytku.

Przykład:

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

Tutaj `name` to prop przekazany z `App` do `WelcomeMessage`.

**Krótko**

Propsy to dane wejściowe od rodzica do dziecka, używane do konfiguracji i przepływu danych.

</details>

<details>
<summary>6. Czym jest state w React Native i jak zarządzać nim hookami?</summary>

#### React Native

State to dane należące do komponentu, które mogą zmieniać się w czasie i
powodować aktualizacje UI.

W komponentach funkcyjnych stan najczęściej obsługuje hook `useState`:

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

Przy bardziej złożonej logice możesz użyć `useReducer`.

**Krótko**

State to lokalne, zmienne dane; hooki pozwalają aktualizować je przewidywalnie i wymuszać rerender.

</details>

<details>
<summary>7. Jaka jest różnica między state a props?</summary>

#### React Native

`state` i `props` przechowują dane używane w renderowaniu, ale pełnią różne role:

1. **Props:** wejścia tylko do odczytu, przekazywane z rodzica do dziecka.
2. **State:** wewnętrzne, mutowalne dane zarządzane przez sam komponent.

Szybkie porównanie:

1. **Kto jest właścicielem danych?** Props: komponent rodzic. State: bieżący komponent.
2. **Czy można zmienić lokalnie?** Props: nie. State: tak, np. przez `useState`.
3. **Do czego służy?** Props: konfiguracja i przepływ danych. State: dynamiczne zachowanie UI w komponencie.

**Krótko**

Propsy służą do przekazywania danych z zewnątrz, a state do lokalnej, zmiennej logiki komponentu.

</details>

<details>
<summary>8. Jak obsługiwać input użytkownika w React Native?</summary>

#### React Native

Input zwykle obsługuje się przez komponenty kontrolowane, najczęściej
`TextInput`, połączone ze stanem.

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

Kluczowe eventy/handlery:

1. `onChangeText`: aktualizuje tekst w stanie.
2. `onPress`: obsługuje akcje przycisków i dotyku.
3. `onSubmitEditing`: reaguje na zatwierdzenie klawiatury w `TextInput`.

**Krótko**

Najlepiej stosować input kontrolowany: wartość trzymasz w stanie i zmieniasz przez handlery.

</details>

<details>
<summary>9. Jak stylować komponenty w React Native?</summary>

#### React Native

React Native używa obiektów JavaScript do stylowania zamiast plików CSS.

Najczęstsze sposoby:

1. **Style inline** (szybkie, lokalne stylowanie):

```jsx
<Text style={{ color: 'blue', fontSize: 18 }}>Hello</Text>
```

2. **`StyleSheet.create`** (rekomendowane w większości przypadków):

```jsx
const styles = StyleSheet.create({
  title: { color: 'blue', fontSize: 18 },
});
```

3. **Tablice stylów** (style warunkowe i składanie stylów):

```jsx
<Text style={[styles.title, isActive && styles.active]}>Hello</Text>
```

Style RN są podobne do CSS, ale właściwości zapisuje się camelCase (np.
`backgroundColor`, `fontSize`).

**Krótko**

W RN stylujesz obiektami JS; dla porządku i reużywalności najczęściej używa się `StyleSheet.create`.

</details>

<details>
<summary>10. Czym jest StyleSheet i kiedy go używać?</summary>

#### React Native

`StyleSheet` to narzędzie React Native do definiowania i organizowania stylów
w uporządkowany sposób.

Przykład:

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

Kiedy używać:

1. Gdy style są współdzielone między wieloma elementami.
2. Gdy chcesz mieć czystszy i łatwiejszy w utrzymaniu kod komponentu.
3. Gdy potrzebujesz spójnego podejścia do stylowania w większych ekranach/aplikacjach.

**Krótko**

`StyleSheet` daje czytelne, wielokrotnego użytku definicje stylów i poprawia utrzymanie kodu.

</details>

<details>
<summary>11. Wyjaśnij Flexbox i jego rolę w layoutcie.</summary>

#### React Native

Flexbox to podstawowy system layoutu w React Native. Odpowiada za rozmiar,
wyrównanie i rozmieszczenie komponentów w kontenerze.

W RN domyślne ustawienia Flexbox różnią się nieco od webowego CSS:

1. Domyślne `flexDirection` to `column`.
2. Domyślne `alignContent` to `flex-start`.
3. Domyślne `flexShrink` to `0`.

Najważniejsze właściwości:

1. `flex`: określa, ile miejsca element zajmuje względem rodzeństwa.
2. `flexDirection`: układ w wierszu lub kolumnie.
3. `justifyContent`: wyrównanie na osi głównej.
4. `alignItems`: wyrównanie na osi poprzecznej.
5. `gap` (nowsze wersje RN): odstępy między dziećmi.

Przykład:

```jsx
<View
  style={{ flex: 1, flexDirection: 'row', justifyContent: 'space-between' }}
>
  <View style={{ width: 50, height: 50, backgroundColor: 'red' }} />
  <View style={{ width: 50, height: 50, backgroundColor: 'blue' }} />
</View>
```

**Krótko**

W Flexboxie kluczowe są osie (główna i poprzeczna) oraz kontrola `justify`/`align`.

</details>

<details>
<summary>12. Jak podejść do responsive design w React Native?</summary>

#### React Native

Responsywność w React Native buduje się przez elastyczny layout i API zależne
od urządzenia.

Najczęstsze podejścia:

1. Używaj Flexbox (`flex`, `%`, wyrównanie) zamiast sztywnych wymiarów.
2. Korzystaj z `Dimensions` lub `useWindowDimensions()` dla rozmiaru ekranu.
3. Używaj `Platform` dla różnic platformowych.
4. Stosuj `SafeAreaView`, aby uwzględnić notche i elementy systemowe.
5. Skaluj typografię i odstępy wspólnymi stałymi.

Przykład:

```jsx
import { useWindowDimensions, View } from 'react-native';

function ResponsiveCard() {
  const { width } = useWindowDimensions();
  const isTablet = width >= 768;

  return <View style={{ padding: isTablet ? 24 : 16 }} />;
}
```

**Krótko**

Łącz elastyczny układ z wymiarami ekranu i obsługą safe area.

</details>

<details>
<summary>13. Jak debugować aplikację React Native?</summary>

#### React Native

Debugowanie w RN zwykle opiera się na połączeniu narzędzi wbudowanych i
zewnętrznych.

Główne opcje:

1. **Logi Metro:** `console.log`, ostrzeżenia i błędy w terminalu.
2. **React Native Dev Menu:** przeładowanie appki, inspekcja UI, narzędzia debug.
3. **React DevTools:** inspekcja drzewa komponentów, propsów i stanu hooków.
4. **Flipper:** inspekcja sieci, logów, layoutu i pluginów wydajności.
5. **Narzędzia natywne:** Xcode (iOS) i Android Studio (Android) dla crashy oraz logów natywnych.

Dobra praktyka: odtwórz problem krok po kroku, zawęź go do konkretnego
komponentu i zweryfikuj na iOS oraz Androidzie.

**Krótko**

Najczęściej używa się kombinacji: logi, DevTools/Flipper i natywne logi platformowe.

</details>

<details>
<summary>14. Czym jest Fast Refresh i jak działa?</summary>

#### React Native

Fast Refresh to funkcja developerska, która odświeża aplikację zaraz po zmianie
kodu, zwykle zachowując lokalny state komponentów.

Jak to działa:

1. Zapisujesz plik.
2. Metro przebudowuje tylko zmienione moduły.
3. React Native wstrzykuje nowy kod do uruchomionej aplikacji.
4. UI aktualizuje się natychmiast, bez pełnego restartu w większości przypadków.

Uwagi:

1. Lokalny state zwykle zostaje zachowany w komponentach funkcyjnych.
2. Gdy zmiany dotyczą inicjalizacji modułu lub eksportów poza komponentem, RN może wykonać szerszy reload.
3. To funkcja tylko developerska, nie działa w produkcji.

**Krótko**

Fast Refresh podmienia zmienione moduły podczas developmentu i zazwyczaj zachowuje state.

</details>

<details>
<summary>15. Czym są komponenty Touchable i jak działają?</summary>

#### React Native

Komponenty Touchable to interaktywne wrappery reagujące na tapnięcia i
naciśnięcia. Pozwalają wywoływać akcje, np. przejście do ekranu, wysyłkę formularza
czy wybór elementu.

Popularne opcje:

1. `Pressable` (nowoczesny i elastyczny, często rekomendowany).
2. `TouchableOpacity` (zmienia przezroczystość przy naciśnięciu).
3. `TouchableHighlight` (pokazuje podświetlenie pod dzieckiem).
4. `TouchableWithoutFeedback` (bez efektu wizualnego).

Przykład:

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

Udostępniają eventy jak `onPress`, `onPressIn`, `onPressOut` i `onLongPress`.

**Krótko**

Touchable dodaje interakcje dotykowe do UI; najczęściej warto wybierać `Pressable`.

</details>

<details>
<summary>16. Jak obsługiwać nawigację w React Native (React Navigation)?</summary>

#### React Native

Nawigację najczęściej realizuje się przez `@react-navigation/*`.

Typowa konfiguracja:

1. Zainstaluj core React Navigation i wymagane navigatory.
2. Owiń aplikację komponentem `NavigationContainer`.
3. Zdefiniuj stacki, taby i/lub drawery.
4. Nawiguj przez `navigation.navigate('ScreenName')`.

W większości aplikacji dobrze sprawdza się połączenie Stack + Tab oraz
typowane nazwy tras.

**Krótko**

Łącz navigatory (stack/tab/drawer) i utrzymuj klarowną, jawną strukturę tras.

</details>

<details>
<summary>17. Jaka jest rola NavigationContainer?</summary>

#### React Native

`NavigationContainer` to główny provider, który zarządza stanem nawigacji i
łączy navigatory ze środowiskiem aplikacji.

Odpowiada za:

1. Przechowywanie bieżącego stanu drzewa nawigacji.
2. Obsługę linking/deep linków.
3. Udostępnienie kontekstu nawigacji wszystkim ekranom.

Bez niego React Navigation nie zadziała.

**Krótko**

To korzeń nawigacji: trzyma jej stan i dostarcza kontekst całej aplikacji.

</details>

<details>
<summary>18. Jak przekazywać parametry między ekranami?</summary>

#### React Native

Parametry przekazuje się przez metody nawigacji.

Przykład:

```jsx
navigation.navigate('Profile', { userId: '42' });
```

Odczyt parametrów na ekranie docelowym:

```jsx
const { userId } = route.params;
```

Parametrów używaj do małego kontekstu trasy, a nie do dużego/globalnego stanu aplikacji.

**Krótko**

Przekazuj małe parametry przez `navigate`, a odczytuj je z `route.params`.

</details>

<details>
<summary>19. Czym jest deep linking i jak go wdrożyć?</summary>

#### React Native

Deep linking pozwala otworzyć konkretny ekran aplikacji z poziomu URL.

Implementacja z React Navigation:

1. Zdefiniuj URL scheme/universal links w konfiguracjach natywnych.
2. Skonfiguruj obiekt `linking` w `NavigationContainer`.
3. Zmapuj ścieżki URL na nazwy ekranów.

Dzięki temu flow typu `myapp://product/123` może otworzyć ekran produktu.

**Krótko**

Mapuj URL-e na ekrany, aby linki zewnętrzne trafiały bezpośrednio w właściwą trasę.

</details>

<details>
<summary>20. Czym są keys w listach i dlaczego są ważne?</summary>

#### React Native

`key` jednoznacznie identyfikuje element listy podczas reconciliacji Reacta.

Dlaczego to ważne:

1. Pomaga Reactowi aktualizować tylko zmienione wiersze.
2. Zapobiega błędnemu reuse elementów i bugom stanu.
3. Poprawia wydajność i przewidywalność renderowania.

Zawsze używaj stabilnych, unikalnych ID, a nie indeksu tablicy (chyba że lista jest statyczna).

**Krótko**

Stabilne unikalne klucze ograniczają błędy list i poprawiają wydajność aktualizacji.

</details>

<details>
<summary>21. Jak wydajnie renderować listy (FlatList, SectionList)?</summary>

#### React Native

Do wydajnego renderowania list w React Native lepiej używać `FlatList` i
`SectionList` zamiast mapowania dużych tablic wewnątrz `ScrollView`.

Dlaczego są wydajne:

1. Renderują elementy leniwie (widoczne wiersze + bufor).
2. Recyklingują widoki elementów i zmniejszają zużycie pamięci.
3. Oferują wbudowaną paginację i optymalizacje przewijania.

Zastosowania:

1. `FlatList`: jednowymiarowa lista podobnych elementów.
2. `SectionList`: lista pogrupowana z nagłówkami sekcji.

Podstawowy przykład `FlatList`:

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

**Krótko**

Przy większych zbiorach danych stawiaj na listy wirtualizowane, aby kontrolować pamięć i płynność scrolla.

</details>

<details>
<summary>22. Czym jest VirtualizedList i kiedy jej używać?</summary>

#### React Native

`VirtualizedList` to bazowy silnik list, na którym opierają się `FlatList` i
`SectionList`. Obsługuje renderowanie okienkowe dla dużych zbiorów danych.

Kiedy użyć jej bezpośrednio:

1. Gdy źródło danych nie jest prostą tablicą.
2. Gdy potrzebujesz pełnej kontroli nad `getItem` i `getItemCount`.
3. Gdy abstrakcje `FlatList`/`SectionList` są zbyt ograniczone.

W większości aplikacji najpierw wybieraj `FlatList` albo `SectionList`, bo są
prostsze i pokrywają typowe przypadki.

**Krótko**

Bezpośrednio używaj `VirtualizedList` głównie przy niestandardowym dostępie do danych; zwykle wystarczy `FlatList`/`SectionList`.

</details>

<details>
<summary>23. Jak pobierać dane w React Native (fetch, axios)?</summary>

#### React Native

Dane możesz pobierać wbudowanym API `fetch` albo biblioteką `axios`.

Przykład `fetch`:

```jsx
async function loadPosts() {
  const response = await fetch('https://api.example.com/posts');
  if (!response.ok) throw new Error('Request failed');
  return response.json();
}
```

Przykład `axios`:

```jsx
import axios from 'axios';

async function loadPosts() {
  const { data } = await axios.get('https://api.example.com/posts');
  return data;
}
```

Typowy flow w komponencie:

1. Ustaw stan ładowania.
2. Wykonaj asynchroniczne żądanie.
3. Zapisz wynik albo błąd w stanie.
4. Wyłącz ładowanie i wyrenderuj odpowiedni widok.

**Krótko**

Najważniejszy jest cykl żądania: loading, sukces, błąd i obsługa anulowania.

</details>

<details>
<summary>24. Jakie są dobre praktyki dla API calls i obsługi błędów?</summary>

#### React Native

Dobre praktyki dla API i obsługi błędów:

1. Centralizuj logikę API w warstwie serwisów.
2. Zawsze obsługuj stany loading/success/error.
3. Ustaw timeouty i strategię retry dla błędów przejściowych.
4. Waliduj kształt odpowiedzi przed użyciem danych.
5. Pokazuj przyjazne komunikaty dla użytkownika (nie surowe błędy serwera).
6. Używaj anulowania (`AbortController`), by nie aktualizować odmontowanych ekranów.
7. Trzymaj odświeżanie tokenów auth w jednym miejscu (interceptory/middleware).

Krótki schemat:

1. `try` żądanie.
2. `catch` błędy sieciowe/serwerowe.
3. Mapowanie na błędy domenowe.
4. Logowanie technicznych szczegółów do debugowania/monitoringu.

**Krótko**

Kluczowe są: jedna warstwa API, spójne mapowanie błędów oraz strategia retry/cancel.

</details>

<details>
<summary>25. Jak obsługiwać async storage (pakiet społeczności AsyncStorage)?</summary>

#### React Native

`AsyncStorage` to trwały magazyn klucz-wartość dla lekkich danych, np. ustawień
użytkownika, flag i prostego cache.

Podstawowe użycie:

```jsx
import AsyncStorage from '@react-native-async-storage/async-storage';

async function saveTheme(theme) {
  await AsyncStorage.setItem('theme', theme);
}

async function loadTheme() {
  return AsyncStorage.getItem('theme');
}
```

Dobre praktyki:

1. Serializuj obiekty przez `JSON.stringify` / `JSON.parse`.
2. Owijaj wywołania w `try/catch`.
3. Trzymaj małe payloady; to nie jest baza danych.
4. Stosuj namespacing kluczy (np. `app:user:token`).
5. Dla danych wrażliwych używaj bezpiecznego storage (Keychain/Keystore).

**Krótko**

`AsyncStorage` nadaje się do lekkiej persystencji; nie do sekretów, i zawsze z obsługą błędów.

</details>

<details>
<summary>26. Jakie są nowoczesne rozwiązania do zarządzania stanem (Context, Zustand, Redux Toolkit)?</summary>

#### React Native

Nowoczesne opcje zależą od złożoności aplikacji:

1. **Context API:** proste dane globalne, mało boilerplate.
2. **Zustand:** lekki store, łatwe API, minimalna ceremonia.
3. **Redux Toolkit:** solidne wzorce, middleware, devtools, skalowanie dla większych zespołów.

Wybieraj najmniejsze narzędzie, które pokrywa realną złożoność i potrzeby zespołu.

**Krótko**

Dobieraj rozwiązanie do skali: Context dla prostszych przypadków, Zustand/RTK dla większych domen stanu.

</details>

<details>
<summary>27. Jak zarządzać globalnym stanem bez Reduxa?</summary>

#### React Native

Możesz użyć Context + hooki albo lekkich store’ów, np. Zustand/Jotai.

Typowy wzorzec:

1. Utwórz provider dla współdzielonego stanu domenowego.
2. Zamknij aktualizacje w custom hookach.
3. Trzymaj server state osobno (React Query/Apollo).

To ogranicza boilerplate Reduxa i nadal dobrze się skaluje w wielu aplikacjach.

**Krótko**

Łącz Context lub lekki store z custom hookami i jasnymi granicami odpowiedzialności.

</details>

<details>
<summary>28. Czym są hooki React i które są najczęściej używane?</summary>

#### React Native

Hooki to funkcje, które pozwalają komponentom funkcyjnym korzystać ze stanu,
efektów i innych możliwości Reacta.

Najczęściej używane hooki:

1. `useState`
2. `useEffect`
3. `useMemo`
4. `useCallback`
5. `useRef`
6. `useContext`
7. `useReducer`

Hooki umożliwiają też reużywalną logikę przez custom hooki.

**Krótko**

Hooki przenoszą logikę stanową do funkcji i ułatwiają jej wielokrotne użycie.

</details>

<details>
<summary>29. Czym jest useEffect i jak zastępuje metody lifecycle?</summary>

#### React Native

`useEffect` uruchamia efekty uboczne po renderze i może je czyścić.

Mapowanie lifecycle (klasy -> hooki):

1. `componentDidMount` -> `useEffect(..., [])`
2. `componentDidUpdate` -> `useEffect(..., [deps])`
3. `componentWillUnmount` -> funkcja cleanup zwracana z `useEffect`

To ujednolica zachowanie lifecycle w komponentach funkcyjnych.

**Krótko**

`useEffect` służy do efektów i cleanupu; myśl zależnościami, nie nazwami metod klasowych.

</details>

<details>
<summary>30. Czym są useMemo i useCallback i kiedy ich używać?</summary>

#### React Native

`useMemo` memoizuje obliczone wartości, a `useCallback` memoizuje referencje
funkcji.

Stosuj je, gdy:

1. Obliczenia są kosztowne.
2. Potrzebujesz stabilnych referencji, by ograniczać rerendery dzieci.
3. Wartości/callbacki są zależnościami innych hooków.

Nie nadużywaj ich; używaj tam, gdzie profilowanie pokazuje realny zysk.

**Krótko**

Używaj selektywnie do stabilizacji kosztownych wartości i callbacków tylko wtedy, gdy to faktycznie pomaga.

</details>

<details>
<summary>31. Czym są refy i kiedy warto ich używać?</summary>

#### React Native

Refy to mutowalne referencje do instancji komponentów albo elementów natywnych.
Pozwalają korzystać z imperatywnych API bez wywoływania rerenderów.

Typowe zastosowania:

1. Focus lub blur na `TextInput`.
2. Wywołanie metod scrolla (`scrollToOffset`, `scrollToEnd`).
3. Pomiar layoutu (`measure`, `measureInWindow`).
4. Przechowywanie mutowalnych wartości, które nie powinny odświeżać UI.

Przykład:

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

Używaj refów do działań imperatywnych, nie jako zamiennika zwykłego przepływu state/props.

**Krótko**

Refy służą do imperatywnego dostępu (focus/scroll/pomiar), a nie do typowego przepływu danych.

</details>

<details>
<summary>32. Jak tworzyć custom hooki?</summary>

#### React Native

Custom hook to funkcja wielokrotnego użytku, która zaczyna się od `use` i
łączy hooki Reacta (`useState`, `useEffect` itd.) w jedną wspólną logikę.

Zasady:

1. Nazwa hooka musi zaczynać się od `use`.
2. Hooki wywołuj tylko na najwyższym poziomie custom hooka.
3. Zwracaj wartości/funkcje potrzebne komponentom.

Przykład:

```jsx
import { useEffect, useState } from 'react';

function useOnlineStatus() {
  const [isOnline, setIsOnline] = useState(true);

  useEffect(() => {
    // Subscribe to network changes here
    return () => {
      // Unsubscribe here
    };
  }, []);

  return isOnline;
}
```

Custom hooki poprawiają reużywalność, czytelność i separację odpowiedzialności.

**Krótko**

Wyciągaj powtarzalną logikę stanową do funkcji `use*`, żeby komponenty były prostsze.

</details>

<details>
<summary>33. Czym jest optymalizacja wydajności w React Native?</summary>

#### React Native

Optymalizacja wydajności w RN polega na ograniczaniu narzutu renderowania,
JavaScriptu i layoutu, aby interakcje były płynne (zwłaszcza na słabszych
urządzeniach).

Typowe obszary optymalizacji:

1. Renderowanie: eliminowanie zbędnych rerenderów.
2. Listy: użycie `FlatList`/`SectionList` z odpowiednim tuningiem.
3. Praca JS: przenoszenie ciężkich obliczeń poza krytyczną ścieżkę renderu.
4. Obrazy: kompresja, cache i poprawne rozmiary.
5. Komunikacja native/JS: ograniczanie kosztownych operacji między warstwami.

Typowy cel: stabilne 60 FPS, szybszy start i responsywna obsługa dotyku.

**Krótko**

Najpierw profiluj, potem optymalizuj realne bottlenecks: render, listy, obrazy i ciężką logikę JS.

</details>

<details>
<summary>34. Jak unikać niepotrzebnych rerenderów?</summary>

#### React Native

Niepotrzebne rerendery ograniczasz przez stabilizację propsów i aktualizowanie
stanu tylko tam, gdzie to konieczne.

Praktyczne techniki:

1. Używaj `React.memo` dla czystych komponentów funkcyjnych.
2. Używaj `useMemo` dla kosztownych wartości pochodnych.
3. Używaj `useCallback` dla stabilnych referencji callbacków.
4. Trzymaj stan możliwie lokalnie.
5. Unikaj tworzenia nowych obiektów/funkcji inline, gdy przekazujesz je głęboko jako props.
6. Dziel duże komponenty na mniejsze, skupione elementy.
7. Stosuj stabilne klucze w listach.

Najpierw profiluj (React DevTools/Flipper), potem optymalizuj tylko rzeczywiste
wąskie gardła.

**Krótko**

Stabilizuj propsy, lokalizuj stan i memoizuj tylko tam, gdzie daje to realny zysk wydajności.

</details>

<details>
<summary>35. Czym jest memoizacja w React Native?</summary>

#### React Native

Memoizacja to technika cache’owania wyników obliczeń albo outputu komponentu,
aby ponownie użyć ich, gdy wejścia się nie zmieniły.

W RN najczęściej używane narzędzia memoizacji to:

1. `React.memo`: memoizacja renderu komponentu przez porównanie propsów.
2. `useMemo`: memoizacja obliczonych wartości.
3. `useCallback`: memoizacja referencji funkcji.

Przykład:

```jsx
import React, { useMemo } from 'react';

function Total({ items }) {
  const sum = useMemo(() => {
    return items.reduce((acc, item) => acc + item.price, 0);
  }, [items]);

  return <Text>{sum}</Text>;
}
```

Stosuj memoizację selektywnie; nadużycie zwiększa złożoność bez mierzalnej
korzyści.

**Krótko**

Memoizacja zapobiega ponownym obliczeniom/rerenderom niezmienionej pracy.

</details>

<details>
<summary>36. Czym jest silnik Hermes i dlaczego jest ważny?</summary>

#### React Native

Hermes to silnik JavaScript zoptymalizowany pod React Native.

Dlaczego jest ważny:

1. Szybszy start aplikacji.
2. Mniejsze zużycie pamięci na wielu urządzeniach.
3. Bardziej przewidywalna wydajność na Androidzie i iOS.
4. Dobra integracja z toolingiem RN.

Hermes jest częstym domyślnym wyborem dla produkcyjnych aplikacji RN.

**Krótko**

Hermes zwykle poprawia czas uruchamiania i charakterystykę pamięci aplikacji RN.

</details>

<details>
<summary>37. Czym jest nowa architektura React Native?</summary>

#### React Native

Nowa architektura to modernizacja wnętrza RN oparta na:

1. rendererze Fabric,
2. TurboModules,
3. JSI (JavaScript Interface),
4. kierunku bridgeless.

Cele: mniejsze opóźnienia między JS i natywną warstwą, lepsze wsparcie
współbieżności i wyższa wydajność.

**Krótko**

To zestaw Fabric + TurboModules + JSI, który zmniejsza narzut i poprawia skalowalność.

</details>

<details>
<summary>38. Czym są Fabric i TurboModules?</summary>

#### React Native

`Fabric` to nowy system renderowania, a `TurboModules` to nowy system modułów
natywnych.

Razem zapewniają:

1. wydajniejsze aktualizacje UI,
2. szybszy dostęp do modułów,
3. lepszą, typowaną integrację natywną przez codegen,
4. lepszy start i wydajność runtime.

**Krótko**

Fabric modernizuje renderowanie, a TurboModules modernizują ładowanie i dostęp do modułów natywnych.

</details>

<details>
<summary>39. Czym jest JSI i jak zastępuje stary bridge?</summary>

#### React Native

JSI (JavaScript Interface) to API C++, które pozwala JS i warstwie natywnej
komunikować się bardziej bezpośrednio.

W porównaniu do starego bridge:

1. redukuje ciężkie asynchroniczne przekazywanie komunikatów JSON,
2. umożliwia wywołania o mniejszym narzucie i współdzielone integracje runtime,
3. wspiera elementy nowej architektury, jak TurboModules i Fabric.

To znacząco zmniejsza wąskie gardła komunikacji.

**Krótko**

JSI ogranicza narzut legacy bridge przez bardziej bezpośrednią interakcję JS z natywną warstwą.

</details>

<details>
<summary>40. Czym jest tryb Bridgeless w React Native?</summary>

#### React Native

Tryb Bridgeless to kierunek architektoniczny, w którym RN działa bez ścieżki
uruchomieniowej opartej o stary bridge.

Korzyści:

1. mniejszy narzut komunikacji,
2. czystszy, nowoczesny model runtime,
3. lepsze dopasowanie do Fabric, TurboModules i JSI.

To część długofalowej ewolucji RN pod kątem wydajności i utrzymania.

**Krótko**

Bridgeless odchodzi od starego bridge, upraszczając runtime i poprawiając wydajność.

</details>

<details>
<summary>41. Jak React Native osiąga wydajność zbliżoną do natywnej?</summary>

#### React Native

React Native osiąga wydajność bliską natywnej, ponieważ renderuje prawdziwe
natywne komponenty UI i optymalizuje pracę między warstwą JavaScript i natywną.

Kluczowe powody:

1. UI renderuje natywne widoki (`UIView`, `android.view`), a nie webview.
2. Deklaratywne aktualizacje Reacta redukują zbędną pracę UI.
3. Hermes może poprawić czas startu i zużycie pamięci.
4. Nowa architektura (Fabric, TurboModules, JSI) zmniejsza narzut bridge.
5. Zoptymalizowane komponenty list (`FlatList`, `SectionList`) wspierają wirtualizację.

Wydajność nadal zależy od projektu aplikacji: ciężka logika JS, nieoptymalne
rerendery i duże obrazy potrafią spowalniać aplikację.

**Krótko**

RN działa jak natywny, gdy ścieżki renderowania są zoptymalizowane, a ciężka praca JS jest kontrolowana.

</details>

<details>
<summary>42. Czym są Native Modules i kiedy ich używać?</summary>

#### React Native

Native Modules to własne moduły platformowe (iOS/Android), które udostępniają
funkcje natywne do JavaScript.

Używaj Native Modules, gdy:

1. Potrzebujesz API niedostępnych w core RN lub pakietach społeczności.
2. Potrzebujesz głębszego dostępu do możliwości urządzenia/platformy.
3. Potrzebujesz lepszej wydajności dla logiki, która powinna działać natywnie.

Przykłady:

1. Zaawansowane funkcje kamery lub Bluetooth.
2. Integracja z zewnętrznym SDK (płatności, biometria, analityka).
3. Usługi background specyficzne dla systemu.

Jeśli istnieje utrzymywany pakiet społeczności, zwykle warto zacząć od niego.
Własne moduły pisz przy unikalnych wymaganiach.

**Krótko**

Native Modules stosuj wtedy, gdy wymagane API platformy nie są dostępne w gotowych rozwiązaniach.

</details>

<details>
<summary>43. Jak pisać kod natywny dla React Native (Swift/Kotlin)?</summary>

#### React Native

Kod natywny piszesz przez utworzenie modułu na iOS (Swift/Objective-C) i/lub
Androidzie (Kotlin/Java), a następnie wystawienie metod/eventów do JavaScript.

Przepływ na wysokim poziomie:

1. Utwórz klasę modułu natywnego na każdej platformie.
2. Wyeksportuj metody/stałe/eventy do React Native.
3. Zarejestruj moduł w projekcie natywnym.
4. Wywołuj moduł z JavaScript/TypeScript.

Minimalny przykład po stronie JS:

```jsx
import { NativeModules } from 'react-native';

const { DeviceInfoModule } = NativeModules;

async function loadDeviceName() {
  const name = await DeviceInfoModule.getDeviceName();
  return name;
}
```

W nowoczesnym RN preferuj wzorce TurboModules/Codegen dla lepszej
kompatybilności długoterminowej.

**Krótko**

Udostępniaj możliwości natywne przez moduły i wywołuj je z JS przez jasny kontrakt API.

</details>

<details>
<summary>44. Jak zintegrować React Native z istniejącą aplikacją natywną?</summary>

#### React Native

React Native możesz osadzić jako funkcję wewnątrz istniejącej aplikacji
iOS/Android, zamiast przepisywać całość od zera.

Typowe podejście:

1. Dodaj zależności React Native do projektów natywnych.
2. Utwórz bundle RN i konfigurację runtime.
3. Uruchom ekran/root view RN z poziomu nawigacji natywnej.
4. Wymieniaj dane między natywną warstwą i RN przez propsy, eventy lub moduły.

Częste use case’y:

1. Zbudowanie jednego modułu cross-platform (np. ustawienia/profil) w głównie natywnej aplikacji.
2. Stopniowa migracja starszych ekranów.

To podejście zmniejsza ryzyko migracji i pozwala wdrażać RN etapami.

**Krótko**

Integruj RN ekran po ekranie, aby modernizować aplikację inkrementalnie, bez pełnego rewrite.

</details>

<details>
<summary>45. Jak obsługiwać kod specyficzny dla platformy (Platform API)?</summary>

#### React Native

Zachowania platformowe obsługuje się przez `Platform` API i rozszerzenia plików
specyficzne dla platformy.

Główne techniki:

1. Sprawdzenia runtime przez `Platform.OS` (`ios`, `android`).
2. Selekcja platformowa przez `Platform.select(...)`.
3. Rozdzielenie plików po rozszerzeniu: `Component.ios.tsx` i `Component.android.tsx`.

Przykład:

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

Preferuj współdzielenie większości logiki i izolowanie tylko niezbędnych
różnic platformowych.

**Krótko**

Różnice platformowe obsługuj selektywnie przez `Platform` i pliki `.ios/.android`, zostawiając wspólny core.

</details>

<details>
<summary>46. Jak budować komponenty pod różnice między iOS i Androidem?</summary>

#### React Native

Buduj wspólną logikę bazową i izoluj platformowe różnice UI/zachowania tylko
w miejscach, gdzie to potrzebne.

Techniki:

1. `Platform.OS` / `Platform.select`.
2. Pliki `Component.ios.tsx` i `Component.android.tsx`.
3. Tokeny design systemu z nadpisaniami per platforma.

Utrzymuj minimalną dywergencję, by zmniejszyć koszt utrzymania.

**Krótko**

Trzymaj jeden wspólny kontrakt komponentu i wydzielaj wyłącznie niezbędne różnice platformowe.

</details>

<details>
<summary>47. Jak obsługiwać gesty w React Native?</summary>

#### React Native

Do niezawodnych i wydajnych interakcji najlepiej używać bibliotek
wyspecjalizowanych w gestach.

Typowe podejście:

1. `react-native-gesture-handler` do rozpoznawania gestów.
2. `react-native-reanimated` do płynnych animacji sterowanych gestami.
3. Łączenie handlerów tap/pan/fling/pinch zależnie od potrzeb ekranu.

Unikaj ciężkiej pracy JS wewnątrz aktywnych callbacków gestów.

**Krótko**

Najczęściej łączy się Gesture Handler z Reanimated, aby uzyskać płynny UX bez zacięć.

</details>

<details>
<summary>48. Czym jest PanResponder i kiedy go używać?</summary>

#### React Native

`PanResponder` to wbudowany w RN responder gestów do obsługi ruchu dotyku.

Używaj go, gdy:

1. Potrzeby gestów są proste.
2. Chcesz uniknąć dodatkowych zależności.

Dla złożonych i wysokowydajnych gestów zwykle lepszy jest duet Gesture Handler + Reanimated.

**Krótko**

PanResponder sprawdzi się przy prostych gestach; bardziej zaawansowane scenariusze zwykle wymagają bibliotek.

</details>

<details>
<summary>49. Jakie biblioteki stosuje się do gestów (Gesture Handler, Reanimated)?</summary>

#### React Native

Najpopularniejszy stos do gestów:

1. `react-native-gesture-handler` do solidnego rozpoznawania gestów.
2. `react-native-reanimated` do wydajnych animacji i workletów.

W praktyce najczęściej używa się ich razem w produkcyjnych interakcjach.

**Krótko**

Gesture Handler odpowiada za rozpoznanie gestu, a Reanimated za płynną odpowiedź animacji.

</details>

<details>
<summary>50. Czym jest Reanimated i dlaczego się go używa?</summary>

#### React Native

Reanimated to wysokowydajna biblioteka animacji dla RN.

Dlaczego jest używana:

1. Zapewnia płynne animacje z małym jankiem.
2. Dobrze obsługuje przejścia sterowane gestami.
3. Wykonuje logikę animacji wydajnie (model worklet/UI-thread friendly).
4. Nadaje się do złożonych interakcji (bottom sheets, shared transitions itd.).

**Krótko**

Reanimated jest standardem przy złożonych, płynnych animacjach i interakcjach gestowych.

</details>

<details>
<summary>51. Czym jest Animated API i jak działa?</summary>

#### React Native

`Animated` to wbudowany system animacji w React Native, który pozwala tworzyć
płynne przejścia UI przez animowanie wartości w czasie.

Jak to działa:

1. Tworzysz wartość animowaną (`new Animated.Value(0)`).
2. Podpinasz tę wartość do właściwości stylu (`opacity`, `transform` itd.).
3. Uruchamiasz animację funkcjami typu `Animated.timing`, `spring` lub `decay`.

Przykład:

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

**Krótko**

`Animated` obsługuje animacje oparte na wartościach; gdzie to możliwe, używaj `useNativeDriver`.

</details>

<details>
<summary>52. Jaka jest różnica między animacjami deklaratywnymi i imperatywnymi?</summary>

#### React Native

Różnica dotyczy sposobu opisu i kontroli animacji.

1. **Animacje deklaratywne:** opisujesz docelowy stan UI i przejścia na wyższym poziomie, a framework realizuje szczegóły.
2. **Animacje imperatywne:** ręcznie sterujesz cyklem animacji krok po kroku (start, stop, aktualizacja wartości).

W React Native:

1. `LayoutAnimation` i wiele wzorców Reanimated mają bardziej deklaratywny charakter.
2. `Animated.Value` z bezpośrednim wywołaniem `.start()` jest bardziej imperatywne.

Podejście deklaratywne bywa łatwiejsze w utrzymaniu, a imperatywne daje precyzyjniejszą kontrolę nad złożonymi sekwencjami.

**Krótko**

Deklaratywne opisuje efekt końcowy, imperatywne ręcznie steruje przebiegiem animacji.

</details>

<details>
<summary>53. Jak implementować płynne animacje?</summary>

#### React Native

Aby animacje były płynne, zmniejszaj obciążenie głównego wątku i unikaj
kosztownych rerenderów podczas ruchu.

Dobre praktyki:

1. Preferuj `useNativeDriver: true`, gdy jest wspierany.
2. Wybieraj animacje `transform` i `opacity` zamiast właściwości ciężkich layoutowo.
3. Izoluj i memoizuj animowane komponenty, gdy to możliwe.
4. Unikaj ciężkich obliczeń w trakcie gestów/animacji.
5. Używaj `react-native-reanimated` do zaawansowanych, wydajnych interakcji.
6. Optymalizuj duże listy i obrazy animowane na ekranie.

Zawsze testuj na realnych urządzeniach ze średniej półki, nie tylko na emulatorze/symulatorze.

**Krótko**

Priorytetem są `transform`/`opacity` i ograniczenie ciężkiej pracy JS podczas aktywnych interakcji.

</details>

<details>
<summary>54. Czym jest LayoutAnimation i kiedy jej używać?</summary>

#### React Native

`LayoutAnimation` animuje globalne zmiany layoutu (pozycja/rozmiar), gdy widoki
są dodawane, usuwane albo zmieniają rozmiar.

Kiedy używać:

1. Rozwijanie/zwijanie sekcji.
2. Proste przejścia przy dodawaniu/usuwaniu wierszy listy.
3. Aktualizacje UI, gdzie chcesz automatycznej interpolacji layoutu.

Przykład:

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

Stosuj ją do prostych przejść layoutu; przy złożonych animacjach sterowanych
gestami zwykle lepiej sprawdza się Reanimated.

**Krótko**

`LayoutAnimation` jest świetna do prostych zmian układu typu expand/collapse, ale nie do złożonej choreografii gestów.

</details>

<details>
<summary>55. Jak obsługiwać safe area (SafeAreaView)?</summary>

#### React Native

Safe area zapobiega nakładaniu treści na notche, zaokrąglone rogi i paski
systemowe.

Rekomendowane podejście:

1. Używaj `react-native-safe-area-context`.
2. Owiń root aplikacji komponentem `SafeAreaProvider`.
3. Korzystaj z `SafeAreaView` albo `useSafeAreaInsets()` w ekranach/komponentach.

Przykład:

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

Dzięki temu spacing zachowuje się spójnie na iOS i Androidzie.

**Krótko**

Używaj `safe-area-context`, żeby treść była poprawnie widoczna obok notcha i elementów systemowych.

</details>

<details>
<summary>56. Jak obsługiwać zmianę orientacji urządzenia?</summary>

#### React Native

Orientację obsługujesz przez nasłuchiwanie zmian wymiarów/orientacji i
odpowiednie dostosowanie layoutu.

Opcje:

1. `useWindowDimensions()` do responsywnego przeliczania UI.
2. Biblioteki orientacji do jawnego lock/listen.
3. Konfiguracja natywna platformy, gdy obrót ekranu ma być ograniczony.

Zawsze testuj przejścia portrait/landscape na realnych urządzeniach.

**Krótko**

Reaguj na zmiany wymiarów i orientacji, tak aby UI pozostał użyteczny po obrocie.

</details>

<details>
<summary>57. Czym jest PixelRatio i kiedy jest przydatny?</summary>

#### React Native

`PixelRatio` udostępnia narzędzia związane z gęstością pikseli urządzenia.

Przydaje się do:

1. Skalowania assetów UI dla ekranów o wysokiej gęstości.
2. Zaokrąglania rozmiarów layoutu, aby uniknąć rozmycia.
3. Ładowania obrazów w odpowiedniej rozdzielczości.

Pomaga uzyskać ostrzejszy i bardziej spójny wygląd na różnych urządzeniach.

**Krótko**

`PixelRatio` wspiera ostre UI i poprawny dobór rozmiarów/obrazów względem gęstości ekranu.

</details>

<details>
<summary>58. Jak implementować własne fonty?</summary>

#### React Native

Własne fonty dodajesz jako assets aplikacji i odwołujesz się do nich przez
`fontFamily`.

Typowe kroki:

1. Dodaj pliki fontów (`.ttf`/`.otf`) do assets.
2. Skonfiguruj linking (RN CLI albo konfiguracja Expo).
3. Używaj nazw fontów w stylach.
4. W Expo ładuj fonty przed renderem, np. przez `expo-font`.

Warto utrzymywać spójną skalę typografii i strategię fallback.

**Krótko**

Załaduj fonty jako zasoby i stosuj jednolity system typografii w całej aplikacji.

</details>

<details>
<summary>59. Jak obsługiwać accessibility w React Native?</summary>

#### React Native

Dostępność powinna być uwzględniona od początku budowy komponentów.

Kluczowe praktyki:

1. Dodawaj etykiety i podpowiedzi dostępności.
2. Używaj semantycznych ról i stanów.
3. Zapewnij odpowiedni kontrast oraz wielkość targetów dotykowych.
4. Wspieraj dynamiczne skalowanie tekstu.
5. Testuj z VoiceOver (iOS) i TalkBack (Android).

Accessibility poprawia UX wszystkich użytkowników, nie tylko osób korzystających
z technologii asystujących.

**Krótko**

Traktuj dostępność jako standard jakości: role, etykiety, stany, kontrast i testy czytników ekranu.

</details>

<details>
<summary>60. Czym są AccessibilityRole i AccessibilityState?</summary>

#### React Native

`accessibilityRole` opisuje, czym jest element (np. button, header, link), a
`accessibilityState` opisuje jego aktualny stan (np. disabled, selected,
checked, busy, expanded).

Dzięki temu czytniki ekranu przekazują użytkownikowi sensowny kontekst
interaktywnych elementów.

Przykład:

```jsx
<Pressable
  accessibilityRole="button"
  accessibilityState={{ disabled: isDisabled }}
>
  <Text>Submit</Text>
</Pressable>
```

**Krótko**

`Role` mówi czym element jest, a `State` opisuje jego bieżący stan interakcji.

</details>

<details>
<summary>61. Jak obsługiwać push notifications?</summary>

#### React Native

Push notifications zwykle wdraża się przez usługi platformowe + bibliotekę RN.

Typowa konfiguracja:

1. Wybierz dostawcę: Firebase Cloud Messaging (FCM), APNs (iOS) lub np. OneSignal.
2. Skonfiguruj uprawnienia i tokeny natywne (APNs token / FCM token).
3. Zarejestruj listenery dla powiadomień foreground, background i opened.
4. Obsłuż deep linki/nawigację po tapnięciu w notyfikację.

Typowe biblioteki:

1. `@react-native-firebase/messaging` dla FCM.
2. `notifee` do bogatszej obsługi lokalnych/zdalnych powiadomień.

Dobra praktyka: trzymaj małe payloady, zabezpieczaj endpointy i obsługuj odświeżanie tokenów.

**Krótko**

Najważniejsze elementy to rejestracja tokenu, flow uprawnień oraz poprawna obsługa foreground/background i tapnięć.

</details>

<details>
<summary>62. Jak implementować background tasks?</summary>

#### React Native

Background tasks zależą od ograniczeń platformy i rodzaju pracy (sync,
lokalizacja, uploady, powiadomienia).

Podejścia:

1. Używaj natywnych API background przez biblioteki.
2. Planuj okresowe zadania dla lekkiej pracy.
3. Korzystaj z headless tasks na Androidzie, gdy app jest zamknięta/w tle.

Popularne narzędzia:

1. `react-native-background-fetch` dla okresowych zadań fetch.
2. Handlery background z `@react-native-firebase/messaging` dla pracy wyzwalanej push.
3. Natywne services/workers dla scenariuszy zaawansowanych.

Ważne: iOS i Android mają restrykcyjne polityki baterii, więc dokładny czas
wykonania tła nie jest w pełni gwarantowany.

**Krótko**

Zadania w tle są ograniczane przez system, więc projektuj je pod niezawodność, a nie idealny timing.

</details>

<details>
<summary>63. Jak obsługiwać tryb offline i synchronizację danych?</summary>

#### React Native

Tryb offline opiera się na podejściu local-first i synchronizacji po powrocie
połączenia.

Główna strategia:

1. Utrwalaj dane lokalnie (AsyncStorage, SQLite, Realm itd.).
2. Kolejkuj operacje zapisu podczas braku internetu.
3. Wykrywaj zmiany łączności.
4. Po reconnect ponawiaj kolejkę i rozwiązuj konflikty.

Rekomendowane praktyki:

1. Projektuj operacje API jako idempotentne tam, gdzie to możliwe.
2. Używaj znaczników czasu/versioningu do rozwiązywania konfliktów.
3. Pokazuj jasny status UI: offline, syncing, failed, synced.
4. Stosuj retry/backoff, by uniknąć stormu requestów.

**Krótko**

Najlepiej działa model local-first z kolejką zapisów i świadomą konfliktów synchronizacją po reconnect.

</details>

<details>
<summary>64. Jak implementować strategie cache’owania?</summary>

#### React Native

Cache zmniejsza opóźnienia, zużycie sieci i liczbę powtarzanych obliczeń.

Typowe warstwy cache:

1. **Cache odpowiedzi API:** pamięć + trwały cache.
2. **Cache obrazów:** biblioteki do obrazów lub HTTP cache headers.
3. **Cache danych obliczanych:** memoizacja (`useMemo`) dla kosztownych wartości.
4. **Cache zapytań:** np. znormalizowany cache React Query/Apollo.

Praktyczne zasady:

1. Definiuj reguły TTL/invalidation dla każdego zasobu.
2. Stosuj stale-while-revalidate dla responsywnego UI.
3. Czyść cache po logout albo zmianie kontekstu auth.
4. Unikaj nieograniczonego wzrostu cache.

**Krótko**

Dobra strategia cache to jasny zakres, reguły unieważniania i balans świeżości z wydajnością.

</details>

<details>
<summary>65. Czym jest GraphQL i jak używać go w React Native?</summary>

#### React Native

GraphQL to język zapytań i runtime API, który pozwala klientowi pobierać
dokładnie te dane, których potrzebuje, przez jeden endpoint.

Dlaczego jest użyteczny w React Native:

1. Ogranicza over-fetching i under-fetching.
2. Dobrze pasuje do potrzeb danych per ekran.
3. Współpracuje z silnymi wzorcami cache po stronie klienta.

Jak się go używa:

1. Definiujesz zapytania/mutacje/subskrypcje GraphQL.
2. Używasz klienta (najczęściej Apollo Client).
3. Wykonujesz operacje w hookach/komponentach.
4. Obsługujesz loading, error i aktualizacje cache.

Przykładowy kształt zapytania:

```graphql
query GetUser($id: ID!) {
  user(id: $id) {
    id
    name
    avatar
  }
}
```

**Krótko**

GraphQL pozwala ekranom mobilnym pobierać precyzyjnie potrzebne pola i ograniczać nadmiar danych.

</details>

<details>
<summary>66. Czym jest Apollo Client i kiedy warto go używać?</summary>

#### React Native

Apollo Client to popularny klient GraphQL do wykonywania
query/mutation/subscription oraz znormalizowanego cache.

Warto go użyć, gdy:

1. Aplikacja mocno opiera się o API GraphQL.
2. Potrzebujesz rozbudowanego cache i narzędzi aktualizacji danych.
3. Chcesz spójnych wzorców GraphQL między ekranami.

W aplikacjach REST-first lżejsze alternatywy mogą być prostsze.

**Krótko**

Apollo ma sens tam, gdzie GraphQL i znormalizowany cache są kluczowym elementem architektury.

</details>

<details>
<summary>67. Czym jest NetInfo i jak go używać?</summary>

#### React Native

`@react-native-community/netinfo` dostarcza status łączności sieciowej.

Przykłady użycia:

1. Wykrywanie przejść offline/online.
2. Blokowanie albo kolejkowanie akcji sieciowych w trybie offline.
3. Uruchamianie sync/retry po odzyskaniu połączenia.

To jeden z podstawowych elementów odpornego UX typu offline-first.

**Krótko**

NetInfo informuje o łączności, dzięki czemu możesz mądrze sterować requestami i ponawianiem.

</details>

<details>
<summary>68. Jak obsługiwać aktualizacje real-time (WebSockets, subskrypcje)?</summary>

#### React Native

Aktualizacje czasu rzeczywistego zwykle realizuje się przez WebSockety albo
subskrypcje GraphQL.

Typowy wzorzec:

1. Otwórz trwałe połączenie.
2. Subskrybuj konkretne kanały/eventy.
3. Scalaj przychodzące eventy z local/app state.
4. Na zerwaniu połączenia reconnect z backoff.

Obsłuż cykl życia aplikacji i zmiany sieci, aby unikać przestarzałych socketów.

**Krótko**

Utrzymuj stałe kanały zdarzeń, poprawnie łącz eventy ze stanem i obsługuj reconnect z backoff.

</details>

<details>
<summary>69. Jakie są popularne narzędzia testowe (Jest, Detox)?</summary>

#### React Native

Najczęściej używany stos testowy:

1. **Jest:** testy unit i integration.
2. **React Native Testing Library:** testy interakcji komponentów.
3. **Detox:** testy end-to-end UI na emulatorze/symulatorze/urządzeniu.
4. **ESLint/TypeScript w CI:** statyczna kontrola poprawności.

Połączenie tych warstw daje bardziej wiarygodne pokrycie jakości.

**Krótko**

Najlepiej działa testowanie warstwowe: Jest dla logiki/komponentów i Detox dla pełnych flow E2E.

</details>

<details>
<summary>70. Jak pisać testy jednostkowe w React Native?</summary>

#### React Native

Testy jednostkowe najczęściej pisze się w Jest (często z Testing Library dla
komponentów).

Ogólne kroki:

1. Arrange: przygotuj wejścia komponentu/funkcji.
2. Act: wyrenderuj komponent albo wywołaj zachowanie.
3. Assert: sprawdź oczekiwany output, stan lub callbacki.

Dobre testy unit są izolowane, deterministyczne i szybkie.

**Krótko**

Dobre testy jednostkowe są szybkie i powtarzalne, a skupiają się na zachowaniu, nie detalach implementacji.

</details>

<details>
<summary>71. Jak wykonywać testy end-to-end?</summary>

#### React Native

Testowanie end-to-end (E2E) weryfikuje pełne flow użytkownika w realnym lub
symulowanym środowisku aplikacji, łącznie z UI, nawigacją i integracją z backendem.

Typowy proces:

1. Uruchom aplikację w trybie testowym.
2. Wykonuj interakcje jak użytkownik (tap, type, scroll).
3. Sprawdzaj widoczne rezultaty i stan nawigacji.
4. Uruchamiaj testy w CI na wielu urządzeniach/konfiguracjach.

Najpopularniejsze narzędzie E2E w RN to **Detox**.

Dobre praktyki:

1. Dodawaj stabilne `testID` do kluczowych elementów.
2. Utrzymuj deterministykę testów (kontrola sieci/danych).
3. Priorytetyzuj krytyczne ścieżki użytkownika (auth, checkout, core flow).

**Krótko**

Testy E2E potwierdzają najważniejsze ścieżki użytkownika na granicy realnej nawigacji i integracji.

</details>

<details>
<summary>72. Jakie narzędzia debugowania są dostępne (Flipper)?</summary>

#### React Native

Debugowanie RN zwykle łączy logi runtime, inspekcję komponentów i diagnostykę
natywną.

Popularne narzędzia:

1. **Flipper:** pluginy do logów, sieci, layout inspectora i wydajności.
2. **React DevTools:** inspekcja drzewa komponentów, propsów, stanu i hooków.
3. **Metro logs:** output konsoli i ostrzeżenia/błędy runtime.
4. **Xcode / Android Studio:** natywne crash logi, logi urządzenia i breakpointy.
5. **Wsparcie debugowania Hermes:** profilowanie/inspekcja specyficzna dla silnika JS.

Flipper jest szczególnie przydatny jako centralny hub desktopowy dla debugowania JS + native.

**Krótko**

Najczęściej używa się zestawu: logi, DevTools/Flipper oraz natywne logi platformowe.

</details>

<details>
<summary>73. Jak profilować wydajność w React Native?</summary>

#### React Native

Profilowanie wydajności pomaga znaleźć realne bottlenecks w renderze,
wykonaniu JS i obciążeniu UI thread.

Kluczowe metody profilowania:

1. Używaj React DevTools Profiler do analizy kosztownych renderów.
2. Używaj pluginów Flippera do wydajności i timingu sieci.
3. Mierz czas startu i opóźnienia przejść ekranów na realnych urządzeniach.
4. Analizuj zachowanie list (`FlatList` config, dropped frames).
5. Profiluj warstwę natywną przez Xcode Instruments / Android Profiler.

Na co patrzeć:

1. Częste, niepotrzebne rerendery.
2. Długie taski JS blokujące interakcje.
3. Ciężkie operacje obrazu/layoutu na kluczowych ekranach.

Profiluj na buildach zbliżonych do produkcyjnych, nie tylko na debug.

**Krótko**

Najpierw profiluj na warunkach produkcyjnych, dopiero potem optymalizuj rzeczywiste wąskie gardła.

</details>

<details>
<summary>74. Czym jest Expo i kiedy warto go używać?</summary>

#### React Native

Expo to platforma i toolchain wokół React Native, który upraszcza development,
buildy i aktualizacje.

Warto użyć Expo, gdy:

1. Chcesz szybszy start projektu i większą produktywność developerską.
2. Potrzebujesz popularnych funkcji natywnych przez Expo SDK (kamera, notyfikacje itd.).
3. Preferujesz uproszczone workflow buildów lokalnych/chmurowych (EAS).

Expo obejmuje:

1. Narzędzia developerskie i runtime.
2. Moduły Expo SDK.
3. Narzędzia build i submission.
4. Wsparcie OTA updates przez usługi Expo.

To mocny domyślny wybór dla wielu aplikacji, o ile od początku nie potrzebujesz
głębokiej, niestandardowej kontroli natywnej.

**Krótko**

Expo jest najlepsze, gdy zależy ci na szybkim dostarczaniu i mniejszym narzucie konfiguracji natywnej.

</details>

<details>
<summary>75. Jaka jest różnica między Expo managed a bare workflow?</summary>

#### React Native

Różnica dotyczy poziomu kontroli nad projektami natywnymi.

1. **Managed workflow:** Expo zarządza konfiguracją natywną za ciebie. Pracujesz głównie w JS/TS i konfiguracji Expo. Szybszy development, mniej utrzymania natywnego.
2. **Bare workflow:** masz pełne projekty natywne iOS/Android (podobnie jak w czystym RN). Większa kontrola, ale też większa złożoność setupu i utrzymania.

Wybierz managed, gdy najważniejsze są szybkość i prostota. Wybierz bare, gdy
potrzebujesz własnego kodu natywnego lub zaawansowanej integracji low-level.

**Krótko**

Managed stawia na szybkość, bare na pełną kontrolę i głębszą personalizację natywną.

</details>

<details>
<summary>76. Jakie są plusy i minusy Expo?</summary>

#### React Native

Plusy:

1. Szybki setup projektu i iteracja.
2. Bogate SDK dla popularnych funkcji natywnych.
3. Prosty pipeline build/update z EAS.
4. Dobre DX dla małych i średnich zespołów.

Minusy:

1. Mniejsza bezpośrednia kontrola natywna w managed workflow.
2. Część edge case’ów natywnych wymaga bare/eject.
3. Zależność od decyzji i narzędzi ekosystemu Expo.

Expo daje świetną produktywność, ale kosztem części elastyczności low-level.

**Krótko**

Expo poprawia DX i szybkość dostarczania, ale głęboka customizacja natywna może wymagać bare workflow.

</details>

<details>
<summary>77. Jak obsługiwać buildy aplikacji i deployment?</summary>

#### React Native

Pipeline build/deploy zwykle obejmuje:

1. Wersjonowanie i changelog.
2. Build CI dla Androida i iOS.
3. Automatyczne testy i quality gates.
4. Signing i generowanie artefaktów.
5. Wysyłkę do sklepów (Play Console / App Store Connect).
6. Monitoring po release i plan rollbacku.

Aplikacje Expo często używają EAS Build/Submit, a bare zwykle Fastlane/skryptów CI.

**Krótko**

Traktuj release jak pipeline: wersjonowanie, kontrola jakości w CI, signing, publikacja i monitoring.

</details>

<details>
<summary>78. Czym jest code signing i dlaczego jest ważny?</summary>

#### React Native

Code signing kryptograficznie potwierdza tożsamość i integralność aplikacji.

Dlaczego to ważne:

1. Potwierdza autentyczność wydawcy aplikacji.
2. Chroni przed zaufaniem do zmodyfikowanych binarek.
3. Jest wymagany przez sklepy aplikacji do dystrybucji.

iOS używa certyfikatów/profili, a Android keystore.

**Krótko**

Code signing potwierdza autentyczność aplikacji i jest obowiązkowy w zaufanej dystrybucji.

</details>

<details>
<summary>79. Jak zarządzać środowiskami (dev/staging/prod)?</summary>

#### React Native

Używaj jawnej konfiguracji środowiskowej dla każdego targetu builda.

Typowy setup:

1. Osobne endpointy API i feature flagi.
2. Build variants/flavors (Android) oraz schemes (iOS).
3. Sekrety środowiskowe w bezpiecznych zmiennych CI.
4. Jasne nazewnictwo kanałów release.

Wybór środowiska powinien być deterministyczny i widoczny w diagnostyce aplikacji.

**Krótko**

Rozdziel konfiguracje per środowisko i nie trzymaj sekretów ani krytycznych configów w kodzie źródłowym.

</details>

<details>
<summary>80. Czym jest CodePush / OTA updates i kiedy tego używać?</summary>

#### React Native

OTA updates dostarczają JavaScript/assets bez pełnego release’u sklepowego.

Kiedy przydatne:

1. Szybkie poprawki błędów w warstwie JS.
2. Małe aktualizacje logiki lub treści.

Ograniczenia:

1. Nie aktualizują natywnego kodu binarnego.
2. Muszą być zgodne z politykami sklepów.

Stosuj OTA do bezpiecznych, inkrementalnych zmian JS, ale nie jako zamiennik
pełnych release’ów binarnych.

**Krótko**

OTA świetnie działa dla poprawek JS, ale zmiany natywne nadal wymagają nowej binarki sklepowej.

</details>

<details>
<summary>81. Jakie są best practices przy strukturze dużego codebase?</summary>

#### React Native

W dużych projektach React Native struktura powinna poprawiać odnajdywanie kodu,
własność feature’ów i długoterminowy refactoring.

Najczęstsze podejście to organizacja feature-first:

1. Grupowanie według domen/feature’ów (`features/auth`, `features/profile` itd.).
2. Wspólne UI w `components/`, a generyczne hooki w `hooks/`.
3. Oddzielenie warstwy API/danych (`services/`, `api/`, `store/`).
4. Centralizacja konfiguracji i stałych aplikacyjnych (`config/`, `theme/`, `env/`).
5. Jasne granice i publiczne entry pointy dla każdego feature’a.

Dodatkowo wymuszaj spójność przez linting, formatowanie, TypeScript i
konwencje architektoniczne opisane w repo.

**Krótko**

Organizuj projekt wokół granic feature’ów, aby utrzymać czytelność, ownership i łatwiejszy refactoring.

</details>

<details>
<summary>82. Jak zapewnić skalowalność i maintainability?</summary>

#### React Native

Skalowalność i utrzymywalność wynikają z dobrej architektury oraz dyscypliny
procesu inżynierskiego.

Kluczowe praktyki:

1. Stosuj modularne granice feature’ów i reużywalne prymitywy.
2. Trzymaj logikę biznesową poza komponentami UI.
3. Używaj TypeScript dla bezpieczniejszych refactorów.
4. Dodaj testy automatyczne na poziomie unit/integration/E2E.
5. Egzekwuj jakość kodu przez ESLint, Prettier, CI checks i code review.
6. Monitoruj regresje wydajności oraz crash analytics.
7. Dokumentuj wzorce (state, navigation, networking, error handling).

Skalowalny codebase jest przewidywalny: nowe feature’y podążają za tymi samymi
wzorcami przy minimalnej liczbie wyjątków.

**Krótko**

Skalowalność daje spójna architektura, automatyzacja i konsekwentnie egzekwowane standardy inżynierskie.

</details>

<details>
<summary>83. Jakie są best practices dla danych wrażliwych?</summary>

#### React Native

Dane wrażliwe (tokeny, sekrety, PII) trzeba chronić w storage, transmisji i
logach.

Dobre praktyki:

1. Nigdy nie hardcode’uj sekretów w kodzie i nie wysyłaj prywatnych kluczy w appce.
2. Używaj secure storage (iOS Keychain / Android Keystore wrappers).
3. Wymuszaj HTTPS/TLS dla całego ruchu API.
4. Ograniczaj zakres i czas przechowywania danych wrażliwych.
5. Redaguj pola wrażliwe w logach, analityce i crash reportach.
6. Rotuj tokeny/klucze i wdrażaj mechanizmy unieważniania.
7. Dodaj jailbreak/root oraz tamper detection, jeśli wymaga tego model zagrożeń.

`AsyncStorage` nie nadaje się do wysoko wrażliwych sekretów.

**Krótko**

Sekrety trzymaj wyłącznie w bezpiecznym storage, minimalizuj ekspozycję i nie traktuj zwykłego storage jako sejfu.

</details>

<details>
<summary>84. Jak obsługiwać authentication (biometria, tokeny)?</summary>

#### React Native

Authentication w React Native najczęściej łączy bezpieczne zarządzanie tokenami
z opcjonalnym biometrycznym odblokowaniem dla wygody.

Typowy flow:

1. Użytkownik loguje się (credentials/OAuth/social).
2. Backend zwraca access + refresh token.
3. Tokeny zapisujesz w secure storage (nie w plain AsyncStorage).
4. Dołączasz access token do requestów API.
5. Odświeżasz token po wygaśnięciu access tokena.
6. Przy logout czyścisz tokeny i stan sesji.

Użycie biometrii:

1. Face ID / Touch ID / biometria Android do lokalnego re-auth.
2. Model serwerowy pozostaje token-based; biometria chroni lokalny dostęp.

Warto mieć scentralizowany auth state i interceptory requestów, by nie
powielać logiki.

**Krótko**

Łącz pełny lifecycle tokenów z biometrią jako wygodną warstwą lokalnego ponownego uwierzytelnienia.

</details>

<details>
<summary>85. Czym jest react-native-webview i kiedy go używać?</summary>

#### React Native

`react-native-webview` to komponent renderujący treści webowe wewnątrz
aplikacji mobilnej.

Use case’y:

1. Wyświetlanie zewnętrznych i wewnętrznych stron web.
2. Osadzanie istniejących flow webowych (help center, płatności, dokumentacja).
3. Integracja modułów hybrydowych, gdy pełny rewrite natywny nie jest potrzebny.

Przykład:

```jsx
import { WebView } from 'react-native-webview';

function DocsScreen() {
  return <WebView source={{ uri: 'https://example.com/docs' }} />;
}
```

W krytycznych flow używaj ostrożnie: pod względem UX, wydajności, bezpieczeństwa
i integracji natywnej pełne ekrany native/RN zwykle wypadają lepiej.

**Krótko**

WebView sprawdza się dla zamkniętych flow webowych, ale rdzeń aplikacji lepiej trzymać w natywnym/RN UI.

</details>

<details>
<summary>86. Czym jest react-native-svg i dlaczego jest przydatny?</summary>

#### React Native

`react-native-svg` dostarcza w RN prymitywy do renderowania SVG.

Dlaczego to przydatne:

1. Grafika wektorowa niezależna od rozdzielczości.
2. Świetnie nadaje się do ikon, wykresów i ilustracji.
3. Jest bardziej elastyczna niż statyczne assety PNG.

To standardowa zależność w wielu aplikacjach z rozbudowanym designem.

**Krótko**

Obsługa SVG daje ostre, skalowalne grafiki i ikony na różnych gęstościach ekranów.

</details>

<details>
<summary>87. Jak zaimplementować drawer navigation?</summary>

#### React Native

Użyj `@react-navigation/drawer`.

Podstawowy flow:

1. Zainstaluj zależności drawer navigatora.
2. Utwórz `Drawer.Navigator` z ekranami.
3. W razie potrzeby spersonalizuj zawartość drawer.
4. Połącz go z navigatorami stack/tab.

Trzymaj główne trasy w drawerze i unikaj nadmiernego zagnieżdżania.

**Krótko**

Drawer dobrze sprawdza się dla sekcji top-level, jeśli hierarchia tras pozostaje prosta i przewidywalna.

</details>

<details>
<summary>88. Czym jest gesture-based navigation?</summary>

#### React Native

Gesture-based navigation oznacza nawigację gestami (swipe back, swipe zakładek,
przeciąganie drawer itd.).

W RN zwykle jest realizowana przez React Navigation + Gesture Handler.

Korzyści:

1. Bardziej natywne odczucie interakcji.
2. Szybsza obsługa nawigacji jedną ręką.

**Krótko**

Nawigacja gestami poprawia mobile UX, jeśli jest zgodna z konwencjami platformy.

</details>

<details>
<summary>89. Jak zaimplementować shared element transitions?</summary>

#### React Native

Shared element transitions animują wspólny element UI między dwoma ekranami.

Typowa implementacja:

1. Użyj biblioteki wspierającej shared transitions.
2. Przypisz zgodne shared ID dla elementu źródłowego i docelowego.
3. Skonfiguruj zachowanie przejścia w nawigacji.

To poprawia ciągłość wizualną w flow typu lista -> detal.

**Krótko**

Shared transitions utrzymują kontekst wizualny przy przejściach między listą a detalem.

</details>

<details>
<summary>90. Czym jest renderer Fabric i czym się różni?</summary>

#### React Native

Fabric to nowy renderer RN w ramach New Architecture.

Różnice względem legacy renderera:

1. Lepsza integracja z współbieżnymi wzorcami React.
2. Wydajniejszy pipeline renderowania.
3. Ścisła współpraca z JSI/TurboModules.
4. Niższe opóźnienia dla części aktualizacji UI.

To kluczowy element modernizacji React Native.

**Krótko**

Fabric poprawia wydajność renderowania i integruje się z nowoczesnym modelem runtime RN.

</details>

<details>
<summary>91. Jaka jest przewaga architektury TurboModules?</summary>

#### React Native

TurboModules to część New Architecture React Native, która usprawnia sposób
ładowania i wywoływania modułów natywnych z JavaScript.

Główne zalety:

1. **Lazy loading:** moduły inicjalizują się dopiero, gdy są potrzebne.
2. **Lepsza wydajność:** mniejszy narzut startowy i niższy koszt bridge.
3. **Type safety przez codegen:** mocniejsze kontrakty między JS i warstwą natywną.
4. **Lepsza maintainability:** bardziej klarowne interfejsy modułów i nowocześniejsza integracja natywna.

TurboModules są szczególnie wartościowe w dużych aplikacjach z wieloma
zależnościami natywnymi.

**Krótko**

TurboModules poprawiają start i dostęp do warstwy natywnej przez lazy loading i typowane interfejsy.

</details>

<details>
<summary>92. Jak obsługiwać error boundaries w React Native?</summary>

#### React Native

Error Boundaries przechwytują błędy renderowania w drzewie potomnym
komponentów i zapobiegają awarii całego UI aplikacji.

W React Native implementuje się je jako komponenty klasowe z:

1. `static getDerivedStateFromError(error)`
2. `componentDidCatch(error, info)`

Przykład:

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
    // Wyślij błąd do narzędzia monitoringu
  }

  render() {
    if (this.state.hasError) {
      return (
        <View>
          <Text>Wystąpił błąd.</Text>
        </View>
      );
    }

    return this.props.children;
  }
}
```

Otaczaj krytyczne drzewa ekranów boundary i raportuj błędy do monitoringu.

**Krótko**

Error boundaries izolują crashe renderowania i pokazują fallback UI zamiast psuć całą aplikację.

</details>

<details>
<summary>93. Jak obsługiwać błędy globalne?</summary>

#### React Native

Globalna obsługa błędów obejmuje nieobsłużone wyjątki JS, odrzucone promises
oraz crashe natywne.

Typowa strategia:

1. Skonfiguruj globalny handler błędów JS.
2. Przechwytuj nieobsłużone odrzucenia promise.
3. Zintegruj monitoring crash/error (np. Sentry, Bugsnag).
4. Loguj kontekst (użytkownik/sesja/ekran) w bezpieczny sposób.
5. Pokazuj fallback UI, gdy to możliwe, i odzyskuj działanie aplikacji.

Dodatkowo śledź crashe natywne osobno przez narzędzia platformowe i SDK monitoringu.

**Krótko**

Przechwytuj nieobsłużone błędy JS i natywne centralnie, a raporty wzbogacaj o kontekst potrzebny do debugowania.

</details>

<details>
<summary>94. Czym jest AppState i jak się go używa?</summary>

#### React Native

`AppState` pozwala wykryć, czy aplikacja jest aktywna, działa w tle czy jest
nieaktywna.

Typowe stany:

1. `active`: aplikacja na pierwszym planie i interaktywna.
2. `background`: aplikacja działa w tle.
3. `inactive` (głównie iOS, stan przejściowy).

Use case’y:

1. Pauza/wznowienie timerów, wideo lub pollingu.
2. Odświeżanie wrażliwych danych po powrocie aplikacji na pierwszy plan.
3. Wyzwalanie zdarzeń analytics/lifecycle sesji.

Przykład:

```jsx
import { AppState } from 'react-native';

const subscription = AppState.addEventListener('change', nextState => {
  // Obsługa zmiany stanu
});

// Później:
subscription.remove();
```

**Krótko**

AppState pomaga poprawnie pauzować i wznawiać pracę, gdy aplikacja przechodzi między foreground a background.

</details>

<details>
<summary>95. Jak obsługiwać przycisk wstecz Androida (BackHandler)?</summary>

#### React Native

Na Androidzie sprzętowy przycisk wstecz można obsłużyć przez `BackHandler`.

Wzorzec:

1. Subskrybuj `hardwareBackPress`.
2. Zwróć `true`, aby przejąć zdarzenie.
3. Zwróć `false`, aby uruchomić domyślne zachowanie (np. nawigację wstecz).

Przykład:

```jsx
import { BackHandler } from 'react-native';
import { useEffect } from 'react';

useEffect(() => {
  const sub = BackHandler.addEventListener('hardwareBackPress', () => {
    // Custom logic
    return false;
  });

  return () => sub.remove();
}, []);
```

Przy React Navigation najpierw preferuj jej API back handling, a `BackHandler`
traktuj jako narzędzie dla niestandardowych edge case’ów.

**Krótko**

BackHandler pozwala świadomie sterować zachowaniem przycisku wstecz i spiąć je z logiką nawigacji.

</details>

<details>
<summary>96. Jak optymalizować rozmiar bundla?</summary>

#### React Native

Optymalizacja rozmiaru bundla polega na zmniejszeniu dostarczanego JS/assets.

Praktyczne kroki:

1. Usuń nieużywane zależności.
2. Importuj tylko potrzebne moduły.
3. Kompresuj i skaluj obrazy oraz media.
4. Włącz minifikację i optymalizacje builda produkcyjnego.
5. Dziel cięższe funkcje tam, gdzie pozwala na to architektura.

Mniejszy bundle poprawia czas startu i szybkość dostarczania aktualizacji.

**Krótko**

Lżejszy bundle przyspiesza uruchamianie i aktualizacje, bo aplikacja wysyła mniej JS i zasobów.

</details>

<details>
<summary>97. Jak obsługiwać upgrade’y wersji i migracje?</summary>

#### React Native

Upgrade’y najlepiej wykonywać krokowo i z automatyczną walidacją.

Rekomendowany proces:

1. Aktualizuj w małych krokach.
2. Czytaj release notes RN i listę breaking changes.
3. Korzystaj z helperów/diffów do upgrade React Native.
4. Uruchamiaj pełne testy na iOS i Androidzie.
5. Wdrażaj z monitoringiem i gotowym planem rollbacku.

W miarę możliwości unikaj dużych skoków o wiele wersji naraz.

**Krótko**

Aktualizuj inkrementalnie, sprawdzaj breaking changes i waliduj regresję na obu platformach.

</details>

<details>
<summary>98. Jakie są ograniczenia React Native?</summary>

#### React Native

Typowe ograniczenia:

1. Część zaawansowanych API natywnych wymaga własnego kodu natywnego.
2. Jakość pakietów w ekosystemie bywa nierówna.
3. Wydajność może spaść przy słabej architekturze i ciężkiej pracy JS.
4. Upgrade’y i tooling natywny mogą być złożone.

Mimo to RN pozostaje bardzo skuteczny dla wielu aplikacji cross-platform.

**Krótko**

RN jest produktywny, ale bardziej zaawansowane scenariusze nadal często wymagają kodu natywnego i świadomego tuningu.

</details>

<details>
<summary>99. Jak implementować synchronizację w czasie rzeczywistym?</summary>

#### React Native

Synchronizacja real-time łączy transport zdarzeń na żywo z bezpiecznymi
aktualizacjami lokalnymi odpornymi na konflikty.

Typowa strategia:

1. Odbieraj zdarzenia przez WebSocket/subskrypcje.
2. Stosuj optimistic updates dla akcji użytkownika.
3. Utrwalaj stan lokalny dla ciągłości offline.
4. Po reconnect uzgadniaj prawdę serwera z lokalnymi zmianami.
5. Używaj versioningu i reguł rozwiązywania konfliktów.

To utrzymuje świeżość danych przy zachowaniu spójności.

**Krótko**

Real-time sync wymaga strumienia zdarzeń, poprawnej rekonsyliacji konfliktów i odporności na tryb offline.

</details>

<details>
<summary>100. Jak projektować skalowalną architekturę mobilną?</summary>

#### React Native

Skalowalna architektura mobilna opiera się na jasnych granicach i przewidywalnych
przepływach.

Główne zasady:

1. Modułowa struktura oparta o feature’y.
2. Separacja UI, logiki domenowej i warstwy danych.
3. Jawna strategia stanu (local/global/server state).
4. Spójne wzorce nawigacji, błędów i komunikacji sieciowej.
5. Automatyczne quality gates (testy, lint, CI, monitoring).

Architektura powinna optymalizować szybkość zmian długoterminowo, a nie tylko
tempo początkowego developmentu.

**Krótko**

Projektuj wokół modułowych granic, czytelnego przepływu danych i egzekwowalnych standardów zespołu.

</details>

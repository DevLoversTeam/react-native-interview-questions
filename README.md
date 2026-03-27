**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  React Native <img src="./assets/reactnative.svg" width="40" height="40" />
</h1>

<h2>Найпопулярніші запитання та відповіді на співбесіді з React Native</h2>

<details>
<summary>1. Що таке React Native і чим він відрізняється від React?</summary>

#### React Native

React Native — це open-source фреймворк для створення мобільних застосунків за
допомогою JavaScript/TypeScript і React.

Ключова відмінність:

1. **React (React.js):** створює веб-інтерфейси, які рендеряться у DOM браузера
   (`div`, `span` тощо).
2. **React Native:** створює iOS/Android застосунки, які рендеряться в нативні
   компоненти платформи (`View`, `Text`, `Image` тощо).

Обидва використовують компонентний підхід, props/state і hooks, але мають різні
цільові платформи та рендеринг.

**Коротко**

React Native — для мобільних застосунків з нативними UI-компонентами, а React —
для вебу та DOM.

</details>

<details>
<summary>2. Поясніть концепцію JSX у React Native.</summary>

#### React Native

JSX (JavaScript XML) — це розширення синтаксису, яке дозволяє декларативно
описувати структуру інтерфейсу в HTML-подібному стилі всередині JavaScript.

У React Native JSX використовується з нативними компонентами:

```jsx
function Greeting() {
  return <Text>Hello, React Native!</Text>;
}
```

Нотатки:

1. JSX — це не HTML. Babel перетворює його у виклики JavaScript.
2. Ви можете вбудовувати JavaScript-вирази всередині `{}`.
3. У React Native JSX використовуються нативні компоненти (`View`, `Text`), а
   не браузерні теги (`div`, `p`).

**Коротко**

JSX — це зручний синтаксис для опису UI, який React Native мапить на нативні
компоненти.

</details>

<details>
<summary>3. Як створити функціональний компонент у React Native?</summary>

#### React Native

Функціональний компонент — це JavaScript-функція, яка повертає JSX.

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

Також можна використовувати синтаксис стрілкової функції:

```jsx
const ProfileCard = () => (
  <View>
    <Text>Profile</Text>
  </View>
);
```

**Коротко**

Це звичайна функція, яка повертає JSX, і зазвичай поєднується з хуками для
стану та побічних ефектів.

</details>

<details>
<summary>4. Які є базові компоненти в React Native (View, Text, Image тощо)?</summary>

#### React Native

Базові компоненти — це вбудовані UI-примітиви React Native для створення
мобільних інтерфейсів.

Поширені базові компоненти:

1. **View:** базовий контейнер для розмітки та стилізації.
2. **Text:** відображення тексту.
3. **Image:** рендер зображень з локальних ресурсів або URL.
4. **TextInput:** поле вводу тексту.
5. **ScrollView:** прокручуваний контейнер.
6. **FlatList / SectionList:** ефективний рендер великих списків.
7. **Pressable / TouchableOpacity:** обробка натискань.
8. **SafeAreaView:** врахування безпечних зон екрана (вирізи, заокруглення).

Ці компоненти відповідають нативним UI-елементам на iOS і Android.

**Коротко**

Це основні будівельні блоки React Native, з яких складається інтерфейс будь-якої
мобільної апки.

</details>

<details>
<summary>5. Що таке props у React Native і як їх використовують?</summary>

#### React Native

Props (properties) — це read-only вхідні дані, які передаються від батьківського
компонента до дочірнього.

Їх використовують для:

1. Передачі даних (текст, числа, об'єкти, масиви).
2. Передачі поведінки (callback-функції).
3. Налаштування повторно використовуваних компонентів.

Приклад:

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

Тут `name` — це prop, який передається з `App` у `WelcomeMessage`.

**Коротко**

Props — це незмінні вхідні параметри компонента для передачі даних і поведінки
зверху вниз по дереву.

</details>

<details>
<summary>6. Що таке state у React Native і як ним керувати за допомогою хуків?</summary>

#### React Native

State — це локальні дані компонента, які можуть змінюватися з часом і
спричиняти оновлення UI.

У функціональних компонентах стан зазвичай керується хуком `useState`:

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

Для складнішої логіки можна використовувати `useReducer`.

**Коротко**

State — це змінювані локальні дані компонента; хуки дають передбачуваний спосіб
оновлювати їх і перерендерювати інтерфейс.

</details>

<details>
<summary>7. Яка різниця між state і props?</summary>

#### React Native

`state` і `props` обидва зберігають дані для рендерингу, але мають різні ролі:

1. **Props:** read-only вхідні дані, які передаються від батьківського
   компонента до дочірнього.
2. **State:** внутрішні, змінювані дані, якими керує сам компонент.

Швидке порівняння:

1. **Хто володіє даними?** Props: батьківський компонент. State: поточний
   компонент.
2. **Чи можна змінити локально?** Props: ні. State: так, через хуки, наприклад
   `useState`.
3. **Призначення:** Props: конфігурація та потік даних між компонентами. State:
   динамічна поведінка UI всередині компонента.

**Коротко**

Головна відмінність — у власності: props приходять ззовні, а state належить
самому компоненту.

</details>

<details>
<summary>8. Як обробляти користувацький ввід у React Native?</summary>

#### React Native

Користувацький ввід зазвичай обробляють через контрольовані компоненти, найчастіше
`TextInput`, у зв'язці зі state.

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

Ключові події/обробники:

1. `onChangeText`: оновлює текст у state.
2. `onPress`: обробляє натискання кнопок/елементів.
3. `onSubmitEditing`: спрацьовує при підтвердженні вводу в `TextInput`.

**Коротко**

Найчастіше використовують контрольований ввід: значення зберігається у state і
оновлюється через обробники.

</details>

<details>
<summary>9. Як стилізувати компоненти у React Native?</summary>

#### React Native

У React Native стилі задаються JavaScript-об'єктами, а не CSS-файлами.

Поширені способи стилізації:

1. **Inline-стилі** (швидко для локальних випадків):

```jsx
<Text style={{ color: 'blue', fontSize: 18 }}>Hello</Text>
```

2. **`StyleSheet.create`** (рекомендовано для більшості випадків):

```jsx
const styles = StyleSheet.create({
  title: { color: 'blue', fontSize: 18 },
});
```

3. **Масиви стилів** (умовна/композиційна стилізація):

```jsx
<Text style={[styles.title, isActive && styles.active]}>Hello</Text>
```

Синтаксис близький до CSS, але властивості пишуться в camelCase (наприклад,
`backgroundColor`, `fontSize`).

**Коротко**

Стилі в RN — це JS-об'єкти; зазвичай їх централізують для повторного
використання та консистентності.

</details>

<details>
<summary>10. Що таке StyleSheet і коли його використовувати?</summary>

#### React Native

`StyleSheet` — це утиліта React Native для структурованого визначення й
організації стилів.

Приклад:

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

Коли використовувати:

1. Коли стилі повторюються в кількох елементах.
2. Коли потрібні чистіший і підтримуваний код компонента.
3. Коли потрібен консистентний і масштабований підхід до стилізації в більших
   екранах/застосунках.

**Коротко**

StyleSheet варто використовувати для чистих, повторно використовуваних стилів і
кращої підтримуваності коду.

</details>

<details>
<summary>11. Поясніть Flexbox і його роль у розмітці.</summary>

#### React Native

Flexbox — це основна система розмітки в React Native. Вона керує тим, як
компоненти змінюють розмір, вирівнюються та розподіляються всередині контейнера.

У React Native значення Flexbox за замовчуванням трохи відрізняються від
веб-CSS:

1. `flexDirection` за замовчуванням — `column`.
2. `alignContent` за замовчуванням — `flex-start`.
3. `flexShrink` за замовчуванням — `0`.

Поширені властивості:

1. `flex`: визначає, скільки простору займає елемент відносно сусідів.
2. `flexDirection`: розкладка по рядку або колонці.
3. `justifyContent`: вирівнювання по головній осі.
4. `alignItems`: вирівнювання по поперечній осі.
5. `gap` (у сучасних версіях RN): відступи між дочірніми елементами.

Приклад:

```jsx
<View
  style={{ flex: 1, flexDirection: 'row', justifyContent: 'space-between' }}
>
  <View style={{ width: 50, height: 50, backgroundColor: 'red' }} />
  <View style={{ width: 50, height: 50, backgroundColor: 'blue' }} />
</View>
```

**Коротко**

Flexbox — це про роботу з осями: головна й поперечна, плюс правильне
`justify/align` вирівнювання.

</details>

<details>
<summary>12. Як реалізувати адаптивний дизайн у React Native?</summary>

#### React Native

Адаптивність у React Native реалізується через поєднання гнучких макетів і
API, що враховують характеристики пристрою.

Поширені підходи:

1. Використовувати Flexbox (`flex`, `%`, вирівнювання) замість фіксованих
   розмірів.
2. Використовувати `Dimensions` або `useWindowDimensions()` для розмірів екрана.
3. Використовувати `Platform` для платформених відмінностей.
4. Використовувати `SafeAreaView`, щоб враховувати вирізи та системні панелі.
5. Масштабувати типографіку й відступи через спільні константи.

Приклад:

```jsx
import { useWindowDimensions, View } from 'react-native';

function ResponsiveCard() {
  const { width } = useWindowDimensions();
  const isTablet = width >= 768;

  return <View style={{ padding: isTablet ? 24 : 16 }} />;
}
```

**Коротко**

Адаптивність у RN зазвичай будується на Flexbox, розмірах екрана і врахуванні
safe-area.

</details>

<details>
<summary>13. Як дебажити React Native застосунок?</summary>

#### React Native

Дебаг у React Native зазвичай виконується комбінацією вбудованих і зовнішніх
інструментів.

Основні варіанти:

1. **Metro logs:** `console.log`, попередження та помилки в терміналі/виводі.
2. **React Native Dev Menu:** перезавантаження застосунку, інспекція UI,
   увімкнення debug-інструментів.
3. **React DevTools:** перегляд дерева компонентів, props і стану хуків.
4. **Flipper:** інспекція мережі, логів, layout та performance-плагіни.
5. **Нативні інструменти:** Xcode (iOS) і Android Studio (Android) для нативних
   падінь і логів.

Найкраща практика: мати чіткі кроки відтворення, ізолювати проблемний компонент
і перевіряти на iOS та Android, якщо це релевантно.

**Коротко**

Найкраще працює стек інструментів: логи, DevTools/Flipper і нативні логи для
платформених проблем.

</details>

<details>
<summary>14. Що таке Fast Refresh і як він працює?</summary>

#### React Native

Fast Refresh — це dev-функція, яка оновлює застосунок одразу після змін коду,
намагаючись зберігати стан компонента.

Як це працює:

1. Ви зберігаєте файл.
2. Metro перебудовує лише змінені модулі.
3. React Native інжектить оновлений код у запущений застосунок.
4. UI оновлюється миттєво, зазвичай без повного рестарту.

Нотатки:

1. Локальний стан функціональних компонентів зазвичай зберігається.
2. Якщо зміни торкаються ініціалізації модулів або некомпонентних експортів,
   React Native може зробити ширше перезавантаження.
3. Це лише інструмент розробки, не частина продакшен-поведінки.

**Коротко**

Fast Refresh швидко підтягує зміни в dev-режимі й у більшості випадків зберігає
локальний стан.

</details>

<details>
<summary>15. Що таке Touchable-компоненти і як вони працюють?</summary>

#### React Native

Touchable-компоненти — це інтерактивні обгортки, що реагують на натискання.
Вони дозволяють виконувати дії на кшталт відкриття екранів, відправки форм або
вибору елементів.

Поширені варіанти:

1. `Pressable` (сучасний і гнучкий, часто рекомендований).
2. `TouchableOpacity` (змінює прозорість при натисканні).
3. `TouchableHighlight` (показує підсвітку під дочірнім елементом).
4. `TouchableWithoutFeedback` (без візуального фідбеку).

Приклад:

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

Вони підтримують події на кшталт `onPress`, `onPressIn`, `onPressOut` та
`onLongPress`.

**Коротко**

Це обгортки для натискань; у сучасних проєктах зазвичай починають із `Pressable`.

</details>

<details>
<summary>16. Як організувати навігацію в React Native (React Navigation)?</summary>

#### React Native

Навігацію в React Native зазвичай реалізують через `@react-navigation/*`.

Типовий підхід:

1. Встановити ядро React Navigation і потрібні навігатори.
2. Обгорнути застосунок у `NavigationContainer`.
3. Описати stack/tab/drawer навігацію.
4. Переходити між екранами через `navigation.navigate('ScreenName')`.

Для більшості застосунків ефективно комбінувати Stack + Tab і тримати чітку
структуру роутів.

**Коротко**

Будуй навігацію композицією навігаторів (stack/tab/drawer) і тримай структуру
маршрутів явною.

</details>

<details>
<summary>17. Яка роль NavigationContainer?</summary>

#### React Native

`NavigationContainer` — це кореневий провайдер, який керує станом навігації та
зв'язує навігатори із середовищем застосунку.

Він відповідає за:

1. Зберігання поточного стану дерева навігації.
2. Обробку deep links/linking.
3. Надання навігаційного контексту всім екранам.

Без нього React Navigation не працюватиме.

**Коротко**

Це кореневий контейнер навігації, який зберігає стан і дає контекст усій
навігаційній системі.

</details>

<details>
<summary>18. Як передавати параметри між екранами?</summary>

#### React Native

Параметри передаються через навігаційні методи.

Приклад:

```jsx
navigation.navigate('Profile', { userId: '42' });
```

Отримання параметрів на цільовому екрані:

```jsx
const { userId } = route.params;
```

Параметри зручні для невеликого route-контексту, але не для великого глобального
стану.

**Коротко**

Передавай невеликі параметри через `navigate`, а на екрані читай їх із
`route.params`.

</details>

<details>
<summary>19. Що таке deep linking і як його реалізувати?</summary>

#### React Native

Deep linking дозволяє відкривати конкретний екран застосунку за URL-посиланням.

Реалізація з React Navigation:

1. Налаштувати URL scheme / universal links у нативних конфігураціях.
2. Передати об'єкт `linking` у `NavigationContainer`.
3. Замапити URL-шляхи на назви екранів.

Це дає можливість, наприклад, відкривати `myapp://product/123` одразу на екрані
товару.

**Коротко**

Deep linking мапить URL на екрани застосунку, щоб зовнішні посилання відкривали
потрібний маршрут напряму.

</details>

<details>
<summary>20. Що таке keys у списках і чому вони важливі?</summary>

#### React Native

`key` унікально ідентифікує елементи списку для механізму reconciliation у
React.

Чому це важливо:

1. Допомагає React оновлювати лише змінені рядки.
2. Запобігає некоректному перевикористанню елементів і багам стану.
3. Покращує продуктивність і передбачуваність рендерингу.

Завжди використовуй стабільні унікальні ID, а не index масиву (якщо список не
статичний).

**Коротко**

Стабільні унікальні `key` зменшують баги в списках і допомагають React
ефективніше оновлювати UI.

</details>

<details>
<summary>21. Як ефективно рендерити списки (FlatList, SectionList)?</summary>

#### React Native

Для ефективного рендерингу списків у React Native варто використовувати
`FlatList` і `SectionList`, а не `map` великого масиву всередині `ScrollView`.

Чому вони ефективні:

1. Рендерять елементи ліниво (лише видима частина + буфер).
2. Перевикористовують представлення елементів і зменшують споживання пам'яті.
3. Мають вбудовані оптимізації пагінації та скролу.

Коли що використовувати:

1. `FlatList`: одновимірний список однотипних елементів.
2. `SectionList`: згруповані списки із заголовками секцій.

Базовий приклад `FlatList`:

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

**Коротко**

Для великих наборів даних обирай віртуалізовані списки — це кращий контроль
пам'яті та продуктивності скролу.

</details>

<details>
<summary>22. Що таке VirtualizedList і коли його використовувати?</summary>

#### React Native

`VirtualizedList` — це базовий рушій списків, на якому побудовані `FlatList` і
`SectionList`. Він відповідає за windowed rendering великих наборів даних.

Коли використовувати напряму:

1. Якщо джерело даних — не простий масив.
2. Якщо потрібен повний контроль над `getItem` і `getItemCount`.
3. Якщо абстракцій `FlatList`/`SectionList` недостатньо.

У більшості випадків краще починати з `FlatList` або `SectionList`, бо вони
простіші та покривають типові сценарії.

**Коротко**

`VirtualizedList` використовують напряму для нестандартних кейсів; у звичайних
сценаріях достатньо `FlatList/SectionList`.

</details>

<details>
<summary>23. Як отримувати дані в React Native (fetch, axios)?</summary>

#### React Native

Дані можна отримувати вбудованим `fetch` API або через `axios`.

Приклад `fetch`:

```jsx
async function loadPosts() {
  const response = await fetch('https://api.example.com/posts');
  if (!response.ok) throw new Error('Request failed');
  return response.json();
}
```

Приклад `axios`:

```jsx
import axios from 'axios';

async function loadPosts() {
  const { data } = await axios.get('https://api.example.com/posts');
  return data;
}
```

Типовий цикл у компоненті:

1. Увімкнути стан завантаження.
2. Виконати асинхронний запит.
3. Зберегти результат або помилку у state.
4. Вимкнути стан завантаження і відрендерити результат.

**Коротко**

Відповідай через життєвий цикл запиту: loading, success, error і коректна
обробка винятків.

</details>

<details>
<summary>24. Які best practices для API-запитів і обробки помилок?</summary>

#### React Native

Рекомендації для API та обробки помилок:

1. Централізувати API-логіку в сервісному шарі.
2. Завжди обробляти стани loading, success і error.
3. Налаштувати таймаути й retry-стратегію для тимчасових збоїв.
4. Валідовувати структуру відповіді перед використанням.
5. Показувати користувацькі повідомлення, а не сирі помилки сервера.
6. Використовувати скасування (`AbortController`), щоб не оновлювати unmounted
   екрани.
7. Тримати логіку refresh токенів в одному місці (interceptors/middleware).

Короткий шаблон:

1. `try` запит.
2. `catch` мережеві/серверні помилки.
3. Мапінг у доменно-зрозумілі помилки.
4. Логування технічних деталей для дебагу/моніторингу.

**Коротко**

Найкращий підхід: централізований API-шар, консистентний мапінг помилок і
керована стратегія retry/cancel.

</details>

<details>
<summary>25. Як працювати з async storage (пакет AsyncStorage community)?</summary>

#### React Native

`AsyncStorage` — це постійне key-value сховище для легких даних: налаштувань,
прапорців, простого кешу.

Базове використання:

```jsx
import AsyncStorage from '@react-native-async-storage/async-storage';

async function saveTheme(theme) {
  await AsyncStorage.setItem('theme', theme);
}

async function loadTheme() {
  return AsyncStorage.getItem('theme');
}
```

Best practices:

1. Серіалізувати об'єкти через `JSON.stringify` / `JSON.parse`.
2. Обгортати виклики у `try/catch`.
3. Тримати дані компактними; не використовувати як повноцінну БД.
4. Використовувати неймспейси ключів (наприклад, `app:user:token`).
5. Для чутливих даних використовувати secure storage (Keychain/Keystore).

**Коротко**

`AsyncStorage` підходить для легкого персистентного стану, але не для секретів;
дані треба серіалізувати й надійно обробляти помилки.

</details>

<details>
<summary>26. Які сучасні рішення для керування станом (Context, Zustand, Redux Toolkit)?</summary>

#### React Native

Сучасний вибір залежить від складності застосунку:

1. **Context API:** простий глобальний стан, мінімум boilerplate.
2. **Zustand:** легкий store, простий API, мало зайвої церемонії.
3. **Redux Toolkit:** потужні патерни, middleware, devtools, масштабування для
   великих команд.

Обирай найменший інструмент, який покриває потрібний рівень складності.

**Коротко**

Інструмент обирається за складністю: Context для простого, Zustand/RTK — для
більшого state-домену.

</details>

<details>
<summary>27. Як керувати глобальним станом без Redux?</summary>

#### React Native

Можна використовувати Context + hooks або легкі стори на кшталт Zustand/Jotai.

Типовий підхід:

1. Створити provider для спільного доменного стану.
2. Інкапсулювати оновлення в custom hooks.
3. Відокремити server state (наприклад, React Query/Apollo).

Це дозволяє уникнути boilerplate Redux і при цьому залишатися масштабованим.

**Коротко**

Комбінація Context/легких store + custom hooks дає керований глобальний стан без
зайвої складності.

</details>

<details>
<summary>28. Що таке React hooks і які з них найчастіше використовують?</summary>

#### React Native

Hooks — це функції, які дають функціональним компонентам доступ до стану,
побічних ефектів та інших можливостей React.

Найуживаніші хуки:

1. `useState`
2. `useEffect`
3. `useMemo`
4. `useCallback`
5. `useRef`
6. `useContext`
7. `useReducer`

Вони дають змогу повторно використовувати логіку через custom hooks.

**Коротко**

Hooks переносять stateful-логіку у функціональні компоненти й роблять її
повторно використовуваною.

</details>

<details>
<summary>29. Що таке useEffect і як він замінює lifecycle-методи?</summary>

#### React Native

`useEffect` запускає побічні ефекти після рендеру та може очищати їх.

Відповідність lifecycle (class -> hooks):

1. `componentDidMount` -> `useEffect(..., [])`
2. `componentDidUpdate` -> `useEffect(..., [deps])`
3. `componentWillUnmount` -> cleanup-функція, яку повертає `useEffect`

Це об'єднує lifecycle-поведінку у функціональних компонентах.

**Коротко**

`useEffect` — це єдиний механізм для side effects і cleanup; мислити треба через
залежності, а не через class lifecycle.

</details>

<details>
<summary>30. Що таке useMemo і useCallback та коли їх використовувати?</summary>

#### React Native

`useMemo` мемоізує обчислені значення, а `useCallback` — посилання на функції.

Коли використовувати:

1. Коли обчислення дорогі.
2. Коли потрібні стабільні посилання, щоб уникати зайвих ререндерів дочірніх
   компонентів.
3. Коли значення/колбеки є залежностями інших хуків.

Не варто застосовувати їх всюди; використовуй там, де профілювання показує
реальну користь.

**Коротко**

Мемоізацію варто вмикати вибірково — для стабілізації дорогих значень/колбеків,
коли це підтверджено профілюванням.

</details>

<details>
<summary>31. Що таке refs і коли їх варто використовувати?</summary>

#### React Native

Refs — це змінювані посилання на екземпляри компонентів або нативні елементи.
Вони дають доступ до імперативних API без запуску ререндеру.

Типові сценарії використання:

1. Фокус або blur для `TextInput`.
2. Виклик методів скролу (`scrollToOffset`, `scrollToEnd`).
3. Вимірювання layout (`measure`, `measureInWindow`).
4. Збереження змінюваних значень, які не мають викликати оновлення UI.

Приклад:

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

Refs потрібні для імперативних дій, а не як заміна звичайного потоку даних через
state/props.

**Коротко**

Refs — це інструмент для імперативного доступу (focus/scroll/measure), а не для
керування основним data flow.

</details>

<details>
<summary>32. Як створювати custom hooks?</summary>

#### React Native

Custom hook — це повторно використовувана функція, яка починається з `use` і
комбінує React hooks (`useState`, `useEffect` тощо) у спільну логіку.

Правила:

1. Назва хука має починатися з `use`.
2. Викликайте хуки лише на верхньому рівні custom hook.
3. Повертайте значення/функції, потрібні компонентам.

Приклад:

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

Custom hooks покращують повторне використання коду, читабельність і розділення
відповідальностей.

**Коротко**

Винось повторювану stateful-логіку в `use*` функції, щоб компоненти залишались
компактними й сфокусованими.

</details>

<details>
<summary>33. Що таке оптимізація продуктивності в React Native?</summary>

#### React Native

Оптимізація продуктивності в React Native — це зменшення накладних витрат на
рендер, JavaScript-обчислення та layout, щоб взаємодія залишалась плавною
(особливо на слабших пристроях).

Основні зони оптимізації:

1. Рендер: уникати зайвих ререндерів.
2. Списки: правильно налаштовувати `FlatList`/`SectionList`.
3. JavaScript-навантаження: виносити важкі обчислення з критичного рендер-шляху.
4. Зображення: стискати, кешувати, задавати коректні розміри.
5. Взаємодія native/JS: мінімізувати дорогі міжшарові операції.

Типова ціль: стабільні 60 FPS, швидший старт застосунку та чуйний інтерфейс.

**Коротко**

Спочатку профілюй, потім цільово оптимізуй рендер, списки, зображення і важкі
JS-ділянки.

</details>

<details>
<summary>34. Як уникати зайвих ререндерів?</summary>

#### React Native

Зайвих ререндерів уникають за рахунок стабілізації props і оновлення лише того
state, який справді потрібен.

Практичні техніки:

1. Використовувати `React.memo` для «чистих» функціональних компонентів.
2. Використовувати `useMemo` для дорогих похідних значень.
3. Використовувати `useCallback` для стабільних посилань на колбеки.
4. Тримати state максимально локальним.
5. Уникати створення нових об'єктів/функцій inline, якщо вони передаються глибоко
   через props.
6. Ділити великі компоненти на менші, сфокусовані.
7. Використовувати стабільні ключі у списках.

Також спершу профілюйте (React DevTools/Flipper), а оптимізуйте вже реальні
bottleneck-и.

**Коротко**

Стабільні props, локальний state і помірна мемоізація дають найбільший ефект у
зменшенні реальних витрат рендеру.

</details>

<details>
<summary>35. Що таке мемоізація в React Native?</summary>

#### React Native

Мемоізація — це техніка кешування обчислених результатів або рендер-результатів
компонентів із повторним використанням, якщо вхідні дані не змінилися.

У React Native найчастіше використовують:

1. `React.memo`: мемоізація рендеру компонента на основі порівняння props.
2. `useMemo`: мемоізація обчислених значень.
3. `useCallback`: мемоізація посилань на функції.

Приклад:

```jsx
import React, { useMemo } from 'react';

function Total({ items }) {
  const sum = useMemo(() => {
    return items.reduce((acc, item) => acc + item.price, 0);
  }, [items]);

  return <Text>{sum}</Text>;
}
```

Використовуйте мемоізацію вибірково: надмірне застосування додає складності без
помітної користі.

**Коротко**

Мемоізація зберігає незмінні значення/функції/рендери, щоб не перераховувати
однакову роботу повторно.

</details>

<details>
<summary>36. Що таке двигун Hermes і чому він важливий?</summary>

#### React Native

Hermes — це JavaScript-двигун, оптимізований для React Native.

Чому це важливо:

1. Швидший запуск застосунку.
2. Менше споживання пам'яті на багатьох пристроях.
3. Більш передбачувана продуктивність на Android/iOS.
4. Хороша інтеграція з RN-інструментами.

Hermes часто є стандартним вибором для продакшен-застосунків на RN.

**Коротко**

Hermes покращує час старту й пам'ять, тому для багатьох RN-проєктів це
практичний дефолт.

</details>

<details>
<summary>37. Що таке нова архітектура React Native?</summary>

#### React Native

Нова архітектура — це модернізація внутрішньої будови RN, яка базується на:

1. Fabric renderer.
2. TurboModules.
3. JSI (JavaScript Interface).
4. Напрямку Bridgeless.

Цілі: менша затримка між JS і native, краща підтримка конкурентності та вища
продуктивність.

**Коротко**

Нова архітектура = Fabric + TurboModules + JSI для нижчого overhead і кращого
масштабування.

</details>

<details>
<summary>38. Що таке Fabric і TurboModules?</summary>

#### React Native

`Fabric` — нова система рендерингу, а `TurboModules` — нова система нативних
модулів.

Разом вони дають:

1. Ефективніше оновлення UI.
2. Швидший доступ до модулів.
3. Кращу type-safe інтеграцію native через codegen.
4. Кращу продуктивність старту і рантайму.

**Коротко**

Fabric модернізує рендеринг, а TurboModules — доступ до native-модулів і їх
завантаження.

</details>

<details>
<summary>39. Що таке JSI і як він замінює старий bridge?</summary>

#### React Native

JSI (JavaScript Interface) — це C++ API, який дозволяє JS і native взаємодіяти
більш напряму.

Порівняно зі старим bridge:

1. Менше важкої асинхронної JSON-передачі повідомлень.
2. Нижчі накладні витрати викликів і краща інтеграція рантаймів.
3. Підтримка можливостей нової архітектури (TurboModules/Fabric).

Це суттєво зменшує bottleneck у комунікації між шарами.

**Коротко**

JSI прибирає частину обмежень legacy bridge і робить JS-native взаємодію прямішою
та швидшою.

</details>

<details>
<summary>40. Що таке Bridgeless mode у React Native?</summary>

#### React Native

Bridgeless mode — це архітектурний напрямок, у якому RN працює без legacy
bridge-шляху виконання.

Переваги:

1. Менші накладні витрати на комунікацію.
2. Чистіша сучасна runtime-модель.
3. Краща узгодженість із Fabric, TurboModules і JSI.

Це частина довгострокової еволюції RN у бік продуктивності й простішої
підтримки.

**Коротко**

Bridgeless зменшує залежність від старого bridge і покращує ефективність
сучасного runtime.

</details>

<details>
<summary>41. Як React Native досягає майже нативної продуктивності?</summary>

#### React Native

React Native наближається до нативної продуктивності завдяки рендерингу реальних
нативних UI-компонентів і оптимізації роботи між JavaScript та native-шарами.

Ключові причини:

1. UI рендериться нативними view (`UIView`, `android.view`), а не всередині web
   view.
2. Декларативні оновлення React зменшують зайві UI-операції.
3. Hermes може покращувати час старту та використання пам'яті.
4. Нова архітектура (Fabric, TurboModules, JSI) знижує накладні витрати bridge.
5. Оптимізовані списки (`FlatList`, `SectionList`) підтримують віртуалізацію.

Продуктивність усе одно залежить від архітектури застосунку: важкі JS-обчислення,
неоптимізований рендер і великі зображення можуть уповільнювати UI.

**Коротко**

RN відчувається «нативним», коли оптимізовані рендер-шляхи й контрольоване
JS-навантаження.

</details>

<details>
<summary>42. Що таке Native Modules і коли їх використовувати?</summary>

#### React Native

Native Modules — це кастомні платформені модулі (iOS/Android), які відкривають
нативний функціонал для JavaScript.

Коли їх варто використовувати:

1. Коли потрібні API, яких немає в core/community пакетах React Native.
2. Коли потрібен глибший доступ до можливостей пристрою/платформи.
3. Коли частину логіки краще виконувати нативно для продуктивності.

Приклади:

1. Розширені можливості камери або Bluetooth.
2. Інтеграція пропрієтарних SDK (payments, biometrics, analytics).
3. ОС-специфічні фонові сервіси.

Якщо є якісний community пакет, зазвичай краще почати з нього. Кастомні модулі
потрібні для унікальних вимог.

**Коротко**

Native Modules потрібні, коли треба платформений API, недоступний у стандартних
RN-бібліотеках.

</details>

<details>
<summary>43. Як писати нативний код для React Native (Swift/Kotlin)?</summary>

#### React Native

Нативний код додається через створення модуля в iOS (Swift/Objective-C) і/або
Android (Kotlin/Java), а потім експонується в JavaScript.

Високорівневий процес:

1. Створити клас нативного модуля на кожній платформі.
2. Експортувати методи/константи/події в React Native.
3. Зареєструвати модуль у нативному проєкті.
4. Викликати модуль із JavaScript/TypeScript.

Мінімальний приклад виклику з JS:

```jsx
import { NativeModules } from 'react-native';

const { DeviceInfoModule } = NativeModules;

async function loadDeviceName() {
  const name = await DeviceInfoModule.getDeviceName();
  return name;
}
```

У сучасному RN бажано орієнтуватися на TurboModules/Codegen для кращої
довгострокової сумісності.

**Коротко**

Нативні можливості відкриваються через модулі, після чого викликаються з JS через
чіткий інтерфейс.

</details>

<details>
<summary>44. Як інтегрувати React Native в існуючий нативний застосунок?</summary>

#### React Native

React Native можна вбудовувати як окрему фічу в уже існуючий iOS/Android
застосунок, а не переписувати все з нуля.

Типовий підхід:

1. Додати залежності React Native у нативні проєкти.
2. Налаштувати bundle і runtime React Native.
3. Запускати RN root view/екран із нативної навігації.
4. Передавати дані між native і RN через props, events або modules.

Поширені сценарії:

1. Винести один кросплатформний модуль (наприклад, settings/profile) в інакше
   нативному застосунку.
2. Мігрувати legacy-екрани поступово.

Такий підхід зменшує ризики міграції та дозволяє впроваджувати RN поетапно.

**Коротко**

Інтеграція «екран за екраном» дозволяє модернізувати застосунок поступово, без
ризику великого одноразового переписування.

</details>

<details>
<summary>45. Як обробляти платформо-специфічний код (Platform API)?</summary>

#### React Native

Платформені відмінності зазвичай реалізують через `Platform` API та
платформо-специфічні файли.

Основні техніки:

1. Runtime-перевірки через `Platform.OS` (`ios`, `android`).
2. Вибір значень через `Platform.select(...)`.
3. Розділення файлів за розширеннями: `Component.ios.tsx` і
   `Component.android.tsx`.

Приклад:

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

Краще максимально ділити спільну логіку, а ізолювати лише необхідні платформені
відмінності.

**Коротко**

Платформені нюанси обробляй через `Platform` і platform-specific файли, зберігаючи
основну логіку спільною.

</details>

<details>
<summary>46. Як будувати компоненти з урахуванням відмінностей iOS та Android?</summary>

#### React Native

Будуйте спільну базову логіку й ізолюйте платформо-специфічний UI/поведінку
лише там, де це справді потрібно.

Техніки:

1. `Platform.OS` / `Platform.select`.
2. Окремі файли `Component.ios.tsx` і `Component.android.tsx`.
3. Токени дизайн-системи з платформеними override-ами.

Тримайте розбіжності мінімальними, щоб зменшити вартість підтримки.

**Коротко**

Зберігай єдиний контракт компонента і винось у платформо-специфічний код лише
те, що дійсно відрізняється.

</details>

<details>
<summary>47. Як обробляти жести в React Native?</summary>

#### React Native

Для надійної й продуктивної роботи з жестами краще використовувати профільні
бібліотеки.

Поширений підхід:

1. `react-native-gesture-handler` для розпізнавання жестів.
2. `react-native-reanimated` для плавних gesture-driven анімацій.
3. Комбінування tap/pan/fling/pinch хендлерів під конкретний екран.

Уникайте важких JS-обчислень під час активних gesture callback-ів.

**Коротко**

Найчастіше оптимальний стек для жестів у продакшені: Gesture Handler +
Reanimated.

</details>

<details>
<summary>48. Що таке PanResponder і коли його використовувати?</summary>

#### React Native

`PanResponder` — це вбудований у RN механізм обробки жестів для роботи з рухом
дотику.

Коли використовувати:

1. Коли сценарій жестів простий.
2. Коли ви хочете обійтися без додаткових залежностей.

Для складних і високопродуктивних gesture-сценаріїв зазвичай краще підійдуть
Gesture Handler + Reanimated.

**Коротко**

PanResponder підходить для базових жестів, але для складної взаємодії частіше
використовують сучасні gesture-бібліотеки.

</details>

<details>
<summary>49. Які бібліотеки використовують для жестів (Gesture Handler, Reanimated)?</summary>

#### React Native

Найпоширеніший gesture-стек:

1. `react-native-gesture-handler` для надійного розпізнавання жестів.
2. `react-native-reanimated` для продуктивних анімацій і worklets.

У продакшені їх часто використовують разом для стабільного UX.

**Коротко**

Gesture Handler + Reanimated — стандартна зв'язка для надійного gesture UX і
плавної анімації.

</details>

<details>
<summary>50. Що таке Reanimated і навіщо його використовують?</summary>

#### React Native

Reanimated — це високопродуктивна бібліотека анімацій для React Native.

Навіщо її використовують:

1. Плавні анімації з мінімальними лагами.
2. Gesture-driven переходи.
3. Ефективне виконання анімаційної логіки (worklets/UI-thread friendly модель).
4. Зручна реалізація складних взаємодій (bottom sheets, shared transitions тощо).

**Коротко**

Reanimated використовують там, де потрібні складні, інтерактивні й дуже плавні
анімації в мобільному UI.

</details>

<details>
<summary>51. Що таке Animated API і як він працює?</summary>

#### React Native

`Animated` — це вбудована в React Native система анімацій для плавних
UI-переходів через анімацію значень у часі.

Як це працює:

1. Створюєте анімоване значення (`new Animated.Value(0)`).
2. Прив'язуєте це значення до style-властивостей (`opacity`, `transform` тощо).
3. Запускаєте анімацію через `Animated.timing`, `spring`, `decay` та інші.

Приклад:

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

**Коротко**

Animated працює через анімовані значення; де можливо, використовуй
`useNativeDriver` для плавнішого рендеру.

</details>

<details>
<summary>52. Яка різниця між декларативними та імперативними анімаціями?</summary>

#### React Native

Різниця в тому, як описується й контролюється поведінка анімації.

1. **Декларативні анімації:** описують цільовий стан UI і переходи на
   високому рівні; фреймворк бере на себе деталі виконання.

2. **Імперативні анімації:** ви вручну керуєте життєвим циклом анімації крок за
   кроком (start, stop, оновлення значень).

У React Native:

1. `LayoutAnimation` і багато патернів Reanimated ближчі до декларативного
   підходу.
2. `Animated.Value` із явним `.start()` — більш імперативний підхід.

Декларативний підхід часто простіше підтримувати, а імперативний дає тонший
контроль у складних інтеракціях.

**Коротко**

Декларативний підхід задає «що має бути», імперативний — «як саме крок за кроком
це виконати».

</details>

<details>
<summary>53. Як реалізувати плавні анімації?</summary>

#### React Native

Щоб анімації були плавними, потрібно зменшувати навантаження на main thread і
уникати дорогих ререндерів під час руху.

Best practices:

1. По можливості використовуйте `useNativeDriver: true`.
2. Віддавайте перевагу `transform` і `opacity` замість layout-heavy властивостей.
3. Ізолюйте анімовані компоненти та, за потреби, мемоізуйте їх.
4. Уникайте важких обчислень під час gestures/animations.
5. Для складних, високопродуктивних взаємодій використовуйте
   `react-native-reanimated`.
6. Оптимізуйте великі списки/зображення, якщо вони анімуються на екрані.

Тестуйте на реальних пристроях середнього класу, а не лише на
емуляторі/симуляторі.

**Коротко**

Для плавності фокусуйся на `transform/opacity` і прибирай важке JS-навантаження
під час активної анімації.

</details>

<details>
<summary>54. Що таке LayoutAnimation і коли його використовувати?</summary>

#### React Native

`LayoutAnimation` анімує глобальні зміни layout (позиція/розмір), коли view
додаються, видаляються або змінюються.

Коли використовувати:

1. Розгортання/згортання секцій.
2. Вставка/видалення рядків у списках із простими переходами.
3. Оновлення UI, де потрібна автоматична інтерполяція layout-змін.

Приклад:

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

Використовуйте його для простих layout-переходів; для gesture-driven і складних
анімацій зазвичай краще підходить Reanimated.

**Коротко**

LayoutAnimation зручний для простих змін layout (expand/collapse), але не для
складної хореографії жестів.

</details>

<details>
<summary>55. Як обробляти safe areas (SafeAreaView)?</summary>

#### React Native

Safe area запобігає накладанню контенту на вирізи, заокруглені кути й системні
панелі.

Рекомендований підхід:

1. Використовувати `react-native-safe-area-context`.
2. Обгорнути корінь застосунку в `SafeAreaProvider`.
3. Використовувати `SafeAreaView` або `useSafeAreaInsets()` на
   екранах/компонентах.

Приклад:

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

Це забезпечує консистентну поведінку відступів на iOS і Android.

**Коротко**

Використовуй safe-area контекст, щоб контент залишався видимим і коректно
розташованим на всіх типах екранів.

</details>

<details>
<summary>56. Як обробляти зміну орієнтації пристрою?</summary>

#### React Native

Зміни орієнтації обробляють через відстеження зміни розмірів/орієнтації екрана
та адаптацію layout.

Варіанти:

1. `useWindowDimensions()` для реактивного перерахунку UI.
2. Orientation-бібліотеки для явного lock/listen керування.
3. Нативна конфігурація платформи, коли обертання екрана потрібно обмежити.

Завжди тестуйте переходи portrait/landscape на реальних пристроях.

**Коротко**

Реагуй на події зміни розмірів/орієнтації і адаптуй layout так, щоб UX не
ламався.

</details>

<details>
<summary>57. Що таке PixelRatio і коли він корисний?</summary>

#### React Native

`PixelRatio` надає утиліти для роботи з щільністю пікселів пристрою.

Корисний для:

1. Масштабування UI-асетів під екрани з високою щільністю.
2. Округлення розмірів layout, щоб уникнути «розмиття».
3. Завантаження зображень відповідного розміру.

Це допомагає отримати чіткіший і консистентніший вигляд на різних пристроях.

**Коротко**

Використовуй PixelRatio для чіткої графіки та розмірів, чутливих до щільності
екрана.

</details>

<details>
<summary>58. Як реалізувати кастомні шрифти?</summary>

#### React Native

Кастомні шрифти додаються як assets застосунку й використовуються через
`fontFamily`.

Типові кроки:

1. Додати файли шрифтів (`.ttf`/`.otf`) в assets.
2. Налаштувати linking (RN CLI або Expo config).
3. Використовувати назви шрифтів у стилях.
4. В Expo — завантажити шрифти до рендеру через `expo-font`.

Тримайте єдину типографічну шкалу та fallback-стратегію для консистентності.

**Коротко**

Додавай шрифти як assets і будуй єдину typography-систему для всіх екранів.

</details>

<details>
<summary>59. Як обробляти accessibility у React Native?</summary>

#### React Native

Accessibility потрібно закладати в компоненти з самого початку.

Ключові практики:

1. Додавати доступні labels/hints.
2. Використовувати семантичні ролі та стани.
3. Забезпечувати достатній контраст і розмір touch-targets.
4. Підтримувати динамічне масштабування тексту.
5. Тестувати з VoiceOver (iOS) і TalkBack (Android).

Accessibility покращує UX для всіх користувачів, не лише для людей з
асистивними технологіями.

**Коротко**

Сприймай accessibility як базову якість продукту: ролі, стани, контраст і
перевірка зі screen reader.

</details>

<details>
<summary>60. Що таке AccessibilityRole і AccessibilityState?</summary>

#### React Native

`accessibilityRole` описує, чим є елемент (button, header, link тощо).
`accessibilityState` описує його поточний стан (disabled, selected, checked,
busy, expanded).

Це допомагає screen reader-ам озвучувати коректний контекст для інтерактивних
елементів.

Приклад:

```jsx
<Pressable
  accessibilityRole="button"
  accessibilityState={{ disabled: isDisabled }}
>
  <Text>Submit</Text>
</Pressable>
```

**Коротко**

Role відповідає за «тип» елемента, а state — за його поточний інтерактивний
стан.

</details>

<details>
<summary>61. Як обробляти push-сповіщення?</summary>

#### React Native

Push-сповіщення зазвичай реалізують через платформені сервіси разом із
React Native бібліотекою.

Типовий setup:

1. Обрати провайдера: Firebase Cloud Messaging (FCM), APNs (iOS) або сервіси
   на кшталт OneSignal.
2. Налаштувати дозволи застосунку й токени (APNs token / FCM token).
3. Зареєструвати listeners для foreground, background і opened notifications.
4. Обробляти deep links/навігацію при натисканні на сповіщення.

Типові бібліотеки:

1. `@react-native-firebase/messaging` для FCM.
2. `notifee` для розширеної роботи з local/remote notifications.

Best practice: тримати payload компактним, захищати endpoint-и і коректно
обробляти оновлення токенів.

**Коротко**

Головне: реєстрація токенів, permissions flow, обробка foreground/background та
навігація по тапу на notification.

</details>

<details>
<summary>62. Як реалізувати фонові задачі?</summary>

#### React Native

Фонові задачі залежать від обмежень платформи й типу задачі (sync, location,
uploads, notifications).

Підходи:

1. Використовувати нативні background API через бібліотеки.
2. Планувати періодичні джоби для легких фонових задач.
3. Використовувати headless tasks на Android, коли застосунок згорнутий або
   завершений.

Поширені інструменти:

1. `react-native-background-fetch` для періодичних fetch-задач.
2. `@react-native-firebase/messaging` background handlers для
   push-тригерних задач.
3. Нативні services/workers для складніших сценаріїв.

Важливо: iOS і Android мають жорсткі battery-policy, тому фонове виконання не
гарантується в точно заданий момент.

**Коротко**

Фонові задачі завжди platform-constrained, тому дизайн має бути про надійність,
а не про ідеальну точність таймінгу.

</details>

<details>
<summary>63. Як обробляти offline-режим і синхронізацію даних?</summary>

#### React Native

Offline-режим зазвичай будується на local-first підході з синхронізацією після
повернення мережі.

Базова стратегія:

1. Зберігати дані локально (AsyncStorage, SQLite, Realm тощо).
2. Ставити write-операції в чергу під час офлайну.
3. Відстежувати зміни підключення.
4. Повторювати queued-операції та розв'язувати конфлікти після reconnect.

Рекомендовані практики:

1. Проєктувати API-операції як idempotent, де це можливо.
2. Використовувати timestamps/versioning для conflict resolution.
3. Показувати явний статус у UI: offline, syncing, failed, synced.
4. Використовувати retry/backoff policy, щоб уникати request storm.

**Коротко**

Надійний offline режим = local-first зберігання + черга змін + conflict-aware
синхронізація після reconnect.

</details>

<details>
<summary>64. Як реалізувати стратегії кешування?</summary>

#### React Native

Кешування зменшує затримки, мережеве навантаження та повторні обчислення.

Поширені шари кешу:

1. **API response cache:** in-memory + persistent cache.
2. **Image cache:** оптимізовані image-бібліотеки або HTTP cache headers.
3. **Computed data cache:** мемоізація (`useMemo`) для дорогих похідних значень.
4. **Request cache:** кеші в бібліотеках на кшталт React Query/Apollo.

Практичні правила:

1. Визначати TTL і invalidation-правила для кожного ресурсу.
2. Використовувати stale-while-revalidate для чуйного UI.
3. Очищати кеш під час logout або зміни auth-контексту.
4. Не допускати необмеженого росту кешу.

**Коротко**

Ефективне кешування — це чіткі межі кешу й інвалідація; stale-while-revalidate
часто дає найкращий UX-баланс.

</details>

<details>
<summary>65. Що таке GraphQL і як його використовують у React Native?</summary>

#### React Native

GraphQL — це мова запитів і runtime для API, що дозволяє клієнту запитувати
рівно ті дані, які потрібні, через єдиний endpoint.

Чому це корисно в React Native:

1. Зменшує over-fetching/under-fetching.
2. Добре лягає на screen-based потреби в даних.
3. Добре працює з потужними клієнтськими кешами.

Як використовують:

1. Описують GraphQL queries/mutations/subscriptions.
2. Підключають клієнтську бібліотеку (найчастіше Apollo Client).
3. Виконують операції в hooks/компонентах.
4. Обробляють loading, error і оновлення кешу.

Приклад запиту:

```graphql
query GetUser($id: ID!) {
  user(id: $id) {
    id
    name
    avatar
  }
}
```

**Коротко**

GraphQL дозволяє мобільним екранам запитувати тільки потрібні поля, зменшуючи
зайвий трафік і спрощуючи роботу з даними.

</details>

<details>
<summary>66. Що таке Apollo Client і коли його використовувати?</summary>

#### React Native

Apollo Client — популярний GraphQL-клієнт для виконання
query/mutation/subscription та normalized caching.

Коли варто використовувати:

1. Коли застосунок суттєво спирається на GraphQL API.
2. Коли потрібні сильні можливості кешу й інструменти оновлення даних.
3. Коли потрібні єдині GraphQL-патерни на всіх екранах.

Для REST-first застосунків інколи доцільніші простіші альтернативи.

**Коротко**

Apollo доцільний, коли GraphQL-кеш і нормалізований клієнтський стан — ключові
вимоги проєкту.

</details>

<details>
<summary>67. Що таке NetInfo і як його використовувати?</summary>

#### React Native

`@react-native-community/netinfo` надає інформацію про стан мережевого
підключення.

Сценарії використання:

1. Відстеження переходів offline/online.
2. Вимкнення або черга мережевих дій в офлайн-режимі.
3. Запуск sync/retry після відновлення з'єднання.

Це базовий інструмент для надійного offline-first UX.

**Коротко**

NetInfo дозволяє керувати запитами на основі реального стану мережі та розумно
перезапускати їх після reconnect.

</details>

<details>
<summary>68. Як обробляти real-time оновлення (WebSockets, subscriptions)?</summary>

#### React Native

Оновлення в реальному часі зазвичай реалізують через WebSockets або GraphQL
subscriptions.

Типовий патерн:

1. Відкрити постійне з'єднання.
2. Підписатися на потрібні канали/події.
3. Мержити вхідні події у локальний/app state.
4. Реалізувати reconnect з backoff при обривах.

Враховуйте app lifecycle і зміни мережі, щоб уникати «застарілих» сокетів.

**Коротко**

Тримай стабільні канали подій, акуратно зливай дані у state і обов'язково
обробляй reconnect/backoff.

</details>

<details>
<summary>69. Які є поширені інструменти тестування (Jest, Detox)?</summary>

#### React Native

Поширений testing stack:

1. **Jest:** unit та integration тести.
2. **React Native Testing Library:** тестування взаємодії компонентів.
3. **Detox:** end-to-end UI тести на emulator/simulator/device.
4. **ESLint/TypeScript у CI:** статичні перевірки коректності.

Поєднання цих рівнів дає надійне покриття.

**Коротко**

Найкраще працює багаторівневий підхід: Jest для логіки/компонентів, Detox — для
повних E2E-флоу.

</details>

<details>
<summary>70. Як писати unit тести в React Native?</summary>

#### React Native

Unit тести в React Native зазвичай пишуть із Jest (+ Testing Library для
компонентів).

Загальний алгоритм:

1. Arrange: підготувати вхідні дані компонента/функції.
2. Act: відрендерити або викликати поведінку.
3. Assert: перевірити очікуваний output/state/callback.

Якісні unit тести мають бути ізольованими, детермінованими та швидкими.

**Коротко**

Хороший unit тест швидкий і передбачуваний: перевіряє поведінку, а не деталі
реалізації.

</details>

<details>
<summary>71. Як виконувати end-to-end тестування?</summary>

#### React Native

End-to-end (E2E) тести перевіряють повні користувацькі сценарії в реальному або
симульованому середовищі застосунку: UI, навігацію та інтеграцію з бекендом.

Типовий процес:

1. Запустити застосунок у test mode.
2. Взаємодіяти з UI як користувач (tap, type, scroll).
3. Перевірити видимі результати й стан навігації.
4. Запустити тести в CI на кількох пристроях/конфігураціях.

Найпоширеніший інструмент E2E в RN — **Detox**.

Best practices:

1. Додавати стабільні test IDs (`testID`) для важливих елементів.
2. Робити тести детермінованими (контролювати мережу/дані, де можливо).
3. Пріоритезувати критичні user journeys (auth, checkout, core flows).

**Коротко**

E2E тести мають покривати критичні користувацькі флоу через реальну навігацію та
інтеграційні межі.

</details>

<details>
<summary>72. Які інструменти дебагу доступні (Flipper)?</summary>

#### React Native

Дебаг у React Native зазвичай поєднує runtime-логи, інспекцію компонентів і
нативну діагностику.

Поширені інструменти:

1. **Flipper:** плагіни для логів, мережі, layout inspector і performance.
2. **React DevTools:** інспекція дерева компонентів, props, state, hooks.
3. **Metro logs:** консольний вивід і runtime warning/error.
4. **Xcode / Android Studio:** нативні crash-логи, device logs, breakpoints.
5. **Hermes debugging support:** профілювання/інспекція специфічно для JS engine.

Flipper особливо корисний як єдиний десктопний центр для JS + native дебагу.

**Коротко**

Найкращий підхід — комбінувати логи, DevTools/Flipper і нативні інструменти для
платформених проблем.

</details>

<details>
<summary>73. Як профілювати продуктивність у React Native?</summary>

#### React Native

Профілювання продуктивності допомагає знайти реальні bottleneck-и в рендері,
виконанні JS і навантаженні UI thread.

Ключові методи профілювання:

1. Використовувати React DevTools Profiler для пошуку дорогих ререндерів.
2. Використовувати Flipper-плагіни для performance і network timing.
3. Вимірювати startup time і latency переходів на реальних пристроях.
4. Аналізувати поведінку списків (`FlatList` config, dropped frames).
5. Профілювати нативну частину через Xcode Instruments / Android Profiler.

На що дивитися:

1. Часті зайві ререндери.
2. Довгі JS tasks, що блокують взаємодію.
3. Важкі image/layout операції на критичних екранах.

Профілювати краще на production-like білдах, а не лише в debug.

**Коротко**

Профілюй у максимально реалістичних умовах, щоб оптимізувати фактичні, а не
уявні вузькі місця.

</details>

<details>
<summary>74. Що таке Expo і коли його варто використовувати?</summary>

#### React Native

Expo — це платформа й toolchain навколо React Native, яка спрощує розробку,
збірки та оновлення застосунків.

Коли Expo доцільний:

1. Коли потрібен швидкий старт і висока продуктивність розробки.
2. Коли потрібні типові нативні можливості через Expo SDK (camera,
   notifications тощо).
3. Коли зручніші cloud/local build workflow (EAS).

Expo включає:

1. Dev tools і runtime.
2. Expo SDK модулі.
3. Інструменти збірки й сабміту.
4. Підтримку OTA оновлень через Expo-сервіси.

Для багатьох застосунків це сильний дефолт, якщо не потрібен глибокий кастомний
native-контроль із першого дня.

**Коротко**

Expo найкращий там, де важливі швидкість розробки і менше нативного setup
overhead.

</details>

<details>
<summary>75. Яка різниця між Expo managed і bare workflow?</summary>

#### React Native

Головна різниця — у рівні контролю над нативним проєктом.

1. **Managed workflow:** Expo керує нативною конфігурацією. Ви переважно
   працюєте в JS/TS і Expo config. Швидше в розробці, менше нативної підтримки.

2. **Bare workflow:** Ви маєте повноцінні нативні iOS/Android проєкти (подібно
   до plain RN). Більше контролю, але вища складність setup/підтримки.

Managed обирають, коли пріоритет — швидкість і простота.
Bare обирають, коли потрібен кастомний native-код або глибока low-level
інтеграція.

**Коротко**

Managed = швидкість, Bare = повний контроль і кастомізація нативного шару.

</details>

<details>
<summary>76. Які плюси й мінуси Expo?</summary>

#### React Native

Плюси:

1. Швидкий старт проєкту й ітерацій.
2. Багатий SDK для типових нативних можливостей.
3. Простий pipeline збірки/оновлень через EAS.
4. Хороший DX для малих/середніх команд.

Мінуси:

1. Менше прямого нативного контролю в managed workflow.
2. Деякі edge-case нативні сценарії вимагають bare/eject.
3. Залежність від рішень і інструментів екосистеми Expo.

Expo дає відмінну продуктивність розробки, але з tradeoff у low-level
гнучкості.

**Коротко**

Expo пришвидшує розробку та релізи, але глибока нативна кастомізація іноді
потребує bare workflow.

</details>

<details>
<summary>77. Як організувати збірки та деплой застосунку?</summary>

#### React Native

Build/deploy pipeline зазвичай включає:

1. Versioning і changelog.
2. CI-збірки для Android/iOS.
3. Автоматизовані тести та quality gates.
4. Signing і генерацію артефактів.
5. Сабміт у стори (Play Console / App Store Connect).
6. Post-release моніторинг і rollback-план.

Expo-проєкти часто використовують EAS Build/Submit, bare-проєкти —
Fastlane/CI-скрипти.

**Коротко**

Сприймай реліз як конвеєр: версіонування, CI-перевірки, підпис, публікація,
моніторинг.

</details>

<details>
<summary>78. Що таке code signing і чому це важливо?</summary>

#### React Native

Code signing криптографічно підтверджує ідентичність і цілісність застосунку.

Чому це важливо:

1. Підтверджує автентичність видавця застосунку.
2. Захищає від довіри до змінених (tampered) бінарників.
3. Є обов'язковим для дистрибуції через app stores.

iOS використовує certificates/profiles, Android — keystore.

**Коротко**

Code signing підтверджує справжність застосунку і є обов'язковим для безпечної
публікації.

</details>

<details>
<summary>79. Як керувати середовищами (dev/staging/prod)?</summary>

#### React Native

Використовуйте явну конфігурацію середовища для кожного build target.

Поширений setup:

1. Окремі API endpoint-и та feature flags.
2. Build variants/flavors (Android) і schemes (iOS).
3. Env-specific секрети через захищені CI variables.
4. Чітка схема іменування release channels.

Вибір середовища має бути детермінованим і видимим у діагностиці застосунку.

**Коротко**

Розділяй конфіги по середовищах і не тримай секрети/конфіг у відкритому
source-коді.

</details>

<details>
<summary>80. Що таке CodePush / OTA updates і коли їх використовувати?</summary>

#### React Native

OTA updates дозволяють доставляти JavaScript/assets без повного релізу в store.

Коли це корисно:

1. Швидкі bugfix у JS-шарі.
2. Невеликі оновлення контенту/логіки.

Обмеження:

1. Не можна оновлювати нативний бінарний код.
2. Потрібно дотримуватись політик store-платформ.

Використовуйте OTA для безпечних інкрементальних JS-оновлень, але не як повну
заміну бінарних релізів.

**Коротко**

OTA чудово підходить для швидких JS-оновлень, але зміни нативного коду все одно
вимагають store-білду.

</details>

<details>
<summary>81. Які best practices структурування великого codebase?</summary>

#### React Native

Для великих React Native проєктів структура має покращувати discoverability,
ownership фіч і довгостроковий рефакторинг.

Поширений підхід — feature-first організація:

1. Групувати код за доменами/фічами (`features/auth`, `features/profile` тощо).
2. Тримати спільний UI в `components/`, а загальні хуки — в `hooks/`.
3. Відокремлювати API/data layer (`services/`, `api/`, `store/`).
4. Централізувати app-wide конфіг/константи (`config/`, `theme/`, `env/`).
5. Визначати чіткі межі та публічні entry points для кожної фічі.

Також важливо підтримувати консистентність через linting, formatting,
TypeScript і зафіксовані архітектурні правила в репозиторії.

**Коротко**

Структуруй по feature-межах, щоб ownership, повторне використання і рефакторинг
залишались керованими.

</details>

<details>
<summary>82. Як забезпечити масштабованість і підтримуваність?</summary>

#### React Native

Масштабованість і підтримуваність з'являються на перетині якісної архітектури та
інженерної дисципліни процесів.

Ключові практики:

1. Використовувати модульні feature-межі й reusable-примітиви.
2. Тримати бізнес-логіку поза UI-компонентами.
3. Використовувати TypeScript для безпечніших рефакторингів.
4. Додавати автоматизовані тести на рівнях unit/integration/E2E.
5. Контролювати якість коду через ESLint, Prettier, CI checks і code review.
6. Безперервно відстежувати performance regression і crash analytics.
7. Документувати ключові патерни (state, navigation, networking, error handling).

Масштабований codebase передбачуваний: нові фічі додаються за сталими правилами
без хаотичних винятків.

**Коротко**

Масштабованість тримається на стабільній архітектурі, автоматизації і чітко
дотримуваних інженерних стандартах.

</details>

<details>
<summary>83. Які best practices роботи з чутливими даними?</summary>

#### React Native

Чутливі дані (tokens, secrets, PII) мають бути захищені в storage, transit і
логах.

Best practices:

1. Ніколи не хардкодити секрети в source-коді й не вшивати приватні ключі в
   застосунок.
2. Використовувати secure storage (iOS Keychain / Android Keystore wrappers).
3. Використовувати HTTPS/TLS для всього API-трафіку.
4. Мінімізувати обсяг і час зберігання чутливих даних.
5. Редагувати (redact) чутливі поля в логах, аналітиці й crash reports.
6. Ротувати токени/ключі та мати механізм revocation.
7. Додавати jailbreak/root і tamper detection, якщо цього вимагає threat model.

`AsyncStorage` не підходить для високочутливих секретів.

**Коротко**

Секрети зберігай лише безпечно, мінімізуй їх експозицію і не сприймай plain
storage як secure vault.

</details>

<details>
<summary>84. Як організувати автентифікацію (біометрія, токени)?</summary>

#### React Native

Автентифікація в React Native зазвичай поєднує безпечний token lifecycle з
опційним біометричним unlock для зручності.

Типовий flow:

1. Користувач входить (credentials/OAuth/social).
2. Бекенд повертає access + refresh tokens.
3. Зберігати токени в secure storage (не в plain AsyncStorage).
4. Додавати access token до API-запитів.
5. Оновлювати токен після expiry access token.
6. На logout очищати токени та session state.

Використання біометрії:

1. Face ID / Touch ID / Android biometrics для повторної локальної
   автентифікації.
2. Серверна auth-модель лишається token-based; біометрія лише «відкриває» локальну
   сесію.

Тримайте централізований auth state і request interceptors, щоб не дублювати
логіку.

**Коротко**

Найкраще працює комбінація: безпечний цикл токенів + біометрія для локального
re-auth.

</details>

<details>
<summary>85. Що таке react-native-webview і коли його використовувати?</summary>

#### React Native

`react-native-webview` — це компонент для рендерингу веб-контенту всередині
мобільного застосунку.

Сценарії використання:

1. Відображення зовнішніх або внутрішніх веб-сторінок.
2. Вбудовування вже готових web-flow (help center, payment pages, docs).
3. Інтеграція гібридних модулів, коли повний native rewrite недоцільний.

Приклад:

```jsx
import { WebView } from 'react-native-webview';

function DocsScreen() {
  return <WebView source={{ uri: 'https://example.com/docs' }} />;
}
```

Для критичних сценаріїв використовуйте обережно: за UX, performance, security та
інтеграцією зазвичай виграють повністю native/RN-екрани.

**Коротко**

WebView зручний для ізольованих web-flow, але core-UX краще реалізовувати
нативно/через RN-компоненти.

</details>

<details>
<summary>86. Що таке react-native-svg і чому це корисно?</summary>

#### React Native

`react-native-svg` надає примітиви для рендерингу SVG у React Native.

Чому це корисно:

1. Векторна графіка, незалежна від роздільної здатності.
2. Зручно для іконок, графіків і ілюстрацій.
3. Гнучкіше, ніж статичні PNG-асети.

Це стандартна залежність для багатьох проєктів із багатим UI-дизайном.

**Коротко**

SVG дає чітку й масштабовану графіку на екранах із різною щільністю.

</details>

<details>
<summary>87. Як реалізувати drawer navigation?</summary>

#### React Native

Використовуйте `@react-navigation/drawer`.

Базовий flow:

1. Встановити залежності drawer navigator.
2. Створити `Drawer.Navigator` з екранами.
3. За потреби кастомізувати drawer content.
4. Комбінувати з stack/tab навігаторами.

Тримайте в drawer лише верхньорівневі маршрути й уникайте зайвої вкладеності.

**Коротко**

Drawer добре підходить для top-level секцій, якщо ієрархія проста й
передбачувана.

</details>

<details>
<summary>88. Що таке gesture-based navigation?</summary>

#### React Native

Gesture-based navigation означає, що користувач рухається між екранами через
swipe та інші touch-патерни (back swipe, tab swipe, drawer drag).

У RN це зазвичай реалізується через React Navigation + Gesture Handler.

Переваги:

1. Більш «нативне» відчуття взаємодії.
2. Швидша навігація однією рукою в багатьох сценаріях.

**Коротко**

Жестова навігація покращує мобільний UX, якщо узгоджена з платформеними
патернами.

</details>

<details>
<summary>89. Як реалізувати shared element transitions?</summary>

#### React Native

Shared element transitions анімують спільний UI-елемент між двома екранами.

Типова реалізація:

1. Використати бібліотеку з підтримкою shared transitions.
2. Призначити однакові shared IDs на source/target елементах.
3. Налаштувати поведінку transition у навігації.

Це покращує візуальну безперервність у сценаріях list -> detail.

**Коротко**

Shared transitions зберігають візуальний контекст між списком і деталями, тому
перехід сприймається природніше.

</details>

<details>
<summary>90. Що таке Fabric renderer і чим він відрізняється?</summary>

#### React Native

Fabric — це новий рендерер RN у межах New Architecture.

Чим відрізняється від legacy renderer:

1. Краща інтеграція з concurrent-підходами React.
2. Ефективніший рендер-пайплайн.
3. Тісна взаємодія з JSI/TurboModules.
4. Менша затримка для частини UI-оновлень.

Fabric — один із ключових елементів модернізації RN.

**Коротко**

Fabric підвищує ефективність рендерингу й краще узгоджується із сучасним
runtime React Native.

</details>

<details>
<summary>91. Яка перевага архітектури TurboModules?</summary>

#### React Native

TurboModules — частина New Architecture у React Native, яка покращує завантаження
і виклик native-модулів із JavaScript.

Ключові переваги:

1. **Lazy loading:** модулі ініціалізуються лише за потреби.
2. **Краща продуктивність:** менше накладних витрат під час старту і нижча
   вартість bridge-взаємодії.
3. **Type safety через codegen:** сильніші контракти між JS і native.
4. **Краща підтримуваність:** чіткіші інтерфейси модулів і сучасніша інтеграція
   native-шару.

TurboModules особливо корисні у великих застосунках із багатьма native
залежностями.

**Коротко**

TurboModules покращують старт і доступ до native-функцій завдяки lazy-loading і
типізованим інтерфейсам.

</details>

<details>
<summary>92. Як обробляти error boundaries у React Native?</summary>

#### React Native

Error Boundaries перехоплюють помилки рендеру в дочірньому дереві компонентів і
не дають впасти всьому UI застосунку.

У React Native їх реалізують як class-компоненти з:

1. `static getDerivedStateFromError(error)`
2. `componentDidCatch(error, info)`

Приклад:

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
    // Send error to monitoring service
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

Огорніть критичні дерева екранів у boundaries і відправляйте помилки в системи
моніторингу.

**Коротко**

Error boundary ізолює render-crash і показує fallback UI замість падіння всього
застосунку.

</details>

<details>
<summary>93. Як обробляти глобальні помилки?</summary>

#### React Native

Глобальна обробка помилок покриває unhandled JS exceptions, promise rejections і
native crashes.

Поширена стратегія:

1. Налаштувати глобальний JS error handler.
2. Перехоплювати unhandled promise rejections.
3. Інтегрувати crash/error моніторинг (наприклад, Sentry, Bugsnag).
4. Безпечно логувати контекст (user/session/screen).
5. Показувати fallback UI, де можливо, і відновлювати роботу.

Окремо відстежуйте native-crashes через platform tooling і monitoring SDK.

**Коротко**

Неперехоплені JS/native помилки слід збирати централізовано і логувати з
достатнім контекстом для діагностики.

</details>

<details>
<summary>94. Що таке AppState і як його використовують?</summary>

#### React Native

`AppState` дозволяє визначити, чи застосунок активний, у background або в
проміжному неактивному стані.

Типові стани:

1. `active`: застосунок у foreground і доступний для взаємодії.
2. `background`: застосунок працює у фоні.
3. `inactive` (переважно перехідний стан на iOS).

Сценарії використання:

1. Pause/resume таймерів, відео або polling.
2. Оновлення чутливих даних при поверненні у foreground.
3. Тригери для analytics/session lifecycle events.

Приклад:

```jsx
import { AppState } from 'react-native';

const subscription = AppState.addEventListener('change', nextState => {
  // Handle state transition
});

// Later:
subscription.remove();
```

**Коротко**

AppState допомагає коректно зупиняти/відновлювати роботу при переходах між
foreground і background.

</details>

<details>
<summary>95. Як обробляти кнопку Back на Android (BackHandler)?</summary>

#### React Native

На Android апаратну кнопку назад можна обробляти через `BackHandler`.

Патерн:

1. Підписатися на `hardwareBackPress`.
2. Повернути `true`, щоб перехопити подію.
3. Повернути `false`, щоб залишити стандартну поведінку (наприклад,
   navigation back).

Приклад:

```jsx
import { BackHandler } from 'react-native';
import { useEffect } from 'react';

useEffect(() => {
  const sub = BackHandler.addEventListener('hardwareBackPress', () => {
    // Custom logic here
    return false;
  });

  return () => sub.remove();
}, []);
```

Якщо використовуєте React Navigation, спочатку покладайтеся на її back handling
API, а `BackHandler` використовуйте для edge-case сценаріїв.

**Коротко**

Back press треба обробляти свідомо та узгоджено з навігаційною логікою
застосунку.

</details>

<details>
<summary>96. Як оптимізувати розмір бандла?</summary>

#### React Native

Оптимізація bundle size фокусується на зменшенні обсягу JS/asset-ів, які
доставляються в застосунок.

Практичні кроки:

1. Видаляти невикористані залежності.
2. Імпортувати лише потрібні модулі.
3. Стискати/ресайзити зображення та медіа.
4. Увімкнути minification і production build optimization.
5. Розділяти важкі фічі там, де це дозволяє архітектура.

Менший бандл покращує startup і швидкість доставки оновлень.

**Коротко**

Чим менше JS/asset-ів відправляється в продакшен, тим кращі старт і оновлення
застосунку.

</details>

<details>
<summary>97. Як проводити version upgrades і міграції?</summary>

#### React Native

Оновлення версій краще робити інкрементально та з автоматизованою валідацією.

Рекомендований процес:

1. Оновлюватися малими кроками.
2. Читати release notes і breaking changes RN.
3. Використовувати upgrade helpers/diffs.
4. Проганяти повні тести на iOS і Android.
5. Релізити з моніторингом і готовністю до rollback.

По можливості уникайте великих стрибків через кілька версій одразу.

**Коротко**

Надійні апгрейди — це дрібні кроки, перевірка змін релізу і повна регресія на
обох платформах.

</details>

<details>
<summary>98. Які обмеження React Native?</summary>

#### React Native

Поширені обмеження:

1. Частина складних native API вимагає кастомного нативного коду.
2. Якість пакетів в екосистемі може суттєво відрізнятись.
3. Продуктивність може деградувати при слабкій архітектурі або великому
   JS-навантаженні.
4. Оновлення й робота з нативним toolchain інколи доволі складні.

Попри це, RN лишається дуже ефективним для багатьох кросплатформних застосунків.

**Коротко**

RN продуктивний у більшості сценаріїв, але для складних кейсів інколи потрібні
native-рішення й ретельний performance-тюнінг.

</details>

<details>
<summary>99. Як реалізувати real-time синхронізацію?</summary>

#### React Native

Real-time sync поєднує live-transport із conflict-safe оновленням локального
стану.

Типова стратегія:

1. Отримувати live events через WebSocket/subscriptions.
2. Використовувати optimistic updates для дій користувача.
3. Персистити локальний state для офлайн-стійкості.
4. Після reconnect узгоджувати server truth із локальними змінами.
5. Використовувати versioning/conflict resolution правила.

Такий підхід дозволяє зберігати дані актуальними й консистентними.

**Коротко**

Real-time синхронізація потребує стріму подій, безпечного reconcile і стійкості
до офлайн/перепідключень.

</details>

<details>
<summary>100. Як спроєктувати масштабовану мобільну архітектуру?</summary>

#### React Native

Масштабована мобільна архітектура базується на чітких межах модулів і
передбачуваних потоках даних.

Ключові принципи:

1. Feature-based модульна структура.
2. Відокремлення UI, domain logic і data layer.
3. Явна стратегія стану (local/global/server state).
4. Консистентні патерни навігації, помилок і мережевої взаємодії.
5. Автоматизовані quality gates (tests, lint, CI, monitoring).

Архітектура має оптимізувати довгострокову швидкість змін, а не лише швидкий
старт.

**Коротко**

Ставка на модульні межі, прозорий data flow і enforceable інженерні конвенції
дає реальну масштабованість продукту.

</details>

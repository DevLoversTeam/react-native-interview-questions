**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  React Native <img src="./assets/reactnative.svg" width="40" height="40" />
</h1>

<h2>Most Popular React Native Interview Questions and Answers</h2>

<details>
<summary>1. What is React Native and how does it differ from React?</summary>

#### React Native

React Native is an open-source framework for building mobile applications using
JavaScript/TypeScript and React.

Key difference:

1. **React (React.js):** Builds web UIs that render to the browser DOM (`div`,
   `span`, etc.).
2. **React Native:** Builds iOS/Android apps that render to native platform
   components (`View`, `Text`, `Image`, etc.).

Both use the same component model, props/state, and hooks, but target different
platforms and rendering layers.

**In short**

Mention that React Native targets mobile with native UI components, while React
targets the web DOM.

</details>

<details>
<summary>2. Explain the concept of JSX in React Native.</summary>

#### React Native

JSX (JavaScript XML) is a syntax extension that lets you write UI structure in a
declarative, HTML-like style inside JavaScript.

In React Native, JSX is used with native components:

```jsx
function Greeting() {
  return <Text>Hello, React Native!</Text>;
}
```

Notes:

1. JSX is not HTML. It is transformed into JavaScript calls by Babel.
2. You can embed JavaScript expressions inside `{}`.
3. React Native JSX uses native components (`View`, `Text`) instead of browser
   tags (`div`, `p`).

**In short**

Explain that JSX is just syntax sugar for describing UI, and React Native maps
it to native components.

</details>

<details>
<summary>3. How do you create a functional component in React Native?</summary>

#### React Native

A functional component is a JavaScript function that returns JSX.

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

You can also use arrow function syntax:

```jsx
const ProfileCard = () => (
  <View>
    <Text>Profile</Text>
  </View>
);
```

**In short**

Say it is a plain function returning JSX, usually combined with hooks for state
and effects.

</details>

<details>
<summary>4. What are core components in React Native (View, Text, Image, etc.)?</summary>

#### React Native

Core components are built-in UI primitives provided by React Native for creating
mobile interfaces.

Common core components:

1. **View:** Basic container for layout and styling.
2. **Text:** Displays text content.
3. **Image:** Renders images from local assets or remote URLs.
4. **TextInput:** Input field for user text entry.
5. **ScrollView:** Scrollable container for content.
6. **FlatList / SectionList:** Efficient list rendering for large datasets.
7. **Pressable / TouchableOpacity:** Handles touch interactions.
8. **SafeAreaView:** Respects screen safe areas (notches, rounded corners).

These components map to native UI elements on iOS and Android.

**In short**

Show that these are RN building blocks and give 2-3 examples you use daily.

</details>

<details>
<summary>5. What are props in React Native and how are they used?</summary>

#### React Native

Props (properties) are read-only inputs passed from a parent component to a
child component.

They are used to:

1. Pass data (text, numbers, objects, arrays).
2. Pass behavior (callback functions).
3. Configure reusable components.

Example:

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

Here, `name` is a prop sent from `App` to `WelcomeMessage`.

**In short**

Describe props as read-only inputs from parent to child, mainly for
configuration and data flow.

</details>

<details>
<summary>6. What is state in React Native and how is it managed with hooks?</summary>

#### React Native

State is component-owned data that can change over time and trigger UI updates.

In functional components, state is commonly managed with the `useState` hook:

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

For more complex logic, you can use `useReducer`.

**In short**

State is mutable local data; with hooks you update it and trigger rerenders
predictably.

</details>

<details>
<summary>7. What is the difference between state and props?</summary>

#### React Native

`state` and `props` both store data for rendering, but they have different
roles:

1. **Props:** Read-only inputs passed from parent to child components.
2. **State:** Internal, mutable data managed by the component itself.

Quick comparison:

1. **Who owns data?** Props: parent component. State: current component.
2. **Can it change locally?** Props: no. State: yes, via hooks like `useState`.
3. **Use case:** Props: configuration and data flow between components. State:
   dynamic UI behavior inside a component.

**In short**

Describe props as read-only inputs from parent to child, mainly for
configuration and data flow.

</details>

<details>
<summary>8. How do you handle user input in React Native?</summary>

#### React Native

User input is usually handled with controlled components, most often
`TextInput`, combined with state.

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

Key events/handlers:

1. `onChangeText`: updates text state.
2. `onPress`: handles button/touch actions.
3. `onSubmitEditing`: reacts to keyboard submit on `TextInput`.

**In short**

Mention controlled inputs: keep value in state and update through handlers.

</details>

<details>
<summary>9. How do you style components in React Native?</summary>

#### React Native

React Native uses JavaScript objects for styles instead of CSS files.

You can style components in three common ways:

1. **Inline styles** (quick, local styling):

```jsx
<Text style={{ color: 'blue', fontSize: 18 }}>Hello</Text>
```

2. **`StyleSheet.create`** (recommended for most cases):

```jsx
const styles = StyleSheet.create({
  title: { color: 'blue', fontSize: 18 },
});
```

3. **Style arrays** (conditional/composed styles):

```jsx
<Text style={[styles.title, isActive && styles.active]}>Hello</Text>
```

React Native styles are close to CSS, but use camelCase properties (for example,
`backgroundColor`, `fontSize`).

**In short**

Explain RN styling uses JS objects, often centralized for consistency and reuse.

</details>

<details>
<summary>10. What is StyleSheet and when should you use it?</summary>

#### React Native

`StyleSheet` is a React Native utility for defining and organizing styles in a
structured way.

Example:

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

When to use:

1. When styles are reused across multiple elements.
2. When you want cleaner, maintainable component code.
3. When you want a consistent, scalable styling approach in larger screens/apps.

**In short**

Use StyleSheet for cleaner, reusable style definitions and better
maintainability.

</details>

<details>
<summary>11. Explain Flexbox and its role in layout.</summary>

#### React Native

Flexbox is the primary layout system in React Native. It controls how components
are sized, aligned, and distributed inside a container.

In React Native, Flexbox defaults are slightly different from web CSS:

1. `flexDirection` default is `column`.
2. `alignContent` default is `flex-start`.
3. `flexShrink` default is `0`.

Common properties:

1. `flex`: defines how much space an item takes relative to siblings.
2. `flexDirection`: row or column layout.
3. `justifyContent`: alignment on the main axis.
4. `alignItems`: alignment on the cross axis.
5. `gap` (modern RN versions): spacing between children.

Example:

```jsx
<View
  style={{ flex: 1, flexDirection: 'row', justifyContent: 'space-between' }}
>
  <View style={{ width: 50, height: 50, backgroundColor: 'red' }} />
  <View style={{ width: 50, height: 50, backgroundColor: 'blue' }} />
</View>
```

**In short**

Focus on axis-based layout: main axis vs cross axis, then justify/align
behavior.

</details>

<details>
<summary>12. How do you handle responsive design in React Native?</summary>

#### React Native

Responsive design in React Native is handled by combining flexible layouts with
device-aware APIs.

Common approaches:

1. Use Flexbox (`flex`, `%`, alignment) instead of fixed sizes.
2. Use `Dimensions` or `useWindowDimensions()` for screen size.
3. Use `Platform` for platform-specific adjustments.
4. Use `SafeAreaView` to respect notches and system UI.
5. Scale typography/spacing with shared constants.

Example:

```jsx
import { useWindowDimensions, View } from 'react-native';

function ResponsiveCard() {
  const { width } = useWindowDimensions();
  const isTablet = width >= 768;

  return <View style={{ padding: isTablet ? 24 : 16 }} />;
}
```

**In short**

Say you combine flexible layouts with screen dimensions and safe-area awareness.

</details>

<details>
<summary>13. How do you debug a React Native application?</summary>

#### React Native

Debugging in React Native is usually done with a combination of built-in and
external tools.

Main options:

1. **Metro logs:** `console.log`, warnings, errors in terminal/output.
2. **React Native Dev Menu:** reload app, inspect UI, enable debugging tools.
3. **React DevTools:** inspect component tree, props, and hooks state.
4. **Flipper:** network inspection, logs, layout inspection, performance
   plugins.
5. **Native tooling:** Xcode (iOS) and Android Studio (Android) for native-level
   crashes and logs.

Best practice: reproduce issues with clear steps, isolate the failing component,
and verify on both iOS and Android when relevant.

**In short**

Answer with tool stack: logs, DevTools/Flipper, and native logs for platform
issues.

</details>

<details>
<summary>14. What is Fast Refresh and how does it work?</summary>

#### React Native

Fast Refresh is a development feature that updates the app immediately after
code changes, while trying to preserve component state.

How it works:

1. You save a file.
2. Metro rebuilds only affected modules.
3. React Native injects updated code into the running app.
4. UI updates instantly without a full restart in most cases.

Notes:

1. Local state is usually preserved for functional components.
2. If edits affect module initialization or non-component exports, React Native
   may perform a broader reload.
3. It is a dev-only feature and not part of production behavior.

**In short**

Explain it updates changed modules in development and usually preserves local
state.

</details>

<details>
<summary>15. What are Touchable components and how do they work?</summary>

#### React Native

Touchable components are interactive wrappers that respond to taps/presses. They
let users trigger actions like opening screens, submitting forms, or selecting
items.

Common options:

1. `Pressable` (modern and flexible, recommended in many cases).
2. `TouchableOpacity` (changes opacity on press).
3. `TouchableHighlight` (shows highlight under child).
4. `TouchableWithoutFeedback` (no visual feedback).

Example:

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

They expose events like `onPress`, `onPressIn`, `onPressOut`, and `onLongPress`.

**In short**

These wrap UI with press interactions; choose Pressable for modern flexible
handling.

</details>

<details>
<summary>16. How do you handle navigation in React Native (React Navigation)?</summary>

#### React Native

Navigation is commonly handled with `@react-navigation/*`.

Typical setup:

1. Install React Navigation core and required navigators.
2. Wrap app with `NavigationContainer`.
3. Define stacks/tabs/drawers.
4. Navigate with `navigation.navigate('ScreenName')`.

For most apps, combine Stack + Tab navigators and keep route names typed.

**In short**

Use navigator composition (stack/tab/drawer) and keep route structure explicit.

</details>

<details>
<summary>17. What is the role of NavigationContainer?</summary>

#### React Native

`NavigationContainer` is the root provider that manages navigation state and
links navigators to the app environment.

It is responsible for:

1. Holding current navigation tree state.
2. Handling linking/deep links.
3. Providing navigation context to all screens.

Without it, React Navigation cannot work.

**In short**

It is the root navigation context and state holder for the entire app.

</details>

<details>
<summary>18. How do you pass parameters between screens?</summary>

#### React Native

Pass params through navigation methods.

Example:

```jsx
navigation.navigate('Profile', { userId: '42' });
```

Read params in target screen:

```jsx
const { userId } = route.params;
```

Use params for small route context, not for large/global app state.

**In short**

Send small route params via navigate and read them from route params.

</details>

<details>
<summary>19. What is deep linking and how do you implement it?</summary>

#### React Native

Deep linking allows opening a specific app screen from a URL.

Implementation with React Navigation:

1. Define URL scheme/universal links in native configs.
2. Configure `linking` object in `NavigationContainer`.
3. Map URL paths to screen names.

This enables flows like `myapp://product/123` opening Product screen.

**In short**

Map URLs to screens so external links can open exact app routes.

</details>

<details>
<summary>20. What are keys in lists and why are they important?</summary>

#### React Native

`key` identifies list items uniquely for React reconciliation.

Why important:

1. Helps React update only changed rows.
2. Prevents incorrect item reuse/state bugs.
3. Improves rendering performance and predictability.

Always use stable unique IDs, not array index (unless list is static).

**In short**

Use stable unique keys to avoid list rendering bugs and improve update
performance.

</details>

<details>
<summary>21. How do you render lists efficiently (FlatList, SectionList)?</summary>

#### React Native

For efficient list rendering in React Native, prefer `FlatList` and
`SectionList` instead of mapping large arrays inside `ScrollView`.

Why they are efficient:

1. They render items lazily (only visible rows + buffer).
2. They recycle item views and reduce memory usage.
3. They provide built-in pagination and scroll optimizations.

Use cases:

1. `FlatList`: one-dimensional list of similar items.
2. `SectionList`: grouped list with section headers.

Basic `FlatList` example:

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

**In short**

Prefer virtualized lists for large data to control memory and scroll
performance.

</details>

<details>
<summary>22. What is VirtualizedList and when should you use it?</summary>

#### React Native

`VirtualizedList` is the base list engine behind `FlatList` and `SectionList`.
It handles windowed rendering for large datasets.

When to use it directly:

1. When your data source is not a simple array.
2. When you need full control over `getItem` and `getItemCount`.
3. When `FlatList`/`SectionList` abstractions are too limited.

In most apps, use `FlatList` or `SectionList` first because they are easier and
cover common scenarios.

**In short**

Use it directly only for custom data access; otherwise FlatList/SectionList is
simpler.

</details>

<details>
<summary>23. How do you fetch data in React Native (fetch, axios)?</summary>

#### React Native

You can fetch data with the built-in `fetch` API or with `axios`.

`fetch` example:

```jsx
async function loadPosts() {
  const response = await fetch('https://api.example.com/posts');
  if (!response.ok) throw new Error('Request failed');
  return response.json();
}
```

`axios` example:

```jsx
import axios from 'axios';

async function loadPosts() {
  const { data } = await axios.get('https://api.example.com/posts');
  return data;
}
```

Typical flow in a component:

1. Start loading state.
2. Perform async request.
3. Save result or error in state.
4. Stop loading and render accordingly.

**In short**

Explain request lifecycle clearly: loading, success, failure, and cancellation
handling.

</details>

<details>
<summary>24. What are best practices for API calls and error handling?</summary>

#### React Native

Best practices for API and error handling:

1. Centralize API logic in a service layer.
2. Always handle loading, success, and error states.
3. Set request timeouts and retry strategy for transient failures.
4. Validate response shape before using data.
5. Show user-friendly error messages (not raw server errors).
6. Use cancellation (`AbortController`) to avoid updating unmounted screens.
7. Add auth token refresh logic in one place (interceptors/middleware).

Short pattern:

1. `try` request.
2. `catch` network/server errors.
3. Map to domain-specific error messages.
4. Log technical details for debugging/monitoring.

**In short**

Stress centralized API layer, consistent error mapping, and retry/cancel
strategy.

</details>

<details>
<summary>25. How do you handle async storage (AsyncStorage community package)?</summary>

#### React Native

`AsyncStorage` is a persistent key-value storage solution for lightweight data
such as user settings, flags, and cached primitives.

Basic usage:

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

1. Serialize objects with `JSON.stringify` / `JSON.parse`.
2. Wrap calls in `try/catch`.
3. Keep payloads small; do not use it as a database.
4. Namespace keys (for example, `app:user:token`).
5. For sensitive data, prefer secure storage solutions (Keychain/Keystore).

**In short**

Use it for lightweight persistence, not secrets; serialize data and handle
errors.

</details>

<details>
<summary>26. What are modern state management solutions (Context, Zustand, Redux Toolkit)?</summary>

#### React Native

Modern options depend on app complexity:

1. **Context API:** simple global data, low boilerplate.
2. **Zustand:** lightweight store, easy API, minimal ceremony.
3. **Redux Toolkit:** robust patterns, middleware, devtools, large-team scaling.

Choose smallest tool that matches complexity and team needs.

**In short**

Choose by complexity: Context for simple cases, Zustand/RTK for larger state
domains.

</details>

<details>
<summary>27. How do you manage global state without Redux?</summary>

#### React Native

Use Context + hooks or lightweight stores like Zustand/Jotai.

Common pattern:

1. Create provider for shared domain state.
2. Encapsulate updates in custom hooks.
3. Keep server state separate (React Query/Apollo).

This avoids Redux boilerplate while staying scalable for many apps.

**In short**

Combine Context or lightweight stores with custom hooks and clear boundaries.

</details>

<details>
<summary>28. What are React hooks and which are commonly used?</summary>

#### React Native

Hooks are functions that let functional components use state, effects, and other
React capabilities.

Common hooks:

1. `useState`
2. `useEffect`
3. `useMemo`
4. `useCallback`
5. `useRef`
6. `useContext`
7. `useReducer`

They enable reusable logic through custom hooks.

**In short**

Hooks bring stateful logic to functions and make behavior reusable through
custom hooks.

</details>

<details>
<summary>29. What is useEffect and how does it replace lifecycle methods?</summary>

#### React Native

`useEffect` runs side effects after render and can clean them up.

Lifecycle mapping (class -> hooks):

1. `componentDidMount` -> `useEffect(..., [])`
2. `componentDidUpdate` -> `useEffect(..., [deps])`
3. `componentWillUnmount` -> cleanup function returned from `useEffect`

It unifies lifecycle behavior in functional components.

**In short**

Use it for side effects and cleanup; think in dependencies, not class lifecycle
names.

</details>

<details>
<summary>30. What is useMemo and useCallback and when to use them?</summary>

#### React Native

`useMemo` memoizes calculated values. `useCallback` memoizes function
references.

Use them when:

1. Computation is expensive.
2. Stable references are required to avoid child rerenders.
3. Values/callbacks are dependencies in other hooks.

Do not overuse them; apply where profiling shows benefit.

**In short**

Apply them selectively to stabilize expensive values/callbacks when profiling
justifies it.

</details>

<details>
<summary>31. What are refs and when should you use them?</summary>

#### React Native

Refs are mutable references to component instances or native elements. They let
you access imperative APIs without triggering re-renders.

Typical use cases:

1. Focus or blur a `TextInput`.
2. Trigger scroll methods (`scrollToOffset`, `scrollToEnd`).
3. Measure layout (`measure`, `measureInWindow`).
4. Store mutable values that should not cause UI updates.

Example:

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

Use refs for imperative actions, not for replacing normal state/props data flow.

**In short**

Refs are for imperative access (focus/scroll/measure), not for normal data flow.

</details>

<details>
<summary>32. How do you create custom hooks?</summary>

#### React Native

A custom hook is a reusable function that starts with `use` and combines React
hooks (`useState`, `useEffect`, etc.) into shared logic.

Rules:

1. Hook name must start with `use`.
2. Call hooks only at the top level of the custom hook.
3. Return values/functions needed by components.

Example:

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

Custom hooks improve reuse, readability, and separation of concerns.

**In short**

Extract repeated stateful logic into use\* functions to keep components focused.

</details>

<details>
<summary>33. What is performance optimization in React Native?</summary>

#### React Native

Performance optimization in React Native means reducing rendering, JavaScript,
and layout overhead to keep interactions smooth (especially on mid/low-end
devices).

Common optimization areas:

1. Rendering: avoid unnecessary re-renders.
2. Lists: use `FlatList`/`SectionList` with proper tuning.
3. JavaScript work: move heavy computations off critical render paths.
4. Images: compress, cache, and size correctly.
5. Native/JS communication: minimize expensive cross-layer operations.

Typical goal: stable 60 FPS, faster startup, and responsive touch handling.

**In short**

Profile first, then optimize renders, list behavior, images, and JS workload
hotspots.

</details>

<details>
<summary>34. How do you avoid unnecessary re-renders?</summary>

#### React Native

You avoid unnecessary re-renders by stabilizing props and reducing state updates
to only what is needed.

Practical techniques:

1. Use `React.memo` for pure functional components.
2. Use `useMemo` for expensive derived values.
3. Use `useCallback` for stable callback references.
4. Keep state as local as possible.
5. Avoid creating new objects/functions inline when passed deep as props.
6. Split large components into smaller focused components.
7. Use stable keys in lists.

Also profile first (React DevTools/Flipper) and optimize where real bottlenecks
exist.

**In short**

Keep props stable, localize state, and memoize only where it reduces real render
cost.

</details>

<details>
<summary>35. What is memoization in React Native?</summary>

#### React Native

Memoization is a technique that caches computed results or component outputs and
reuses them when inputs have not changed.

In React Native, common memoization tools are:

1. `React.memo`: memoizes component rendering by props comparison.
2. `useMemo`: memoizes computed values.
3. `useCallback`: memoizes function references.

Example:

```jsx
import React, { useMemo } from 'react';

function Total({ items }) {
  const sum = useMemo(() => {
    return items.reduce((acc, item) => acc + item.price, 0);
  }, [items]);

  return <Text>{sum}</Text>;
}
```

Use memoization selectively; overusing it can add complexity without measurable
benefit.

**In short**

Memoization caches values/functions/renders to avoid recomputing unchanged work.

</details>

<details>
<summary>36. What is Hermes engine and why is it important?</summary>

#### React Native

Hermes is a JavaScript engine optimized for React Native.

Why important:

1. Faster app startup.
2. Lower memory usage on many devices.
3. Better performance predictability on Android/iOS.
4. Good integration with RN tooling.

Hermes is a common default choice for production RN apps.

**In short**

Hermes improves startup and memory characteristics for many RN production apps.

</details>

<details>
<summary>37. What is the new React Native architecture?</summary>

#### React Native

New Architecture is the modernization of RN internals centered on:

1. Fabric renderer.
2. TurboModules.
3. JSI (JavaScript Interface).
4. Bridgeless direction.

Goals: lower latency between JS/native, better concurrency support, and improved
performance.

**In short**

Summarize it as Fabric + TurboModules + JSI for lower overhead and better
scalability.

</details>

<details>
<summary>38. What are Fabric and TurboModules?</summary>

#### React Native

`Fabric` is the new rendering system. `TurboModules` are the new native module
system.

Together they provide:

1. More efficient UI updates.
2. Faster module access.
3. Better type-safe native integration via codegen.
4. Improved startup and runtime performance.

**In short**

Fabric modernizes rendering; TurboModules modernize native module access and
loading.

</details>

<details>
<summary>39. What is JSI and how does it replace the old bridge?</summary>

#### React Native

JSI (JavaScript Interface) is a C++ API that lets JS and native interact more
directly.

Compared to old bridge:

1. Reduces heavy async JSON message passing.
2. Enables lower-overhead calls and shared runtime integrations.
3. Supports new architecture features like TurboModules/Fabric.

This significantly cuts communication bottlenecks.

**In short**

JSI reduces legacy bridge overhead by enabling more direct JS-native
interaction.

</details>

<details>
<summary>40. What is Bridgeless mode in React Native?</summary>

#### React Native

Bridgeless mode is an architecture direction where RN runs without the legacy
bridge runtime path.

Benefits:

1. Less communication overhead.
2. Cleaner modern runtime model.
3. Better alignment with Fabric, TurboModules, and JSI.

It is part of RN's long-term performance and maintainability evolution.

**In short**

Bridgeless removes dependency on the old bridge path for cleaner runtime
performance.

</details>

<details>
<summary>41. How does React Native achieve near-native performance?</summary>

#### React Native

React Native achieves near-native performance by rendering real native UI
components and optimizing work across JavaScript and native layers.

Key reasons:

1. UI is rendered with native views (`UIView`, `android.view`) rather than
   inside a web view.
2. React's declarative updates reduce unnecessary UI work.
3. Hermes can improve startup time and memory usage.
4. New Architecture (Fabric, TurboModules, JSI) reduces bridge overhead.
5. Optimized list components (`FlatList`, `SectionList`) support virtualization.

Performance still depends on app design: heavy JS work, unoptimized renders, and
large images can make apps feel slow.

**In short**

RN feels native when UI/render paths are optimized and heavy JS work is
controlled.

</details>

<details>
<summary>42. What are Native Modules and when should you use them?</summary>

#### React Native

Native Modules are custom platform-specific modules (iOS/Android) that expose
native functionality to JavaScript.

Use Native Modules when:

1. You need APIs not available in React Native core/community packages.
2. You need deeper access to device/platform capabilities.
3. You need better performance for logic that should run natively.

Examples:

1. Advanced camera or Bluetooth features.
2. Proprietary SDK integration (payments, biometrics, analytics).
3. OS-specific background services.

If a maintained community package exists, prefer it first. Write custom modules
when requirements are unique.

**In short**

Use native modules when you need platform APIs unavailable in core/community
packages.

</details>

<details>
<summary>43. How do you write native code for React Native (Swift/Kotlin)?</summary>

#### React Native

You write native code by creating a module in iOS (Swift/Objective-C) and/or
Android (Kotlin/Java), then exposing methods/events to JavaScript.

High-level flow:

1. Create native module class on each platform.
2. Export methods/constants/events to React Native.
3. Register module in native project.
4. Call module from JavaScript/TypeScript.

Minimal JS usage example:

```jsx
import { NativeModules } from 'react-native';

const { DeviceInfoModule } = NativeModules;

async function loadDeviceName() {
  const name = await DeviceInfoModule.getDeviceName();
  return name;
}
```

In modern RN, prefer TurboModules/Codegen patterns for long-term compatibility.

**In short**

Expose native capabilities through modules, then call them from JS through typed
interfaces.

</details>

<details>
<summary>44. How do you integrate React Native into an existing native app?</summary>

#### React Native

You can embed React Native as a feature inside an existing iOS/Android app
instead of rewriting the whole application.

Typical approach:

1. Add React Native dependencies to native projects.
2. Create a React Native bundle and runtime setup.
3. Start a React Native root view/screen from native navigation.
4. Exchange data between native and RN via props, events, or modules.

Common use cases:

1. Build one cross-platform module (for example, settings/profile) in an
   otherwise native app.
2. Migrate legacy screens incrementally.

This strategy reduces migration risk and lets teams adopt RN gradually.

**In short**

Integrate RN screen-by-screen to modernize incrementally instead of rewriting
all at once.

</details>

<details>
<summary>45. How do you handle platform-specific code (Platform API)?</summary>

#### React Native

Platform-specific behavior is handled with the `Platform` API and platform file
extensions.

Main techniques:

1. Runtime checks with `Platform.OS` (`ios`, `android`).
2. Platform selectors with `Platform.select(...)`.
3. Split files by extension: `Component.ios.tsx` and `Component.android.tsx`.

Example:

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

Prefer sharing most logic and isolating only necessary platform differences.

**In short**

Handle differences with Platform checks or platform-specific files while sharing
most logic.

</details>

<details>
<summary>46. How do you build components for iOS and Android differences?</summary>

#### React Native

Build shared core logic and isolate platform-specific UI/behavior only where
needed.

Techniques:

1. `Platform.OS` / `Platform.select`.
2. `Component.ios.tsx` and `Component.android.tsx` files.
3. Design system tokens with platform overrides.

Keep divergence minimal to reduce maintenance cost.

**In short**

Keep one shared component contract and isolate only platform-specific behavior.

</details>

<details>
<summary>47. How do you handle gestures in React Native?</summary>

#### React Native

Use gesture-focused libraries for reliable, high-performance interactions.

Common approach:

1. `react-native-gesture-handler` for recognizers.
2. `react-native-reanimated` for smooth gesture-driven animations.
3. Compose tap, pan, fling, and pinch handlers by screen needs.

Avoid heavy JS work inside active gesture callbacks.

**In short**

Use Gesture Handler and pair with Reanimated for smooth, production-grade
gesture UX.

</details>

<details>
<summary>48. What is PanResponder and when should you use it?</summary>

#### React Native

`PanResponder` is RN's built-in gesture responder for handling touch movement.

Use it when:

1. Gesture needs are simple.
2. You want zero extra dependency.

For complex, high-performance gestures, prefer Gesture Handler + Reanimated.

**In short**

PanResponder works for simple gestures; modern complex interactions usually need
gesture libraries.

</details>

<details>
<summary>49. What libraries are used for gestures (Gesture Handler, Reanimated)?</summary>

#### React Native

Most common gesture stack:

1. `react-native-gesture-handler` for robust gesture recognition.
2. `react-native-reanimated` for performant animations and worklets.

They are often used together for production-grade gesture UX.

**In short**

Use Gesture Handler and pair with Reanimated for smooth, production-grade
gesture UX.

</details>

<details>
<summary>50. What is Reanimated and why is it used?</summary>

#### React Native

Reanimated is a high-performance animation library for RN.

Why used:

1. Smooth animations with low jank.
2. Gesture-driven transitions.
3. Runs animation logic efficiently (worklets/UI-thread friendly model).
4. Great for complex interactions (bottom sheets, shared transitions, etc.).

**In short**

This combo is standard for robust recognition plus performant animated
responses.

</details>

<details>
<summary>51. What is the Animated API and how does it work?</summary>

#### React Native

`Animated` is React Native's built-in animation system for creating fluid UI
transitions by animating values over time.

How it works:

1. Create an animated value (`new Animated.Value(0)`).
2. Bind that value to style properties (`opacity`, `transform`, etc.).
3. Start animations with functions like `Animated.timing`, `spring`, or `decay`.

Example:

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

**In short**

Animated handles value-based transitions; use native driver where supported for
smoothness.

</details>

<details>
<summary>52. What is the difference between declarative and imperative animations?</summary>

#### React Native

The difference is in how animation behavior is described and controlled.

1. **Declarative animations:** Define the target UI state and transitions in a
   high-level way; the framework handles execution details.

2. **Imperative animations:** Manually control animation lifecycle step-by-step
   (start, stop, update values).

In React Native:

1. `LayoutAnimation` and many Reanimated patterns feel more declarative.
2. `Animated.Value` with direct `.start()` orchestration is more imperative.

Declarative approaches are often easier to maintain; imperative approaches can
provide finer control for complex interaction sequences.

**In short**

Declarative defines target behavior; imperative controls animation steps
manually.

</details>

<details>
<summary>53. How do you implement smooth animations?</summary>

#### React Native

To keep animations smooth, reduce main-thread work and avoid expensive rerenders
while motion is active.

Best practices:

1. Prefer `useNativeDriver: true` when supported.
2. Use `transform` and `opacity` animations over layout-heavy properties.
3. Keep animated components isolated and memoized when possible.
4. Avoid heavy computations during gestures/animations.
5. Use `react-native-reanimated` for advanced, high-performance interactions.
6. Optimize large lists/images that animate on screen.

Always test on real mid-range devices, not only emulator/simulator.

**In short**

Prioritize transform/opacity animations and avoid heavy JS during active
interactions.

</details>

<details>
<summary>54. What is LayoutAnimation and when should you use it?</summary>

#### React Native

`LayoutAnimation` animates global layout changes (position/size) when views are
added, removed, or resized.

When to use it:

1. Expanding/collapsing sections.
2. Insert/remove list rows with simple transitions.
3. UI updates where you want automatic layout interpolation.

Example:

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

Use it for straightforward layout transitions; for gesture-driven and complex
animations, Reanimated is usually a better fit.

**In short**

Use it for simple layout changes like expand/collapse, not advanced gesture
choreography.

</details>

<details>
<summary>55. How do you handle safe areas (SafeAreaView)?</summary>

#### React Native

Safe areas prevent content from overlapping with notches, rounded corners, and
system bars.

Recommended approach:

1. Use `react-native-safe-area-context`.
2. Wrap app root with `SafeAreaProvider`.
3. Use `SafeAreaView` or `useSafeAreaInsets()` in screens/components.

Example:

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

This ensures consistent spacing behavior across iOS and Android devices.

**In short**

Use safe-area context so content stays visible around notches and system UI.

</details>

<details>
<summary>56. How do you handle device orientation changes?</summary>

#### React Native

Handle orientation by listening to dimension/orientation changes and updating
layout accordingly.

Options:

1. `useWindowDimensions()` for responsive recalculation.
2. Orientation libraries for explicit lock/listen behaviors.
3. Platform-native config when screen rotation must be restricted.

Always test portrait/landscape transitions on real devices.

**In short**

Respond to dimension/orientation events and adapt layout without breaking
usability.

</details>

<details>
<summary>57. What is PixelRatio and when is it useful?</summary>

#### React Native

`PixelRatio` provides device pixel density utilities.

Useful for:

1. Scaling UI assets for high-density screens.
2. Rounding layout sizes to avoid blur.
3. Loading appropriately sized images.

It helps produce sharper and more consistent visuals across devices.

**In short**

Use PixelRatio for crisp visuals and density-aware sizing/image decisions.

</details>

<details>
<summary>58. How do you implement custom fonts?</summary>

#### React Native

Custom fonts are added as app assets and referenced in `fontFamily`.

Typical steps:

1. Add font files (`.ttf`/`.otf`) to assets.
2. Configure linking (RN CLI or Expo config).
3. Use font names in styles.
4. In Expo, load fonts before rendering with `expo-font`.

Keep a typography scale and fallback strategy for consistency.

**In short**

Load fonts as assets and apply a consistent typography system across screens.

</details>

<details>
<summary>59. How do you handle accessibility in React Native?</summary>

#### React Native

Accessibility should be built into components from the start.

Key practices:

1. Add accessible labels/hints.
2. Use semantic roles/states.
3. Ensure sufficient color contrast and touch targets.
4. Support dynamic text scaling.
5. Test with VoiceOver (iOS) and TalkBack (Android).

Accessibility improves UX for all users, not only assistive-tech users.

**In short**

Treat accessibility as baseline quality: labels, roles, state, contrast, and
screen-reader testing.

</details>

<details>
<summary>60. What are AccessibilityRole and AccessibilityState?</summary>

#### React Native

`accessibilityRole` describes what an element is (button, header, link, etc.).
`accessibilityState` describes current status (disabled, selected, checked,
busy, expanded).

They help screen readers announce meaningful context for interactive elements.

Example:

```jsx
<Pressable
  accessibilityRole="button"
  accessibilityState={{ disabled: isDisabled }}
>
  <Text>Submit</Text>
</Pressable>
```

**In short**

Role describes what element is; state describes its current interactive status.

</details>

<details>
<summary>61. How do you handle push notifications?</summary>

#### React Native

Push notifications are typically implemented with platform services plus a RN
library.

Common setup:

1. Choose provider: Firebase Cloud Messaging (FCM), APNs (iOS), or services like
   OneSignal.
2. Configure native app permissions and tokens (APNs token / FCM token).
3. Register listeners for foreground, background, and opened notifications.
4. Handle deep links/navigation when user taps a notification.

Typical libraries:

1. `@react-native-firebase/messaging` for FCM.
2. `notifee` for rich local/remote notification handling.

Best practice: keep payloads small, secure endpoints, and handle token refresh.

**In short**

Cover token registration, permission flow, foreground/background handling, and
tap navigation.

</details>

<details>
<summary>62. How do you implement background tasks?</summary>

#### React Native

Background tasks depend on platform limits and task type (sync, location,
uploads, notifications).

Approaches:

1. Use platform-native background APIs via libraries.
2. Schedule periodic jobs for lightweight work.
3. Use headless tasks on Android when app is terminated/backgrounded.

Common tools:

1. `react-native-background-fetch` for periodic fetch tasks.
2. `@react-native-firebase/messaging` background handlers for push-triggered
   work.
3. Native services/workers for advanced scenarios.

Important: iOS and Android apply strict battery policies, so background work is
never fully guaranteed at exact times.

**In short**

Background work is platform-constrained, so design for reliability rather than
exact timing.

</details>

<details>
<summary>63. How do you handle offline mode and data synchronization?</summary>

#### React Native

Offline mode is built around local-first data and sync when connectivity
returns.

Core strategy:

1. Persist data locally (AsyncStorage, SQLite, Realm, etc.).
2. Queue write operations while offline.
3. Detect connectivity changes.
4. Retry queued operations and resolve conflicts on reconnect.

Recommended practices:

1. Design API operations to be idempotent where possible.
2. Use timestamps/versioning for conflict resolution.
3. Show clear UI status: offline, syncing, failed, synced.
4. Keep a retry/backoff policy to avoid request storms.

**In short**

Use local-first storage plus queued writes and conflict-aware sync on reconnect.

</details>

<details>
<summary>64. How do you implement caching strategies?</summary>

#### React Native

Caching reduces latency, network usage, and repeated computation.

Common caching layers:

1. **API response cache:** in-memory + persistent cache.
2. **Image cache:** use optimized image libraries or HTTP cache headers.
3. **Computed data cache:** memoization (`useMemo`) for expensive derived
   values.
4. **Request cache:** libraries like React Query/Apollo normalized caches.

Practical rules:

1. Define TTL/invalidation rules per resource.
2. Use stale-while-revalidate patterns for responsive UI.
3. Clear cache on logout or auth-context changes.
4. Avoid unbounded cache growth.

**In short**

Define cache scope and invalidation rules; stale-while-revalidate often gives
best UX balance.

</details>

<details>
<summary>65. What is GraphQL and how do you use it in React Native?</summary>

#### React Native

GraphQL is a query language and runtime for APIs that lets clients request
exactly the data they need through a single endpoint.

Why it is useful in React Native:

1. Reduces over-fetching/under-fetching.
2. Fits screen-based data requirements well.
3. Works with strong client caching patterns.

How it is used:

1. Define GraphQL queries/mutations/subscriptions.
2. Use a client library (most commonly Apollo Client).
3. Execute operations in hooks/components.
4. Handle loading, error, and cache updates.

Small example shape:

```graphql
query GetUser($id: ID!) {
  user(id: $id) {
    id
    name
    avatar
  }
}
```

**In short**

GraphQL lets mobile screens request exactly needed fields, reducing
over-fetching.

</details>

<details>
<summary>66. What is Apollo Client and when should you use it?</summary>

#### React Native

Apollo Client is a popular GraphQL client for query/mutation/subscription
execution and normalized caching.

Use it when:

1. App relies heavily on GraphQL APIs.
2. You need strong cache features and update tools.
3. You need consistent GraphQL patterns across screens.

For REST-first apps, lighter alternatives may be simpler.

**In short**

Use Apollo when GraphQL caching and normalized client state are core
requirements.

</details>

<details>
<summary>67. What is NetInfo and how do you use it?</summary>

#### React Native

`@react-native-community/netinfo` provides network connectivity status.

Use cases:

1. Detect offline/online transitions.
2. Disable or queue network actions while offline.
3. Trigger sync/retry when connection is restored.

It is a core building block for resilient offline-first UX.

**In short**

NetInfo tracks connectivity so you can gate requests and trigger retries
intelligently.

</details>

<details>
<summary>68. How do you handle real-time updates (WebSockets, subscriptions)?</summary>

#### React Native

Real-time updates are typically handled with WebSockets or GraphQL
subscriptions.

Pattern:

1. Open persistent connection.
2. Subscribe to specific channels/events.
3. Merge incoming events into local/app state.
4. Reconnect with backoff on drops.

Handle app lifecycle and network changes to avoid stale sockets.

**In short**

Maintain persistent channels, reconcile events into state, and handle
reconnect/backoff.

</details>

<details>
<summary>69. What are common testing tools (Jest, Detox)?</summary>

#### React Native

Common testing stack:

1. **Jest:** unit and integration tests.
2. **React Native Testing Library:** component interaction testing.
3. **Detox:** end-to-end UI tests on emulator/simulator/device.
4. **ESLint/TypeScript in CI:** static correctness checks.

Combine these layers for reliable coverage.

**In short**

Use layered testing: Jest for logic/components and Detox for full end-to-end
flows.

</details>

<details>
<summary>70. How do you write unit tests in React Native?</summary>

#### React Native

Unit tests are usually written with Jest (+ Testing Library for components).

General steps:

1. Arrange component/function inputs.
2. Act by rendering or invoking behavior.
3. Assert output/state/callback expectations.

Good unit tests are isolated, deterministic, and fast.

**In short**

Good unit tests are fast and deterministic, validating behavior over
implementation details.

</details>

<details>
<summary>71. How do you perform end-to-end testing?</summary>

#### React Native

End-to-end (E2E) testing validates full user flows in a real or simulated app
environment, including UI, navigation, and integration with backend behavior.

Typical process:

1. Launch app in test mode.
2. Interact with UI like a user (tap, type, scroll).
3. Assert visible outcomes and navigation state.
4. Run tests in CI on multiple devices/configurations.

Most common RN E2E tool is **Detox**.

Best practices:

1. Add stable test IDs (`testID`) to important elements.
2. Keep tests deterministic (control network/data where possible).
3. Prioritize critical user journeys first (auth, checkout, core flows).

**In short**

E2E tests verify critical user journeys across real navigation and integration
boundaries.

</details>

<details>
<summary>72. What debugging tools are available (Flipper)?</summary>

#### React Native

React Native debugging usually combines runtime logs, component inspection, and
native diagnostics.

Common tools:

1. **Flipper:** plugins for logs, network, layout inspector, and performance.
2. **React DevTools:** inspect component tree, props, state, hooks.
3. **Metro logs:** console output and runtime warnings/errors.
4. **Xcode / Android Studio:** native crash logs, device logs, breakpoints.
5. **Hermes debugging support:** JS engine-specific profiling/inspection.

Flipper is especially useful as a central desktop hub for JS + native debugging.

**In short**

Answer with tool stack: logs, DevTools/Flipper, and native logs for platform
issues.

</details>

<details>
<summary>73. How do you profile performance in React Native?</summary>

#### React Native

Performance profiling helps identify real bottlenecks in render, JS execution,
and UI thread workload.

Key profiling methods:

1. Use React DevTools Profiler to inspect expensive renders.
2. Use Flipper plugins for performance and network timing.
3. Measure startup time and screen transition latency on real devices.
4. Inspect list rendering behavior (`FlatList` configs, dropped frames).
5. Profile native side with Xcode Instruments / Android Profiler.

What to look for:

1. Frequent unnecessary rerenders.
2. Long JS tasks blocking interactions.
3. Heavy image/layout work on critical screens.

Always profile production-like builds, not only debug builds.

**In short**

Profile on production-like builds to find real bottlenecks before optimizing.

</details>

<details>
<summary>74. What is Expo and when should you use it?</summary>

#### React Native

Expo is a platform and toolchain built around React Native that simplifies app
development, builds, and updates.

Use Expo when:

1. You want faster setup and developer productivity.
2. You need common native features via Expo SDK (camera, notifications, etc.).
3. You prefer streamlined cloud/local build workflows (EAS).

Expo includes:

1. Dev tools and runtime.
2. Expo SDK modules.
3. Build and submission tooling.
4. OTA update support through Expo services.

It is a strong default for many apps unless you need deep custom native control
from day one.

**In short**

Expo is best when you want faster delivery and less native setup overhead.

</details>

<details>
<summary>75. What is the difference between Expo managed and bare workflow?</summary>

#### React Native

The difference is how much native project control you have.

1. **Managed workflow:** Expo manages native configuration for you. You
   primarily work in JS/TS and Expo config. Faster development, less native
   maintenance.

2. **Bare workflow:** You have full native iOS/Android projects (similar to
   plain RN). More control, but more setup/maintenance complexity.

Choose managed when speed and simplicity matter most. Choose bare when you need
custom native code or advanced low-level integration.

**In short**

Managed favors speed; bare favors full native control and customization.

</details>

<details>
<summary>76. What are pros and cons of Expo?</summary>

#### React Native

Pros:

1. Fast project setup and iteration.
2. Rich SDK for common native features.
3. Easy build/update pipeline with EAS.
4. Good DX for small/medium teams.

Cons:

1. Less direct native control in managed workflow.
2. Some native edge cases require bare/eject.
3. Dependency on Expo ecosystem decisions/tools.

Expo is excellent for productivity, with tradeoffs in low-level flexibility.

**In short**

Expo improves DX and release speed, but deep native customization can require
bare workflow.

</details>

<details>
<summary>77. How do you handle app builds and deployment?</summary>

#### React Native

Build/deploy pipeline usually includes:

1. Versioning and changelog.
2. CI build for Android/iOS.
3. Automated tests and quality gates.
4. Signing and artifact generation.
5. Store submission (Play Console / App Store Connect).
6. Post-release monitoring and rollback plan.

Expo apps often use EAS Build/Submit; bare apps often use Fastlane/CI scripts.

**In short**

Treat releases as a pipeline: versioning, CI checks, signing, store submission,
monitoring.

</details>

<details>
<summary>78. What is code signing and why is it important?</summary>

#### React Native

Code signing cryptographically verifies app identity and integrity.

Why important:

1. Confirms app publisher authenticity.
2. Prevents tampered binaries from being trusted.
3. Required by app stores for distribution.

iOS uses certificates/profiles; Android uses keystores.

**In short**

Code signing proves app authenticity and is mandatory for trusted distribution.

</details>

<details>
<summary>79. How do you manage environments (dev/staging/prod)?</summary>

#### React Native

Use explicit environment configuration per build target.

Common setup:

1. Separate API endpoints and feature flags.
2. Build variants/flavors (Android) and schemes (iOS).
3. Env-specific secrets via secure CI variables.
4. Clear release channel naming.

Keep environment selection deterministic and visible in app diagnostics.

**In short**

Separate configs per environment and keep secrets/configuration out of source
code.

</details>

<details>
<summary>80. What is CodePush / OTA updates and when to use them?</summary>

#### React Native

OTA updates deliver JavaScript/assets without full store release.

When useful:

1. Fast bug fixes in JS layer.
2. Small content/logic updates.

Limits:

1. Cannot update native binary code.
2. Must follow store policies.

Use OTA for safe incremental JS updates, not as a replacement for binary
releases.

**In short**

OTA is great for JS fixes, but native code changes still require store binaries.

</details>

<details>
<summary>81. What are best practices for structuring a large codebase?</summary>

#### React Native

For large React Native projects, structure should optimize discoverability,
feature ownership, and long-term refactoring.

Common approach is feature-first organization:

1. Group by domain/feature (`features/auth`, `features/profile`, etc.).
2. Keep shared UI in `components/` and generic hooks in `hooks/`.
3. Keep API/data layer separated (`services/`, `api/`, `store/`).
4. Centralize app-wide config/constants (`config/`, `theme/`, `env/`).
5. Add clear boundaries and public entry points per feature.

Also enforce consistency with linting, formatting, TypeScript, and architecture
conventions documented in the repo.

**In short**

Organize by feature boundaries so ownership, reuse, and refactoring stay
manageable.

</details>

<details>
<summary>82. How do you ensure scalability and maintainability?</summary>

#### React Native

Scalability and maintainability come from good architecture plus engineering
process discipline.

Key practices:

1. Use modular feature boundaries and reusable primitives.
2. Keep business logic outside UI components.
3. Use TypeScript for safer refactors.
4. Add automated tests at unit/integration/E2E levels.
5. Enforce code quality with ESLint, Prettier, CI checks, and code review.
6. Track performance regressions and crash analytics continuously.
7. Document patterns (state, navigation, networking, error handling).

A scalable codebase is predictable: new features follow the same patterns with
minimal custom exceptions.

**In short**

Scalability comes from consistent architecture, automation, and enforced
engineering standards.

</details>

<details>
<summary>83. What are best practices for handling sensitive data?</summary>

#### React Native

Sensitive data (tokens, secrets, PII) should be protected in storage, transit,
and logs.

Best practices:

1. Never hardcode secrets in source code or ship private keys in the app.
2. Use secure storage (iOS Keychain / Android Keystore wrappers).
3. Use HTTPS/TLS for all API traffic.
4. Minimize stored sensitive data and retention duration.
5. Redact sensitive fields from logs, analytics, and crash reports.
6. Rotate tokens/keys and implement revocation.
7. Add jailbreak/root and tamper detection if threat model requires it.

`AsyncStorage` is not appropriate for highly sensitive secrets.

**In short**

Store secrets securely, minimize exposure, and never treat plain storage as
secure vault.

</details>

<details>
<summary>84. How do you handle authentication (biometrics, tokens)?</summary>

#### React Native

Authentication in React Native usually combines secure token management with
optional biometric unlock for convenience.

Typical flow:

1. User signs in (credentials/OAuth/social).
2. Backend returns access + refresh tokens.
3. Store tokens in secure storage (not plain AsyncStorage).
4. Attach access token to API requests.
5. Refresh token when access token expires.
6. Clear tokens and session state on logout.

Biometrics usage:

1. Use Face ID / Touch ID / Android biometrics to re-authenticate local session.
2. Keep server auth model token-based; biometrics gate local access.

Implement centralized auth state and request interceptors to avoid duplicated
logic.

**In short**

Combine secure token lifecycle with optional biometrics for local re-auth
convenience.

</details>

<details>
<summary>85. What is react-native-webview and when should you use it?</summary>

#### React Native

`react-native-webview` is a component that renders web content inside your
mobile app.

Use cases:

1. Display external or internal web pages.
2. Embed existing web-based flows (help center, payment pages, docs).
3. Integrate hybrid modules when full native rewrite is unnecessary.

Example:

```jsx
import { WebView } from 'react-native-webview';

function DocsScreen() {
  return <WebView source={{ uri: 'https://example.com/docs' }} />;
}
```

Use it carefully for critical flows: UX, performance, security, and native
integration are usually better with fully native/RN screens.

**In short**

Use WebView for contained web flows, but prefer native/RN UI for core app
experiences.

</details>

<details>
<summary>86. What is react-native-svg and why is it useful?</summary>

#### React Native

`react-native-svg` provides SVG rendering primitives in RN.

Why useful:

1. Resolution-independent vector graphics.
2. Great for icons, charts, and illustrations.
3. More flexible than static PNG assets.

It is a standard dependency for many design-heavy apps.

**In short**

SVG support enables sharp, scalable icons and graphics across screen densities.

</details>

<details>
<summary>87. How do you implement a drawer navigation?</summary>

#### React Native

Use `@react-navigation/drawer`.

Basic flow:

1. Install drawer navigator dependencies.
2. Create `Drawer.Navigator` with screens.
3. Customize drawer content if needed.
4. Combine with stack/tab navigators.

Keep primary routes in drawer and avoid excessive nesting.

**In short**

Drawer navigation is useful for top-level sections; keep hierarchy simple and
predictable.

</details>

<details>
<summary>88. What is gesture-based navigation?</summary>

#### React Native

Gesture-based navigation means users navigate screens via swipes and touch
patterns (back swipe, tab swipe, drawer drag).

In RN it is typically powered by React Navigation + Gesture Handler.

Benefits:

1. More native-feeling interactions.
2. Faster one-hand navigation patterns.

**In short**

Gestural navigation improves mobile UX when tuned to platform conventions.

</details>

<details>
<summary>89. How do you implement shared element transitions?</summary>

#### React Native

Shared element transitions animate a common UI element between two screens.

Typical implementation:

1. Use a library supporting shared transitions.
2. Assign matching shared IDs on source/target elements.
3. Configure navigation transition behavior.

This improves visual continuity in detail/list flows.

**In short**

Shared transitions preserve visual context between list and detail screens.

</details>

<details>
<summary>90. What is Fabric renderer and how is it different?</summary>

#### React Native

Fabric is RN's new renderer in the New Architecture.

How it differs from legacy renderer:

1. Better integration with concurrent React patterns.
2. More efficient rendering pipeline.
3. Works closely with JSI/TurboModules.
4. Lower latency for certain UI updates.

It is a core piece of RN modernization.

**In short**

Fabric improves rendering efficiency and integrates with the modern RN runtime
model.

</details>

<details>
<summary>91. What is TurboModules architecture advantage?</summary>

#### React Native

TurboModules are part of React Native's New Architecture and improve how native
modules are loaded and called from JavaScript.

Main advantages:

1. **Lazy loading:** modules are initialized only when needed.
2. **Better performance:** less startup overhead and lower bridge cost.
3. **Type safety with codegen:** stronger contracts between JS and native.
4. **Improved maintainability:** clearer module interfaces and modernized native
   integration.

TurboModules are especially valuable in large apps with many native
dependencies.

**In short**

TurboModules improve startup and native access by lazy-loading typed modules.

</details>

<details>
<summary>92. How do you handle error boundaries in React Native?</summary>

#### React Native

Error Boundaries catch rendering errors in child component trees and prevent the
entire app UI from crashing.

In React Native, they are implemented as class components with:

1. `static getDerivedStateFromError(error)`
2. `componentDidCatch(error, info)`

Example:

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

Wrap critical screen trees with boundaries and report errors to monitoring
tools.

**In short**

Error boundaries isolate render crashes and show fallback UI instead of breaking
the whole app.

</details>

<details>
<summary>93. How do you handle global errors?</summary>

#### React Native

Global error handling covers unhandled JS exceptions, promise rejections, and
native crashes.

Common strategy:

1. Configure a global JS error handler.
2. Capture unhandled promise rejections.
3. Integrate crash/error monitoring (for example, Sentry, Bugsnag).
4. Log context (user/session/screen) safely.
5. Show fallback UI when possible and recover gracefully.

Also track native crashes separately through platform tooling and monitoring
SDKs.

**In short**

Capture uncaught JS/native failures centrally and report them with enough
context to debug.

</details>

<details>
<summary>94. What is AppState and how is it used?</summary>

#### React Native

`AppState` lets you detect whether the app is active, in background, or
inactive.

Typical states:

1. `active`: app is in foreground and interactive.
2. `background`: app is running in background.
3. `inactive` (mainly iOS transitional state).

Use cases:

1. Pause/resume timers, video, or polling.
2. Refresh sensitive data when app returns to foreground.
3. Trigger analytics/session lifecycle events.

Example:

```jsx
import { AppState } from 'react-native';

const subscription = AppState.addEventListener('change', nextState => {
  // Handle state transition
});

// Later:
subscription.remove();
```

**In short**

AppState helps pause/resume work correctly when app moves between foreground and
background.

</details>

<details>
<summary>95. How do you handle Android back button (BackHandler)?</summary>

#### React Native

On Android, the hardware back button can be handled with `BackHandler`.

Pattern:

1. Subscribe to `hardwareBackPress`.
2. Return `true` to consume the event.
3. Return `false` to let default behavior run (for example, navigation back).

Example:

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

When using React Navigation, prefer its back handling APIs first and use
`BackHandler` for custom edge cases.

**In short**

Handle back presses intentionally and integrate with navigation behavior.

</details>

<details>
<summary>96. How do you optimize bundle size?</summary>

#### React Native

Bundle size optimization focuses on reducing shipped JS/assets.

Practical steps:

1. Remove unused dependencies.
2. Import only needed modules.
3. Compress/resize images and media.
4. Enable minification and production build optimizations.
5. Split heavy features where architecture allows.

Smaller bundles improve startup and update delivery.

**In short**

Smaller bundles improve startup and update speed by shipping less JS/assets.

</details>

<details>
<summary>97. How do you handle version upgrades and migrations?</summary>

#### React Native

Handle upgrades incrementally and with automated validation.

Recommended process:

1. Upgrade in small steps.
2. Read RN release notes and breaking changes.
3. Use RN upgrade helpers/diffs.
4. Run full tests on iOS and Android.
5. Ship behind monitoring and rollback readiness.

Avoid large multi-version jumps when possible.

**In short**

Upgrade incrementally with release-note checks and full platform regression
testing.

</details>

<details>
<summary>98. What are limitations of React Native?</summary>

#### React Native

Common limitations:

1. Some advanced native APIs require custom native code.
2. Ecosystem package quality varies.
3. Performance can degrade with poor architecture/large JS workload.
4. Upgrade and native tooling complexity can be non-trivial.

Despite this, RN is highly effective for many cross-platform apps.

**In short**

RN is productive but some advanced scenarios still need native code and careful
tuning.

</details>

<details>
<summary>99. How do you implement real-time synchronization?</summary>

#### React Native

Real-time sync combines live transport with conflict-safe local updates.

Typical strategy:

1. Receive live events via WebSocket/subscriptions.
2. Apply optimistic updates for user actions.
3. Persist local state for offline continuity.
4. Reconcile server truth with local changes on reconnect.
5. Use versioning/conflict resolution rules.

This keeps data fresh while preserving consistency.

**In short**

Real-time sync needs event streams plus conflict-safe reconciliation and offline
resilience.

</details>

<details>
<summary>100. How do you design scalable mobile architecture?</summary>

#### React Native

Scalable mobile architecture emphasizes clear boundaries and predictable flows.

Core principles:

1. Feature-based modular structure.
2. Separation of UI, domain logic, and data layer.
3. Explicit state strategy (local/global/server state).
4. Consistent navigation, error, and networking patterns.
5. Automated quality gates (tests, lint, CI, monitoring).

Architecture should optimize long-term change velocity, not only initial speed.

**In short**

Design around modular boundaries, clear data flow, and enforceable team
conventions.

</details>

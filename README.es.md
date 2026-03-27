**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  React Native <img src="./assets/reactnative.svg" width="40" height="40" />
</h1>

<h2>Las preguntas y respuestas más populares de entrevista sobre React Native</h2>

<details>
<summary>1. ¿Qué es React Native y en qué se diferencia de React?</summary>

#### React Native

React Native es un framework de código abierto para crear aplicaciones móviles
con JavaScript/TypeScript y React.

Diferencia clave:

1. **React (React.js):** Construye interfaces web que se renderizan en el DOM
   del navegador (`div`, `span`, etc.).
2. **React Native:** Construye apps iOS/Android que se renderizan en
   componentes nativos de la plataforma (`View`, `Text`, `Image`, etc.).

Ambos comparten el mismo modelo de componentes, props/state y hooks, pero
apuntan a plataformas y capas de renderizado distintas.

**En resumen**

React Native está orientado a móvil con componentes nativos, mientras React se
orienta al DOM web.

</details>

<details>
<summary>2. Explica el concepto de JSX en React Native.</summary>

#### React Native

JSX (JavaScript XML) es una extensión de sintaxis que permite escribir la
estructura de la UI de forma declarativa, con estilo similar a HTML, dentro de
JavaScript.

En React Native, JSX se usa con componentes nativos:

```jsx
function Greeting() {
  return <Text>Hello, React Native!</Text>;
}
```

Notas:

1. JSX no es HTML. Babel lo transforma en llamadas JavaScript.
2. Puedes insertar expresiones JavaScript dentro de `{}`.
3. En React Native, JSX usa componentes nativos (`View`, `Text`) en lugar de
   etiquetas del navegador (`div`, `p`).

**En resumen**

JSX es azúcar sintáctico para describir la UI, y React Native lo mapea a
componentes nativos.

</details>

<details>
<summary>3. ¿Cómo creas un componente funcional en React Native?</summary>

#### React Native

Un componente funcional es una función de JavaScript que devuelve JSX.

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

También puedes usar sintaxis de función flecha:

```jsx
const ProfileCard = () => (
  <View>
    <Text>Profile</Text>
  </View>
);
```

**En resumen**

Es una función normal que retorna JSX, normalmente combinada con hooks para
estado y efectos.

</details>

<details>
<summary>4. ¿Cuáles son los componentes core en React Native (View, Text, Image, etc.)?</summary>

#### React Native

Los componentes core son primitivas de UI integradas que React Native ofrece
para construir interfaces móviles.

Componentes core comunes:

1. **View:** Contenedor básico para layout y estilos.
2. **Text:** Muestra contenido de texto.
3. **Image:** Renderiza imágenes locales o remotas.
4. **TextInput:** Campo de entrada de texto.
5. **ScrollView:** Contenedor con desplazamiento.
6. **FlatList / SectionList:** Renderizado eficiente de listas grandes.
7. **Pressable / TouchableOpacity:** Manejo de interacciones táctiles.
8. **SafeAreaView:** Respeta áreas seguras de pantalla (notch, esquinas
   redondeadas).

Estos componentes se mapean a elementos nativos de iOS y Android.

**En resumen**

Son los bloques base de RN para construir pantallas; conviene mencionar 2-3 que
usas a diario.

</details>

<details>
<summary>5. ¿Qué son las props en React Native y cómo se usan?</summary>

#### React Native

Las props (properties) son entradas de solo lectura que un componente padre
pasa a un componente hijo.

Se usan para:

1. Pasar datos (texto, números, objetos, arreglos).
2. Pasar comportamiento (funciones callback).
3. Configurar componentes reutilizables.

Ejemplo:

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

Aquí, `name` es una prop que `App` envía a `WelcomeMessage`.

**En resumen**

Las props son datos de entrada inmutables de padre a hijo para configurar y
controlar el flujo de datos.

</details>

<details>
<summary>6. ¿Qué es el state en React Native y cómo se gestiona con hooks?</summary>

#### React Native

El state es información propia del componente que puede cambiar con el tiempo y
provocar actualizaciones de la UI.

En componentes funcionales, normalmente se gestiona con el hook `useState`:

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

Para lógica más compleja, puedes usar `useReducer`.

**En resumen**

El state es dato local mutable; con hooks lo actualizas y disparas rerenders de
forma predecible.

</details>

<details>
<summary>7. ¿Cuál es la diferencia entre state y props?</summary>

#### React Native

`state` y `props` guardan datos para renderizar, pero cumplen funciones
distintas:

1. **Props:** Entradas de solo lectura que van del componente padre al hijo.
2. **State:** Datos internos y mutables administrados por el propio componente.

Comparación rápida:

1. **¿Quién es dueño de los datos?** Props: componente padre. State:
   componente actual.
2. **¿Puede cambiar localmente?** Props: no. State: sí, con hooks como
   `useState`.
3. **Caso de uso:** Props: configuración y flujo de datos entre componentes.
   State: comportamiento dinámico de la UI dentro del componente.

**En resumen**

Props transportan datos de entrada inmutables; state modela cambios internos del
componente.

</details>

<details>
<summary>8. ¿Cómo manejas la entrada de usuario en React Native?</summary>

#### React Native

La entrada de usuario suele manejarse con componentes controlados, sobre todo
`TextInput`, junto con state.

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

Eventos/handlers clave:

1. `onChangeText`: actualiza el state del texto.
2. `onPress`: maneja acciones de botones/toques.
3. `onSubmitEditing`: responde al envío desde teclado en `TextInput`.

**En resumen**

Entrada controlada: el valor vive en state y se actualiza mediante handlers.

</details>

<details>
<summary>9. ¿Cómo aplicas estilos a componentes en React Native?</summary>

#### React Native

React Native usa objetos de JavaScript para estilos en lugar de archivos CSS.

Puedes estilizar de tres formas comunes:

1. **Estilos inline** (rápido y local):

```jsx
<Text style={{ color: 'blue', fontSize: 18 }}>Hello</Text>
```

2. **`StyleSheet.create`** (recomendado en la mayoría de casos):

```jsx
const styles = StyleSheet.create({
  title: { color: 'blue', fontSize: 18 },
});
```

3. **Arreglos de estilos** (condicionales/compuestos):

```jsx
<Text style={[styles.title, isActive && styles.active]}>Hello</Text>
```

Los estilos en RN se parecen a CSS, pero usan propiedades en camelCase (por
ejemplo, `backgroundColor`, `fontSize`).

**En resumen**

RN estiliza con objetos JS; lo ideal es centralizar estilos para consistencia y
reutilización.

</details>

<details>
<summary>10. ¿Qué es StyleSheet y cuándo deberías usarlo?</summary>

#### React Native

`StyleSheet` es una utilidad de React Native para definir y organizar estilos de
forma estructurada.

Ejemplo:

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

Cuándo usarlo:

1. Cuando reutilizas estilos en múltiples elementos.
2. Cuando buscas código de componentes más limpio y mantenible.
3. Cuando quieres un enfoque consistente y escalable en pantallas/apps grandes.

**En resumen**

Usa `StyleSheet` para estilos reutilizables, código más limpio y mejor
mantenibilidad.

</details>

<details>
<summary>11. Explica Flexbox y su papel en el layout.</summary>

#### React Native

Flexbox es el sistema principal de layout en React Native. Controla cómo se
redimensionan, alinean y distribuyen los componentes dentro de un contenedor.

En React Native, los valores por defecto de Flexbox difieren un poco de CSS web:

1. `flexDirection` por defecto es `column`.
2. `alignContent` por defecto es `flex-start`.
3. `flexShrink` por defecto es `0`.

Propiedades comunes:

1. `flex`: define cuánto espacio ocupa un ítem respecto a sus hermanos.
2. `flexDirection`: layout en fila o columna.
3. `justifyContent`: alineación en el eje principal.
4. `alignItems`: alineación en el eje cruzado.
5. `gap` (en versiones modernas de RN): espaciado entre hijos.

Ejemplo:

```jsx
<View
  style={{ flex: 1, flexDirection: 'row', justifyContent: 'space-between' }}
>
  <View style={{ width: 50, height: 50, backgroundColor: 'red' }} />
  <View style={{ width: 50, height: 50, backgroundColor: 'blue' }} />
</View>
```

**En resumen**

Lo clave es pensar por ejes: eje principal vs eje cruzado, y luego justificar/alinear.

</details>

<details>
<summary>12. ¿Cómo manejas diseño responsive en React Native?</summary>

#### React Native

El diseño responsive en React Native se resuelve combinando layouts flexibles
con APIs conscientes del dispositivo.

Enfoques comunes:

1. Usar Flexbox (`flex`, `%`, alineación) en lugar de tamaños fijos.
2. Usar `Dimensions` o `useWindowDimensions()` para tamaño de pantalla.
3. Usar `Platform` para ajustes por plataforma.
4. Usar `SafeAreaView` para respetar notch y UI del sistema.
5. Escalar tipografía/espaciado con constantes compartidas.

Ejemplo:

```jsx
import { useWindowDimensions, View } from 'react-native';

function ResponsiveCard() {
  const { width } = useWindowDimensions();
  const isTablet = width >= 768;

  return <View style={{ padding: isTablet ? 24 : 16 }} />;
}
```

**En resumen**

Combina layout flexible con dimensiones de pantalla y manejo de safe areas.

</details>

<details>
<summary>13. ¿Cómo depuras una aplicación React Native?</summary>

#### React Native

La depuración en React Native suele hacerse con una combinación de herramientas
integradas y externas.

Opciones principales:

1. **Logs de Metro:** `console.log`, warnings y errores en terminal/salida.
2. **React Native Dev Menu:** recargar app, inspeccionar UI, habilitar tools.
3. **React DevTools:** inspección de árbol de componentes, props y estado de hooks.
4. **Flipper:** inspección de red, logs, layout y plugins de performance.
5. **Tooling nativo:** Xcode (iOS) y Android Studio (Android) para crashes y logs
   a nivel nativo.

Mejor práctica: reproducir el problema con pasos claros, aislar el componente
fallido y verificar en iOS y Android cuando aplique.

**En resumen**

Usa una pila de depuración: logs, DevTools/Flipper y logs nativos para issues de plataforma.

</details>

<details>
<summary>14. ¿Qué es Fast Refresh y cómo funciona?</summary>

#### React Native

Fast Refresh es una función de desarrollo que actualiza la app de inmediato
tras cambios de código, intentando conservar el estado de los componentes.

Cómo funciona:

1. Guardas un archivo.
2. Metro recompila solo los módulos afectados.
3. React Native inyecta el código actualizado en la app en ejecución.
4. La UI se actualiza al instante sin reinicio completo en la mayoría de casos.

Notas:

1. El estado local normalmente se conserva en componentes funcionales.
2. Si los cambios afectan inicialización de módulo o exports no visuales, RN
   puede hacer una recarga más amplia.
3. Es una característica solo de desarrollo, no de producción.

**En resumen**

Actualiza módulos modificados en desarrollo y normalmente preserva el estado local.

</details>

<details>
<summary>15. ¿Qué son los componentes Touchable y cómo funcionan?</summary>

#### React Native

Los componentes Touchable son envoltorios interactivos que responden a toques/
presiones. Permiten abrir pantallas, enviar formularios o seleccionar elementos.

Opciones comunes:

1. `Pressable` (moderno y flexible, recomendado en muchos casos).
2. `TouchableOpacity` (cambia opacidad al presionar).
3. `TouchableHighlight` (muestra resaltado bajo el hijo).
4. `TouchableWithoutFeedback` (sin feedback visual).

Ejemplo:

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

Exponen eventos como `onPress`, `onPressIn`, `onPressOut` y `onLongPress`.

**En resumen**

Envuelven UI con interacciones de toque; para casos modernos suele convenir `Pressable`.

</details>

<details>
<summary>16. ¿Cómo manejas la navegación en React Native (React Navigation)?</summary>

#### React Native

La navegación normalmente se gestiona con `@react-navigation/*`.

Configuración típica:

1. Instalar el core de React Navigation y los navegadores requeridos.
2. Envolver la app con `NavigationContainer`.
3. Definir stacks/tabs/drawers.
4. Navegar con `navigation.navigate('ScreenName')`.

En la mayoría de apps conviene combinar Stack + Tab y mantener tipados los
nombres de rutas.

**En resumen**

Usa composición de navegadores (stack/tab/drawer) y una estructura de rutas explícita.

</details>

<details>
<summary>17. ¿Cuál es el rol de NavigationContainer?</summary>

#### React Native

`NavigationContainer` es el proveedor raíz que administra el estado de
navegación y conecta los navegadores con el entorno de la app.

Se encarga de:

1. Mantener el estado actual del árbol de navegación.
2. Manejar linking/deep links.
3. Proveer contexto de navegación a todas las pantallas.

Sin él, React Navigation no puede funcionar.

**En resumen**

Es el contenedor raíz del estado y contexto de navegación de toda la aplicación.

</details>

<details>
<summary>18. ¿Cómo pasas parámetros entre pantallas?</summary>

#### React Native

Los params se pasan mediante métodos de navegación.

Ejemplo:

```jsx
navigation.navigate('Profile', { userId: '42' });
```

Lectura en pantalla destino:

```jsx
const { userId } = route.params;
```

Usa params para contexto pequeño de ruta, no para estado global o voluminoso.

**En resumen**

Envía params ligeros con `navigate` y recupéralos desde `route.params`.

</details>

<details>
<summary>19. ¿Qué es deep linking y cómo se implementa?</summary>

#### React Native

El deep linking permite abrir una pantalla específica de la app desde una URL.

Implementación con React Navigation:

1. Definir URL scheme/universal links en configuración nativa.
2. Configurar el objeto `linking` en `NavigationContainer`.
3. Mapear rutas URL a nombres de pantallas.

Esto habilita flujos como `myapp://product/123` para abrir la pantalla de
producto.

**En resumen**

Mapea URLs a pantallas para que enlaces externos abran rutas exactas de la app.

</details>

<details>
<summary>20. ¿Qué son las keys en listas y por qué son importantes?</summary>

#### React Native

`key` identifica de forma única cada ítem en listas para la reconciliación de
React.

Por qué importa:

1. Ayuda a React a actualizar solo las filas modificadas.
2. Evita reutilización incorrecta de ítems y bugs de estado.
3. Mejora rendimiento y previsibilidad del render.

Debes usar IDs únicas y estables, no índices del array (salvo listas estáticas).

**En resumen**

Keys únicas y estables previenen bugs de renderizado de listas y mejoran rendimiento.

</details>

<details>
<summary>21. ¿Cómo renderizas listas de forma eficiente (FlatList, SectionList)?</summary>

#### React Native

Para renderizar listas eficientemente en React Native, conviene usar `FlatList`
y `SectionList` en lugar de mapear arreglos grandes dentro de `ScrollView`.

Por qué son eficientes:

1. Renderizan ítems de forma lazy (solo filas visibles + buffer).
2. Reciclan vistas de ítems y reducen uso de memoria.
3. Incluyen optimizaciones de paginación y scroll.

Casos de uso:

1. `FlatList`: lista unidimensional de elementos similares.
2. `SectionList`: lista agrupada con encabezados de sección.

Ejemplo básico de `FlatList`:

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

**En resumen**

Para volúmenes grandes, prioriza listas virtualizadas para controlar memoria y rendimiento de scroll.

</details>

<details>
<summary>22. ¿Qué es VirtualizedList y cuándo deberías usarlo?</summary>

#### React Native

`VirtualizedList` es el motor base detrás de `FlatList` y `SectionList`.
Gestiona renderizado por ventanas para datasets grandes.

Cuándo usarlo directamente:

1. Cuando tu fuente de datos no es un arreglo simple.
2. Cuando necesitas control total sobre `getItem` y `getItemCount`.
3. Cuando las abstracciones de `FlatList`/`SectionList` se quedan cortas.

En la mayoría de apps, empieza por `FlatList` o `SectionList` porque son más
simples y cubren los escenarios habituales.

**En resumen**

Úsalo directo solo en casos avanzados de acceso a datos; en general `FlatList`/`SectionList` basta.

</details>

<details>
<summary>23. ¿Cómo obtienes datos en React Native (fetch, axios)?</summary>

#### React Native

Puedes obtener datos con la API nativa `fetch` o con `axios`.

Ejemplo con `fetch`:

```jsx
async function loadPosts() {
  const response = await fetch('https://api.example.com/posts');
  if (!response.ok) throw new Error('Request failed');
  return response.json();
}
```

Ejemplo con `axios`:

```jsx
import axios from 'axios';

async function loadPosts() {
  const { data } = await axios.get('https://api.example.com/posts');
  return data;
}
```

Flujo típico en un componente:

1. Activar estado de carga.
2. Ejecutar request asíncrona.
3. Guardar resultado o error en state.
4. Finalizar carga y renderizar según el estado.

**En resumen**

Explica claramente el ciclo de request: loading, success, failure y manejo de cancelación.

</details>

<details>
<summary>24. ¿Cuáles son las mejores prácticas para llamadas API y manejo de errores?</summary>

#### React Native

Buenas prácticas para API y manejo de errores:

1. Centralizar la lógica API en una capa de servicios.
2. Manejar siempre estados de loading, success y error.
3. Definir timeouts y estrategia de reintento para fallos transitorios.
4. Validar el shape de la respuesta antes de usar los datos.
5. Mostrar mensajes de error amigables (no errores crudos del servidor).
6. Usar cancelación (`AbortController`) para evitar actualizar pantallas desmontadas.
7. Mantener en un solo lugar el refresh de tokens de autenticación
   (interceptors/middleware).

Patrón corto:

1. `try` del request.
2. `catch` de errores de red/servidor.
3. Mapeo a errores de dominio comprensibles.
4. Log de detalles técnicos para debug/monitoring.

**En resumen**

Clave: capa API centralizada, mapeo consistente de errores y estrategia clara de retry/cancel.

</details>

<details>
<summary>25. ¿Cómo manejas almacenamiento asíncrono (paquete comunitario AsyncStorage)?</summary>

#### React Native

`AsyncStorage` es una solución persistente key-value para datos ligeros como
ajustes de usuario, flags y cachés simples.

Uso básico:

```jsx
import AsyncStorage from '@react-native-async-storage/async-storage';

async function saveTheme(theme) {
  await AsyncStorage.setItem('theme', theme);
}

async function loadTheme() {
  return AsyncStorage.getItem('theme');
}
```

Buenas prácticas:

1. Serializar objetos con `JSON.stringify` / `JSON.parse`.
2. Envolver llamadas con `try/catch`.
3. Mantener payloads pequeños; no usarlo como base de datos.
4. Namespacing de keys (por ejemplo, `app:user:token`).
5. Para datos sensibles, preferir almacenamiento seguro (Keychain/Keystore).

**En resumen**

Úsalo para persistencia liviana, no para secretos; serializa datos y maneja errores.

</details>

<details>
<summary>26. ¿Cuáles son las soluciones modernas de gestión de estado (Context, Zustand, Redux Toolkit)?</summary>

#### React Native

Las opciones modernas dependen de la complejidad de la app:

1. **Context API:** estado global simple con poco boilerplate.
2. **Zustand:** store liviano, API simple y mínima ceremonia.
3. **Redux Toolkit:** patrones robustos, middleware, devtools y escalado para equipos grandes.

Conviene elegir la herramienta más pequeña que cubra la complejidad real del proyecto.

**En resumen**

Elige por complejidad: Context para casos simples, Zustand/RTK para dominios de estado más grandes.

</details>

<details>
<summary>27. ¿Cómo gestionas estado global sin Redux?</summary>

#### React Native

Puedes usar Context + hooks o stores ligeros como Zustand/Jotai.

Patrón común:

1. Crear un provider para estado compartido por dominio.
2. Encapsular actualizaciones en custom hooks.
3. Mantener separado el estado del servidor (React Query/Apollo).

Así evitas boilerplate de Redux y mantienes buena escalabilidad en muchas apps.

**En resumen**

Combina Context o stores ligeros con custom hooks y límites claros entre responsabilidades.

</details>

<details>
<summary>28. ¿Qué son los React hooks y cuáles se usan con más frecuencia?</summary>

#### React Native

Los hooks son funciones que permiten a componentes funcionales usar estado,
efectos y otras capacidades de React.

Hooks comunes:

1. `useState`
2. `useEffect`
3. `useMemo`
4. `useCallback`
5. `useRef`
6. `useContext`
7. `useReducer`

También permiten reutilizar lógica a través de custom hooks.

**En resumen**

Los hooks llevan lógica con estado a funciones y facilitan reutilización mediante custom hooks.

</details>

<details>
<summary>29. ¿Qué es useEffect y cómo reemplaza métodos de ciclo de vida?</summary>

#### React Native

`useEffect` ejecuta efectos secundarios después del render y permite cleanup.

Equivalencia de ciclo de vida (clases -> hooks):

1. `componentDidMount` -> `useEffect(..., [])`
2. `componentDidUpdate` -> `useEffect(..., [deps])`
3. `componentWillUnmount` -> función de limpieza retornada por `useEffect`

Con esto se unifica el comportamiento de lifecycle en componentes funcionales.

**En resumen**

Úsalo para efectos y limpieza; piensa en dependencias más que en nombres de lifecycle de clases.

</details>

<details>
<summary>30. ¿Qué son useMemo y useCallback y cuándo conviene usarlos?</summary>

#### React Native

`useMemo` memoiza valores calculados. `useCallback` memoiza referencias de
funciones.

Conviene usarlos cuando:

1. El cálculo es costoso.
2. Se necesitan referencias estables para evitar rerenders en hijos.
3. Valores/callbacks son dependencias de otros hooks.

No deben usarse en exceso; aplícalos donde el profiling muestre beneficio real.

**En resumen**

Úsalos de forma selectiva para estabilizar valores/callbacks costosos cuando haya mejora medible.

</details>

<details>
<summary>31. ¿Qué son los refs y cuándo deberías usarlos?</summary>

#### React Native

Los refs son referencias mutables a instancias de componentes o elementos
nativos. Permiten acceder a APIs imperativas sin provocar re-renders.

Casos de uso típicos:

1. Enfocar o quitar foco a un `TextInput`.
2. Disparar métodos de scroll (`scrollToOffset`, `scrollToEnd`).
3. Medir layout (`measure`, `measureInWindow`).
4. Guardar valores mutables que no deben actualizar la UI.

Ejemplo:

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

Usa refs para acciones imperativas, no como reemplazo del flujo normal de
state/props.

**En resumen**

Los refs son para acceso imperativo (focus/scroll/medición), no para flujo de datos normal.

</details>

<details>
<summary>32. ¿Cómo creas custom hooks?</summary>

#### React Native

Un custom hook es una función reutilizable que empieza con `use` y combina hooks
de React (`useState`, `useEffect`, etc.) en lógica compartida.

Reglas:

1. El nombre del hook debe comenzar con `use`.
2. Llama hooks solo en el nivel superior del custom hook.
3. Devuelve los valores/funciones que los componentes necesiten.

Ejemplo:

```jsx
import { useEffect, useState } from 'react';

function useOnlineStatus() {
  const [isOnline, setIsOnline] = useState(true);

  useEffect(() => {
    // Suscribirse a cambios de red aquí
    return () => {
      // Cancelar suscripción aquí
    };
  }, []);

  return isOnline;
}
```

Los custom hooks mejoran reutilización, legibilidad y separación de
responsabilidades.

**En resumen**

Extrae lógica repetida con estado en funciones `use*` para mantener componentes enfocados.

</details>

<details>
<summary>33. ¿Qué es optimización de rendimiento en React Native?</summary>

#### React Native

Optimizar rendimiento en React Native significa reducir sobrecarga de render,
JavaScript y layout para mantener interacciones fluidas (sobre todo en
dispositivos medios/bajos).

Áreas comunes de optimización:

1. Renderizado: evitar re-renders innecesarios.
2. Listas: usar `FlatList`/`SectionList` con tuning correcto.
3. Trabajo de JavaScript: mover cálculos pesados fuera de rutas críticas de render.
4. Imágenes: comprimir, cachear y dimensionar correctamente.
5. Comunicación Native/JS: minimizar operaciones costosas entre capas.

Objetivo típico: 60 FPS estables, inicio más rápido y respuesta táctil fluida.

**En resumen**

Primero perfila, luego optimiza renderizado, listas, imágenes y hotspots de carga JS.

</details>

<details>
<summary>34. ¿Cómo evitas re-renders innecesarios?</summary>

#### React Native

Se evitan re-renders innecesarios estabilizando props y reduciendo updates de
state a lo estrictamente necesario.

Técnicas prácticas:

1. Usar `React.memo` en componentes funcionales puros.
2. Usar `useMemo` para valores derivados costosos.
3. Usar `useCallback` para referencias de callbacks estables.
4. Mantener el state lo más local posible.
5. Evitar crear objetos/funciones nuevas inline si se pasan profundo por props.
6. Dividir componentes grandes en partes pequeñas y enfocadas.
7. Usar keys estables en listas.

Además, perfilar primero (React DevTools/Flipper) y optimizar donde haya
bottlenecks reales.

**En resumen**

Props estables, state local y memoización selectiva reducen costo real de render.

</details>

<details>
<summary>35. ¿Qué es memoization en React Native?</summary>

#### React Native

Memoization es una técnica que cachea resultados calculados o salidas de
componentes y los reutiliza cuando las entradas no cambian.

En React Native, herramientas comunes de memoización son:

1. `React.memo`: memoiza render de componentes comparando props.
2. `useMemo`: memoiza valores calculados.
3. `useCallback`: memoiza referencias de funciones.

Ejemplo:

```jsx
import React, { useMemo } from 'react';

function Total({ items }) {
  const sum = useMemo(() => {
    return items.reduce((acc, item) => acc + item.price, 0);
  }, [items]);

  return <Text>{sum}</Text>;
}
```

Usa memoización de forma selectiva; abusar de ella puede añadir complejidad sin
beneficio medible.

**En resumen**

Memoization evita recomputar trabajo sin cambios al cachear valores, funciones o renders.

</details>

<details>
<summary>36. ¿Qué es el motor Hermes y por qué es importante?</summary>

#### React Native

Hermes es un motor JavaScript optimizado para React Native.

Por qué es importante:

1. Inicio de app más rápido.
2. Menor consumo de memoria en muchos dispositivos.
3. Rendimiento más predecible en Android/iOS.
4. Buena integración con el tooling de RN.

Hermes es una elección por defecto común en apps RN de producción.

**En resumen**

Hermes mejora especialmente tiempo de arranque y uso de memoria en muchas apps RN.

</details>

<details>
<summary>37. ¿Qué es la nueva arquitectura de React Native?</summary>

#### React Native

La New Architecture moderniza internals de RN y se centra en:

1. Fabric renderer.
2. TurboModules.
3. JSI (JavaScript Interface).
4. Dirección Bridgeless.

Objetivos: menor latencia entre JS/native, mejor soporte de concurrencia y mayor
rendimiento.

**En resumen**

Se resume como Fabric + TurboModules + JSI para menos sobrecarga y mejor escalabilidad.

</details>

<details>
<summary>38. ¿Qué son Fabric y TurboModules?</summary>

#### React Native

`Fabric` es el nuevo sistema de renderizado. `TurboModules` es el nuevo sistema
de módulos nativos.

Juntos aportan:

1. Actualizaciones de UI más eficientes.
2. Acceso más rápido a módulos.
3. Mejor integración nativa con tipado seguro vía codegen.
4. Mejor rendimiento en arranque y ejecución.

**En resumen**

Fabric moderniza el render y TurboModules moderniza acceso/carga de módulos nativos.

</details>

<details>
<summary>39. ¿Qué es JSI y cómo reemplaza el bridge antiguo?</summary>

#### React Native

JSI (JavaScript Interface) es una API en C++ que permite interacción más directa
entre JS y native.

Comparado con el bridge antiguo:

1. Reduce mensajería asíncrona pesada basada en JSON.
2. Habilita llamadas con menor overhead e integraciones de runtime compartido.
3. Soporta features de nueva arquitectura como TurboModules/Fabric.

Esto reduce de forma notable cuellos de botella de comunicación.

**En resumen**

JSI reduce el overhead del bridge legado permitiendo interacción más directa JS-native.

</details>

<details>
<summary>40. ¿Qué es el modo Bridgeless en React Native?</summary>

#### React Native

Bridgeless es una dirección arquitectónica en la que RN funciona sin la ruta de
runtime del bridge legado.

Beneficios:

1. Menor overhead de comunicación.
2. Modelo de runtime más limpio y moderno.
3. Mejor alineación con Fabric, TurboModules y JSI.

Forma parte de la evolución de RN hacia mayor rendimiento y mantenibilidad.

**En resumen**

Bridgeless elimina dependencia del bridge antiguo para una base de runtime más eficiente.

</details>

<details>
<summary>41. ¿Cómo logra React Native un rendimiento cercano al nativo?</summary>

#### React Native

React Native logra rendimiento cercano al nativo renderizando componentes UI
nativos reales y optimizando trabajo entre capas JavaScript y native.

Razones clave:

1. La UI se renderiza con vistas nativas (`UIView`, `android.view`) en lugar de
   una web view.
2. Las actualizaciones declarativas de React reducen trabajo de UI innecesario.
3. Hermes puede mejorar tiempo de arranque y uso de memoria.
4. La New Architecture (Fabric, TurboModules, JSI) reduce overhead del bridge.
5. Componentes de lista optimizados (`FlatList`, `SectionList`) soportan virtualización.

El rendimiento final también depende del diseño: JS pesado, renders no
optimizados e imágenes grandes pueden degradar la experiencia.

**En resumen**

RN se siente nativo cuando optimizas rutas de render y controlas carga pesada en JS.

</details>

<details>
<summary>42. ¿Qué son los Native Modules y cuándo deberías usarlos?</summary>

#### React Native

Native Modules son módulos personalizados por plataforma (iOS/Android) que
exponen funcionalidades nativas a JavaScript.

Úsalos cuando:

1. Necesitas APIs que no existen en core/community de React Native.
2. Requieres acceso más profundo a capacidades de dispositivo/plataforma.
3. Buscas mejor rendimiento para lógica que debe correr nativamente.

Ejemplos:

1. Funciones avanzadas de cámara o Bluetooth.
2. Integración de SDKs propietarios (pagos, biometría, analytics).
3. Servicios en background específicos del sistema operativo.

Si existe un paquete comunitario mantenido, suele ser mejor opción inicial.
Escribe módulos propios cuando los requisitos son específicos.

**En resumen**

Usa Native Modules cuando necesitas APIs de plataforma no cubiertas por opciones estándar.

</details>

<details>
<summary>43. ¿Cómo escribes código nativo para React Native (Swift/Kotlin)?</summary>

#### React Native

Se escribe código nativo creando un módulo en iOS (Swift/Objective-C) y/o
Android (Kotlin/Java), y exponiendo métodos/eventos a JavaScript.

Flujo de alto nivel:

1. Crear clase de módulo nativo en cada plataforma.
2. Exportar métodos/constantes/eventos a React Native.
3. Registrar el módulo en el proyecto nativo.
4. Invocar el módulo desde JavaScript/TypeScript.

Ejemplo mínimo de uso en JS:

```jsx
import { NativeModules } from 'react-native';

const { DeviceInfoModule } = NativeModules;

async function loadDeviceName() {
  const name = await DeviceInfoModule.getDeviceName();
  return name;
}
```

En RN moderno, conviene priorizar patrones TurboModules/Codegen para
compatibilidad a largo plazo.

**En resumen**

Expón capacidades nativas en módulos y consúmelas desde JS mediante interfaces claras.

</details>

<details>
<summary>44. ¿Cómo integras React Native en una app nativa existente?</summary>

#### React Native

Puedes incrustar React Native como funcionalidad dentro de una app iOS/Android
existente, sin reescribir toda la aplicación.

Enfoque típico:

1. Añadir dependencias de React Native a proyectos nativos.
2. Configurar bundle y runtime de RN.
3. Lanzar una root view/pantalla RN desde navegación nativa.
4. Intercambiar datos entre native y RN vía props, eventos o módulos.

Casos comunes:

1. Implementar un módulo cross-platform (por ejemplo ajustes/perfil) en una app
   mayormente nativa.
2. Migrar pantallas legacy de forma incremental.

Esta estrategia reduce riesgo de migración y permite adopción gradual de RN.

**En resumen**

Integra RN pantalla por pantalla para modernizar de forma incremental, sin reescritura total.

</details>

<details>
<summary>45. ¿Cómo manejas código específico por plataforma (Platform API)?</summary>

#### React Native

El comportamiento específico por plataforma se maneja con la API `Platform` y
con extensiones de archivo por plataforma.

Técnicas principales:

1. Checks en runtime con `Platform.OS` (`ios`, `android`).
2. Selectores por plataforma con `Platform.select(...)`.
3. Separar archivos por extensión: `Component.ios.tsx` y
   `Component.android.tsx`.

Ejemplo:

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

Lo ideal es compartir la mayor parte de lógica y aislar solo diferencias
necesarias por plataforma.

**En resumen**

Aplica checks de `Platform` o archivos por plataforma, manteniendo máximo código compartido.

</details>

<details>
<summary>46. ¿Cómo construyes componentes para diferencias entre iOS y Android?</summary>

#### React Native

Construye una lógica base compartida y aísla UI/comportamiento específico de
plataforma solo donde sea necesario.

Técnicas:

1. `Platform.OS` / `Platform.select`.
2. Archivos `Component.ios.tsx` y `Component.android.tsx`.
3. Tokens de design system con overrides por plataforma.

Mantén la divergencia mínima para reducir costo de mantenimiento.

**En resumen**

Mantén un contrato común de componente y aísla solo el comportamiento específico por plataforma.

</details>

<details>
<summary>47. ¿Cómo manejas gestos en React Native?</summary>

#### React Native

Para interacciones fiables y de alto rendimiento, se usan librerías enfocadas
en gestos.

Enfoque común:

1. `react-native-gesture-handler` para reconocimiento de gestos.
2. `react-native-reanimated` para animaciones fluidas guiadas por gesto.
3. Componer handlers de tap, pan, fling y pinch según necesidades de la pantalla.

Evita trabajo JS pesado dentro de callbacks de gestos activos.

**En resumen**

Combina Gesture Handler con Reanimated para UX gestual fluida y lista para producción.

</details>

<details>
<summary>48. ¿Qué es PanResponder y cuándo deberías usarlo?</summary>

#### React Native

`PanResponder` es el gestor de gestos integrado en RN para manejar movimiento táctil.

Úsalo cuando:

1. Las necesidades de gesto son simples.
2. Quieres cero dependencias extra.

Para gestos complejos y de alto rendimiento, suele convenir Gesture Handler + Reanimated.

**En resumen**

PanResponder funciona para gestos básicos; para interacciones complejas conviene stack moderno.

</details>

<details>
<summary>49. ¿Qué librerías se usan para gestos (Gesture Handler, Reanimated)?</summary>

#### React Native

Stack de gestos más común:

1. `react-native-gesture-handler` para reconocimiento robusto de gestos.
2. `react-native-reanimated` para animaciones performantes y worklets.

A menudo se usan juntas para una UX gestual de nivel producción.

**En resumen**

Gesture Handler detecta gestos con solidez y Reanimated responde con animaciones fluidas.

</details>

<details>
<summary>50. ¿Qué es Reanimated y por qué se utiliza?</summary>

#### React Native

Reanimated es una librería de animación de alto rendimiento para RN.

Por qué se usa:

1. Animaciones suaves con menos jank.
2. Transiciones guiadas por gestos.
3. Ejecución eficiente de lógica de animación (worklets/modelo cercano al UI thread).
4. Muy útil en interacciones complejas (bottom sheets, shared transitions, etc.).

**En resumen**

Reanimated es estándar para animaciones avanzadas con alto rendimiento en apps RN modernas.

</details>

<details>
<summary>51. ¿Qué es la API Animated y cómo funciona?</summary>

#### React Native

`Animated` es el sistema de animación integrado de React Native para crear
transiciones de UI fluidas animando valores en el tiempo.

Cómo funciona:

1. Crear un valor animado (`new Animated.Value(0)`).
2. Vincular ese valor a propiedades de estilo (`opacity`, `transform`, etc.).
3. Iniciar animaciones con funciones como `Animated.timing`, `spring` o `decay`.

Ejemplo:

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

**En resumen**

Animated maneja transiciones basadas en valores; usa native driver cuando esté soportado.

</details>

<details>
<summary>52. ¿Cuál es la diferencia entre animaciones declarativas e imperativas?</summary>

#### React Native

La diferencia está en cómo se describe y controla el comportamiento de la animación.

1. **Animaciones declarativas:** defines estado objetivo y transiciones a alto
   nivel; el framework se encarga de los detalles de ejecución.

2. **Animaciones imperativas:** controlas manualmente el ciclo de vida paso a
   paso (start, stop, update).

En React Native:

1. `LayoutAnimation` y muchos patrones con Reanimated se sienten más declarativos.
2. `Animated.Value` con orquestación directa mediante `.start()` es más imperativo.

El enfoque declarativo suele ser más mantenible; el imperativo da control fino
para secuencias complejas.

**En resumen**

Declarativo define el resultado objetivo; imperativo controla manualmente cada paso.

</details>

<details>
<summary>53. ¿Cómo implementas animaciones fluidas?</summary>

#### React Native

Para mantener fluidez, reduce trabajo en el hilo principal y evita rerenders
costosos durante el movimiento.

Buenas prácticas:

1. Preferir `useNativeDriver: true` cuando sea compatible.
2. Usar animaciones de `transform` y `opacity` en lugar de propiedades pesadas de layout.
3. Mantener componentes animados aislados y memoizados cuando aplique.
4. Evitar cálculos pesados durante gestos/animaciones.
5. Usar `react-native-reanimated` para interacciones avanzadas de alto rendimiento.
6. Optimizar listas/imágenes grandes que se animan en pantalla.

Siempre probar en dispositivos reales de gama media, no solo en emulador/simulador.

**En resumen**

Prioriza `transform`/`opacity` y reduce carga JS durante interacciones activas.

</details>

<details>
<summary>54. ¿Qué es LayoutAnimation y cuándo deberías usarlo?</summary>

#### React Native

`LayoutAnimation` anima cambios globales de layout (posición/tamaño) cuando las
vistas se agregan, eliminan o redimensionan.

Cuándo usarlo:

1. Secciones que se expanden/colapsan.
2. Insertar/eliminar filas de lista con transiciones simples.
3. Actualizaciones de UI donde quieres interpolación automática de layout.

Ejemplo:

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

Úsalo para transiciones de layout sencillas; para gestos y animaciones complejas,
Reanimated suele encajar mejor.

**En resumen**

Es ideal para cambios simples de layout como expandir/colapsar, no para coreografías complejas.

</details>

<details>
<summary>55. ¿Cómo manejas safe areas (SafeAreaView)?</summary>

#### React Native

Las safe areas evitan que el contenido quede solapado con notches, esquinas
redondeadas y barras del sistema.

Enfoque recomendado:

1. Usar `react-native-safe-area-context`.
2. Envolver la raíz de la app con `SafeAreaProvider`.
3. Usar `SafeAreaView` o `useSafeAreaInsets()` en pantallas/componentes.

Ejemplo:

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

Esto asegura espaciado consistente entre dispositivos iOS y Android.

**En resumen**

Usa safe-area context para que el contenido permanezca visible alrededor de notch y UI del sistema.

</details>

<details>
<summary>56. ¿Cómo manejas cambios de orientación del dispositivo?</summary>

#### React Native

La orientación se maneja escuchando cambios de dimensiones/orientación y
actualizando el layout en consecuencia.

Opciones:

1. `useWindowDimensions()` para recalcular diseño responsive.
2. Librerías de orientación para lock/listen explícitos.
3. Configuración nativa de plataforma cuando debes restringir rotación.

Siempre prueba transiciones portrait/landscape en dispositivos reales.

**En resumen**

Responde a eventos de dimensión/orientación y adapta el layout sin romper usabilidad.

</details>

<details>
<summary>57. ¿Qué es PixelRatio y cuándo es útil?</summary>

#### React Native

`PixelRatio` ofrece utilidades de densidad de píxeles del dispositivo.

Útil para:

1. Escalar assets UI en pantallas de alta densidad.
2. Redondear tamaños de layout y evitar blur.
3. Cargar imágenes con tamaño adecuado según densidad.

Ayuda a lograr visuales más nítidos y consistentes entre dispositivos.

**En resumen**

Usa PixelRatio para imágenes/UI más nítidas y decisiones de tamaño sensibles a densidad.

</details>

<details>
<summary>58. ¿Cómo implementas fuentes personalizadas?</summary>

#### React Native

Las fuentes personalizadas se añaden como assets de la app y se referencian con
`fontFamily`.

Pasos típicos:

1. Añadir archivos de fuente (`.ttf`/`.otf`) a assets.
2. Configurar linking (RN CLI o config de Expo).
3. Usar nombres de fuente en estilos.
4. En Expo, cargar fuentes antes del render con `expo-font`.

Mantén una escala tipográfica y estrategia de fallback para consistencia.

**En resumen**

Carga fuentes como assets y aplica una tipografía consistente en todas las pantallas.

</details>

<details>
<summary>59. ¿Cómo manejas accesibilidad en React Native?</summary>

#### React Native

La accesibilidad debe incorporarse desde el inicio en los componentes.

Prácticas clave:

1. Añadir labels/hints accesibles.
2. Usar roles y estados semánticos.
3. Garantizar contraste suficiente y tamaños táctiles adecuados.
4. Soportar escalado dinámico de texto.
5. Probar con VoiceOver (iOS) y TalkBack (Android).

La accesibilidad mejora la UX para todos, no solo para usuarios con tecnologías
de asistencia.

**En resumen**

Trátala como calidad base: labels, roles, estado, contraste y pruebas con lector de pantalla.

</details>

<details>
<summary>60. ¿Qué son AccessibilityRole y AccessibilityState?</summary>

#### React Native

`accessibilityRole` describe qué es un elemento (button, header, link, etc.).
`accessibilityState` describe su estado actual (disabled, selected, checked,
busy, expanded).

Esto ayuda a lectores de pantalla a anunciar contexto útil en elementos
interactivos.

Ejemplo:

```jsx
<Pressable
  accessibilityRole="button"
  accessibilityState={{ disabled: isDisabled }}
>
  <Text>Submit</Text>
</Pressable>
```

**En resumen**

`Role` define el tipo de elemento y `State` su estado interactivo actual.

</details>

<details>
<summary>61. ¿Cómo manejas push notifications?</summary>

#### React Native

Las push notifications normalmente se implementan con servicios de plataforma
más una librería de RN.

Configuración común:

1. Elegir proveedor: Firebase Cloud Messaging (FCM), APNs (iOS) o servicios como OneSignal.
2. Configurar permisos y tokens nativos (APNs token / FCM token).
3. Registrar listeners para notificaciones en foreground, background y abiertas.
4. Manejar deep links/navegación cuando el usuario toca una notificación.

Librerías típicas:

1. `@react-native-firebase/messaging` para FCM.
2. `notifee` para manejo avanzado de notificaciones locales/remotas.

Buena práctica: payloads pequeños, endpoints seguros y manejo de refresh de token.

**En resumen**

Cubre registro de tokens, flujo de permisos, manejo foreground/background y navegación al tocar.

</details>

<details>
<summary>62. ¿Cómo implementas tareas en background?</summary>

#### React Native

Las tareas en background dependen de límites de plataforma y del tipo de tarea
(sync, ubicación, uploads, notificaciones).

Enfoques:

1. Usar APIs nativas de background mediante librerías.
2. Programar jobs periódicos para trabajo ligero.
3. Usar headless tasks en Android cuando la app está terminada/en segundo plano.

Herramientas comunes:

1. `react-native-background-fetch` para fetch periódico.
2. Handlers background de `@react-native-firebase/messaging` para trabajo
disparado por push.
3. Servicios/workers nativos para escenarios avanzados.

Importante: iOS y Android aplican políticas estrictas de batería, por lo que el
background nunca está garantizado al segundo exacto.

**En resumen**

El trabajo en background está restringido por plataforma, así que diseña para confiabilidad, no timing exacto.

</details>

<details>
<summary>63. ¿Cómo manejas modo offline y sincronización de datos?</summary>

#### React Native

El modo offline se basa en datos local-first y sincronización al volver la
conectividad.

Estrategia central:

1. Persistir datos localmente (AsyncStorage, SQLite, Realm, etc.).
2. Encolar operaciones de escritura mientras no hay conexión.
3. Detectar cambios de conectividad.
4. Reintentar cola y resolver conflictos al reconectar.

Prácticas recomendadas:

1. Diseñar operaciones API idempotentes cuando sea posible.
2. Usar timestamps/versionado para resolución de conflictos.
3. Mostrar estado UI claro: offline, syncing, failed, synced.
4. Mantener política retry/backoff para evitar tormentas de requests.

**En resumen**

Usa almacenamiento local-first + cola de escrituras y sincronización con manejo de conflictos al reconectar.

</details>

<details>
<summary>64. ¿Cómo implementas estrategias de caché?</summary>

#### React Native

El caché reduce latencia, uso de red y recomputaciones.

Capas comunes de caché:

1. **Caché de respuestas API:** en memoria + persistente.
2. **Caché de imágenes:** librerías optimizadas o headers HTTP de caché.
3. **Caché de datos calculados:** memoización (`useMemo`) para valores costosos.
4. **Caché de requests:** librerías como React Query/Apollo con cachés normalizadas.

Reglas prácticas:

1. Definir TTL/reglas de invalidación por recurso.
2. Usar patrones stale-while-revalidate para UI reactiva.
3. Limpiar caché en logout o cambios de contexto auth.
4. Evitar crecimiento de caché sin límite.

**En resumen**

Define alcance e invalidación del caché; stale-while-revalidate suele dar buen equilibrio UX.

</details>

<details>
<summary>65. ¿Qué es GraphQL y cómo se usa en React Native?</summary>

#### React Native

GraphQL es un lenguaje de consulta y runtime para APIs que permite al cliente
pedir exactamente los datos que necesita desde un endpoint único.

Por qué es útil en React Native:

1. Reduce over-fetching y under-fetching.
2. Encaja bien con necesidades de datos por pantalla.
3. Funciona bien con patrones sólidos de caché en cliente.

Cómo se usa:

1. Definir queries/mutations/subscriptions GraphQL.
2. Usar una librería cliente (normalmente Apollo Client).
3. Ejecutar operaciones en hooks/componentes.
4. Manejar loading, error y actualizaciones de caché.

Ejemplo de forma:

```graphql
query GetUser($id: ID!) {
  user(id: $id) {
    id
    name
    avatar
  }
}
```

**En resumen**

GraphQL permite pedir solo los campos necesarios en móvil, reduciendo over-fetching.

</details>

<details>
<summary>66. ¿Qué es Apollo Client y cuándo deberías usarlo?</summary>

#### React Native

Apollo Client es un cliente GraphQL muy popular para ejecutar queries/mutations/
subscriptions y para caché normalizada.

Úsalo cuando:

1. La app depende mucho de APIs GraphQL.
2. Necesitas funciones sólidas de caché y herramientas de actualización.
3. Buscas patrones GraphQL consistentes entre pantallas.

Para apps orientadas principalmente a REST, alternativas más ligeras pueden ser
más simples.

**En resumen**

Usa Apollo cuando caché GraphQL y estado cliente normalizado sean requisitos centrales.

</details>

<details>
<summary>67. ¿Qué es NetInfo y cómo se usa?</summary>

#### React Native

`@react-native-community/netinfo` proporciona estado de conectividad de red.

Casos de uso:

1. Detectar transiciones offline/online.
2. Deshabilitar o encolar acciones de red sin conexión.
3. Disparar sync/retry al restaurarse la conexión.

Es una pieza base para UX robusta de tipo offline-first.

**En resumen**

NetInfo permite controlar requests según conectividad y activar reintentos de forma inteligente.

</details>

<details>
<summary>68. ¿Cómo manejas actualizaciones en tiempo real (WebSockets, subscriptions)?</summary>

#### React Native

Las actualizaciones en tiempo real suelen manejarse con WebSockets o
subscriptions de GraphQL.

Patrón:

1. Abrir conexión persistente.
2. Suscribirse a canales/eventos específicos.
3. Integrar eventos entrantes en state local/global.
4. Reconectar con backoff ante cortes.

Debes manejar lifecycle de app y cambios de red para evitar sockets obsoletos.

**En resumen**

Mantén canales persistentes, reconcilia eventos en estado y controla reconnect/backoff.

</details>

<details>
<summary>69. ¿Cuáles son herramientas de testing comunes (Jest, Detox)?</summary>

#### React Native

Stack de testing común:

1. **Jest:** tests unitarios e integración.
2. **React Native Testing Library:** pruebas de interacción de componentes.
3. **Detox:** tests end-to-end UI en emulador/simulador/dispositivo.
4. **ESLint/TypeScript en CI:** chequeos estáticos de corrección.

Combinar estas capas da cobertura más confiable.

**En resumen**

Testing por capas: Jest para lógica/componentes y Detox para flujos end-to-end completos.

</details>

<details>
<summary>70. ¿Cómo escribes tests unitarios en React Native?</summary>

#### React Native

Los tests unitarios suelen escribirse con Jest (+ Testing Library para
componentes).

Pasos generales:

1. Preparar entradas del componente/función (Arrange).
2. Ejecutar render o comportamiento (Act).
3. Validar salidas/estado/callbacks esperados (Assert).

Un buen test unitario es aislado, determinista y rápido.

**En resumen**

Los mejores unit tests son rápidos y deterministas, y validan comportamiento por encima de detalles internos.

</details>

<details>
<summary>71. ¿Cómo realizas pruebas end-to-end?</summary>

#### React Native

Las pruebas end-to-end (E2E) validan flujos completos de usuario en un entorno
real o simulado, incluyendo UI, navegación e integración con backend.

Proceso típico:

1. Lanzar la app en modo de prueba.
2. Interactuar con la UI como un usuario (tap, escribir, scroll).
3. Verificar resultados visibles y estado de navegación.
4. Ejecutar pruebas en CI sobre múltiples dispositivos/configuraciones.

La herramienta E2E más común en RN es **Detox**.

Buenas prácticas:

1. Añadir `testID` estables a elementos importantes.
2. Mantener pruebas deterministas (controlar red/datos cuando sea posible).
3. Priorizar primero los journeys críticos (auth, checkout, core flows).

**En resumen**

Las E2E validan recorridos críticos del usuario a través de navegación e integraciones reales.

</details>

<details>
<summary>72. ¿Qué herramientas de debugging están disponibles (Flipper)?</summary>

#### React Native

El debugging en React Native suele combinar logs de runtime, inspección de
componentes y diagnóstico nativo.

Herramientas comunes:

1. **Flipper:** plugins para logs, red, inspector de layout y performance.
2. **React DevTools:** inspección de árbol de componentes, props, state y hooks.
3. **Logs de Metro:** salida de consola y warnings/errores de runtime.
4. **Xcode / Android Studio:** crash logs nativos, device logs y breakpoints.
5. **Soporte de debugging Hermes:** profiling/inspección específica del motor JS.

Flipper es especialmente útil como hub de escritorio central para debugging JS + native.

**En resumen**

Respuesta corta: logs + DevTools/Flipper + logs nativos para problemas de plataforma.

</details>

<details>
<summary>73. ¿Cómo perfilas rendimiento en React Native?</summary>

#### React Native

El profiling de rendimiento ayuda a encontrar cuellos de botella reales en
render, ejecución JS y carga del UI thread.

Métodos clave:

1. Usar React DevTools Profiler para renders costosos.
2. Usar plugins de Flipper para timing de performance/red.
3. Medir startup y latencia de transición entre pantallas en dispositivos reales.
4. Inspeccionar comportamiento de listas (`FlatList` configs, dropped frames).
5. Perfilar lado nativo con Xcode Instruments / Android Profiler.

Qué observar:

1. Rerenders innecesarios frecuentes.
2. Tareas JS largas que bloquean interacción.
3. Trabajo pesado de imagen/layout en pantallas críticas.

Perfila en builds tipo producción, no solo en debug.

**En resumen**

Perfilar en condiciones cercanas a producción permite optimizar cuellos de botella reales.

</details>

<details>
<summary>74. ¿Qué es Expo y cuándo deberías usarlo?</summary>

#### React Native

Expo es una plataforma y toolchain sobre React Native que simplifica desarrollo,
builds y updates.

Úsalo cuando:

1. Buscas setup más rápido y alta productividad.
2. Necesitas features nativas comunes vía Expo SDK (cámara, notificaciones, etc.).
3. Prefieres flujos cloud/local de build simplificados (EAS).

Expo incluye:

1. Dev tools y runtime.
2. Módulos de Expo SDK.
3. Tooling de build y submission.
4. Soporte OTA mediante servicios Expo.

Es una opción por defecto fuerte para muchas apps, salvo que necesites control
nativo profundo desde el primer día.

**En resumen**

Expo conviene cuando quieres entregar más rápido y reducir overhead de configuración nativa.

</details>

<details>
<summary>75. ¿Cuál es la diferencia entre Expo managed workflow y bare workflow?</summary>

#### React Native

La diferencia es cuánto control nativo tiene el proyecto.

1. **Managed workflow:** Expo gestiona configuración nativa por ti. Trabajas
   principalmente en JS/TS y config de Expo. Desarrollo más rápido, menos
   mantenimiento nativo.

2. **Bare workflow:** Tienes proyectos nativos completos iOS/Android (similar a
   RN puro). Más control, pero más complejidad de setup/mantenimiento.

Elige managed cuando velocidad y simplicidad sean prioridad. Elige bare cuando
necesites código nativo propio o integración low-level avanzada.

**En resumen**

Managed prioriza velocidad; bare prioriza control nativo total y personalización.

</details>

<details>
<summary>76. ¿Cuáles son pros y contras de Expo?</summary>

#### React Native

Pros:

1. Setup de proyecto rápido e iteración ágil.
2. SDK rico para funcionalidades nativas comunes.
3. Pipeline sencilla de build/update con EAS.
4. Buena DX para equipos pequeños/medianos.

Contras:

1. Menor control nativo directo en managed workflow.
2. Algunos edge cases nativos requieren bare/eject.
3. Dependencia de decisiones/herramientas del ecosistema Expo.

Expo es excelente para productividad, con tradeoffs en flexibilidad low-level.

**En resumen**

Expo mejora DX y velocidad de release, pero personalización nativa profunda puede requerir bare.

</details>

<details>
<summary>77. ¿Cómo manejas builds y deployment de la app?</summary>

#### React Native

El pipeline build/deploy normalmente incluye:

1. Versionado y changelog.
2. Build CI para Android/iOS.
3. Tests automatizados y quality gates.
4. Signing y generación de artefactos.
5. Submission a tiendas (Play Console / App Store Connect).
6. Monitoreo post-release y plan de rollback.

Apps Expo suelen usar EAS Build/Submit; apps bare suelen usar Fastlane o scripts CI.

**En resumen**

Trata releases como pipeline: versionado, checks CI, signing, submission y monitoreo.

</details>

<details>
<summary>78. ¿Qué es code signing y por qué es importante?</summary>

#### React Native

El code signing verifica criptográficamente identidad e integridad de la app.

Por qué importa:

1. Confirma autenticidad del publisher.
2. Evita confiar en binarios manipulados.
3. Es obligatorio para distribución en tiendas.

iOS usa certificados/perfiles; Android usa keystores.

**En resumen**

Code signing prueba autenticidad de la app y es requisito para distribución confiable.

</details>

<details>
<summary>79. ¿Cómo gestionas entornos (dev/staging/prod)?</summary>

#### React Native

Usa configuración explícita de entorno por target de build.

Setup común:

1. Endpoints API y feature flags separados.
2. Variantes/flavors de build (Android) y schemes (iOS).
3. Secrets por entorno vía variables CI seguras.
4. Nombres claros para release channels.

Mantén la selección de entorno determinista y visible en diagnóstico de app.

**En resumen**

Separa config por entorno y mantén secretos/configuración fuera del código fuente.

</details>

<details>
<summary>80. ¿Qué es CodePush / OTA updates y cuándo usarlo?</summary>

#### React Native

Las OTA updates entregan JavaScript/assets sin release completo en tienda.

Útil para:

1. Bug fixes rápidos en capa JS.
2. Pequeños updates de contenido/lógica.

Límites:

1. No puede actualizar código binario nativo.
2. Debe cumplir políticas de tiendas.

Usa OTA para updates JS incrementales y seguros, no como reemplazo de releases
binarios.

**En resumen**

OTA es ideal para fixes JS rápidos; cambios nativos siguen requiriendo binarios de tienda.

</details>

<details>
<summary>81. ¿Cuáles son las mejores prácticas para estructurar una codebase grande?</summary>

#### React Native

En proyectos grandes de React Native, la estructura debe optimizar
localización, ownership por feature y refactor a largo plazo.

Un enfoque común es organización feature-first:

1. Agrupar por dominio/feature (`features/auth`, `features/profile`, etc.).
2. Mantener UI compartida en `components/` y hooks genéricos en `hooks/`.
3. Separar capa API/datos (`services/`, `api/`, `store/`).
4. Centralizar config/constantes globales (`config/`, `theme/`, `env/`).
5. Definir límites claros y entry points públicos por feature.

Además, conviene forzar consistencia con linting, formatting, TypeScript y
convenciones de arquitectura documentadas en el repo.

**En resumen**

Organiza por límites de feature para mantener ownership, reutilización y refactor bajo control.

</details>

<details>
<summary>82. ¿Cómo aseguras escalabilidad y mantenibilidad?</summary>

#### React Native

Escalabilidad y mantenibilidad vienen de buena arquitectura más disciplina de
proceso de ingeniería.

Prácticas clave:

1. Usar límites modulares por feature y primitivas reutilizables.
2. Mantener lógica de negocio fuera de componentes UI.
3. Usar TypeScript para refactors más seguros.
4. Añadir tests automatizados a nivel unit/integration/E2E.
5. Exigir calidad de código con ESLint, Prettier, checks CI y code review.
6. Vigilar de forma continua regresiones de performance y crash analytics.
7. Documentar patrones (state, navegación, networking, error handling).

Una codebase escalable es predecible: features nuevas siguen patrones comunes
con mínimas excepciones.

**En resumen**

Escalar bien exige arquitectura consistente, automatización y estándares técnicos aplicados de forma estricta.

</details>

<details>
<summary>83. ¿Cuáles son mejores prácticas para manejar datos sensibles?</summary>

#### React Native

Los datos sensibles (tokens, secretos, PII) deben protegerse en almacenamiento,
tránsito y logs.

Buenas prácticas:

1. Nunca hardcodear secretos en código ni incluir claves privadas en la app.
2. Usar almacenamiento seguro (wrappers de iOS Keychain / Android Keystore).
3. Usar HTTPS/TLS en todo el tráfico API.
4. Minimizar cantidad y tiempo de retención de datos sensibles.
5. Redactar campos sensibles en logs, analytics y crash reports.
6. Rotar tokens/keys e implementar revocación.
7. Añadir detección de jailbreak/root y tamper si el threat model lo exige.

`AsyncStorage` no es apropiado para secretos altamente sensibles.

**En resumen**

Guarda secretos en almacenamiento seguro, minimiza exposición y evita storage plano para datos críticos.

</details>

<details>
<summary>84. ¿Cómo manejas autenticación (biometría, tokens)?</summary>

#### React Native

La autenticación en React Native suele combinar manejo seguro de tokens con
desbloqueo biométrico opcional por conveniencia.

Flujo típico:

1. Usuario inicia sesión (credenciales/OAuth/social).
2. Backend devuelve access + refresh tokens.
3. Guardar tokens en almacenamiento seguro (no AsyncStorage plano).
4. Adjuntar access token a requests API.
5. Refrescar token cuando expire el access token.
6. Limpiar tokens y estado de sesión al cerrar sesión.

Uso de biometría:

1. Usar Face ID / Touch ID / biometría Android para reautenticar sesión local.
2. Mantener modelo server auth basado en tokens; biometría protege acceso local.

Implementar estado auth central e interceptores evita duplicación de lógica.

**En resumen**

Combina ciclo de vida seguro de tokens con biometría opcional para reautenticación local.

</details>

<details>
<summary>85. ¿Qué es react-native-webview y cuándo deberías usarlo?</summary>

#### React Native

`react-native-webview` es un componente que renderiza contenido web dentro de tu
app móvil.

Casos de uso:

1. Mostrar páginas web externas o internas.
2. Incrustar flujos web existentes (help center, pagos, docs).
3. Integrar módulos híbridos cuando no conviene reescritura nativa completa.

Ejemplo:

```jsx
import { WebView } from 'react-native-webview';

function DocsScreen() {
  return <WebView source={{ uri: 'https://example.com/docs' }} />;
}
```

Úsalo con cuidado en flujos críticos: UX, performance, seguridad e integración
nativa suelen ser mejores con pantallas totalmente native/RN.

**En resumen**

WebView sirve para flujos web acotados; para experiencias core, suele preferirse UI nativa/RN.

</details>

<details>
<summary>86. ¿Qué es react-native-svg y por qué es útil?</summary>

#### React Native

`react-native-svg` provee primitivas para renderizar SVG en RN.

Por qué es útil:

1. Gráficos vectoriales independientes de resolución.
2. Excelente para íconos, charts e ilustraciones.
3. Más flexible que assets PNG estáticos.

Es una dependencia estándar en muchas apps con fuerte componente de diseño.

**En resumen**

El soporte SVG permite gráficos e íconos nítidos y escalables en distintas densidades de pantalla.

</details>

<details>
<summary>87. ¿Cómo implementas una navegación drawer?</summary>

#### React Native

Se implementa normalmente con `@react-navigation/drawer`.

Flujo básico:

1. Instalar dependencias del drawer navigator.
2. Crear `Drawer.Navigator` con pantallas.
3. Personalizar contenido del drawer si hace falta.
4. Combinar con navegadores stack/tab.

Mantén rutas principales en el drawer y evita anidamiento excesivo.

**En resumen**

Drawer funciona bien para secciones de primer nivel; la jerarquía debe ser simple y predecible.

</details>

<details>
<summary>88. ¿Qué es navegación basada en gestos?</summary>

#### React Native

La navegación basada en gestos significa navegar pantallas mediante swipes y
patrones táctiles (back swipe, tab swipe, drawer drag).

En RN suele estar soportada por React Navigation + Gesture Handler.

Beneficios:

1. Interacciones con sensación más nativa.
2. Navegación con una mano más rápida en muchos flujos.

**En resumen**

La navegación gestual mejora UX móvil cuando está ajustada a convenciones de plataforma.

</details>

<details>
<summary>89. ¿Cómo implementas shared element transitions?</summary>

#### React Native

Las shared element transitions animan un elemento UI común entre dos pantallas.

Implementación típica:

1. Usar una librería con soporte de shared transitions.
2. Asignar IDs compartidos iguales en elemento origen/destino.
3. Configurar comportamiento de transición de navegación.

Esto mejora continuidad visual en flujos lista/detalle.

**En resumen**

Las shared transitions preservan contexto visual entre pantallas de lista y detalle.

</details>

<details>
<summary>90. ¿Qué es el renderer Fabric y en qué se diferencia?</summary>

#### React Native

Fabric es el nuevo renderer de RN dentro de la New Architecture.

Cómo difiere del renderer legacy:

1. Mejor integración con patrones concurrentes de React.
2. Pipeline de render más eficiente.
3. Funciona de forma estrecha con JSI/TurboModules.
4. Menor latencia en ciertas actualizaciones UI.

Es una pieza central de la modernización de RN.

**En resumen**

Fabric mejora eficiencia de render e integra mejor con el modelo moderno de runtime en RN.

</details>

<details>
<summary>91. ¿Cuál es la ventaja de la arquitectura TurboModules?</summary>

#### React Native

TurboModules forma parte de la New Architecture de React Native y mejora cómo
los módulos nativos se cargan y se invocan desde JavaScript.

Ventajas principales:

1. **Lazy loading:** los módulos se inicializan solo cuando se necesitan.
2. **Mejor rendimiento:** menos overhead de arranque y menor costo de bridge.
3. **Seguridad de tipos con codegen:** contratos más sólidos entre JS y native.
4. **Mayor mantenibilidad:** interfaces de módulo más claras e integración
   nativa modernizada.

TurboModules es especialmente útil en apps grandes con muchas dependencias
nativas.

**En resumen**

TurboModules mejora arranque y acceso nativo al cargar módulos tipados bajo demanda.

</details>

<details>
<summary>92. ¿Cómo manejas error boundaries en React Native?</summary>

#### React Native

Los Error Boundaries capturan errores de render en subárboles de componentes y
evitan que toda la UI de la app se caiga.

En React Native se implementan como componentes de clase con:

1. `static getDerivedStateFromError(error)`
2. `componentDidCatch(error, info)`

Ejemplo:

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
    // Enviar error al servicio de monitoreo
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

Envuelve árboles críticos de pantalla con boundaries y reporta errores a
herramientas de monitoreo.

**En resumen**

Error boundaries aíslan crashes de render y muestran fallback UI sin romper toda la app.

</details>

<details>
<summary>93. ¿Cómo manejas errores globales?</summary>

#### React Native

El manejo global de errores cubre excepciones JS no controladas, promise
rejections y crashes nativos.

Estrategia común:

1. Configurar un manejador global de errores JS.
2. Capturar unhandled promise rejections.
3. Integrar monitoreo de crashes/errores (por ejemplo, Sentry, Bugsnag).
4. Registrar contexto (usuario/sesión/pantalla) de forma segura.
5. Mostrar fallback UI cuando sea posible y recuperarse de forma controlada.

También conviene rastrear crashes nativos por separado con tooling de plataforma
y SDKs de monitoreo.

**En resumen**

Captura fallos JS/native no controlados en un punto central y repórtalos con contexto útil.

</details>

<details>
<summary>94. ¿Qué es AppState y cómo se usa?</summary>

#### React Native

`AppState` permite detectar si la app está activa, en background o inactiva.

Estados típicos:

1. `active`: app en foreground e interactiva.
2. `background`: app ejecutándose en segundo plano.
3. `inactive`: estado transitorio (principalmente en iOS).

Casos de uso:

1. Pausar/reanudar timers, video o polling.
2. Refrescar datos sensibles cuando la app vuelve al foreground.
3. Disparar eventos de analytics/ciclo de sesión.

Ejemplo:

```jsx
import { AppState } from 'react-native';

const subscription = AppState.addEventListener('change', nextState => {
  // Manejar transición de estado
});

// Luego:
subscription.remove();
```

**En resumen**

AppState ayuda a pausar/reanudar trabajo correctamente al cambiar entre foreground y background.

</details>

<details>
<summary>95. ¿Cómo manejas el botón atrás de Android (BackHandler)?</summary>

#### React Native

En Android, el botón físico de retroceso puede manejarse con `BackHandler`.

Patrón:

1. Suscribirse a `hardwareBackPress`.
2. Devolver `true` para consumir el evento.
3. Devolver `false` para permitir comportamiento por defecto (por ejemplo, navegar atrás).

Ejemplo:

```jsx
import { BackHandler } from 'react-native';
import { useEffect } from 'react';

useEffect(() => {
  const sub = BackHandler.addEventListener('hardwareBackPress', () => {
    // Lógica personalizada
    return false;
  });

  return () => sub.remove();
}, []);
```

Cuando uses React Navigation, prioriza sus APIs de back handling y usa
`BackHandler` para casos específicos.

**En resumen**

Maneja back presses de forma explícita e intégralos de manera coherente con navegación.

</details>

<details>
<summary>96. ¿Cómo optimizas el tamaño del bundle?</summary>

#### React Native

La optimización de bundle se centra en reducir JS/assets enviados.

Pasos prácticos:

1. Eliminar dependencias no usadas.
2. Importar solo módulos necesarios.
3. Comprimir/redimensionar imágenes y medios.
4. Activar minificación y optimizaciones de build de producción.
5. Dividir features pesadas donde la arquitectura lo permita.

Bundles más pequeños mejoran arranque y entrega de updates.

**En resumen**

Menos JS/assets enviados acelera startup y mejora velocidad de actualización.

</details>

<details>
<summary>97. ¿Cómo manejas upgrades de versión y migraciones?</summary>

#### React Native

Los upgrades deben hacerse de forma incremental y con validación automatizada.

Proceso recomendado:

1. Actualizar en pasos pequeños.
2. Leer release notes de RN y breaking changes.
3. Usar upgrade helpers/diffs de RN.
4. Ejecutar pruebas completas en iOS y Android.
5. Liberar con monitoreo y plan de rollback.

Evita saltos grandes de múltiples versiones cuando sea posible.

**En resumen**

Actualiza gradualmente con revisión de release notes y regresión completa por plataforma.

</details>

<details>
<summary>98. ¿Cuáles son las limitaciones de React Native?</summary>

#### React Native

Limitaciones comunes:

1. Algunas APIs nativas avanzadas requieren código nativo propio.
2. La calidad de paquetes del ecosistema varía.
3. El rendimiento puede degradarse con mala arquitectura o carga JS alta.
4. Upgrade y tooling nativo pueden ser complejos.

Aun así, RN es muy efectivo para muchas apps cross-platform.

**En resumen**

RN es productivo, pero escenarios avanzados pueden exigir código nativo y tuning cuidadoso.

</details>

<details>
<summary>99. ¿Cómo implementas sincronización en tiempo real?</summary>

#### React Native

La sincronización en tiempo real combina transporte en vivo con updates locales
seguros ante conflictos.

Estrategia típica:

1. Recibir eventos en vivo vía WebSocket/subscriptions.
2. Aplicar updates optimistas a acciones de usuario.
3. Persistir estado local para continuidad offline.
4. Reconciliar verdad del servidor con cambios locales al reconectar.
5. Usar versionado/reglas de resolución de conflictos.

Esto mantiene datos frescos preservando consistencia.

**En resumen**

El sync en tiempo real requiere streams de eventos más reconciliación robusta con soporte offline.

</details>

<details>
<summary>100. ¿Cómo diseñas una arquitectura móvil escalable?</summary>

#### React Native

Una arquitectura móvil escalable prioriza límites claros y flujos predecibles.

Principios base:

1. Estructura modular basada en features.
2. Separación entre UI, lógica de dominio y capa de datos.
3. Estrategia explícita de estado (local/global/server state).
4. Patrones consistentes de navegación, errores y networking.
5. Quality gates automatizados (tests, lint, CI, monitoring).

La arquitectura debe optimizar velocidad de cambio a largo plazo, no solo
rapidez inicial.

**En resumen**

Diseña con límites modulares, flujo de datos claro y convenciones de equipo que puedan aplicarse siempre.

</details>

# 🎰 Juegos de Cartas - Proyecto de Práctica

## 📋 Descripción

Este proyecto fue desarrollado como una práctica personal para mejorar y demostrar mis habilidades en **JavaScript vanilla** y **CSS puro**, sin utilizar frameworks ni librerías externas. El objetivo principal fue crear juegos de casino completamente funcionales utilizando únicamente las tecnologías web fundamentales.

## 🎯 Objetivo del Proyecto

Desarrollar aplicaciones web interactivas y visualmente atractivas utilizando:

- **HTML5** para la estructura
- **CSS3** para el diseño y animaciones
- **JavaScript puro (Vanilla JS)** para toda la lógica del juego

**Sin dependencias externas** - Todo el código está escrito desde cero, sin frameworks, librerías o herramientas de terceros (excepto Google Fonts para tipografía).

## 🎮 Juegos Incluidos

### 1. **Blackjack 21** (`index.html` y `test.html`)

Un juego completo de Blackjack con las siguientes características:

- Sistema de apuestas con fichas virtuales
- Mecánicas completas del juego (pedir carta, plantarse, doblar)
- Lógica del crupier automática
- Cálculo automático de puntuaciones
- Detección de Blackjack, bust y empates
- Sistema de estadísticas (victorias/derrotas)
- Interfaz moderna con efectos visuales premium

### 2. **Poker Machine** (`poker-machine.html`)

Máquina de video poker con:

- Sistema de apuestas
- Detección automática de manos ganadoras
- Animaciones de cartas
- Interfaz estilo casino

### 3. **Ruleta** (`ruleta.html`)

Juego de ruleta con:

- Animación de la rueda giratoria
- Sistema de apuestas múltiples
- Cálculo de pagos según tipo de apuesta
- Efectos visuales dinámicos

## 💡 Habilidades Demostradas

### JavaScript

- ✅ Manipulación del DOM
- ✅ Programación orientada a eventos
- ✅ Lógica de juego compleja
- ✅ Algoritmos de barajado (Fisher-Yates)
- ✅ Gestión de estado de la aplicación
- ✅ Validación de datos
- ✅ Animaciones con JavaScript
- ✅ Funciones asíncronas y temporizadores

### CSS

- ✅ Diseño responsive
- ✅ Flexbox y Grid Layout
- ✅ Animaciones y transiciones CSS
- ✅ Gradientes complejos
- ✅ Efectos de glassmorphism
- ✅ Pseudo-elementos y pseudo-clases
- ✅ Variables CSS personalizadas
- ✅ Transformaciones 3D
- ✅ Keyframe animations
- ✅ Box-shadow y efectos de iluminación

### HTML

- ✅ Estructura semántica
- ✅ Accesibilidad básica
- ✅ Meta tags apropiados
- ✅ Organización lógica del contenido

## 🎨 Características de Diseño

- **Diseño moderno y premium**: Uso de gradientes, sombras y efectos de neón
- **Animaciones fluidas**: Transiciones suaves en todas las interacciones
- **Efectos visuales avanzados**:
  - Partículas animadas en el fondo
  - Efectos de brillo (glow) dinámicos
  - Animaciones de entrada de cartas
  - Efectos hover interactivos
- **Paleta de colores profesional**: Tonos oscuros con acentos en azul neón
- **Tipografía moderna**: Uso de Google Fonts (Orbitron, Roboto Condensed, Rajdhani)
- **Responsive design**: Adaptable a diferentes tamaños de pantalla

## 🎲 Provably Fair - Sistema de Juego Justo y Verificable

Este proyecto implementa principios de **"Provably Fair"** (juego demostrable y justo), un concepto fundamental en los juegos de casino en línea que garantiza transparencia y equidad.

### ¿Qué es Provably Fair?

**Provably Fair** es un sistema que permite a los jugadores verificar que los resultados del juego son genuinamente aleatorios y no han sido manipulados. A diferencia de los casinos tradicionales donde debes confiar ciegamente en el sistema, aquí puedes **verificar matemáticamente** que cada resultado es justo.

### Implementación en este Proyecto

#### 🔀 Algoritmo de Barajado: Fisher-Yates

Todos los juegos de cartas utilizan el **algoritmo Fisher-Yates** (también conocido como Knuth shuffle), que es el estándar de la industria para barajado aleatorio:

```javascript
function shuffleDeck() {
  for (let i = deck.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [deck[i], deck[j]] = [deck[j], deck[i]];
  }
}
```

**Ventajas del Fisher-Yates:**

- ✅ Distribución uniforme perfecta
- ✅ Cada permutación tiene la misma probabilidad
- ✅ Eficiencia O(n) - una sola pasada
- ✅ Usado por casinos profesionales en línea

#### 🎯 Transparencia del Código

- **Código abierto**: Todo el código fuente es visible y auditable
- **Sin servidor**: Los juegos se ejecutan 100% en el navegador del cliente
- **Sin comunicación externa**: No hay llamadas a APIs que puedan manipular resultados
- **Aleatorización del cliente**: El navegador genera los números aleatorios usando `Math.random()`

#### 🔍 Verificabilidad

Puedes verificar la equidad del juego de las siguientes maneras:

1. **Inspeccionar el código**: Abre las DevTools del navegador y revisa el código JavaScript
2. **Verificar la lógica**: Todas las funciones de barajado y cálculo son visibles
3. **Probar estadísticamente**: Juega múltiples rondas y verifica que los resultados siguen una distribución normal
4. **Sin trucos ocultos**: No hay código ofuscado ni minificado

### Principios de Equidad Implementados

| Principio         | Implementación                                  |
| ----------------- | ----------------------------------------------- |
| **Aleatoriedad**  | Algoritmo Fisher-Yates con `Math.random()`      |
| **Transparencia** | Código fuente completamente visible             |
| **Inmutabilidad** | Las cartas no se modifican después del barajado |
| **Determinismo**  | Mismas reglas para jugador y crupier            |
| **Auditabilidad** | Todo el código es open source                   |

### Limitaciones y Consideraciones

⚠️ **Nota importante**: Este proyecto usa `Math.random()` de JavaScript, que es un generador pseudoaleatorio. Para un casino real en producción, se debería usar:

- **Crypto.getRandomValues()** para aleatoriedad criptográficamente segura
- **Semillas verificables** que el jugador pueda inspeccionar antes del juego
- **Hashes criptográficos** para probar que los resultados no fueron alterados después

### Ejemplo de Mejora para Producción

Para un sistema Provably Fair de nivel profesional, se implementaría:

```javascript
// Generar semilla del servidor (hash SHA-256)
const serverSeed = "hash_generado_antes_del_juego";

// Semilla del cliente (puede ser proporcionada por el jugador)
const clientSeed = "semilla_del_jugador";

// Combinar y generar resultado verificable
const result = generateProvablyFairResult(serverSeed, clientSeed);

// El jugador puede verificar después que:
// SHA-256(serverSeed + clientSeed) = resultado_mostrado
```

### Por qué es Importante

En casinos tradicionales en línea, debes confiar en que:

- Las cartas están realmente barajadas
- El sistema no favorece a la casa más allá de la ventaja matemática normal
- Los resultados no están predeterminados

Con **Provably Fair**, puedes **verificar** todo esto tú mismo.

## 🚀 Cómo Ejecutar

1. Clona o descarga este repositorio
2. Abre cualquiera de los archivos HTML en tu navegador web favorito
3. ¡Comienza a jugar!

No se requiere instalación ni configuración adicional.

## 📁 Estructura de Archivos

```
juego-cartas/
│
├── index.html          # Blackjack (versión principal con efectos avanzados)
├── test.html           # Blackjack (versión alternativa)
├── poker-machine.html  # Máquina de Video Poker
├── ruleta.html         # Juego de Ruleta
└── README.md          # Este archivo
```

## 🔧 Tecnologías Utilizadas

- **HTML5**
- **CSS3**
- **JavaScript (ES6+)**
- **Google Fonts** (única dependencia externa para tipografía)

## 📚 Conceptos Aplicados

### Programación

- Separación de responsabilidades
- Código modular y reutilizable
- Manejo de eventos
- Gestión de estado
- Algoritmos de juego

### Diseño

- Mobile-first approach
- Principios de UX/UI
- Jerarquía visual
- Feedback visual al usuario
- Microinteracciones

## 🎓 Aprendizajes Clave

Este proyecto me permitió:

- Profundizar en JavaScript puro sin depender de frameworks
- Mejorar mis habilidades de CSS para crear interfaces modernas
- Entender mejor la manipulación del DOM
- Practicar la lógica de programación con casos de uso reales
- Desarrollar habilidades de diseño UI/UX
- Implementar animaciones y transiciones complejas
- Optimizar el rendimiento sin herramientas externas

## 🌟 Características Destacadas

1. **Sin frameworks**: Todo el código está escrito desde cero
2. **Animaciones premium**: Efectos visuales de nivel profesional
3. **Lógica completa**: Implementación completa de las reglas de cada juego
4. **Código limpio**: Estructura organizada y comentada
5. **Responsive**: Funciona en dispositivos móviles y desktop

## 📝 Notas del Desarrollador

Este proyecto fue creado con el propósito de:

- Demostrar competencia en tecnologías web fundamentales
- Practicar desarrollo sin dependencias externas
- Crear algo funcional y visualmente atractivo
- Mejorar habilidades de resolución de problemas
- Construir un portfolio de proyectos personales

---

**Desarrollado por Kevin** - Proyecto de práctica personal para demostrar habilidades en JavaScript y CSS básico sin frameworks.

_Última actualización: Diciembre 2025_

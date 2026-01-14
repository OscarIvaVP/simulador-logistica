# Simulador de Logística Industrial 3D

**[>> Ver Demo en Vivo <<](https://oscarivavp.github.io/simulador-logistica/)**

Una simulación 3D interactiva en tiempo real de un almacén de logística industrial que visualiza el flujo de trabajo de operarios humanos transportando cajas desde una zona de recepción a una zona de despacho. La aplicación permite gestionar dinámicamente la cantidad de trabajadores, controlar la velocidad de simulación y monitorear métricas de rendimiento en tiempo real.

## Características Principales

- **Simulación 3D Realista**: Entorno de almacén completamente modelado en 3D con iluminación, sombras y efectos de partículas
- **Operarios Humanoides**: Trabajadores 3D con animaciones realistas (caminar, cargar, descargar, respiración)
- **Gestión Dinámica**: Agregar o eliminar operarios en tiempo real durante la simulación
- **Control de Velocidad**: Ajustar la velocidad de simulación de 0.1x a 3.0x mediante un slider interactivo
- **Monitoreo en Tiempo Real**: Panel de KPIs que muestra métricas de productividad y rendimiento
- **Interfaz Glassmorphism**: UI moderna con efectos de cristal, gradientes y animaciones suaves
- **Cámara Interactiva**: Rotar, hacer zoom y desplazar la vista libremente por el almacén
- **Sistema de Estados**: Cada operario pasa por estados claramente identificados (Esperando, Cargando, Transportando, Descargando)

## Tecnologías Utilizadas

### Frontend
- **HTML5** - Estructura del documento
- **CSS3** - Estilos personalizados con Glassmorphism, gradientes y animaciones
- **JavaScript (ES6 Modules)** - Lógica de la simulación

### Librerías Principales
- **[Three.js](https://threejs.org/) v0.160.0** - Motor de renderizado 3D WebGL
  - Geometrías: Box, Sphere, Cylinder, Capsule, Cone, Torus, Plane, Shape
  - Materiales: MeshStandardMaterial, PointsMaterial, LineBasicMaterial
  - Iluminación: AmbientLight, DirectionalLight, PointLight, HemisphereLight
  - Efectos: Fog exponencial, Tone Mapping (ACESFilmic), Shadow Maps (2048x2048)
  - Controles: OrbitControls para navegación de cámara
- **[Tailwind CSS](https://tailwindcss.com/)** - Framework de estilos utilitarios vía CDN

### Características de Rendering
- Anti-aliasing habilitado
- Shadow Mapping con PCFSoftShadowMap (sombras suaves)
- Tone Mapping ACESFilmicToneMapping para iluminación cinematográfica
- Fog exponencial para profundidad visual
- Pixel Ratio adaptativo (hasta 2x)

## Componentes 3D del Almacén

### Estructura Principal
- **Suelo**: Plano de concreto texturizado de 50x50 unidades con líneas de división
- **Paredes**: 3 muros (trasero y dos laterales) de 8 unidades de altura
- **Techo**: Vigas estructurales de acero a intervalos de 10 unidades
- **Columnas**: 8 columnas de soporte de acero pintadas en amarillo de seguridad

### Zonas de Trabajo
- **Zona A - Recepción (Verde)**: 10x16 unidades con postes y luces verdes en esquinas
- **Zona B - Despacho (Azul)**: 10x16 unidades con postes y luces azules en esquinas

### Operarios Humanoides
Personajes 3D completos con:
- Torso con chaleco reflectante (6 colores distintos para identificación)
- Extremidades articuladas con movimientos realistas
- Cabeza con casco de seguridad amarillo y ojos
- Equipo de protección: guantes y botas de seguridad
- Badge luminoso en el pecho con el color del chaleco
- Animaciones: caminar, agacharse para cargar/descargar, respiración sutil

### Equipamiento Industrial
- **Carretillas Elevadoras**: 2 forklifts con mástil, horquillas, ruedas y luz de advertencia
- **Estanterías**: 3 unidades con 4 niveles y cajas de colores variados
- **Transpaletas Manuales**: Con ruedas direccionales, manijas y horquillas
- **Cinta Transportadora**: 12 unidades de largo con rodillos animados y motor verde

### Equipamiento de Seguridad
- 4 Conos de seguridad naranjas con franjas reflectantes
- 2 Extintores rojos con válvulas metálicas y mangueras
- Botiquín de primeros auxilios con cruz roja
- 3 Barriles azules con símbolo de peligro
- Cartel de seguridad con icono de casco

### Elementos Arquitectónicos
- **Ventanas Industriales**: 5 ventanas con marcos de acero y cristales transparentes
- **Puertas de Carga**: 2 puertas enrollables parcialmente abiertas con rampas
- **Reloj Industrial**: Reloj de pared con manecillas funcionales
- **Iluminación**: 9 lámparas industriales en techo emitiendo luz

### Señalización
- Líneas amarillas: carriles principales
- Líneas blancas: líneas punteadas centrales y cruces peatonales
- Flechas direccionales: indicadores de flujo de movimiento

### Sistema de Partículas
- **Polvo Ambiental**: 500 partículas flotantes con movimiento sinusoidal
- **Partículas de Luz**: 200 partículas ambientales rotantes para atmósfera inmersiva

## KPIs y Métricas

El panel de control muestra las siguientes métricas en tiempo real:

### Cajas Movidas
Contador total de cajas transportadas completamente desde la zona de recepción hasta la zona de despacho.

### Throughput (Cajas/Minuto)
Tasa de productividad calculada como: `(cajas movidas / tiempo transcurrido) × 60`

### Ciclo Promedio (segundos)
Tiempo promedio que tarda un operario en completar un ciclo completo:
1. Moverse a la zona de recepción
2. Cargar la caja (1.2s)
3. Transportar a la zona de despacho
4. Descargar la caja (1.0s)
5. Regresar a posición inicial

Historial de los últimos 50 ciclos para cálculo preciso.

### Número de Operarios
Cantidad de trabajadores activos en la simulación (actualización dinámica).

### Tiempo de Simulación
Reloj formato MM:SS que incorpora el multiplicador de velocidad.

## Controles e Interacción

### Botones de Control
- **Agregar** - Crea un nuevo operario en posición aleatoria dentro del almacén
- **Quitar** - Elimina el último operario agregado de la simulación
- **Reiniciar** - Resetea todos los parámetros y métricas al estado inicial

### Slider de Velocidad
- **Rango**: 0.1x a 3.0x
- **Visualización**: Muestra el multiplicador actual en tiempo real
- **Efecto**: Afecta la velocidad de movimiento de operarios y el tiempo de simulación

### Controles de Cámara (OrbitControls)
- **Arrastrar con ratón**: Rotar la vista 360° alrededor del almacén
- **Scroll**: Zoom in/out (distancia mínima: 12, máxima: 70 unidades)
- **Click derecho + arrastrar**: Desplazamiento (pan) de la vista
- **Ángulo máximo**: π/2.1 radianes (evita voltear la cámara)

## Sistema de Estados de Operarios

Los trabajadores ciclan continuamente entre 5 estados claramente definidos:

```
IDLE (Esperando)
  ↓
MOVING_TO_PICK (Hacia Recepción)
  ↓
LOADING (Cargando - 1200ms)
  ↓
MOVING_TO_DROP (Hacia Despacho)
  ↓
UNLOADING (Descargando - 1000ms)
  ↓
[Regresa a IDLE]
```

Cada estado tiene:
- Animaciones específicas (caminata, agacharse, levantarse)
- Color visual identificatorio en la interfaz
- Tiempos de ciclo medibles para análisis de productividad

## Instalación y Uso

### Requisitos
- Navegador web moderno con soporte para:
  - WebGL
  - ES6 Modules
  - CSS3
- Conexión a internet (para cargar librerías desde CDN)

### Ejecución
1. Clona este repositorio:
   ```bash
   git clone https://github.com/tuusuario/simulador-logistica.git
   ```

2. Abre el archivo `index.html` en tu navegador preferido:
   ```bash
   cd simulador-logistica
   # Opción 1: Doble click en index.html
   # Opción 2: Servidor local
   python -m http.server 8000
   # Luego abre http://localhost:8000 en tu navegador
   ```

3. La simulación cargará automáticamente con 3 operarios iniciales

4. Usa los controles del panel lateral para:
   - Agregar o quitar operarios
   - Ajustar la velocidad
   - Monitorear las métricas en tiempo real
   - Rotar y explorar la escena 3D

## Configuración

Los parámetros de la simulación se pueden ajustar en la sección `CONFIG` del código JavaScript:

```javascript
const CONFIG = {
    FLOOR_SIZE: 50,              // Tamaño del piso en unidades
    GRID_DIVISIONS: 50,          // Divisiones de la cuadrícula visual

    // Zonas de trabajo
    ZONE_A: { x: -15, z: 0, width: 10, depth: 16, color: 0x10b981 },
    ZONE_B: { x: 15, z: 0, width: 10, depth: 16, color: 0x3b82f6 },

    // Parámetros de operarios
    WORKER_SPEED: 3.5,           // Velocidad de movimiento (unidades/segundo)
    LOAD_TIME: 1200,             // Tiempo de carga (milisegundos)
    UNLOAD_TIME: 1000,           // Tiempo de descarga (milisegundos)

    // Colores de chalecos para identificación
    VEST_COLORS: [0xff6b00, 0xffdd00, 0x00ff88, 0xff00aa, 0x00aaff, 0xaa00ff],

    BOX_SIZE: 0.45               // Tamaño de las cajas
};
```

## Animaciones y Movimientos

### Animación de Caminar
- Oscilación de piernas: ±0.6 radianes
- Balanceo de brazos: ±0.4 radianes (sin carga)
- Rebote vertical sutil: 0.03 unidades
- Rotación de cabeza sincronizada con el movimiento

### Animación de Carga/Descarga
- Inclinación del torso hacia adelante: hasta 0.4 radianes
- Descenso vertical del cuerpo: 0.2 unidades
- Brazos se posicionan para sostener la caja
- Duración: 1200ms para carga, 1000ms para descarga

### Respiración en Reposo
- Escala sutil del torso: ±2% en eje Y
- Frecuencia: 0.003 radianes/ms
- Efecto calmado y realista cuando el operario está en estado IDLE

## Características Visuales

### Glassmorphism UI
- Paneles con fondo translúcido (90% opacidad)
- Efecto de desenfoque (blur) de 20px
- Bordes suaves con transparencia
- Diseño moderno y limpio

### Sistema de Iluminación
- **Luz Ambiental**: Color 404060, intensidad 0.4
- **Luz Direccional Principal**: Blanca, intensidad 1.2, sombras 2048x2048
- **Luz de Relleno**: Azul, intensidad 0.3
- **Lámparas Industriales**: 9 luces punto en el techo
- **Luces de Zona**: Luces verdes y azules en esquinas de zonas

### Paleta de Colores
- **Fondo**: #0a0a0f (negro azulado oscuro)
- **Acentos**: Azul (#60a5fa), Púrpura (#a78bfa), Rosa (#f472b6)
- **Seguridad**: Verde (#10b981), Rojo (#ef4444), Amarillo (#f1c40f)
- **Metales**: Grises (#333333-#718096), Dorados (#f39c12)

## Casos de Uso

Esta simulación es una herramienta educativa y de análisis excelente para:

- **Enseñanza de Logística Industrial**: Visualizar conceptos de flujo de materiales
- **Optimización de Procesos**: Analizar el impacto del número de operarios en la productividad
- **Análisis de Throughput**: Identificar cuellos de botella en operaciones de almacén
- **Capacitación**: Entrenamiento visual en gestión de recursos humanos
- **Simulación de Escenarios**: Probar diferentes configuraciones antes de implementación real
- **Presentaciones**: Demostración interactiva de conceptos de logística

## Performance

- **Partículas**: 700 partículas totales (500 polvo + 200 ambientales)
- **Shadow Maps**: Resolución 2048x2048 para máxima calidad
- **FPS Target**: 60 FPS con rendering continuo
- **Memoria**: Gestión automática con métodos `dispose()` para geometrías y materiales

## Compatibilidad

- **Navegadores**: Chrome, Firefox, Safari, Edge (versiones modernas)
- **Dispositivos**: Desktop (recomendado), tablets y móviles con WebGL
- **Responsive**: Canvas se adapta automáticamente al tamaño del viewport

## Estructura del Proyecto

```
simulador-logistica/
│
├── index.html          # Aplicación completa (HTML + CSS + JavaScript)
├── README.md           # Este archivo
└── (opcional) assets/  # Capturas de pantalla o recursos adicionales
```

## Créditos

- **Motor 3D**: [Three.js](https://threejs.org/)
- **Framework CSS**: [Tailwind CSS](https://tailwindcss.com/)
- **Desarrollado por**: Miguel Rico
- **Curso**: GIT - GITHUB

## Licencia

Este proyecto es de código abierto y está disponible bajo la licencia MIT.
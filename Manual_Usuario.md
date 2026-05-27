# Manual de Usuario

Bienvenido al Sistema de Gestión de Proyectos basado en Modelos de Redes. Esta herramienta permite visualizar y optimizar proyectos desde un enfoque de Ingeniería Industrial.

## 1. Cómo crear un proyecto
1. En la pantalla principal ("Mis Proyectos"), haga clic en el botón `+ Nuevo Proyecto`.
2. Ingrese el nombre y la descripción (opcional) del proyecto.
3. Haga clic en `Guardar`. El proyecto aparecerá en la cuadrícula.
4. Haga clic en `Abrir Proyecto` en la tarjeta correspondiente.

## 2. Cómo registrar actividades
Una vez dentro del proyecto, en la pestaña "Actividades & Dependencias":
1. Haga clic en `+ Actividad`.
2. Defina el Nombre, la Duración (en la unidad de tiempo elegida, ej. días) y el Costo.
3. Haga clic en `Guardar`. La actividad representa un **Nodo** en el grafo de su proyecto.

## 3. Cómo definir dependencias
Las dependencias conectan actividades, formando los **Arcos** del grafo:
1. Haga clic en `+ Dependencia`.
2. Seleccione el nodo "Desde" (Origen) y "Hasta" (Destino).
3. Establezca:
   - **Peso:** Representa la distancia o el costo entre ambas actividades (usado en Árboles de Expansión y Rutas más Cortas).
   - **Tiempo:** Tiempo específico de esta conexión.
   - **Capacidad:** Capacidad de flujo (usado en el algoritmo de Flujo Máximo).
4. Haga clic en `Guardar`.

## 4. Cómo visualizar el grafo y ejecutar algoritmos
Navegue a la pestaña "Grafo & Algoritmos":
- Verá el modelo de red dibujado automáticamente.
- Puede hacer zoom y arrastrar los nodos (actividades) para organizarlos a su gusto.

### Ejecución de Algoritmos:
1. En el panel izquierdo, seleccione la **Categoría** (Árbol de Expansión, Rutas, Flujo Máximo, Gestión).
2. Elija el **Algoritmo Específico** (por ejemplo, Dijkstra, Kruskal, CPM).
3. Si el algoritmo lo requiere, seleccione los nodos **Origen** y **Destino**.
4. Haga clic en `Ejecutar`.

## 5. Interpretación de resultados
- Al ejecutar un algoritmo, los nodos o bordes resultantes (ruta más corta, árbol mínimo, ruta crítica) se resaltarán en color rojo en el grafo de manera automática.
- Debajo del botón "Ejecutar", aparecerá un panel con resultados técnicos (como distancias totales, flujos máximos, tiempos tempranos y tardíos `ES/EF/LS/LF`).

## 6. Cómo usar el Diagrama de Gantt
Navegue a la pestaña "Diagrama de Gantt":
- El diagrama se genera basándose en el análisis de Ruta Crítica (CPM).
- Verá las actividades organizadas en el tiempo, mostrando dependencias mediante flechas.
- Las barras resaltadas en color rojo indican que la actividad pertenece a la **Ruta Crítica** (no puede retrasarse sin afectar la fecha final del proyecto).
- Puede cambiar la escala de tiempo (Día, Semana, Mes) utilizando los controles integrados (si la librería lo permite).

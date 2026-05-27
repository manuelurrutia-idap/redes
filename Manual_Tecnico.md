# Manual Técnico

## Arquitectura del Sistema
El sistema se basa en una arquitectura de tres capas, orquestadas mediante Docker Compose:
1. **Base de Datos:** PostgreSQL 15, almacena las entidades persistentes (Proyectos, Actividades, Dependencias).
2. **Backend (API REST):** Desarrollado en Python utilizando FastAPI y SQLAlchemy como ORM. Encargado de exponer los endpoints CRUD y los algoritmos de redes.
3. **Frontend:** Implementado como una Single Page Application (SPA) utilizando HTML, Vanilla CSS y Vanilla JS. Consume la API REST del backend.

## Modelo de Base de Datos
El ORM mapea las siguientes tablas principales:
- `projects`: `id`, `name`, `description`, `created_at`
- `activities` (Nodos): `id`, `project_id`, `name`, `duration`, `cost`
- `dependencies` (Arcos): `id`, `project_id`, `from_activity_id`, `to_activity_id`, `weight`, `time`, `capacity`

## Endpoints del Backend
- **Proyectos:**
  - `GET /projects/`: Listar proyectos.
  - `POST /projects/`: Crear proyecto.
  - `DELETE /projects/{id}`: Eliminar proyecto.
- **Actividades:**
  - `GET /projects/{project_id}/activities/`: Listar actividades.
  - `POST /projects/{project_id}/activities/`: Crear actividad.
  - `DELETE /activities/{id}`: Eliminar actividad.
- **Dependencias:**
  - `GET /projects/{project_id}/dependencies/`: Listar dependencias.
  - `POST /projects/{project_id}/dependencies/`: Crear dependencia.
  - `DELETE /dependencies/{id}`: Eliminar dependencia.
- **Algoritmos:**
  - `GET /projects/{project_id}/algorithms/shortest-path`
  - `GET /projects/{project_id}/algorithms/mst`
  - `GET /projects/{project_id}/algorithms/max-flow`
  - `GET /projects/{project_id}/algorithms/cpm`
  - `GET /projects/{project_id}/algorithms/pert`

## Implementación de Algoritmos
Todos los algoritmos están implementados manualmente en el módulo `backend/algorithms.py` utilizando estructuras de datos estándar de Python (como `heapq` para colas de prioridad y `deque` para listas enlazadas doblemente).
- **MST:** Prim, Kruskal (con Union-Find).
- **Ruta más corta:** Dijkstra, Bellman-Ford, Floyd-Warshall, A*.
- **Flujo Máximo:** Ford-Fulkerson (utilizando BFS).
- **Gestión:** CPM y PERT basados en grafos dirigidos acíclicos (DAG).

## Ejecución con Docker
Asegúrese de tener Docker y Docker Compose instalados.
1. Abra una terminal en el directorio del proyecto.
2. Ejecute el comando: `docker-compose up --build`
3. El frontend estará disponible en `http://localhost:8080`.
4. El backend estará disponible en `http://localhost:8000` (con documentación Swagger en `http://localhost:8000/docs`).

# Acuerdos del equipo

## Integrantes
- Victor Manuel Mendoza Lara
- Dennis Adrián Quintana Lazgare
- Omar Mandujano Ávila

## Responsables
- **Victor**: `apps/api`, base de datos y migraciones, despliegue en Render, contrato OpenAPI, modelo de datos, roles y permisos, `.env.example`, README y datos semilla.
- **Omar**: `web/features/cliente` y `web/features/tienda`; cliente de API generado y librería de UI base en `web/shared`.
- **Dennis**: `web/features/repartidor` y `web/features/soporte`; mocks del backend y servicio de mapas.
- `web/shared` y `packages/shared` se cambian solo por PR, avisando en el grupo.

## Cosas por compartir
Cada quien entrega lo siguiente al resto del equipo (subiéndolo al repo o avisando en el grupo cuando esté listo).

### Victor
1. **Contrato de la API** (`docs/openapi.yaml`): lo comparte con Omar y Dennis, y avisa cada vez que cambie.
2. **Modelo de datos y diagrama ER** (`docs/modelo-datos`): lo comparte con Omar y Dennis y lo aprueban los tres antes de migrar.
3. **Matriz de roles y permisos** (`docs/roles-permisos.md`): qué endpoint puede usar cada rol, para que Omar y Dennis protejan sus rutas.
4. **`.env.example` y README** (raíz del repo): pasos para levantar el proyecto en local.
5. **Datos semilla** (`apps/api/seeds`): un usuario por rol, tiendas y pedidos de prueba.
6. **Decisión del ORM** (`docs/decisiones.md`): se decide en la primera reunión y se comparte con todos.

### Omar
1. **Cliente de API generado** (`web/shared/api`): lo comparte con Dennis, con instrucciones en el README para regenerarlo cuando cambie el yaml.
2. **Tema y componentes base de la librería de UI** (`web/shared/ui`): lo comparte con Dennis para que ambos módulos se vean igual.

### Dennis
1. **Mock del backend** (`web/mocks`): lo comparte con Omar para que ambos puedan trabajar sin esperar la API.
2. **Decisión del servicio de mapas** (`docs/decisiones.md`): se decide en la primera reunión y se comparte con todos.

### Cuándo se entrega cada cosa
- **Antes de escribir código:** las decisiones técnicas (ORM y mapas), el contrato de la API y el modelo de datos, que se revisan entre los tres.
- **Primeras semanas de desarrollo:** roles y permisos, README y datos semilla (Victor); cliente de API y librería de UI (Omar); mock del backend (Dennis).
- Quien reciba algo confirma que le funciona; si no, avisa el mismo día al responsable.
- Si algo compartido cambia después (contrato, modelo de datos, roles), quien lo cambia avisa en el grupo y actualiza el archivo en el mismo PR.




## Git
- Ramas: `main` (producción), `develop` (integración), `feature/<modulo>-<descripcion>`.
- Nadie hace push directo a `main` ni `develop`; todo entra por Pull Request.
- Cada PR necesita 1 aprobación de otro compañero.
- Commits en español, formato: `feat(tienda): crear pedido manual`
  Tipos: feat, fix, docs, refactor, chore.
- PRs pequeños (que se revisen en menos de 15 min). Se borra la rama al fusionar.

## API
- Contrato en `docs/openapi.yaml`. Si un endpoint cambia, se actualiza el yaml PRIMERO.
- Rutas en plural y minúsculas: `/api/v1/pedidos`, `/api/v1/tiendas`.
- Respuesta de error estándar: `{ "statusCode": 400, "message": "...", "error": "..." }`
- Fechas en ISO 8601 UTC. Dinero en centavos (enteros).
- Estados de pedido definidos una sola vez en `packages/shared`.

## Base de datos
- Solo Victor modifica el esquema, siempre con migración.
- Nombres de tablas y columnas en snake_case, en un solo idioma (acordar: ___).
- Seeds con datos de prueba en el repo para que todos tengan lo mismo.

## Código
- Prettier + ESLint obligatorios (config única en la raíz). El PR no pasa si falla el lint.
- Variables de entorno en `.env` (nunca al repo); se documentan en `.env.example`.
- Componentes en PascalCase, hooks en useCamelCase.
- Sin credenciales, llaves de Google Maps/Mapbox ni JWT secrets en el código.

## Definición de terminado
- Funciona en local, pasa lint, tiene PR aprobado y no rompe `develop`.
- Si agrega un endpoint, está en `openapi.yaml`.
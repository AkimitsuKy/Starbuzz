# Starbuzz – Laboratorio List views and adapters

App Android (Java) con navegación top-level → category → detail usando `ListView`, `ArrayAdapter` y `OnItemClickListener`.

## Propuesta de navegación

```
                 TopLevelActivity (top-level)
              logo + ListView: Drinks | Food | Stores
          ┌──────────────┼────────────────┐
          ▼              ▼                ▼
 DrinkCategoryActivity  FoodCategory*    StoreCategory*      (category)
  ListView de bebidas   menú de comida   lista de tiendas
          │              │                │
          ▼              ▼                ▼
   DrinkActivity       FoodActivity*    StoreActivity*       (detail/edit)
 imagen+nombre+desc.  detalle comida   dirección y horario
```
\* Propuestas en el diseño; el laboratorio implementa la rama **Drinks**.

| Tipo | Actividad | Layout | Función |
|---|---|---|---|
| Top-level | `TopLevelActivity` | `activity_top_level.xml` | Punto de entrada; lista de opciones (`@array/options`) |
| Category | `DrinkCategoryActivity` | `activity_drink_category.xml` | Lista de bebidas vía `ArrayAdapter<Drink>` |
| Detail | `DrinkActivity` | `activity_drink.xml` | Detalle de la bebida recibida por `EXTRA_DRINKID` |

## Flujo
1. Clic en **Drinks** (posición 0) → `Intent` a `DrinkCategoryActivity`.
2. Clic en una bebida → `Intent` con `putExtra(EXTRA_DRINKID, id)` a `DrinkActivity`.
3. `DrinkActivity` obtiene `Drink.drinks[drinkId]` y llena sus vistas.

## Ejecutar
Abrir la carpeta en Android Studio → Sync → Run.

Referencia: Griffiths, D. & Griffiths, D. (2017). *Head First Android Development*. O'Reilly.

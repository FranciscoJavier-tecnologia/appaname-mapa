## 🌎 Appañame - Mapa

Este repositorio (`A`) almacena el "mapa" de objetivos para el scraper de Appañame. Define qué emisores y qué URLs debe procesar el motor del "Cerebro" (`B`).

### Esquema de `targets.json`

El archivo `targets.json` es un array `[ ]` de objetos "emisor". Cada emisor debe tener la siguiente estructura:

```json
{
  "enabled": true,
  "segment": "...",
  "country": "CL",
  "issuer_id": "...",
  "issuer_name": "...",
  "parser_strategy": "...",
  "metadata": { "...": "..." },
  "sources": [ { "...": "..." } ]
}
```

#### Explicación de Campos (Nivel Emisor)

| Campo | Tipo | Requerido | Descripción |
| :--- | :--- | :--- | :--- |
| `enabled` | Booleano | Sí | Poner en `false` para deshabilitar el scraping de **todo** este emisor. |
| `segment` | String | Sí | La categoría general (Ej: "Bancos & Tarjetas", "Retail"). |
| `country` | String | Sí | El código del país (Ej: "CL"). |
| `issuer_id` | String | Sí | Identificador único (Ej: "banco_de_chile"). |
| `issuer_name`| String | Sí | Nombre público (Ej: "Banco de Chile"). |
| `parser_strategy`| String | Sí | El nombre del script en el "Cerebro" que procesará esto (Ej: "bancochile_v1"). |
| `metadata` | Objeto | No | Contiene datos extra para la app (logo_url, main_url). |

#### Explicación de Campos (Nivel Fuente/Source)

```json
{
  "source_id": "...",
  "url": "https://...",
  "category_hint": "...",
  "enabled": true,
  "priority": 5,
  "requires_js_render": true
}
```

| Campo | Tipo | Requerido | Descripción |
| :--- | :--- | :--- | :--- |
| `source_id` | String | Sí | Identificador único de la URL (Ej: "bch_sabores"). |
| `url` | String | Sí | La URL exacta que el scraper debe visitar. |
| `category_hint` | String | Sí | Pista de categoría para el scraper (Ej: "Restaurantes"). |
| `enabled` | Booleano | Sí | Poner en `false` para deshabilitar **solo esta URL**. |
| `priority` | Número | No | Define la importancia (1 = más alta). Aún no se usa. |
| `requires_js_render`| Booleano | Sí | **`true`** si es "Caja Mágica" (JavaScript). **`false`** si es HTML simple. |

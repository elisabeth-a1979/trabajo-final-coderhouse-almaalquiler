# Ecosistema de Automatización IA — AlmaAlquiler

Trabajo Final — Coderhouse, Automatización con IA (Elisabeth Elfi)

Sistema que clasifica automáticamente las consultas de huéspedes que llegan por Gmail, las procesa con IA (Claude Haiku 4.5), pide aprobación humana antes de responder, y registra todo en Airtable.

## Stack

- **Orquestador:** n8n
- **Base de datos:** Airtable
- **Procesamiento IA:** Anthropic (Claude Haiku 4.5)
- **Canal de salida:** Gmail

## Estructura del repositorio

```
/
├── README.md
├── docs/
│   ├── 01_mapa_arquitectura.pdf
│   ├── 02_estructuras_datos.pdf
│   ├── 03_matriz_costos.pdf
│   └── 04_seguridad_resiliencia.pdf
├── flow/
│   └── centro_de_comando_almaalquiler.json
├── evidence/
│   ├── screenshot_nodo_anthropic.png
│   ├── screenshot_nodo_if.png
│   ├── screenshot_airtable_leads.png
│   ├── screenshot_airtable_registro_contactos.png
│   └── screenshot_airtable_registro_errores.png
└── links.md
```

## Documentación (criterios de evaluación)

| # | Criterio | Archivo |
|---|---|---|
| 1 | Mapa de arquitectura | [`docs/01_mapa_arquitectura.pdf`](docs/01_mapa_arquitectura.pdf) |
| 2 | Estructuras de datos | [`docs/02_estructuras_datos.pdf`](docs/02_estructuras_datos.pdf) |
| 3 | Optimización de costos | [`docs/03_matriz_costos.pdf`](docs/03_matriz_costos.pdf) |
| 4 | Seguridad y resiliencia | [`docs/04_seguridad_resiliencia.pdf`](docs/04_seguridad_resiliencia.pdf) |
| 5 | Dashboard de control | ver [`links.md`](links.md) |

## Enlaces

Ver [`links.md`](links.md) para:
- Dashboard de Control (Airtable Shared View)
- Base de datos en modo lectura
- Video demo (3 min)

## Flujo técnico

El archivo `flow/centro_de_comando_almaalquiler.json` es el blueprint exportado directamente de n8n, listo para importar.

Resumen del flujo: Gmail Trigger → Filter → Basic LLM Chain (Claude Haiku 4.5 + Structured Output Parser) → Airtable (Leads) → Gmail HITL (esperar aprobación) → If → Gmail (respuesta al huésped) o descarte → Airtable (Registro Contactos / Registro_Errores).

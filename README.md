# Boletín Claro — el MCP de los datos públicos de España

**Datos públicos españoles para tu IA: el dinero público —subvenciones y licitaciones— y todos los boletines oficiales (BOE, BORME, autonómicos). Con datos reales, no suposiciones.**

[![MCP](https://img.shields.io/badge/MCP-Streamable_HTTP-1f6feb)](https://modelcontextprotocol.io)
[![Sin instalación](https://img.shields.io/badge/conexi%C3%B3n-1_clic_(URL)-2ea043)](#conexión-rápida)
[![Cuenta gratuita](https://img.shields.io/badge/acceso-cuenta_gratuita-2ea043)](#conexión-rápida)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)
[![Web](https://img.shields.io/badge/web-boletinclaro.es-111)](https://boletinclaro.es)

Conecta tu IA (Claude, ChatGPT, Cursor, VS Code, Gemini…) a [**Boletín Claro**](https://boletinclaro.es) y pregúntale en lenguaje natural. Dos superficies, una sola conexión:

- 💶 **Dinero público** — subvenciones, licitaciones, ayudas y a quién se las llevan.
- 📰 **Boletines oficiales** — leyes, decretos, anuncios y normativa del BOE, el BORME y los boletines autonómicos.

Las respuestas salen de datos reales indexados, no de suposiciones del modelo.

> **Una sola URL, sin instalar nada ni API key; basta una cuenta gratuita de Boletín Claro:**
> ```
> https://boletinclaro.es/mcp
> ```
> **[▶ Añadir a Claude en un clic](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=Bolet%C3%ADn+Claro&connectorUrl=https%3A%2F%2Fboletinclaro.es%2Fmcp)** — abre el conector ya rellenado en claude.ai; solo confirmas.
> Instrucciones para cada asistente en [boletinclaro.es/conector](https://boletinclaro.es/conector).

---

## Conexión rápida

Es un servidor **remoto** (Streamable HTTP). No descargas nada: das la URL a tu cliente.
Todas las herramientas requieren iniciar sesión con una cuenta gratuita de Boletín Claro. Gratis incluye 100 créditos mensuales compartidos con API.

### Claude Code (CLI)
```bash
claude mcp add --transport http boletinclaro https://boletinclaro.es/mcp
```

### Claude Desktop · claude.ai (Connectors)
**[Añadir a Claude en un clic](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=Bolet%C3%ADn+Claro&connectorUrl=https%3A%2F%2Fboletinclaro.es%2Fmcp)** — el enlace abre «Add custom connector» con el nombre y la URL ya puestos.

A mano: Ajustes → **Connectors** → **Add custom connector** → pega `https://boletinclaro.es/mcp`.

<details>
<summary>¿Plan sin connectors? Puente con <code>mcp-remote</code></summary>

En `claude_desktop_config.json`:
```json
{
  "mcpServers": {
    "boletinclaro": {
      "command": "npx",
      "args": ["mcp-remote", "https://boletinclaro.es/mcp"]
    }
  }
}
```
</details>

### Cursor
En `~/.cursor/mcp.json`:
```json
{
  "mcpServers": {
    "boletinclaro": {
      "url": "https://boletinclaro.es/mcp"
    }
  }
}
```

### VS Code (GitHub Copilot)
En `.vscode/mcp.json`:
```json
{
  "servers": {
    "boletinclaro": {
      "type": "http",
      "url": "https://boletinclaro.es/mcp"
    }
  }
}
```

### ChatGPT
Modo desarrollador → Ajustes → **Connectors** → crea un conector y pega `https://boletinclaro.es/mcp`.

### Gemini CLI y otros clientes
```json
{
  "mcpServers": {
    "boletinclaro": {
      "httpUrl": "https://boletinclaro.es/mcp"
    }
  }
}
```
Cualquier cliente compatible con MCP remoto sirve. Si el tuyo solo soporta stdio, usa el puente universal:
```bash
npx mcp-remote https://boletinclaro.es/mcp
```

---

## Créditos de lectura por workspace

| Plan | Créditos/mes | Llamadas/minuto | Créditos/minuto | Perfiles/mes |
|---|---:|---:|---:|---:|
| Gratis | 100 | 20 | 20 | 5 |
| Individual | 500 | 30 | 100 | Sin tope adicional |
| Pro | 2.000 | 60 | 300 | Sin tope adicional |
| Mega | 15.000 | 300 | 1.500 | Sin tope adicional |

Trial y Oposiciones tienen el cupo Gratis. El mes y el minuto son naturales UTC; el mes se renueva el día 1 a las 00:00 UTC. Terminar Trial o cambiar de plan no reinicia el consumo. Todas las claves API, usuarios y clientes MCP del workspace comparten el saldo, salvo en Mega, que tiene dos saldos de 15.000: uno para la web y el conector, y otro para la API. Cada saldo de Mega tiene además un tope de 1.500 créditos al día y de 500 llamadas de 5 créditos al mes, y el de la web y el conector, de 2.000 créditos al mes por persona. Gratis permite cinco **llamadas**, aunque se repita el NIF, entre `perfil_empresa` y `GET /v1/empresas/{nif}`.

| Herramientas | Créditos por llamada |
|---|---:|
| `buscar_oportunidades`, `buscar_boletines`, `resumen_boletin`, `mis_novedades`, `resumen_semana`, `listar_clientes`, `listar_entradas`, `ver_entrada`, `listar_notas` | 1 |
| `buscar_empresa`, `perfil_empresa`, `detalle_licitacion`, `detalle_convocatoria` | 5 |
| `vigilar_empresa` | 5 por nombre que haya que resolver; 0 con NIF |
| `expediente`, `leer_documento` | 1 |
| `guardar_ficha` | 5 con `prerrellenar`; 0 sin él |
| `guardar_documento`, `confirmar_documento`, `revisar_documento`, `pasos`, `pasos_guardados`, `plazo`, `importes`, `cambiar_estado`, `pedir_documentos` | 0 |
| `listar_mis_alertas`, `crear_alerta`, `pausar_alerta`, `reactivar_alerta`, `editar_alerta`, `borrar_alerta`, `asignar_entrada`, `desasignar_entrada`, `descartar_entrada`, `crear_cliente`, `editar_cliente`, `vincular_alerta`, `desvincular_alerta`, `anotar_entrada`, `borrar_nota` | 0 |

Las escrituras mantienen los límites y confirmaciones del plan. Los lotes reservan todo su coste atómicamente antes de ejecutar herramientas. Una admisión consume incluso con caché o fallo posterior; los rechazos no descuentan. Sin login se devuelve 401; con saldo agotado, tope de perfiles o ráfaga excesiva, 429 con `Retry-After`. `X-Quota-Admission-ID` identifica la reserva registrada atómicamente con el débito; en [Ajustes → API](https://boletinclaro.es/ajustes/api) se puede consultar y conciliar el registro mensual de MCP, API y web (actor, operación, coste y saldo antes/después, sin consultas ni claves en claro; retención 400 días desde el cierre del mes). El consumo anterior al inicio del registro se muestra como saldo de apertura. `X-Quota-*` informa del saldo en créditos; `X-RateLimit-Minute-*`, de las llamadas; `X-Credits-Minute-*`, de los créditos por minuto. Si no se puede reservar se devuelve 503 y no se consultan datos. Puede esperar o cambiar de plan en [Planes](https://boletinclaro.es/planes).

`initialize` y `tools/list` siguen públicos. Las rutas de datos `/v1` requieren clave, disponible también en Gratis; su documentación sigue pública. Las fichas públicas leen snapshots: un fallo nunca provoca consultas a BigQuery.

## Herramientas

Todas requieren iniciar sesión con una cuenta de Boletín Claro (vale la gratuita): tu cliente MCP te lo pedirá la primera vez que uses una.

### Datos públicos

| Herramienta | Para qué |
|---|---|
| **`buscar_oportunidades`** | Subvenciones y licitaciones que encajan con el perfil de una empresa, en lenguaje natural. Filtros: tipo, zona (CCAA/provincia/municipio), importe mín/máx, en plazo o histórico. |
| **`buscar_boletines`** | Normativa, leyes, decretos y anuncios en los boletines oficiales (BOE, BORME y autonómicos: BOJA, DOGC, DOG, BOCM…). |
| **`resumen_boletin`** | Qué se publicó en un boletín un día concreto, agrupado por materia. |
| **`buscar_empresa`** | Encuentra el NIF de una empresa por su nombre y su total de dinero público recibido. |
| **`perfil_empresa`** | Cuánto dinero público ha recibido una empresa (por NIF): subvenciones, contratos, I+D europeo y mercantil, con totales y sectores. |
| **`detalle_convocatoria`** | Detalle de una convocatoria de subvenciones (BDNS): importe total, nº de concesiones y principales beneficiarios. |
| **`detalle_licitacion`** | Detalle de una licitación pública (PLACSP): importe, plazo, lugar, CPV, lotes, órgano y adjudicatarios. |

### Tus alertas

| Herramienta | Para qué |
|---|---|
| **`mis_novedades`** | Lo que han encajado tus alertas en los últimos días. |
| **`resumen_semana`** | El resumen de la semana de todas tus alertas. |
| **`listar_mis_alertas`** | Tus alertas: qué vigila cada una, en qué boletines y en qué estado está. |
| **`crear_alerta`** | Crea una alerta a partir de una descripción en lenguaje natural (te enseña un resumen antes de crearla). Puedes fijar los boletines que vigila o quitar alguno, por ejemplo los fondos europeos. |
| **`editar_alerta`** | Cambia qué vigila una alerta: tema, zona, importes o boletines. |
| **`pausar_alerta`** · **`reactivar_alerta`** | Deja de recibir avisos de una alerta, o vuelve a recibirlos. |
| **`borrar_alerta`** | Borra una alerta y las entradas que solo encontró ella y no has archivado bajo un cliente, con sus notas y documentos (también las descartadas, que ya no podrás recuperar). Lo archivado bajo un cliente se queda, con sus notas y documentos, igual que lo que también encontró otra de tus alertas. Pide confirmación; pausarla es la alternativa reversible. |
| **`vigilar_empresa`** | Vigila empresas concretas por nombre o NIF y entérate de lo que ganan o publican. |

### Entradas, notas y plazos

Lo que apuntes queda también en la ficha de la entrada en boletinclaro.es.

| Herramienta | Para qué |
|---|---|
| **`ver_entrada`** | Muestra una entrada tuya por su id (o su enlace `/entradas/…`), esté en el inbox, archivada o descartada: boletín, importe, plazo, lugar, en qué punto está en tu flujo, la alerta que la detectó, los datos de su ficha, el resumen, los enlaces, sus notas y el código BDNS o expediente para seguir con `detalle_convocatoria` / `detalle_licitacion`. |
| **`anotar_entrada`** | Escribe una nota en una entrada: una gestión hecha, un pendiente o algo que recordar. Con `fecha` se convierte en un vencimiento del calendario y te avisamos por email 15 días, 7 días y el día antes. |
| **`listar_notas`** | Las notas de una entrada, de la más reciente a la más antigua, con su vencimiento y quién la escribió. |
| **`borrar_nota`** | Borra una nota tuya (solo el autor puede). |

### Modo clientes (asesorías y gestorías)

Para quien sigue el dinero público de varios clientes. Requieren tener el modo clientes activado.

| Herramienta | Para qué |
|---|---|
| **`listar_clientes`** | Tus clientes, con su descripción y las alertas que nutren a cada uno. |
| **`listar_entradas`** | El inbox: lo que ha encajado con tus alertas y aún no has archivado bajo ningún cliente. Se filtra por alerta, cliente, veredicto, fecha de llegada, importe o texto del título, admite una línea por entrada y pagina con cursor. |
| **`asignar_entrada`** · **`desasignar_entrada`** | Archiva una entrada bajo uno o varios clientes, o deshaz un archivado. |
| **`descartar_entrada`** | Saca del inbox lo que no interesa a ningún cliente (no borra nada: se recupera desde la web). Por ids o en bloque con los filtros de `listar_entradas`, siempre con vista previa antes. |
| **`crear_cliente`** · **`editar_cliente`** | Da de alta un cliente y mantén al día su descripción, que es el contexto del triaje. |
| **`vincular_alerta`** · **`desvincular_alerta`** | Vincula una alerta a un cliente, o deshaz el vínculo. |

### Expediente — preparar una solicitud

Lo que hagas queda en la ficha del expediente en boletinclaro.es, que ve tu equipo.

| Herramienta | Para qué |
|---|---|
| **`expediente`** | Lee el expediente de una subvención o licitación: estado, lo que falta, pasos, documentos, plazos, importes e instrucciones para seguir. Sin entrada, la ficha del cliente, sus papeles y sus expedientes. Solo lee. |
| **`leer_documento`** | Lee un documento del expediente (también los PDF y Word subidos) o uno oficial por su enlace. |
| **`guardar_documento`** · **`confirmar_documento`** | Guarda requisitos, encaje y borradores en markdown o CSV (de la convocatoria, del cliente o de esta solicitud), y marca la versión que el usuario da por buena. Un borrador se descarga en Word desde la web. |
| **`pasos`** · **`pasos_guardados`** | Los pasos del expediente por fases, y los guardados de otros expedientes para reutilizar lo que funcionó. |
| **`plazo`** | Un plazo fijo, o uno legal en días hábiles que calcula Boletín Claro con los calendarios oficiales. |
| **`importes`** · **`cambiar_estado`** | Lo solicitado y lo concedido (por lote en una licitación), y el estado: presentada con su registro, concedida, descartada… |
| **`pedir_documentos`** · **`revisar_documento`** | Un enlace para que un tercero suba documentos, y la revisión de lo que llega. |
| **`guardar_ficha`** | Los datos de la ficha del cliente o de tu entidad, que se pueden completar del Registro Mercantil por el NIF. |

Lo que cambia algo importante se enseña antes de aplicarlo. Los papeles del cliente sirven en todos sus expedientes; lo común de la convocatoria, en todos sus clientes.

Cada resultado enlaza a su ficha en **[boletinclaro.es](https://boletinclaro.es)**.

## Límite de consultas

El saldo mensual pertenece al workspace y se comparte entre todas sus claves de API, usuarios y clientes MCP. **Gratis: 100 créditos; Individual: 500; Pro: 2.000; Mega: 15.000 (dos saldos: web y conector, y API).** Trial y Oposiciones usan el cupo Gratis. El mes se renueva el día 1 a las 00:00 UTC; cambiar de plan o finalizar Trial no reinicia el consumo. Las lecturas sencillas cuestan 1 crédito; `buscar_empresa`, `perfil_empresa`, `detalle_convocatoria` y `detalle_licitacion`, 5. Gratis admite además **5 llamadas mensuales a perfil de empresa**, compartidas con `GET /v1/empresas/{nif}`, aunque repitas el NIF. Las escrituras MCP cuestan 0; resolver nombres en `vigilar_empresa` cuesta 5 por nombre (con NIF directo, 0). Las investigaciones de empresa que acompañen un borrador consumen por cada búsqueda o perfil. Ráfagas compartidas (llamadas/créditos por minuto): Gratis 20/20, Individual 30/100, Pro 60/300 y Mega 300/1.500. Los límites devuelven 429 con `Retry-After`; un rechazo no consume. Las admisiones consumen incluso con caché o error posterior. La documentación y el listado de herramientas son públicos y no consumen; todo `tools/call` requiere login.

## Ejemplos (pregúntale a tu IA)

- *«¿Qué ayudas hay para mi empresa de software en Bilbao?»*
- *«¿Qué licitaciones de catering de menos de 200.000 € hay abiertas en Madrid?»*
- *«¿Cuánto dinero público ha recibido Grifols?»*
- *«¿Qué ha publicado el BOE sobre protección de datos?»*

## Qué datos hay detrás

**Dinero público**
- **BDNS** — subvenciones y ayudas públicas (concedidas y convocatorias).
- **PLACSP** — licitaciones y contratos del sector público español.
- **TED** — contratación pública de la UE.
- **CORDIS** — proyectos de I+D financiados por la UE.

**Boletines oficiales**
- **BOE** — normativa estatal: leyes, reales decretos, órdenes, resoluciones, anuncios.
- **BORME** — actos mercantiles y datos de empresas.
- **Boletines autonómicos** — BOJA, DOGC, DOG, BOCM y los demás.

## Para desarrolladores

Transporte **Streamable HTTP**, **stateless**, con login OAuth en cada `tools/call`; `initialize` y `tools/list` son públicos. Prueba el protocolo directo:

```bash
curl -s -X POST https://boletinclaro.es/mcp \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json, text/event-stream' \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list","params":{}}'
```

## ¿Quieres que te avisen cuando salga algo nuevo?

Estas herramientas son para **búsquedas puntuales**. Si quieres vigilancia automática —que Boletín Claro te avise por email en cuanto se publique una subvención o licitación que te encaje— crea una alerta en **[boletinclaro.es](https://boletinclaro.es)** o pídele a tu IA que la cree con `crear_alerta`.

---

## In English

**Boletín Claro is the MCP server for Spanish public-sector data** — public money (government grants via BDNS, public tenders via PLACSP/TED, EU R&D funding via CORDIS) and the official gazettes (BOE, BORME and regional bulletins: laws, decrees, announcements) — with real indexed data instead of model guesses.

Remote server (Streamable HTTP), **no install, no API key**. Reading public data is free with a Boletín Claro account. Your MCP client will prompt you to sign in when you use a tool. Point it at:

Monthly workspace credits are shared across MCP and API: **Free 100, Individual 500, Pro 2,000, Mega 15,000** (Mega keeps two balances of 15,000: web and connector, and API). Trial and Oposiciones use Free limits. Free also allows five company-profile calls per month, shared with `GET /v1/empresas/{nif}`; repeated tax IDs count again. Simple reads cost 1 credit; company search, profile and detail cost 5. Writes and `listar_mis_alertas` cost 0, except company-name resolution in `vigilar_empresa` (5 per name). `expediente` and `leer_documento` cost 1, `guardar_ficha` 5 when it prefills from the company registry, and the other expediente tools 0. Company research attached to a draft consumes credits for each search or profile. Shared burst limits (calls/credits per minute) are Free 20/20, Individual 30/100, Pro 60/300 and Mega 300/1,500. The calendar month resets on the first day at 00:00 UTC; plan changes and Trial expiry do not refill it. Limits return 429 with `Retry-After`; rejected requests do not consume. Admitted requests consume even on cache hits or subsequent errors. Discovery and documentation remain public; every tool call requires login.

```
https://boletinclaro.es/mcp
```

On Claude, **[add it in one click](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=Bolet%C3%ADn+Claro&connectorUrl=https%3A%2F%2Fboletinclaro.es%2Fmcp)**.

## Tools

Spanish tool names, natural-language Spanish queries.

Every tool requires signing in with a Boletín Claro account (the free one works).

**Public data:**

| Tool | What it does |
|---|---|
| `buscar_oportunidades` | Grants and tenders matching a company profile. Filters: type, area (region/province/town), min/max amount, open or historical. |
| `buscar_boletines` | Laws, decrees and announcements in the official gazettes (BOE, BORME and regional ones: BOJA, DOGC, DOG, BOCM…). |
| `resumen_boletin` | What a given gazette published on a given day, grouped by subject. |
| `buscar_empresa` | Find a company's tax ID (NIF) by name, with the total public money it has received. |
| `perfil_empresa` | How much public money a company (by NIF) has received: grants, contracts, EU R&D and company-registry data, with totals and sectors. |
| `detalle_convocatoria` | Full detail of a grant call (BDNS): total amount, number of awards and main beneficiaries. |
| `detalle_licitacion` | Full detail of a public tender (PLACSP): amount, deadline, place, CPV, lots, contracting body and awardees. |

**Your alerts:**

| Tool | What it does |
|---|---|
| `mis_novedades` | What your alerts matched over the last few days. |
| `resumen_semana` | This week's digest across all your alerts. |
| `listar_mis_alertas` | Your alerts: what each one watches, in which gazettes, and its status. |
| `crear_alerta` | Create an alert from a natural-language description (previewed before it is created). You can pin the gazettes it watches or leave some out, such as EU funding. |
| `editar_alerta` | Change what an alert watches: topic, area, amounts or gazettes. |
| `pausar_alerta` · `reactivar_alerta` | Stop or resume the notifications of one alert. |
| `borrar_alerta` | Delete an alert and the entries only it found that you have not filed under a client, with their notes and documents (discarded ones too, which can then no longer be recovered). Entries filed under a client keep their notes and documents, and entries another of your alerts also found stay (confirmation required). |
| `vigilar_empresa` | Watch specific companies by name or tax ID. |

**Entries, notes and deadlines** (they show up on the entry at boletinclaro.es too):

| Tool | What it does |
|---|---|
| `ver_entrada` | Show one of your entries by id (or its `/entradas/…` link) — in the inbox, archived or discarded: gazette, amount, deadline, place, where it sits in your flow, the alert that matched it, its ficha facts, summary, links and notes, plus the BDNS code or tender id to continue with `detalle_convocatoria` / `detalle_licitacion`. |
| `anotar_entrada` | Write a note on an entry: something done, something pending, something to remember. With `fecha` it becomes a calendar deadline and you get an email 15 days, 7 days and 1 day before. |
| `listar_notas` | An entry's notes, newest first, with their due date and author. |
| `borrar_nota` | Delete one of your own notes (author only). |

**Client mode** (for consultancies tracking public money for several clients):

| Tool | What it does |
|---|---|
| `listar_clientes` | Your clients, with their description and the alerts feeding each one. |
| `listar_entradas` | The inbox: what your alerts matched and you have not filed under any client yet. Filter by alert, client, verdict, arrival date, amount or title text; one line per entry if you like; paged with a cursor. |
| `asignar_entrada` · `desasignar_entrada` | File an entry under one or more clients, or undo it. |
| `descartar_entrada` | Discard what interests no client (recoverable from the web, never deleted). By id or in bulk with `listar_entradas`' filters, always previewed first. |
| `crear_cliente` · `editar_cliente` | Create a client and keep its description current — it is the context used to triage. |
| `vincular_alerta` · `desvincular_alerta` | Link an alert to a client, or unlink it. |

**Expediente** (preparing an application; it shows up on the expediente at boletinclaro.es):

| Tool | What it does |
|---|---|
| `expediente` | Read a grant or tender application: status, what is missing, steps, documents, deadlines, amounts and how to go on; without an entry, the client's file, papers and applications. Read-only. |
| `leer_documento` · `guardar_documento` · `confirmar_documento` | Read a document (uploaded PDFs and Word files too, or an official one by its link), save requirements, fit and drafts in markdown or CSV, and mark the version the user approved. |
| `pasos` · `pasos_guardados` | The application's steps by phase, and the steps saved from other applications to reuse what worked. |
| `plazo` · `importes` · `cambiar_estado` | A fixed deadline or a legal one in working days computed by Boletín Claro; the amounts asked for and granted (per lot in a tender); the status (submitted with its registry number, granted, discarded…). |
| `pedir_documentos` · `revisar_documento` · `guardar_ficha` | A link for a third party to upload documents and the review of what arrives; the client's or your own entity's file, which can be prefilled from the company registry. |

See the connection snippets above.

---

## Más información

- 🌐 **Web:** [boletinclaro.es](https://boletinclaro.es) — el dinero público español, indexado y resumido con IA.
- 🔌 **Conector MCP (esta guía, online):** [boletinclaro.es/conector](https://boletinclaro.es/conector)
- 📰 **Conecta tu IA al BOE:** [boletinclaro.es/mcp-boe](https://boletinclaro.es/mcp-boe)
- 💶 **Buscar subvenciones con ChatGPT o Claude:** [boletinclaro.es/subvenciones-con-chatgpt](https://boletinclaro.es/subvenciones-con-chatgpt)
- 📋 **Buscar licitaciones con ChatGPT o Claude:** [boletinclaro.es/licitaciones-con-chatgpt](https://boletinclaro.es/licitaciones-con-chatgpt)

## Sobre Boletín Claro

[Boletín Claro](https://boletinclaro.es) indexa los datos públicos de España —el dinero público y los boletines oficiales— y publica resúmenes con IA. Este repositorio documenta su **conector MCP público y gratuito**.

[boletinclaro.es](https://boletinclaro.es) · Licencia [MIT](LICENSE)

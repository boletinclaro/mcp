# Boletín Claro — el MCP de los datos públicos de España

**Datos públicos españoles para tu IA: el dinero público —subvenciones y licitaciones— y todos los boletines oficiales (BOE, BORME, autonómicos). Con datos reales, no suposiciones.**

[![MCP](https://img.shields.io/badge/MCP-Streamable_HTTP-1f6feb)](https://modelcontextprotocol.io)
[![Sin instalación](https://img.shields.io/badge/conexi%C3%B3n-1_clic_(URL)-2ea043)](#conexión-rápida)
[![Sin registro ni API key](https://img.shields.io/badge/acceso-libre,_sin_registro-2ea043)](#conexión-rápida)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)
[![Web](https://img.shields.io/badge/web-boletinclaro.es-111)](https://boletinclaro.es)

Conecta tu IA (Claude, ChatGPT, Cursor, VS Code, Gemini…) a [**Boletín Claro**](https://boletinclaro.es) y pregúntale en lenguaje natural. Dos superficies, una sola conexión:

- 💶 **Dinero público** — subvenciones, licitaciones, ayudas y a quién se las llevan.
- 📰 **Boletines oficiales** — leyes, decretos, anuncios y normativa del BOE, el BORME y los boletines autonómicos.

Las respuestas salen de datos reales indexados, no de suposiciones del modelo.

> **Una sola URL, sin instalar nada, sin API key, sin registro:**
> ```
> https://boletinclaro.es/mcp
> ```
> Conéctate y míralo en [boletinclaro.es/mcp](https://boletinclaro.es/mcp).

---

## Conexión rápida

Es un servidor **remoto** (Streamable HTTP). No descargas nada: das la URL a tu cliente.

### Claude Code (CLI)
```bash
claude mcp add --transport http boletinclaro https://boletinclaro.es/mcp
```

### Claude Desktop · claude.ai (Connectors)
Ajustes → **Connectors** → **Add custom connector** → pega `https://boletinclaro.es/mcp`.

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

## Herramientas

### Sin login — datos públicos

| Herramienta | Para qué |
|---|---|
| **`buscar_oportunidades`** | Subvenciones y licitaciones que encajan con el perfil de una empresa, en lenguaje natural. Filtros: tipo, zona (CCAA/provincia/municipio), importe mín/máx, en plazo o histórico. |
| **`buscar_boletines`** | Normativa, leyes, decretos y anuncios en los boletines oficiales (BOE, BORME y autonómicos: BOJA, DOGC, DOG, BOCM…). |
| **`resumen_boletin`** | Qué se publicó en un boletín un día concreto, agrupado por materia. |
| **`buscar_empresa`** | Encuentra el NIF de una empresa por su nombre y su total de dinero público recibido. |
| **`perfil_empresa`** | Cuánto dinero público ha recibido una empresa (por NIF): subvenciones, contratos, I+D europeo y mercantil, con totales y sectores. |
| **`detalle_convocatoria`** | Detalle de una convocatoria de subvenciones (BDNS): importe total, nº de concesiones y principales beneficiarios. |
| **`detalle_licitacion`** | Detalle de una licitación pública (PLACSP): importe, plazo, lugar, CPV, lotes, órgano y adjudicatarios. |

### Con tu cuenta — tus alertas

Requieren iniciar sesión: tu cliente MCP te lo pedirá la primera vez que uses una.

| Herramienta | Para qué |
|---|---|
| **`mis_novedades`** | Lo que han encajado tus alertas en los últimos días. |
| **`resumen_semana`** | El resumen de la semana de todas tus alertas. |
| **`listar_mis_alertas`** | Tus alertas: qué vigila cada una, en qué boletines y en qué estado está. |
| **`crear_alerta`** | Crea una alerta a partir de una descripción en lenguaje natural (te enseña un resumen antes de crearla). |
| **`editar_alerta`** | Cambia qué vigila una alerta: tema, zona, importes o boletines. |
| **`pausar_alerta`** · **`reactivar_alerta`** | Deja de recibir avisos de una alerta, o vuelve a recibirlos. |
| **`borrar_alerta`** | Borra una alerta y su historial (pide confirmación; pausarla es la alternativa reversible). |
| **`vigilar_empresa`** | Vigila empresas concretas por nombre o NIF y entérate de lo que ganan o publican. |

### Con tu cuenta — modo clientes (asesorías y gestorías)

Para quien sigue el dinero público de varios clientes. Requieren tener el modo clientes activado.

| Herramienta | Para qué |
|---|---|
| **`listar_clientes`** | Tus clientes, con su descripción y las alertas que nutren a cada uno. |
| **`listar_entradas`** | El inbox: lo que ha encajado con tus alertas y aún no has archivado bajo ningún cliente. |
| **`asignar_entrada`** · **`desasignar_entrada`** | Archiva una entrada bajo uno o varios clientes, o deshaz un archivado. |
| **`descartar_entrada`** | Saca del inbox lo que no interesa a ningún cliente (no borra nada: se recupera desde la web). |
| **`crear_cliente`** · **`editar_cliente`** | Da de alta un cliente y mantén al día su descripción, que es el contexto del triaje. |
| **`vincular_alerta`** · **`desvincular_alerta`** | Vincula una alerta a un cliente, o deshaz el vínculo. |

Cada resultado enlaza a su ficha en **[boletinclaro.es](https://boletinclaro.es)**.

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

Transporte **Streamable HTTP**, **stateless**, **anónimo** (límite ~120 req/min por IP). Prueba el protocolo directo:

```bash
curl -s -X POST https://boletinclaro.es/mcp \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json, text/event-stream' \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list","params":{}}'
```

## ¿Quieres que te avisen cuando salga algo nuevo?

Estas herramientas son para **búsquedas puntuales**. Si quieres vigilancia automática —que Boletín Claro te avise por email en cuanto se publique una subvención o licitación que te encaje— crea una alerta en **[boletinclaro.es](https://boletinclaro.es)**.

---

## In English

**Boletín Claro is the MCP server for Spanish public-sector data** — public money (government grants via BDNS, public tenders via PLACSP/TED, EU R&D funding via CORDIS) and the official gazettes (BOE, BORME and regional bulletins: laws, decrees, announcements) — with real indexed data instead of model guesses.

Remote server (Streamable HTTP), **no install, no API key**. Just point your MCP client at:

```
https://boletinclaro.es/mcp
```

## Tools

Spanish tool names, natural-language Spanish queries.

**Anonymous — no login, no API key:**

| Tool | What it does |
|---|---|
| `buscar_oportunidades` | Grants and tenders matching a company profile. Filters: type, area (region/province/town), min/max amount, open or historical. |
| `buscar_boletines` | Laws, decrees and announcements in the official gazettes (BOE, BORME and regional ones: BOJA, DOGC, DOG, BOCM…). |
| `resumen_boletin` | What a given gazette published on a given day, grouped by subject. |
| `buscar_empresa` | Find a company's tax ID (NIF) by name, with the total public money it has received. |
| `perfil_empresa` | How much public money a company (by NIF) has received: grants, contracts, EU R&D and company-registry data, with totals and sectors. |
| `detalle_convocatoria` | Full detail of a grant call (BDNS): total amount, number of awards and main beneficiaries. |
| `detalle_licitacion` | Full detail of a public tender (PLACSP): amount, deadline, place, CPV, lots, contracting body and awardees. |

**With a Boletín Claro account** (your client prompts you to sign in the first time):

| Tool | What it does |
|---|---|
| `mis_novedades` | What your alerts matched over the last few days. |
| `resumen_semana` | This week's digest across all your alerts. |
| `listar_mis_alertas` | Your alerts: what each one watches, in which gazettes, and its status. |
| `crear_alerta` | Create an alert from a natural-language description (previewed before it is created). |
| `editar_alerta` | Change what an alert watches: topic, area, amounts or gazettes. |
| `pausar_alerta` · `reactivar_alerta` | Stop or resume the notifications of one alert. |
| `borrar_alerta` | Delete an alert and its history (confirmation required). |
| `vigilar_empresa` | Watch specific companies by name or tax ID. |

**Client mode** (for consultancies tracking public money for several clients):

| Tool | What it does |
|---|---|
| `listar_clientes` | Your clients, with their description and the alerts feeding each one. |
| `listar_entradas` | The inbox: what your alerts matched and you have not filed under any client yet. |
| `asignar_entrada` · `desasignar_entrada` | File an entry under one or more clients, or undo it. |
| `descartar_entrada` | Discard what interests no client (recoverable from the web, never deleted). |
| `crear_cliente` · `editar_cliente` | Create a client and keep its description current — it is the context used to triage. |
| `vincular_alerta` · `desvincular_alerta` | Link an alert to a client, or unlink it. |

See the connection snippets above.

---

## Más información

- 🌐 **Web:** [boletinclaro.es](https://boletinclaro.es) — el dinero público español, indexado y resumido con IA.
- 🔌 **Conector MCP (esta guía, online):** [boletinclaro.es/mcp](https://boletinclaro.es/mcp)
- 📰 **Conecta tu IA al BOE:** [boletinclaro.es/mcp-boe](https://boletinclaro.es/mcp-boe)
- 💶 **Buscar subvenciones con ChatGPT o Claude:** [boletinclaro.es/subvenciones-con-chatgpt](https://boletinclaro.es/subvenciones-con-chatgpt)
- 📋 **Buscar licitaciones con ChatGPT o Claude:** [boletinclaro.es/licitaciones-con-chatgpt](https://boletinclaro.es/licitaciones-con-chatgpt)

## Sobre Boletín Claro

[Boletín Claro](https://boletinclaro.es) indexa los datos públicos de España —el dinero público y los boletines oficiales— y publica resúmenes con IA. Este repositorio documenta su **conector MCP público y gratuito**.

[boletinclaro.es](https://boletinclaro.es) · Licencia [MIT](LICENSE)

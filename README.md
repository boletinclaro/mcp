# Boletín Claro — MCP del dinero público español

**El servidor [MCP](https://modelcontextprotocol.io) para buscar subvenciones, licitaciones y ayudas públicas de España con datos reales, desde tu asistente de IA.**

[![MCP](https://img.shields.io/badge/MCP-Streamable_HTTP-1f6feb)](https://modelcontextprotocol.io)
[![Sin instalación](https://img.shields.io/badge/conexi%C3%B3n-1_clic_(URL)-2ea043)](#conexión-rápida)
[![Sin API key](https://img.shields.io/badge/auth-an%C3%B3nimo-2ea043)](#conexión-rápida)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)
[![Web](https://img.shields.io/badge/web-boletinclaro.es-111)](https://boletinclaro.es)

Conecta tu IA (Claude, ChatGPT, Cursor, VS Code, Gemini…) a **Boletín Claro** y pregúntale en lenguaje natural por el dinero público español. Las respuestas salen de datos reales indexados —subvenciones, licitaciones, I+D europeo y mercantil— no de suposiciones del modelo.

> **Una sola URL, sin instalar nada, sin API key, sin registro:**
> ```
> https://boletinclaro.es/mcp
> ```

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
[![Add to Cursor](https://img.shields.io/badge/Cursor-Add_to_Cursor-000)](cursor://anysphere.cursor-deeplink/mcp/install?name=boletinclaro&config=eyJ1cmwiOiJodHRwczovL2JvbGV0aW5jbGFyby5lcy9tY3AifQ==)

O en `~/.cursor/mcp.json`:
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

| Herramienta | Para qué |
|---|---|
| **`buscar_oportunidades`** | Subvenciones y licitaciones que encajan con el perfil de una empresa, en lenguaje natural. Filtros: tipo, zona (CCAA/provincia/municipio), importe mín/máx, en plazo o histórico. |
| **`buscar_boletines`** | Normativa, leyes, decretos y anuncios en los boletines oficiales (BOE, BORME y autonómicos: BOJA, DOGC, DOG, BOCM…). |
| **`buscar_empresa`** | Encuentra el NIF de una empresa por su nombre y su total de dinero público recibido. |
| **`perfil_empresa`** | Cuánto dinero público ha recibido una empresa (por NIF): subvenciones, contratos, I+D europeo y mercantil, con totales y sectores. |
| **`detalle_convocatoria`** | Detalle de una convocatoria de subvenciones (BDNS): importe total, nº de concesiones y principales beneficiarios. |
| **`detalle_licitacion`** | Detalle de una licitación pública (PLACSP): importe, plazo, lugar, CPV, lotes, órgano y adjudicatarios. |

Cada resultado enlaza a su ficha en **boletinclaro.es**.

## Ejemplos (pregúntale a tu IA)

- *«¿Qué ayudas hay para mi empresa de software en Bilbao?»*
- *«¿Qué licitaciones de catering de menos de 200.000 € hay abiertas en Madrid?»*
- *«¿Cuánto dinero público ha recibido Grifols?»*
- *«¿Qué ha publicado el BOE sobre protección de datos?»*

## Qué datos hay detrás

- **BDNS** — subvenciones y ayudas públicas (concedidas y convocatorias).
- **PLACSP** — licitaciones y contratos del sector público español.
- **TED** — contratación pública de la UE.
- **CORDIS** — proyectos de I+D financiados por la UE.
- **BORME** — datos mercantiles de empresas.
- **BOE + boletines autonómicos** — normativa y anuncios oficiales.

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

**Boletín Claro is the MCP server for searching Spanish public money** — government grants (BDNS), public tenders (PLACSP/TED), EU R&D funding (CORDIS) and company registry data (BORME), with real indexed data instead of model guesses.

Remote server (Streamable HTTP), **no install, no API key**. Just point your MCP client at:

```
https://boletinclaro.es/mcp
```

Tools (Spanish names, natural-language Spanish queries): `buscar_oportunidades` (grants & tenders matching a company profile), `buscar_boletines` (official-gazette law/announcement search), `buscar_empresa` / `perfil_empresa` (public money received by a company), `detalle_convocatoria` / `detalle_licitacion` (full detail of a grant call / tender). See the connection snippets above.

---

## Sobre Boletín Claro

[Boletín Claro](https://boletinclaro.es) indexa el dinero público español y publica resúmenes con IA. Este repositorio documenta su **conector MCP público y gratuito**.

Hecho en España 🇪🇸 · [boletinclaro.es](https://boletinclaro.es) · Licencia [MIT](LICENSE)

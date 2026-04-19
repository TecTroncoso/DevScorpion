# 🤖 BotDiscord — Inteligencia Artificial con Memoria y Skills

¡Bienvenido al futuro de tu servidor! Este no es el típico bot que repite comandos. **BotDiscord** es un asistente avanzado construido sobre `discord.js` v14, diseñado para ser un compañero de desarrollo y gestión, con memoria a largo plazo y un sistema de "Skills" modular.

---

## ✨ Características Principales

### 🧠 Memoria Evolutiva (Engram-lite)
El bot no solo recuerda los últimos mensajes, sino que posee un sistema de **observaciones persistentes**:
- **Historial Reciente**: Mantiene el contexto de los últimos 20 mensajes por usuario.
- **Memoria a Largo Plazo**: Detecta y guarda preferencias (ej: "prefiero TypeScript"), decisiones de diseño y bugs reportados automáticamente en una base de datos SQLite/Turso.

### 🛠️ Sistema de Skills Modulares
Inspirado en flujos de trabajo profesionales, el bot cuenta con habilidades específicas que se activan por comandos o lenguaje natural:
- **`resumir`**: Condensa hilos de conversación o textos largos.
- **`explicar-codigo`**: Desglosa fragmentos de código línea por línea.
- **`debug`**: Ayuda a encontrar la raíz de errores y propone soluciones.
- **`planificar-proyecto`**: Divide tareas complejas en fases (Explorar, Proponer, Especificar, etc.).

### ⚡ Rendimiento de Grado Industrial
- **Write-Behind Cache**: Las memorias se guardan en RAM y se sincronizan con la DB cada 5 segundos para evitar latencia.
- **Streaming Inteligente**: Respuestas en tiempo real que se editan dinámicamente, manejando los límites de rate-limit de Discord.
- **Auto-Adjuntos**: Si la respuesta supera los 2000 caracteres, el bot genera automáticamente un archivo `.txt` para no cortar la información.

---

## 🚀 Instalación y Configuración

### Requisitos Previos
- [Node.js](https://nodejs.org/) v16.11.0 o superior.
- Una instancia de [Turso](https://turso.tech/) (o SQLite local).
- Claves de API para OpenAI/Groq y Discord.

### Configuración del Entorno
Crea un archivo `.env` en la raíz del proyecto:

```env
DISCORD_TOKEN=tu_token_de_discord
GROQ_API_KEY=tu_api_key_de_groq_o_ollama
TURSO_DATABASE_URL=libsql://tu-db.turso.io
TURSO_AUTH_TOKEN=tu_auth_token
```

### Instalación
```bash
npm install
node bot2.js
```

---

## 🎮 Comandos y Uso

| Comando | Descripción | Permisos |
| :--- | :--- | :--- |
| `!setchannel` | Configura el canal de respuesta automática. | Administrador |
| `!clearmemory` | Borra todo el historial y observaciones del usuario. | Usuario |
| `!resumir` | Activa el skill de resumen. | Usuario |
| `!planificar` | Inicia una planificación de proyecto. | Usuario |

> [!TIP]
> También podés mencionar al bot `@BotDiscord` en cualquier canal para interactuar con él fuera del canal configurado.

---

## 🏗️ Arquitectura Técnica

El bot sigue un patrón de **arquitectura híbrida**:
- **Persistencia**: SQLite (vía LibSQL) para datos estructurados.
- **Caché**: `lru-cache` para acceso instantáneo a sesiones activas.
- **IA**: Motor compatible con OpenAI (probado con `minimax-m2.7` y modelos locales vía Ollama).

### Flujo de Razonamiento (SDD)
Internamente, cuando le pedís algo complejo, el bot sigue el flujo de **Spec-Driven Development**:
1. **Explorar**: Entiende el contexto.
2. **Proponer/Diseñar**: Esboza la solución.
3. **Implementar/Verificar**: Entrega el resultado final.

---

## 📜 Licencia
Este proyecto es de código abierto. ¡Sentite libre de forkearlo y meterle toda la magia que quieras!

---
*Desarrollado con ❤️ para la comunidad de Discord.*

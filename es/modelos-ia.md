# Cómo funciona la IA — Mathsboard

[English version](../ai-models.md)

Mathsboard usa dos motores distintos.

1. **Su propio motor matemático**, incluido en la App. Calcula los pasos resueltos de cada lección, las gráficas y los exploradores interactivos. No necesita IA ni internet, y está siempre disponible.
2. **Un modelo de IA**, que hace lo que requiere lenguaje:
   - leer tu escritura;
   - explicar los pasos con palabras;
   - responder tus preguntas;
   - dar pistas;
   - crear ejercicios nuevos.

Puedes elegir una de tres opciones de IA en **Ajustes**. Solo se usa la que eliges.

## 1. Apple Intelligence (por defecto)

- La App usa el modelo de lenguaje de Apple que corre en el propio iPad (Foundation Models).
- Todo ocurre **en tu iPad**. No se envía nada a ningún lado.
- Responde al instante y no necesita descarga.
- Requiere un iPad compatible con Apple Intelligence, con Apple Intelligence activado en Ajustes.

## 2. Modelo en el dispositivo (opcional)

- Un modelo abierto, **Gemma 4 E2B** (4 bits, formato MLX), corre directamente en el chip del iPad con el framework MLX de Apple.
- Funciona sin conexión y lee imágenes (tu escritura) por sí mismo.
- **Descarga:** unos 3,5 GB, una sola vez, la primera vez que lo eliges.
  - El modelo se descarga de nuestra réplica en GitHub ([dafo-swarm-downloads](https://github.com/gabgiani/dafo-swarm-downloads/releases/tag/mlx-gemma4-e2b-it-4bit-v1)), en partes. Cada parte y el archivo final se verifican con SHA-256.
  - Si la réplica no está disponible, la App descarga el mismo modelo de Hugging Face (`mlx-community/gemma-4-e2b-it-4bit`).
  - La descarga se hace en segundo plano. Puedes seguir usando la App o cancelarla.
- **Privacidad:** después de la descarga no sale nada del iPad. La única conexión es la descarga en sí.
- Necesita un iPad con 8 GB de memoria o más.

## 3. DAFO Swarm

DAFO Swarm es una app aparte que instalas **en tu propio Mac** (Apple Silicon). Convierte el Mac en un servidor de IA para tu iPad.

- **Para qué sirve:** un Mac puede correr modelos más grandes y capaces que un iPad, y el iPad no gasta memoria ni batería.
- **Cómo funciona:**
  1. Instalas DAFO Swarm en el Mac. Descarga y corre el modelo en el Mac, con MLX.
  2. El Mac publica una API estándar, compatible con OpenAI, en tu red local.
  3. En Mathsboard, abres los Ajustes de la App y escribes la dirección del Mac, por ejemplo `http://192.168.1.20:43100/v1`.
  4. Cuando preguntas algo, el iPad envía el ejercicio (texto e imagen de tu escritura) a **tu** Mac. El Mac responde y el iPad muestra el resultado.
- **Privacidad:** tus ejercicios solo viajan entre tu iPad y tu Mac, dentro de tu red. Nunca nos llegan.
- **Descarga:** los instaladores de DAFO Swarm están en [github.com/gabgiani/dafo-swarm-downloads](https://github.com/gabgiani/dafo-swarm-downloads/releases).
- **Réplicas de los modelos:** esa misma página tiene copias de los modelos divididas en partes. DAFO Swarm las usa cuando Hugging Face está lento o no disponible, y vuelve a unir las partes automáticamente.

## Resumen

| | Apple Intelligence | Modelo en el dispositivo | DAFO Swarm |
|---|---|---|---|
| Corre en | iPad | iPad | Tu Mac |
| Descarga | Ninguna | ~3,5 GB, una vez | El modelo se descarga en el Mac |
| Funciona sin internet | Sí | Sí | Hace falta la red local |
| Tus datos salen del iPad | No | No | Solo hacia tu propio Mac |

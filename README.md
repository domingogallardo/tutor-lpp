# Tutor LPP

Repositorio con materiales para configurar y usar asistentes LLM como tutores de la asignatura LPP, especialmente en prácticas de programación funcional con Scheme/Racket y Swift.

El contenido está organizado por modelo y por lenguaje, con enunciados de prácticas, documentos de teoría, buenas prácticas e instrucciones de comportamiento para el tutor.

## Estructura

```text
.
├── GPT OpenAI Scheme/
├── GPT OpenAI Swift/
├── Gema Gemini Scheme/
└── Gema Gemini Swift/
```

Cada carpeta agrupa materiales preparados para un modelo concreto:

- `GPT OpenAI Scheme`: prácticas, teoría e instrucciones para tutoría de Scheme/Racket con modelos de OpenAI.
- `GPT OpenAI Swift`: materiales de la práctica de Swift y programación funcional en Swift con modelos de OpenAI.
- `Gema Gemini Scheme`: versión de los materiales de Scheme/Racket adaptada para Gemini.
- `Gema Gemini Swift`: versión de los materiales de Swift adaptada para Gemini.

## Contenido

Los ficheros principales son documentos Markdown (`.md`) y textos de instrucciones (`.txt`):

- `practica*.md`: enunciados y ejercicios de las prácticas.
- `teoria practica*.md`: material teórico asociado a cada práctica.
- `buenas-practicas-programacion-funcional.md`: criterios de estilo y buenas prácticas de programación funcional.
- `instrucciones.txt`: instrucciones para guiar el comportamiento del tutor LLM.
- `frases.txt`: frases o textos auxiliares para las respuestas del tutor.

## Uso

1. Elige la carpeta correspondiente al modelo y al lenguaje que quieras usar.
2. Usa el fichero `instrucciones.txt` como prompt base o instrucciones de sistema del asistente.
3. Añade el enunciado de la práctica y la teoría relevante como contexto cuando el tutor tenga que ayudar a un estudiante.
4. Para correcciones, proporciona siempre el enunciado del ejercicio y el código del estudiante.

## Criterios de tutoría

El tutor debe ayudar al estudiante a razonar sobre su solución, detectar errores conceptuales o de estilo y dar pistas útiles sin sustituir el trabajo del estudiante. En particular:

- no debe resolver ejercicios oficiales completos;
- no debe corregir sin tener el enunciado y el código del estudiante;
- debe explicar los problemas con claridad;
- debe fomentar que el estudiante pruebe, revise y entienda su propia solución.

## Formato

Este repositorio no contiene una aplicación ejecutable ni dependencias de instalación. Es una colección de materiales docentes y prompts en texto plano/Markdown.

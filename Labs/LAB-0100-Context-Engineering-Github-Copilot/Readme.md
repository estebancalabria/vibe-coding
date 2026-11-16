# Laboratorio: Preparar un repositorio con Context Engineering para GitHub Copilot

## Objetivo

En este laboratorio trabajarás con una aplicación full stack existente y utilizarás GitHub Copilot para preparar el repositorio con contexto persistente sobre el proyecto.

La aplicación ya está desarrollada y funcionando. No implementaremos nuevas funcionalidades ni modificaremos su comportamiento.

Durante el laboratorio crearás y organizarás diferentes fuentes de contexto para que GitHub Copilot pueda comprender:

- qué hace la aplicación;
- qué tecnologías utiliza;
- cómo está organizada;
- qué convenciones debe respetar;
- qué restricciones debe considerar;
- dónde encontrar información específica cuando la necesite.

El objetivo es observar cómo el contexto almacenado en el repositorio puede ayudar a GitHub Copilot a comprender el proyecto y responder de acuerdo con sus características y convenciones sin tener que repetir toda esta información en cada prompt.

---

# 1. Requisitos

Para realizar el laboratorio necesitarás:

- Visual Studio Code.
- Node.js y npm instalados.
- GitHub Copilot habilitado.
- GitHub Copilot Chat.
- Acceso al modo Agent de GitHub Copilot.
- El repositorio inicial proporcionado para el laboratorio.

---

# 2. Conocer la aplicación

El proyecto utilizado en este laboratorio es **Task Board**, una aplicación full stack sencilla para gestionar tareas.

La aplicación permite:

- visualizar tareas;
- crear tareas;
- marcar tareas como completadas;
- eliminar tareas;
- asignar prioridades.

La aplicación utiliza:

- React;
- Vite;
- Node.js;
- Express;
- una API REST;
- almacenamiento simple en memoria.

El objetivo del laboratorio no es desarrollar esta aplicación. La utilizaremos como proyecto existente sobre el cual construiremos el contexto que utilizará GitHub Copilot.

---

# 3. Explorar la estructura inicial

Abre el repositorio en Visual Studio Code.

La estructura general del proyecto será similar a:

```text
task-board/
├── client/
│   ├── src/
│   │   ├── components/
│   │   ├── services/
│   │   ├── App.jsx
│   │   └── main.jsx
│   └── package.json
│
├── server/
│   ├── routes/
│   ├── services/
│   ├── app.js
│   └── package.json
│
├── README.md
└── .gitignore
```

Observa brevemente:

- la separación entre frontend y backend;
- la estructura de `client`;
- la estructura de `server`;
- los archivos `package.json`;
- los componentes existentes;
- los servicios existentes;
- las rutas de la API.

No realices cambios en el código.

---

# 4. Ejecutar la aplicación

Antes de generar documentación sobre un proyecto es conveniente comprobar su estado actual.

Instala las dependencias del frontend y backend utilizando los comandos definidos por el proyecto.

Inicia ambos componentes de la aplicación.

Abre la aplicación en el navegador y comprueba brevemente que funciona.

Por ejemplo:

- visualiza las tareas existentes;
- crea una tarea;
- cambia su estado;
- observa cómo se muestran las prioridades.

Una vez comprobado el funcionamiento, vuelve a Visual Studio Code.

Durante el resto del laboratorio no será necesario realizar cambios funcionales en la aplicación.

---

# 5. Analizar el proyecto con GitHub Copilot

Abre GitHub Copilot Chat en Visual Studio Code y selecciona:

```text
Agent
```

Antes de agregar contexto explícito al repositorio, pide a GitHub Copilot que analice el proyecto.

Utiliza el siguiente prompt:

```text
Analiza este repositorio completo.

Explícame:

1. cuál es el propósito de la aplicación;
2. qué tecnologías utiliza;
3. cómo está organizado el frontend;
4. cómo está organizado el backend;
5. cómo se comunican frontend y backend;
6. qué convenciones de desarrollo puedes identificar en el código actual.

Basa tu respuesta únicamente en la información disponible actualmente en el repositorio.

No modifiques ningún archivo.
```

Observa la respuesta.

En este momento GitHub Copilot puede analizar el código, los archivos de configuración y la documentación existente, pero todavía no hemos proporcionado instrucciones específicas sobre cómo queremos que trabaje dentro del repositorio.

---

# 6. Preparar el contexto del repositorio

Vamos a preparar tres fuentes de contexto:

```text
README.md

.github/
└── copilot-instructions.md

docs/
└── ui-guidelines.md
```

Cada una tendrá una responsabilidad diferente:

- `README.md` describirá el proyecto y permitirá comprenderlo rápidamente.
- `.github/copilot-instructions.md` contendrá las instrucciones persistentes y las principales convenciones que GitHub Copilot deberá respetar al trabajar en el repositorio.
- `docs/ui-guidelines.md` contendrá información específica sobre las convenciones visuales de la aplicación.

La mayor parte de las instrucciones permanecerá en:

```text
.github/copilot-instructions.md
```

El documento ubicado en `docs` será deliberadamente pequeño y específico.

Esto permitirá observar cómo las instrucciones principales pueden dirigir al agente hacia documentación adicional cuando una tarea necesita contexto más especializado.

---

# 7. Generar el README.md

Vamos a utilizar GitHub Copilot para analizar el proyecto existente y generar el README.

En GitHub Copilot Chat utiliza el siguiente prompt:

```text
Analiza el repositorio completo antes de realizar cualquier cambio.

Genera o actualiza únicamente el archivo README.md.

El README debe estar basado en el proyecto real y debe incluir:

# Task Board

## Descripción

Explica brevemente qué hace la aplicación.

## Funcionalidades

Enumera las principales funcionalidades disponibles actualmente.

## Tecnologías

Identifica las tecnologías utilizadas por el frontend y el backend.

## Arquitectura

Explica brevemente la separación entre frontend y backend y cómo se comunican.

## Estructura del proyecto

Describe los principales directorios del repositorio.

## Ejecución del proyecto

Documenta los comandos reales necesarios para instalar dependencias y ejecutar frontend y backend.

## Documentación adicional

Incluye una referencia a:

docs/ui-guidelines.md

Importante:

- Basa toda la información en archivos existentes en el repositorio.
- Examina package.json y los archivos de configuración antes de documentar comandos.
- No inventes tecnologías, scripts, funcionalidades ni decisiones arquitectónicas.
- No modifiques código.
- No modifiques archivos de configuración.
- No agregues dependencias.
- Solo crea o modifica README.md.
```

Revisa el archivo generado.

Comprueba especialmente que:

- las tecnologías sean correctas;
- los comandos correspondan con los scripts reales;
- la estructura descrita exista;
- no se hayan documentado funcionalidades inexistentes.

---

# 8. Crear una guía visual específica

Ahora agregaremos un pequeño documento con información especializada sobre la interfaz de usuario.

Crea la carpeta:

```text
docs
```

Dentro de ella crea:

```text
ui-guidelines.md
```

La estructura será:

```text
task-board/
├── docs/
│   └── ui-guidelines.md
├── client/
├── server/
├── README.md
└── .gitignore
```

Agrega el siguiente contenido:

```markdown
# UI Guidelines

## Colors

- Primary: `#2563EB`
- Success: `#16A34A`
- Warning: `#F59E0B`
- Danger: `#DC2626`
- Background: `#F8FAFC`
- Text: `#0F172A`

## Spacing

Use an 8px spacing system:

- Small: 8px
- Medium: 16px
- Large: 24px
- Extra large: 32px

## Buttons

- Use the primary color for the main action.
- Use the danger color only for destructive actions.
- Buttons should have an 8px border radius.
- Keep button labels short and action-oriented.

## Task Cards

- Use a white background.
- Use a subtle border.
- Use a 12px border radius.
- Display the task title prominently.
- Show priority and status as badges.
- Keep actions at the bottom of the card.

## General Principles

- Keep the interface simple and clean.
- Maintain consistent spacing.
- Avoid unnecessary visual elements.
- Reuse existing components before creating new ones.
```

Este archivo representa información específica que solo será especialmente relevante cuando GitHub Copilot tenga que analizar o trabajar con la interfaz de usuario.

---

# 9. Crear las instrucciones del repositorio

Ahora vamos a crear las instrucciones principales que GitHub Copilot utilizará al trabajar con este proyecto.

Crearemos:

```text
.github/copilot-instructions.md
```

En lugar de escribir manualmente toda la información, utilizaremos GitHub Copilot para analizar el proyecto y generar una primera versión utilizando un template.

De esta manera las instrucciones quedan preparadas una vez dentro del repositorio y pueden mantenerse junto con el proyecto.

---

# 10. Generar copilot-instructions.md con GitHub Copilot

En GitHub Copilot Chat utiliza el siguiente prompt:

```text
Analiza el repositorio completo antes de realizar cualquier cambio.

Crea únicamente el archivo:

.github/copilot-instructions.md

Utiliza el siguiente template como estructura:

# Copilot Instructions

## Project Overview

Describe brevemente el propósito de la aplicación y sus principales capacidades.

## Technology Stack

Documenta las tecnologías realmente utilizadas por el proyecto.

## Architecture

Describe:

- la organización del frontend;
- la organización del backend;
- las responsabilidades principales de cada parte;
- cómo se comunican frontend y backend.

## Repository Structure

Documenta únicamente los directorios y archivos importantes para comprender y modificar el proyecto.

## Development Commands

Documenta los comandos reales definidos por el proyecto para:

- instalar dependencias;
- iniciar el frontend;
- iniciar el backend;
- construir la aplicación si existe un comando para hacerlo.

## Frontend Conventions

Identifica las convenciones utilizadas en el código existente y agrega instrucciones sobre:

- componentes;
- manejo de estado;
- llamadas a la API;
- organización del código;
- reutilización de componentes.

## Backend Conventions

Identifica las convenciones utilizadas en el código existente y agrega instrucciones sobre:

- rutas;
- lógica de negocio;
- respuestas de la API;
- validación;
- manejo de errores.

## Naming Conventions

Identifica y documenta las convenciones existentes para:

- archivos;
- componentes;
- funciones;
- variables;
- valores booleanos;
- endpoints.

## UI and Styling

Cuando una consulta o cambio involucre la interfaz de usuario o estilos, consulta:

docs/ui-guidelines.md

Utiliza ese documento como contexto para mantener la consistencia visual de la aplicación.

## Change Guidelines

Incluye las siguientes instrucciones:

- Analiza los archivos relevantes antes de proponer un cambio.
- Mantén la estructura existente del proyecto.
- Realiza el cambio mínimo necesario.
- No modifiques archivos que no estén relacionados con la tarea.
- No agregues dependencias salvo que sean necesarias.
- Mantén el comportamiento existente salvo que se solicite explícitamente modificarlo.
- Identifica los archivos afectados antes de realizar un cambio.
- Sigue los patrones existentes en el repositorio.

## Restrictions

Incluye las siguientes instrucciones:

- No reemplaces el stack tecnológico existente.
- No introduzcas abstracciones innecesarias.
- No muevas o renombres archivos sin una razón clara.
- No expongas secretos, credenciales ni variables de entorno.
- No inventes requisitos que no hayan sido especificados.
- Si el usuario solicita únicamente análisis, no modifiques archivos.

Reglas para generar el archivo:

- Basa las instrucciones en evidencia encontrada en el repositorio.
- Analiza código, dependencias, scripts, rutas y estructura antes de escribir.
- No inventes tecnologías, comandos o convenciones.
- Mantén las instrucciones concisas y específicas para este proyecto.
- No copies innecesariamente todo el contenido de README.md.
- No copies todo el contenido de docs/ui-guidelines.md.
- Solo referencia docs/ui-guidelines.md cuando corresponda.
- No modifiques código.
- No modifiques ningún otro archivo.
```

Permite que GitHub Copilot cree:

```text
.github/copilot-instructions.md
```

---

# 11. Revisar las instrucciones generadas

Abre:

```text
.github/copilot-instructions.md
```

No aceptes automáticamente que toda la información generada sea correcta.

Comprueba que GitHub Copilot haya identificado correctamente:

- React y Vite;
- Node.js y Express;
- la separación entre `client` y `server`;
- los comandos definidos en los archivos `package.json`;
- la ubicación de componentes;
- la ubicación de servicios;
- las rutas del backend;
- las convenciones presentes realmente en el código.

Comprueba también que exista una referencia similar a:

```markdown
## UI and Styling

When working on user interface components or styles, follow the visual guidelines defined in `docs/ui-guidelines.md`.

Maintain visual consistency with those guidelines and with the existing components.
```

Si GitHub Copilot documentó algo que no existe en el proyecto, corrígelo antes de continuar.

---

# 12. Observar la estructura final de contexto

El repositorio ahora incluye:

```text
task-board/
├── .github/
│   └── copilot-instructions.md
│
├── docs/
│   └── ui-guidelines.md
│
├── client/
│   └── ...
│
├── server/
│   └── ...
│
├── README.md
└── .gitignore
```

Tenemos diferentes tipos de información dentro del repositorio:

### README.md

Describe principalmente:

- qué es el proyecto;
- qué funcionalidades tiene;
- qué tecnologías utiliza;
- cómo está organizado;
- cómo ejecutarlo.

### .github/copilot-instructions.md

Define principalmente:

- cómo está organizado el proyecto;
- qué convenciones debe seguir GitHub Copilot;
- qué restricciones debe respetar;
- cómo debe comportarse cuando realice tareas dentro del repositorio;
- qué documentación adicional debe consultar cuando corresponda.

### docs/ui-guidelines.md

Contiene contexto especializado sobre:

- colores;
- espaciado;
- botones;
- tarjetas;
- principios visuales.

No toda la información del proyecto tiene que estar concentrada en un único archivo.

La información general y las instrucciones que deben considerarse habitualmente pueden permanecer en `copilot-instructions.md`.

La información más específica, que resulta especialmente relevante para determinados tipos de tareas, puede mantenerse en archivos separados y ser referenciada desde las instrucciones principales.

---

# 13. Verificar el contexto general

Ahora comprobaremos qué comprende GitHub Copilot utilizando el contexto disponible en el repositorio.

Abre una nueva conversación de GitHub Copilot Chat.

Utiliza el siguiente prompt:

```text
Analiza este repositorio.

Sin modificar ningún archivo, explícame:

1. cuál es el propósito de la aplicación;
2. qué tecnologías utiliza;
3. cómo está organizado el frontend;
4. cómo está organizado el backend;
5. cómo se comunican frontend y backend;
6. qué convenciones debes respetar al trabajar en este proyecto;
7. qué restricciones debes considerar antes de realizar un cambio.

Indica también qué archivos del repositorio utilizaste como contexto para responder.

No realices ningún cambio.
```

Observa la respuesta de GitHub Copilot.

Comprueba si utiliza información obtenida de:

```text
README.md
.github/copilot-instructions.md
```

y del propio código del proyecto.

---

# 14. Verificar el contexto específico de UI

Ahora realizaremos una consulta relacionada específicamente con la interfaz de usuario.

No vamos a implementar ningún cambio.

Utiliza el siguiente prompt:

```text
Estoy evaluando agregar un nuevo botón "Create Task" a la interfaz.

No realices ningún cambio.

Analiza el contexto disponible en el repositorio y explícame cómo debería diseñarse ese botón para mantener la consistencia con este proyecto.

Incluye:

- color;
- espaciado;
- border radius;
- tipo de acción que representa;
- criterio para su etiqueta;
- cualquier otra convención relevante.

Indica qué archivo utilizaste como fuente para estas decisiones.
```

Observa si GitHub Copilot consulta:

```text
docs/ui-guidelines.md
```

y utiliza las reglas definidas allí.

Por ejemplo, debería poder identificar aspectos como:

- el color primario `#2563EB`;
- el uso del sistema de espaciado definido;
- `8px` de border radius para botones;
- etiquetas cortas y orientadas a una acción;
- reutilización de componentes existentes.

Esta información no fue proporcionada nuevamente en el prompt.

Forma parte del contexto persistente disponible dentro del repositorio.

---

# 15. Comprender cuándo separar el contexto

En este proyecto podríamos haber colocado toda la información dentro de:

```text
.github/copilot-instructions.md
```

Para un proyecto pequeño esto podría ser perfectamente válido.

Sin embargo, algunas partes del contexto pueden ser relevantes solamente para determinados tipos de tareas.

En este laboratorio:

```text
.github/copilot-instructions.md
```

contiene las instrucciones generales y las principales convenciones del proyecto.

Mientras que:

```text
docs/ui-guidelines.md
```

contiene información especializada que resulta especialmente relevante cuando una tarea involucra la interfaz de usuario.

Como regla práctica:

- Si es información o una instrucción que la IA debería considerar habitualmente, puede mantenerse en `copilot-instructions.md`.
- Si es información detallada y especializada que resulta especialmente relevante para determinadas tareas, puede mantenerse en `docs/` y ser referenciada desde las instrucciones.

Separar información no es obligatorio.

El objetivo es mantener el contexto organizado y proporcionar al agente la información relevante cuando la necesita.

---

# 16. Qué hemos aprendido

En este laboratorio:

- Trabajamos sobre una aplicación full stack existente sin modificar su funcionalidad.
- Utilizamos GitHub Copilot para analizar un repositorio completo.
- Documentamos el proyecto mediante `README.md`.
- Creamos instrucciones persistentes mediante `.github/copilot-instructions.md`.
- Utilizamos un template para generar una primera versión de las instrucciones a partir del proyecto real.
- Revisamos las instrucciones generadas para evitar información inventada o incorrecta.
- Incorporamos `docs/ui-guidelines.md` como una fuente adicional de contexto especializado.
- Referenciamos documentación específica desde las instrucciones principales.
- Observamos que no todo el contexto tiene que estar concentrado en un único archivo.
- Diferenciamos entre contexto general y contexto especializado.
- Verificamos que GitHub Copilot puede combinar información del código, README, instrucciones y documentación del proyecto.
- Comprobamos el uso del contexto realizando preguntas sin modificar el código.
- Observamos cómo el contexto persistente permite evitar repetir las mismas características, convenciones y restricciones en cada prompt.

El objetivo de Context Engineering no es simplemente escribir prompts más largos.

Consiste en preparar y organizar el contexto que necesita el agente para comprender correctamente el proyecto y trabajar de manera consistente dentro de él.

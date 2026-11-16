# Laboratorio: Desarrollo en Python con y sin una Agent Skill en OpenAI Codex CLI

## Objetivo

En este laboratorio crearás un proyecto de Python desde cero y utilizarás **OpenAI Codex desde la línea de comandos** para implementar funciones sencillas.

Primero crearás una función utilizando solamente un prompt.

Después incorporarás una **Agent Skill** que define prácticas reutilizables para desarrollar código Python y utilizarás Codex para crear una nueva función teniendo esa Skill disponible.

El objetivo es observar cómo cambia la forma de trabajar de Codex cuando dispone de instrucciones y procedimientos reutilizables.

---

# 1. Requisitos

Para realizar el laboratorio necesitarás:

- Un editor de código, como Visual Studio Code.
- Python 3 instalado.
- Node.js y npm instalados.
- OpenAI Codex CLI instalado.
- Acceso a un modelo compatible con Codex.
- Una terminal, como PowerShell, Windows Terminal, CMD, Bash o Zsh.

Puedes instalar Codex CLI mediante npm:

```bash
npm install -g @openai/codex
```

Comprueba la instalación:

```bash
codex --version
```

> Dependiendo de la configuración utilizada, Codex puede autenticarse mediante una cuenta de OpenAI o utilizar una configuración compatible con otro proveedor.

---

# 2. Crear el proyecto

Crea una carpeta llamada:

```text
python-skills-lab
```

Abre una terminal y ejecuta:

```bash
mkdir python-skills-lab
cd python-skills-lab
```

También puedes crear y abrir la carpeta utilizando Visual Studio Code.

Desde la terminal, puedes abrir el proyecto con:

```bash
code .
```

---

# 3. Crear el archivo inicial

En la raíz del proyecto crea un archivo llamado:

```text
statistics_utils.py
```

Déjalo vacío.

La estructura inicial del proyecto será:

```text
python-skills-lab/
└── statistics_utils.py
```

En PowerShell puedes crear el archivo con:

```powershell
New-Item statistics_utils.py -ItemType File
```

En Bash puedes utilizar:

```bash
touch statistics_utils.py
```

También puedes crear el archivo directamente desde Visual Studio Code.

---

# 4. Iniciar Codex CLI

Asegúrate de que la terminal se encuentre en la raíz del proyecto:

```text
python-skills-lab
```

Inicia Codex:

```bash
codex
```

Codex utilizará el directorio actual como espacio de trabajo.

Durante el laboratorio presta atención no solamente al código generado, sino también a:

- los archivos que Codex consulta;
- los archivos que modifica;
- las instrucciones que descubre;
- las Skills que utiliza;
- las decisiones que toma;
- las explicaciones que proporciona.

---

# 5. Crear una función sin una Agent Skill personalizada

En este momento el proyecto no contiene ninguna Agent Skill personalizada.

Copia y pega el siguiente prompt en Codex:

```text
Crea una función de Python llamada calculate_average en statistics_utils.py.

La función debe recibir una lista de números y devolver su promedio aritmético.
```

Permite que Codex modifique:

```text
statistics_utils.py
```

Codex puede mostrar un resumen de los cambios o solicitar autorización antes de modificar el archivo, dependiendo de la configuración y del modo de aprobación utilizado.

---

# 6. Observar la primera implementación

Abre:

```text
statistics_utils.py
```

Observa cómo Codex implementó:

```python
calculate_average(...)
```

Presta atención a las decisiones que tomó más allá de lo solicitado explícitamente en el prompt.

Por ejemplo, observa si agregó elementos como:

- type hints;
- una docstring;
- validaciones;
- manejo de una lista vacía;
- manejo de errores;
- nombres descriptivos;
- otras prácticas de desarrollo Python.

El objetivo en este momento es simplemente observar cómo resolvió la tarea Codex antes de incorporar nuestra Agent Skill.

---

# 7. Introducción a las Agent Skills en Codex

Una **Agent Skill** permite proporcionar a Codex conocimientos, instrucciones y procedimientos reutilizables.

Una Skill puede definir, por ejemplo:

- cómo trabajar con un lenguaje de programación;
- qué convenciones utilizar;
- cómo documentar el código;
- cómo manejar errores;
- qué casos límite considerar;
- qué procedimiento seguir;
- qué recursos consultar;
- qué scripts ejecutar;
- qué verificaciones realizar antes de completar una tarea.

Cada Skill tiene su propia carpeta e incluye como punto de entrada un archivo llamado:

```text
SKILL.md
```

Codex puede descubrir Skills disponibles y utilizarlas cuando resultan relevantes para una tarea.

---

# 8. Ubicación de las Skills en Codex

Codex puede trabajar con Skills almacenadas en diferentes ámbitos.

Para una Skill específica del proyecto utilizaremos:

```text
.agents/
└── skills/
    └── python-development/
        └── SKILL.md
```

La estructura completa del proyecto será:

```text
python-skills-lab/
├── .agents/
│   └── skills/
│       └── python-development/
│           └── SKILL.md
└── statistics_utils.py
```

Una Skill almacenada dentro del proyecto puede:

- formar parte del repositorio;
- compartirse con otros integrantes del equipo;
- utilizarse únicamente cuando Codex trabaja en ese proyecto;
- evolucionar junto con el código;
- proporcionar procedimientos consistentes para tareas relacionadas.

Codex también puede disponer de Skills instaladas para el usuario en su directorio de configuración, pero en este laboratorio utilizaremos una Skill almacenada directamente dentro del proyecto.

---

# 9. Sintaxis de una Agent Skill

El archivo `SKILL.md` comienza con un bloque de metadatos YAML.

Por ejemplo:

```markdown
---
name: python-development
description: Use this skill when creating, reviewing, debugging, or modifying Python code.
---
```

Después del bloque de metadatos se escriben las instrucciones utilizando Markdown.

Por ejemplo:

```markdown
# Python Development

Follow these practices when working with Python code:

1. Follow PEP 8 conventions.
2. Use type hints.
3. Add docstrings.
```

Por lo tanto, la estructura básica de `SKILL.md` es:

```markdown
---
name: skill-name
description: Describe what the skill does and when the agent should use it.
---

# Skill title

Instructions, procedures, conventions, examples, and references required by the agent.
```

## `name`

El campo `name` identifica la Skill.

Por ejemplo:

```yaml
name: python-development
```

Conviene utilizar:

- letras minúsculas;
- palabras separadas mediante guiones;
- nombres breves y descriptivos.

## `description`

El campo `description` describe qué hace la Skill y cuándo resulta relevante utilizarla.

Por ejemplo:

```yaml
description: Use this skill when creating, reviewing, debugging, or modifying Python functions, modules, and scripts.
```

La descripción es especialmente importante porque ayuda a Codex a descubrir la Skill y determinar si resulta relevante para la tarea actual.

Después del bloque YAML se escriben en Markdown las instrucciones y procedimientos reutilizables que proporciona la Skill.

---

# 10. Documentación oficial

Consulta la documentación oficial de OpenAI sobre Skills en Codex:

```text
https://developers.openai.com/codex/skills
```

Documentación general de Codex:

```text
https://developers.openai.com/codex
```

Repositorio oficial de Codex CLI:

```text
https://github.com/openai/codex
```

La documentación de Codex describe conceptos como:

- qué son las Agent Skills;
- dónde se almacenan;
- cómo se descubren;
- cómo se estructura una Skill;
- la sintaxis de `SKILL.md`;
- los metadatos YAML;
- las instrucciones y recursos adicionales;
- las Skills disponibles para un proyecto;
- las Skills instaladas para el usuario;
- la creación y la instalación de Skills.

---

# 11. Crear la Agent Skill mediante un prompt

En lugar de crear manualmente cada carpeta, vamos a pedirle a Codex que cree la Skill dentro del proyecto.

Copia y pega el siguiente prompt:

```text
Utiliza la Skill $skill-creator para crear una nueva Agent Skill para este proyecto.

Requisitos:

1. La Skill debe llamarse python-development.
2. Debe almacenarse en .agents/skills/python-development.
3. Debe utilizar un archivo SKILL.md como punto de entrada.
4. Debe aplicarse cuando se creen, revisen, depuren o modifiquen funciones, módulos y scripts de Python.
5. No debe incluir scripts, assets ni archivos de referencia adicionales.
6. No modifiques statistics_utils.py.
7. Antes de crearla, indica brevemente qué archivos vas a crear.
8. Después de crearla, muestra la ruta de la Skill y resume su propósito.

Utiliza exactamente el contenido proporcionado a continuación para SKILL.md:

---
name: python-development
description: Use this skill when creating, reviewing, debugging, or modifying Python functions, modules, and scripts.
---

# Python Development

Follow these practices whenever you create or modify Python code.

## Code quality

1. Follow PEP 8 conventions.
2. Use descriptive names for functions, variables, and parameters.
3. Add type hints to function parameters and return values.
4. Add concise docstrings to public functions.
5. Keep each function focused on a single responsibility.
6. Prefer simple and readable implementations.
7. Use the Python standard library when it provides an appropriate solution.
8. Avoid unnecessary external dependencies.
9. Avoid duplicating existing logic.
10. Add comments only when they explain a decision that is not evident from the code.

## Validation and error handling

1. Identify relevant edge cases before implementation.
2. Validate inputs when appropriate.
3. Define the behavior for empty collections.
4. Raise an appropriate built-in exception when an input cannot be processed.
5. Include clear and useful error messages.
6. Consider negative numbers, repeated values, decimal values, and large inputs when relevant.
7. Preserve the original input unless the task explicitly requires modifying it.

## Completion

Before completing the task:

1. Review the implementation against these instructions.
2. Verify that the requested functionality is complete.
3. Report which instructions from this skill were applied.
4. Report any assumptions made during the implementation.
```

Permite que Codex cree la estructura de la Skill.

> Si `$skill-creator` no estuviera disponible en la instalación utilizada, Codex puede crear directamente la carpeta y el archivo solicitados. El resultado importante para este laboratorio es que exista `.agents/skills/python-development/SKILL.md`.

---

# 12. Revisar la Skill creada

Comprueba que Codex haya creado la siguiente estructura:

```text
.agents/
└── skills/
    └── python-development/
        └── SKILL.md
```

La estructura completa del proyecto debe ser:

```text
python-skills-lab/
├── .agents/
│   └── skills/
│       └── python-development/
│           └── SKILL.md
└── statistics_utils.py
```

Abre:

```text
.agents/skills/python-development/SKILL.md
```

Comprueba que contenga:

- el bloque YAML;
- el nombre `python-development`;
- una descripción que indique cuándo utilizar la Skill;
- las instrucciones de calidad de código;
- las instrucciones de validación y manejo de errores;
- las instrucciones que Codex debe seguir antes de completar una tarea.

---

# 13. Analizar las Agent Skills disponibles

Ahora vamos a pedirle a Codex que analice el proyecto y determine qué Agent Skills tiene disponibles.

Copia y pega el siguiente prompt:

```text
Analiza este proyecto y las Agent Skills disponibles.

Antes de modificar cualquier archivo:

1. Indica qué Agent Skills encontraste.
2. Muestra la ruta de cada Skill.
3. Explica brevemente para qué sirve cada una.
4. Indica cuáles son relevantes para trabajar con código Python en este proyecto.
5. Resume las principales instrucciones que deberías tener en cuenta.
6. Distingue entre las Skills proporcionadas por Codex y las Skills específicas de este proyecto.

No modifiques ningún archivo.
```

Revisa la respuesta de Codex.

Observa si identifica:

```text
python-development
```

y si la relaciona con:

```text
.agents/skills/python-development/SKILL.md
```

Presta atención a cómo interpreta el propósito de la Skill y cuáles de sus instrucciones considera relevantes.

---

# 14. Crear una función utilizando la Agent Skill

Ahora utilizaremos Codex para implementar una nueva funcionalidad teniendo disponible la Skill.

Copia y pega:

```text
Analiza las Agent Skills disponibles en este proyecto y utiliza las que sean relevantes para esta tarea.

Utiliza explícitamente $python-development.

Crea una función de Python llamada calculate_median en statistics_utils.py.

La función debe recibir una lista de números y devolver la mediana.

Aplica las instrucciones de la Agent Skill python-development.

Cuando termines, indica:

1. Qué Skill utilizaste.
2. Dónde se encuentra esa Skill.
3. Qué instrucciones de la Skill aplicaste.
4. Cómo se reflejan esas instrucciones en el código generado.
5. Qué casos límite consideraste.
6. Qué supuestos realizaste.

No crees archivos adicionales.
No modifiques la función calculate_average.
```

Permite que Codex modifique:

```text
statistics_utils.py
```

La referencia explícita:

```text
$python-development
```

indica directamente la Skill que Codex debe utilizar.

La descripción incluida en los metadatos de la Skill también permite que Codex determine automáticamente que resulta relevante para una tarea relacionada con Python.

---

# 15. Observar el resultado

Abre:

```text
statistics_utils.py
```

Observa cómo Codex implementó:

```python
calculate_median(...)
```

Presta atención a las prácticas que aparecen en el código y relaciónalas con las instrucciones definidas en:

```text
.agents/skills/python-development/SKILL.md
```

Por ejemplo, observa elementos como:

- type hints;
- docstrings;
- nombres descriptivos;
- validación de entradas;
- comportamiento ante una lista vacía;
- manejo de errores;
- consideración de casos límite;
- conservación de la lista original;
- utilización de la biblioteca estándar cuando corresponda;
- ausencia de dependencias externas innecesarias.

Revisa también la respuesta de Codex.

Observa:

- qué Skill indica haber utilizado;
- qué instrucciones explica que fueron aplicadas;
- qué casos límite identificó;
- qué suposiciones realizó;
- cómo relaciona cada decisión con la Skill.

Compara lo observado con la primera función:

```python
calculate_average(...)
```

La primera función fue creada antes de incorporar la Agent Skill personalizada.

---

# 16. Creación e instalación de Skills en Codex

En Codex, crear e instalar una Skill son operaciones relacionadas, pero diferentes.

## Crear una Skill

Crear una Skill significa generar una nueva carpeta con un archivo `SKILL.md` y, opcionalmente, recursos adicionales.

Por ejemplo:

```text
.agents/
└── skills/
    └── python-development/
        └── SKILL.md
```

Podemos pedirle a Codex que utilice:

```text
$skill-creator
```

Ejemplo:

```text
Utiliza $skill-creator para crear una Skill llamada python-development dentro de .agents/skills.
```

También podemos indicarle directamente que cree la carpeta y el archivo.

## Instalar una Skill existente

Instalar una Skill significa obtener una Skill que ya existe, normalmente desde un repositorio o catálogo, y copiarla al directorio de Skills de Codex.

Codex proporciona una Skill llamada:

```text
$skill-installer
```

Podemos pedirle que muestre las Skills disponibles para instalación:

```text
Utiliza $skill-installer para mostrar las Skills disponibles que puedo instalar.
No instales ninguna todavía.
```

También podemos pedirle que instale una Skill existente desde una fuente compatible:

```text
Utiliza $skill-installer para instalar la Skill indicada desde su repositorio.

Antes de instalarla:

1. Indica el repositorio de origen.
2. Indica qué archivos se instalarán.
3. Indica dónde quedará almacenada.
4. No modifiques los archivos del proyecto.
```

La instalación se utiliza cuando la Skill ya existe en otra ubicación.

La creación se utiliza cuando queremos definir una Skill nueva y personalizada para nuestro proyecto o equipo.

En este laboratorio creamos una Skill específica del proyecto porque queremos:

- controlar exactamente sus instrucciones;
- observar directamente su contenido;
- almacenarla junto con el proyecto;
- compartirla con el repositorio;
- comparar el comportamiento de Codex antes y después de incorporarla.

---

# 17. Invocación explícita y descubrimiento automático

Codex puede utilizar una Skill de dos maneras.

## Invocación explícita

Podemos mencionar directamente la Skill en el prompt:

```text
Utiliza $python-development para crear una función calculate_median.
```

Esta forma resulta útil cuando queremos asegurarnos de que Codex considere una Skill determinada.

## Descubrimiento automático

También podemos describir la tarea sin mencionar la Skill:

```text
Crea una función de Python llamada calculate_median en statistics_utils.py.
```

Codex puede analizar las descripciones de las Skills disponibles y determinar que:

```text
python-development
```

resulta relevante para una tarea de desarrollo en Python.

El campo:

```yaml
description
```

es fundamental para este mecanismo de descubrimiento.

Una buena descripción debe explicar:

- qué hace la Skill;
- para qué tareas resulta útil;
- cuándo debería ser utilizada.

Durante un laboratorio resulta conveniente mencionar explícitamente la Skill para que su utilización sea más visible.

En un proyecto real, Codex también puede descubrirla automáticamente cuando la descripción coincide con la tarea.

---

# 18. Lo que hemos aprendido

En este laboratorio comenzamos con un proyecto mínimo:

```text
python-skills-lab/
└── statistics_utils.py
```

Primero utilizamos Codex CLI para crear:

```python
calculate_average(...)
```

En ese momento nuestro proyecto todavía no contenía una Agent Skill personalizada.

Después incorporamos:

```text
.agents/
└── skills/
    └── python-development/
        └── SKILL.md
```

Finalmente creamos:

```python
calculate_median(...)
```

teniendo disponible la Skill `python-development`.

## Conceptos aprendidos

- **Codex CLI se ejecuta desde la carpeta del proyecto.**

  ```bash
  codex
  ```

- **Un prompt expresa una tarea concreta.**

  Por ejemplo:

  ```text
  Crea una función de Python llamada calculate_median.
  ```

- **Una Agent Skill proporciona conocimiento, instrucciones y procedimientos reutilizables.**

- **Cada Skill tiene su propia carpeta y utiliza un archivo llamado `SKILL.md`.**

- **Las Skills específicas de un proyecto pueden almacenarse en:**

  ```text
  .agents/skills/
  ```

- **`SKILL.md` combina metadatos YAML con instrucciones escritas en Markdown.**

- **El campo `name` identifica la Skill.**

- **El campo `description` ayuda a Codex a determinar cuándo la Skill resulta relevante.**

- **El contenido Markdown define las instrucciones y procedimientos reutilizables de la Skill.**

- **Una Skill puede incluir instrucciones, procedimientos, referencias, scripts y otros recursos.**

- **Una Skill puede definir prácticas generales para un lenguaje, tecnología o tipo de trabajo.**

- **Una misma Skill puede aplicarse a diferentes tareas relacionadas.**

- **Las instrucciones reutilizables pueden mantenerse en una Skill en lugar de repetirse completamente en cada prompt.**

- **Podemos pedirle a Codex que analice qué Agent Skills tiene disponibles.**

- **Codex puede determinar automáticamente qué Skills son relevantes para una tarea.**

- **También podemos invocar explícitamente una Skill mediante su nombre:**

  ```text
  $python-development
  ```

- **Podemos solicitar la creación de una Skill utilizando:**

  ```text
  $skill-creator
  ```

- **Podemos solicitar la instalación de una Skill existente utilizando:**

  ```text
  $skill-installer
  ```

- **Crear una Skill no es lo mismo que instalar una Skill.**

- **Crear una Skill genera una nueva definición adaptada a nuestro proyecto o proceso.**

- **Instalar una Skill incorpora una Skill existente desde otra fuente.**

- **Una Skill almacenada dentro del proyecto puede versionarse y compartirse mediante Git.**

- **Podemos pedirle a Codex que indique qué Skill utilizó y qué instrucciones aplicó.**

- **El código generado permite observar cómo las instrucciones proporcionadas por una Skill se reflejan en decisiones concretas de implementación.**

- **El prompt y la Agent Skill tienen responsabilidades diferentes.**

  ```text
  Prompt → ¿Qué quiero hacer?
  ```

  ```text
  Agent Skill → ¿Qué conocimiento y procedimientos reutilizables tiene disponible Codex para realizar este tipo de trabajo?
  ```

- **Separar la tarea concreta de las prácticas reutilizables permite mantener prompts más enfocados y proporcionar a Codex un contexto de trabajo consistente.**

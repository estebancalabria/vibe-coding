# Laboratorio: Desarrollo en Python con y sin una Agent Skill

## Objetivo

En este laboratorio crearás un proyecto de Python desde cero y utilizarás GitHub Copilot en modo agente para implementar funciones sencillas.

Primero crearás una función utilizando solamente un prompt.

Después incorporarás una **Agent Skill** que define prácticas reutilizables para desarrollar código Python y utilizarás GitHub Copilot para crear nuevas funciones teniendo esa Skill disponible.

El objetivo es observar cómo cambia la forma de trabajar del agente cuando dispone de instrucciones y procedimientos reutilizables.

---

# 1. Requisitos

Para realizar el laboratorio necesitarás:

- Visual Studio Code.
- Python 3 instalado.
- La extensión de Python para Visual Studio Code.
- GitHub Copilot habilitado.
- GitHub Copilot Chat.
- Acceso al modo agente de GitHub Copilot.

---

# 2. Crear el proyecto

Crea una carpeta llamada:

```text
python-skills-lab
```

Abre Visual Studio Code.

Selecciona:

```text
File > Open Folder
```

Abre la carpeta:

```text
python-skills-lab
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

---

# 4. Abrir GitHub Copilot Chat

Abre GitHub Copilot Chat en Visual Studio Code.

Selecciona:

```text
Agent
```

como modo de trabajo.

Durante el laboratorio presta atención no solamente al código generado, sino también a las decisiones que toma el agente y a las explicaciones que proporciona.

---

# 5. Crear una función sin una Agent Skill personalizada

En este momento el proyecto no contiene ninguna Agent Skill personalizada.

Copia y pega el siguiente prompt en GitHub Copilot Chat:

```text
Crea una función de Python llamada calculate_average en statistics_utils.py.

La función debe recibir una lista de números y devolver su promedio aritmético.
```

Permite que GitHub Copilot modifique:

```text
statistics_utils.py
```

---

# 6. Observar la primera implementación

Abre:

```text
statistics_utils.py
```

Observa cómo GitHub Copilot implementó:

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

El objetivo en este momento es simplemente observar cómo resolvió la tarea GitHub Copilot antes de incorporar nuestra Agent Skill.

---

# 7. Introducción a las Agent Skills

Una **Agent Skill** permite proporcionar al agente conocimientos, instrucciones y procedimientos reutilizables.

Una Skill puede definir, por ejemplo:

- cómo trabajar con un lenguaje de programación;
- qué convenciones utilizar;
- cómo documentar el código;
- cómo manejar errores;
- qué casos límite considerar;
- qué prácticas aplicar al crear o modificar código.

Estas instrucciones pueden utilizarse en diferentes tareas relacionadas.

En este laboratorio crearemos una Skill general para trabajar con código Python.

---

# 8. Estructura de una Agent Skill

Cada Skill tiene su propia carpeta.

Dentro de esa carpeta existe un archivo llamado:

```text
SKILL.md
```

Crearemos la siguiente estructura:

```text
.github/
└── skills/
    └── python-development/
        └── SKILL.md
```

La estructura completa del proyecto será:

```text
python-skills-lab/
├── .github/
│   └── skills/
│       └── python-development/
│           └── SKILL.md
└── statistics_utils.py
```

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
description: Describe when the agent should use this skill.
---

# Skill Title

Instructions, procedures, conventions, examples, and other information required by the agent.
```

## `name`

El campo `name` identifica la Skill.

Por ejemplo:

```yaml
name: python-development
```

## `description`

El campo `description` describe cuándo resulta relevante utilizar la Skill.

Por ejemplo:

```yaml
description: Use this skill when creating, reviewing, debugging, or modifying Python code.
```

La descripción ayuda al agente a determinar cuándo una Skill resulta relevante para la tarea que está realizando.

Después del bloque YAML se escriben en Markdown las instrucciones y procedimientos reutilizables que proporciona la Skill.

---

# 10. Documentación oficial

Consulta la documentación oficial de GitHub sobre Agent Skills:

https://docs.github.com/en/copilot/concepts/agents/about-agent-skills

También puedes consultar la documentación sobre creación de Agent Skills:

https://docs.github.com/en/copilot/customizing-copilot/creating-agent-skills

La documentación describe conceptos como:

- qué son las Agent Skills;
- dónde se almacenan;
- cómo se descubren;
- cómo se estructura una Skill;
- la sintaxis de `SKILL.md`;
- los metadatos YAML;
- las instrucciones y recursos que puede contener una Skill.

---

# 11. Crear la Agent Skill

Dentro del proyecto crea la siguiente estructura:

```text
.github/
└── skills/
    └── python-development/
        └── SKILL.md
```

La ruta completa del archivo será:

```text
.github/skills/python-development/SKILL.md
```

---

# 12. Definir la Skill de desarrollo Python

Abre:

```text
.github/skills/python-development/SKILL.md
```

Copia y pega exactamente el siguiente contenido:

```markdown
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

Guarda el archivo.

---

# 13. Analizar la Agent Skill con GitHub Copilot

Ahora vamos a pedirle a GitHub Copilot que analice el proyecto y determine qué Agent Skills tiene disponibles.

Copia y pega el siguiente prompt en GitHub Copilot Chat:

```text
Analiza este proyecto y las Agent Skills disponibles.

Antes de modificar cualquier archivo:

1. Indica qué Agent Skills encontraste.
2. Explica brevemente para qué sirve cada una.
3. Indica cuáles son relevantes para trabajar con código Python en este proyecto.
4. Resume las principales instrucciones que deberías tener en cuenta.

No modifiques ningún archivo.
```

Revisa la respuesta de GitHub Copilot.

Observa si identifica:

```text
python-development
```

y si relaciona la Skill con:

```text
.github/skills/python-development/SKILL.md
```

Presta atención a cómo interpreta el propósito de la Skill y cuáles de sus instrucciones considera relevantes.

---

# 14. Crear una función utilizando la Agent Skill

Ahora utilizaremos GitHub Copilot para implementar una nueva funcionalidad teniendo disponible la Skill.

Copia y pega:

```text
Analiza las Agent Skills disponibles en este proyecto y utiliza las que sean relevantes para esta tarea.

Crea una función de Python llamada calculate_median en statistics_utils.py.

La función debe recibir una lista de números y devolver la mediana.

Aplica las instrucciones de las Agent Skills relevantes.

Cuando termines, indica:

1. Qué Skill utilizaste.
2. Qué instrucciones de la Skill aplicaste.
3. Cómo se reflejan esas instrucciones en el código generado.

No crees archivos adicionales.
```

Permite que GitHub Copilot modifique:

```text
statistics_utils.py
```

---

# 15. Observar el resultado

Abre:

```text
statistics_utils.py
```

Observa cómo GitHub Copilot implementó:

```python
calculate_median(...)
```

Presta atención a las prácticas que aparecen en el código y relaciónalas con las instrucciones definidas en:

```text
.github/skills/python-development/SKILL.md
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
- utilización de la biblioteca estándar cuando corresponda.

Revisa también la respuesta de GitHub Copilot Chat.

Observa qué Skill indica haber utilizado y qué instrucciones explica que fueron aplicadas durante la implementación.

Compara lo observado con la primera función:

```python
calculate_average(...)
```

La primera función fue creada antes de incorporar nuestra Agent Skill personalizada.

---

# 16. Lo que hemos aprendido

En este laboratorio comenzamos con un proyecto mínimo:

```text
python-skills-lab/
└── statistics_utils.py
```

Primero utilizamos GitHub Copilot para crear:

```python
calculate_average(...)
```

En ese momento nuestro proyecto todavía no contenía una Agent Skill personalizada.

Después incorporamos:

```text
.github/
└── skills/
    └── python-development/
        └── SKILL.md
```

Analizamos la Skill con GitHub Copilot y finalmente creamos:

```python
calculate_median(...)
find_range(...)
```

teniendo disponible `python-development`.

## Conceptos aprendidos

- **Un prompt expresa una tarea concreta.**

  Por ejemplo:

  ```text
  Crea una función de Python llamada calculate_median.
  ```

- **Una Agent Skill proporciona conocimiento, instrucciones y procedimientos reutilizables.**

- **Cada Skill tiene su propia carpeta y utiliza un archivo llamado `SKILL.md`.**

- **`SKILL.md` combina metadatos YAML con instrucciones escritas en Markdown.**

- **El campo `name` identifica la Skill.**

- **El campo `description` ayuda al agente a determinar cuándo la Skill resulta relevante.**

- **El contenido Markdown define las instrucciones y procedimientos reutilizables de la Skill.**

- **Una Skill puede definir prácticas generales para un lenguaje, tecnología o tipo de trabajo.**

- **Una misma Skill puede aplicarse a diferentes tareas relacionadas.**

- **Las instrucciones reutilizables pueden mantenerse en una Skill en lugar de repetirse completamente en cada prompt.**

- **Podemos pedirle a GitHub Copilot que analice qué Agent Skills tiene disponibles.**

- **GitHub Copilot puede determinar qué Skills son relevantes para una tarea determinada.**

- **Podemos pedirle al agente que indique qué Skill utilizó y qué instrucciones aplicó.**

- **El código generado permite observar cómo las instrucciones proporcionadas por una Skill se reflejan en decisiones concretas de implementación.**

- **El prompt y la Agent Skill tienen responsabilidades diferentes.**

  ```text
  Prompt → ¿Qué quiero hacer?
  ```

  ```text
  Agent Skill → ¿Qué conocimiento y procedimientos reutilizables tiene disponibles el agente para realizar este tipo de trabajo?
  ```

- **Separar la tarea concreta de las prácticas reutilizables permite mantener prompts más enfocados y proporcionar al agente un contexto de trabajo consistente.**

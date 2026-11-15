# Vibe Coding Estructurado
## De una idea a una aplicación funcional con Inteligencia Artificial

**Duración:** 12 horas  
**Modalidad:** 4 clases de 3 horas  
**Enfoque:** práctico, guiado y basado en proyectos

---

## Objetivo del curso

La Inteligencia Artificial está transformando la forma de crear software. Hoy es posible describir una idea en lenguaje natural y utilizar asistentes de IA para planificar, generar código, crear interfaces, detectar errores y desarrollar funcionalidades completas.

Pero crear software con IA no consiste simplemente en escribir un prompt y esperar que todo funcione.

El objetivo de este curso es que el alumno aprenda una metodología de **Vibe Coding Estructurado** para transformar una idea en una aplicación funcional, utilizando Inteligencia Artificial durante todo el proceso de desarrollo.

A lo largo del curso se trabajará desde la definición y planificación de una solución hasta su construcción, prueba, depuración y mejora.

Además, se introducirá el trabajo con **agentes especializados**, asignando diferentes etapas del proyecto a distintos agentes con roles, instrucciones y templates específicos.

De esta manera, el alumno aprenderá a pasar de una conversación improvisada con la IA a un **proceso de desarrollo estructurado, repetible y controlado**.

---

# Programa

## Clase 1 | De la idea al proyecto

El primer paso no es generar código, sino aprender a definir correctamente qué queremos construir.

### Vamos a ver

- ¿Qué es Vibe Coding?
- Cómo cambia el desarrollo de software con la IA generativa.
- Diferencias entre desarrollo tradicional, programación asistida por IA y Vibe Coding.
- Qué puede hacer la IA y qué decisiones siguen dependiendo de nosotros.
- Cómo transformar una idea en requerimientos concretos.
- Definición del objetivo de una aplicación.
- Identificación de usuarios y funcionalidades.
- Alcance inicial y definición de un **MVP (Minimum Viable Product)**.
- Cómo dividir un proyecto en funcionalidades pequeñas.
- Cómo proporcionar contexto a un asistente de IA.
- Prompts efectivos para trabajar con código.
- Documentación inicial del proyecto.
- Creación de la estructura inicial.
- Primer prototipo de la aplicación.

### Práctica

Partiremos de una idea y construiremos conjuntamente la primera versión funcional del proyecto que evolucionará durante todo el curso.

El objetivo será comenzar a transformar una idea expresada en lenguaje natural en una especificación que pueda ser utilizada posteriormente por diferentes asistentes y agentes de IA.

---

## Clase 2 | Construcción asistida por IA

Con el proyecto definido, comenzaremos a utilizar la IA como compañero de desarrollo.

El foco estará en aprender a trabajar de manera incremental, proporcionando contexto y controlando cada modificación realizada sobre el proyecto.

### Vamos a ver

- Cómo pedirle a la IA que implemente funcionalidades.
- Prompting aplicado al desarrollo de software.
- Trabajar por tareas pequeñas e incrementales.
- Cómo pedir modificaciones sin romper funcionalidades existentes.
- Leer y entender código generado por IA.
- Archivos, carpetas y estructura básica de un proyecto.
- Frontend y lógica de aplicación.
- Formularios y validación de datos.
- Manejo del estado de una aplicación.
- Persistencia de información.
- Instalación y utilización de dependencias.
- Uso de la terminal durante el desarrollo.
- Ejecución local de una aplicación.
- Cómo mantener contexto durante una sesión de desarrollo con IA.
- Cómo documentar decisiones para que puedan ser reutilizadas por la IA.
- Construcción progresiva de una aplicación funcional.

### Práctica

Ampliaremos el proyecto incorporando nuevas funcionalidades y trabajando sobre código generado y modificado con asistencia de IA.

El alumno comenzará a documentar el contexto, las decisiones y las reglas del proyecto para evitar depender exclusivamente del historial de una conversación.

---

## Clase 3 | Git, Agents y desarrollo estructurado con IA

Hasta este punto utilizamos la IA como asistente de desarrollo.

En esta clase daremos el siguiente paso: convertir ese trabajo en un proceso más estructurado utilizando **Git, agentes especializados y templates reutilizables**.

La idea será dejar de utilizar un único asistente para todo y comenzar a separar responsabilidades.

### Vamos a ver

- Introducción al control de versiones con Git.
- Repositorios y conceptos fundamentales de Git.
- GitHub como repositorio remoto.
- Commits como puntos seguros durante el desarrollo.
- Cómo experimentar sin perder una versión funcional.
- Qué es un agente de IA.
- Diferencia entre utilizar un asistente general y trabajar con agentes especializados.
- Cómo definir el rol y la responsabilidad de un agente.
- Cómo proporcionar instrucciones permanentes a un agente.
- Cómo proporcionar contexto del proyecto.
- Separación de responsabilidades entre agentes.
- Uso de archivos y documentación como contexto.
- Creación de templates reutilizables.
- Cómo utilizar templates para estandarizar las respuestas de los agentes.
- Cómo definir entradas y resultados esperados para cada agente.
- Cómo evitar que diferentes agentes tomen decisiones contradictorias.
- Encadenamiento de tareas entre distintos agentes.
- Revisión humana entre etapas del proceso.

### Trabajaremos con agentes especializados

A partir del proyecto desarrollado durante el curso, separaremos diferentes responsabilidades entre agentes.

Por ejemplo:

#### Agent de Producto

Responsable de transformar una idea en una definición clara del producto.

Utilizará un template para generar:

- Objetivo.
- Usuarios.
- Problema que resuelve.
- Funcionalidades.
- Alcance.
- MVP.

#### Agent de Requerimientos

Recibirá la definición del producto y la transformará en requerimientos concretos.

Utilizará templates para generar:

- Requerimientos funcionales.
- Requerimientos no funcionales.
- Historias de usuario.
- Criterios de aceptación.

#### Agent de Arquitectura

Analizará los requerimientos y propondrá la estructura técnica de la solución.

Utilizará un template para definir:

- Componentes.
- Estructura del proyecto.
- Tecnologías.
- Modelo de datos.
- Dependencias.
- Decisiones técnicas.

#### Agent de Desarrollo

Recibirá tareas concretas y será responsable de implementar funcionalidades.

Trabajará utilizando:

- Requerimientos.
- Criterios de aceptación.
- Arquitectura definida.
- Reglas del proyecto.
- Templates de implementación.

#### Agent de Testing

Su responsabilidad será verificar lo desarrollado.

Utilizará templates para generar:

- Casos de prueba.
- Escenarios.
- Validaciones.
- Casos límite.
- Posibles errores.

#### Agent de Code Review

Revisará el código generado antes de aceptar los cambios.

Analizará:

- Calidad del código.
- Duplicaciones.
- Complejidad innecesaria.
- Posibles errores.
- Problemas de seguridad.
- Cumplimiento de los requerimientos.

### Flujo de trabajo

En lugar de pedirle todo a una única IA, construiremos un flujo estructurado:

**Idea → Agent de Producto → Agent de Requerimientos → Agent de Arquitectura → Agent de Desarrollo → Agent de Testing → Agent de Code Review**

Cada agente tendrá:

- Un rol específico.
- Instrucciones.
- Contexto.
- Responsabilidades.
- Límites.
- Un template de entrada.
- Un template de salida.

De esta manera, el proceso puede repetirse de forma consistente a medida que evoluciona el proyecto.

### Práctica

Tomaremos el proyecto creado durante las clases anteriores y separaremos el proceso de desarrollo entre diferentes agentes.

Crearemos instrucciones y templates para cada rol, utilizaremos Git para controlar los cambios y construiremos un flujo en el que la salida de un agente se convierta en contexto para el siguiente.

El objetivo será transformar el Vibe Coding inicial en un **workflow de desarrollo asistido por agentes**.

---

## Clase 4 | Testing, debugging y de prototipo a aplicación

Una vez construido un flujo estructurado de desarrollo, el siguiente paso será aprender a validar el resultado.

La IA puede generar código rápidamente, pero también puede introducir errores, asumir requerimientos inexistentes o modificar partes del proyecto que ya funcionaban.

En esta clase integraremos agentes, testing, debugging y revisión para convertir el prototipo inicial en una aplicación más sólida.

### Vamos a ver

- Por qué el código generado por IA puede fallar.
- Errores de sintaxis, ejecución y lógica.
- Cómo interpretar mensajes de error.
- Cómo proporcionar errores y contexto a la IA.
- Debugging asistido por IA.
- Utilización de agentes para investigar errores.
- Cómo verificar los cambios realizados por la IA.
- Pruebas funcionales asistidas por IA.
- Generación de casos de prueba.
- Validación de criterios de aceptación.
- Revisión integral de una aplicación generada con IA.
- Detectar funcionalidades incompletas.
- Mejorar la experiencia de usuario.
- Refinamiento de interfaces.
- Validaciones y manejo de errores.
- Variables de entorno.
- Manejo de claves y secretos.
- Buenas prácticas básicas de seguridad.
- Revisión y limpieza del código.
- Refactorización asistida por IA.
- Cómo solicitar mejoras sin reescribir innecesariamente la aplicación.
- Checklist antes de publicar una aplicación.
- Conceptos de build y producción.
- Introducción al despliegue.
- Documentación del proyecto con IA.
- Límites actuales del Vibe Coding.
- Cuándo confiar en la IA y cuándo detenerse y revisar.
- Cómo continuar evolucionando una aplicación después del curso.

### Práctica

Los diferentes agentes participarán en la etapa final del proyecto.

El Agent de Testing generará escenarios de prueba, el Agent de Code Review analizará la implementación y utilizaremos IA para investigar y corregir los problemas encontrados.

Finalmente revisaremos la aplicación completa y prepararemos una versión funcional del proyecto.

---

# Proyecto integrador

Durante las cuatro clases se desarrollará progresivamente un mismo proyecto.

El alumno recorrerá un proceso completo:

**Idea → Producto → Requerimientos → Arquitectura → Desarrollo → Testing → Code Review → Debugging → Mejora → Publicación**

Inicialmente estas tareas se realizarán de forma interactiva con un asistente de IA.

A medida que avance el curso, el proceso se irá estructurando mediante **agentes especializados, documentación y templates reutilizables**.

El objetivo no será solamente terminar una aplicación, sino construir una metodología que pueda reutilizarse en futuros proyectos.

---

# Metodología

El curso tendrá un enfoque **eminentemente práctico**.

No se trabajará con ejercicios aislados de programación. Durante las cuatro clases se desarrollará progresivamente un mismo proyecto, utilizando asistentes y agentes de Inteligencia Artificial como parte del flujo real de trabajo.

La metodología evolucionará durante el curso.

Comenzaremos con un ciclo sencillo:

**Definir → Pedir → Generar → Ejecutar → Verificar → Corregir**

Y progresivamente lo transformaremos en un proceso estructurado:

**Definir → Documentar → Delegar → Implementar → Verificar → Revisar → Mejorar**

El docente realizará demostraciones en vivo y los alumnos reproducirán y adaptarán las mismas técnicas en sus propios proyectos.

Se priorizará especialmente aprender a:

- Describir correctamente lo que queremos construir.
- Dividir problemas grandes en tareas manejables.
- Proporcionar contexto relevante a la IA.
- Convertir conversaciones en documentación reutilizable.
- Definir agentes con responsabilidades específicas.
- Crear instrucciones claras para cada agente.
- Utilizar templates para estandarizar resultados.
- Coordinar el trabajo entre diferentes agentes.
- Evaluar el código propuesto.
- Detectar y resolver errores.
- Utilizar Git para mantener el control del proyecto.
- Iterar sin destruir lo que ya funciona.
- Utilizar IA con criterio y no simplemente aceptar sus respuestas.

---

# ¿A quién está dirigido?

Este curso está pensado para personas que quieren comenzar a **crear aplicaciones utilizando Inteligencia Artificial como asistente**, incluso si no cuentan con una formación profunda en programación.

También resulta especialmente útil para:

- Profesionales IT.
- Analistas funcionales.
- Usuarios técnicos.
- Emprendedores.
- Docentes y estudiantes.
- Personas que experimentan con herramientas de IA para crear software.
- Desarrolladores que quieren incorporar asistentes y agentes de IA a sus flujos de trabajo.

No es necesario ser un desarrollador profesional, pero sí tener **curiosidad tecnológica, ganas de experimentar y disposición para entender qué está haciendo la IA**.

---

# Al finalizar el curso

El alumno habrá recorrido el ciclo completo de creación de una aplicación asistida por IA y contará con una metodología reutilizable para nuevos proyectos.

Será capaz de:

- Transformar una idea en un proyecto abordable.
- Definir un MVP.
- Convertir una idea en requerimientos estructurados.
- Utilizar IA para generar y modificar código.
- Trabajar iterativamente sobre una aplicación.
- Comprender la estructura general de un proyecto.
- Ejecutar y probar aplicaciones.
- Utilizar Git y GitHub para controlar cambios.
- Definir agentes especializados para diferentes etapas del desarrollo.
- Crear instrucciones para agentes.
- Crear y reutilizar templates.
- Utilizar documentación como contexto para la IA.
- Coordinar diferentes agentes dentro de un flujo de trabajo.
- Generar casos de prueba con IA.
- Diagnosticar errores con ayuda de IA.
- Revisar y mejorar código generado.
- Aplicar prácticas básicas de seguridad.
- Llevar un prototipo hasta una aplicación funcional.

---

## Idea central

> **Vibe Coding no significa pedirle a la IA que haga todo. Significa estructurar el contexto, las instrucciones y el proceso para que diferentes agentes de IA puedan colaborar en la construcción de software de manera controlada y repetible.**

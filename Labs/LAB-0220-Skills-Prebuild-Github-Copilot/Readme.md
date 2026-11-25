# Laboratorio: Arte generativo con la Agent Skill `algorithmic-art` y GitHub Copilot

**Duración estimada:** 20 minutos
**Resultado:** un visor interactivo en HTML con arte generativo animado (p5.js), creado por Copilot usando una Agent Skill.

## Requisitos previos

- Visual Studio Code con las extensiones **GitHub Copilot** y **GitHub Copilot Chat**, con sesión iniciada.
- Git instalado.
- Un navegador.
- Conexión a Internet (el visor carga p5.js desde un CDN).

## Paso 1: Crear el proyecto vacío

1. [WINDOWS] Abrí **PowerShell** y ejecutá:

```powershell
mkdir generative-art-demo
cd generative-art-demo
git init
mkdir .github\skills
```

2. Abrí la carpeta en VS Code:

```powershell
code .
```

## Paso 2: Descargar la Skill

1. En la terminal, cloná el repositorio de ejemplos de Anthropic a una carpeta temporal:

```powershell
git clone https://github.com/anthropics/skills.git $env:TEMP\anthropic-skills
```

2. Copiá **la carpeta completa** de la Skill a tu proyecto:

```powershell
Copy-Item -Recurse $env:TEMP\anthropic-skills\skills\algorithmic-art .\.github\skills\algorithmic-art
```

> Hay que copiar la carpeta entera y no solo `SKILL.md`. La Skill le indica al agente que lea `templates/viewer.html` antes de generar el HTML, y sin esa plantilla el resultado se degrada.

## Paso 3: Verificar la estructura

1. [TAB] En el **Explorer** de VS Code, confirmá que tengas esta estructura:

```text
generative-art-demo/
└── .github/
    └── skills/
        └── algorithmic-art/
            ├── SKILL.md
            ├── LICENSE.txt
            └── templates/
                ├── viewer.html
                └── (archivo JS de plantilla)
```

2. Abrí `SKILL.md` y revisá el encabezado YAML. Tiene que mostrar `name: algorithmic-art` y un campo `description`. Copilot usa esa descripción para decidir cuándo cargar la Skill.

## Paso 4: Recargar VS Code

1. [MENU] Presioná **Ctrl+Shift+P** y ejecutá **Developer: Reload Window**.
2. Si en el Paso 6 Copilot no detecta la Skill, [MENU] abrí **File > Preferences > Settings**, buscá `skills` y verificá que el soporte de Agent Skills esté habilitado. Esta opción puede variar según tu versión de VS Code.

## Paso 5: Abrir Copilot Chat en modo Agent

1. [TAB] Abrí el panel de **Copilot Chat** (Ctrl+Alt+I).
2. En el selector de modo, elegí **Agent**. Este modo es necesario para que Copilot pueda crear archivos en el proyecto.

## Paso 6: Ejecutar la Skill

1. Escribí el siguiente prompt en el chat:

```text
Using the algorithmic-art skill, create generative art based on flow fields
and thousands of particles. Theme: ocean currents at dusk. Save the files
inside an "art" folder in the project.
```

2. Copilot debería trabajar en dos fases:
   - **Fase 1:** escribe una "filosofía algorítmica" en un archivo `.md` (un manifiesto de 4 a 6 párrafos del movimiento estético).
   - **Fase 2:** genera un visor `.html` y un `.js` con el algoritmo, partiendo de `templates/viewer.html`.
3. [DIALOG] Si Copilot pide confirmación para crear archivos o ejecutar comandos, aceptá.

> Si Copilot no usó la Skill por su cuenta, probá invocarla de forma explícita escribiendo `/algorithmic-art` al inicio del prompt.

## Paso 7: Ver el resultado

1. [TAB] En el Explorer, abrí la carpeta `art` y hacé clic derecho sobre el archivo `.html`.
2. [MENU] Elegí **Reveal in File Explorer**.
3. [BROWSER] Abrí el archivo con doble clic en tu navegador.
4. Verificá que veas:
   - Partículas animadas siguiendo un campo de flujo.
   - Una barra lateral con **Seed**, **Parameters** y **Actions**.

## Paso 8: Explorar la parte interactiva

1. Cambiá la **Seed** y observá cómo la misma lógica produce una composición distinta.
2. Mové los sliders de parámetros (cantidad de partículas, escala del ruido, etc.) y mirá el efecto en tiempo real.
3. Probá las opciones de **Actions** (por ejemplo, regenerar o guardar la imagen).

## Paso 9: Iterar con Copilot

1. Volvé al chat y pedí un cambio concreto:

```text
Change the color palette to warm sunset tones and add a slider to control
particle trail length.
```

2. [BROWSER] Recargá el `.html` en el navegador (F5) y comprobá que el nuevo control aparece.

## Paso 10: Registrar el trabajo en Git

```powershell
git add .
git commit -m "Add algorithmic-art skill and generated flow field artwork"
```

## Validación del laboratorio

| Verificación | Resultado esperado |
|---|---|
| La carpeta de la Skill incluye `templates/` | Sí |
| Copilot generó un `.md` con la filosofía | Sí |
| El `.html` abre en el navegador y anima partículas | Sí |
| Cambiar la Seed produce una composición distinta | Sí |
| El slider agregado en el Paso 9 funciona | Sí |

## Problemas frecuentes

- **Copilot no menciona ni usa la Skill:** verificá que la ruta sea exactamente `.github/skills/algorithmic-art/SKILL.md`, recargá la ventana y probá con `/algorithmic-art`.
- **El HTML abre en blanco:** abrí las herramientas de desarrollador del navegador (F12). Si falla la carga de p5.js, revisá tu conexión, porque se descarga desde un CDN.
- **El visor no tiene la barra lateral esperada:** es probable que Copilot haya generado el HTML desde cero en lugar de usar la plantilla. Pedile:

```text
Rebuild the viewer starting from templates/viewer.html
```

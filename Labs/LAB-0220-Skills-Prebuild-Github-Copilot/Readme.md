# Laboratorio: Arte generativo con la Agent Skill `algorithmic-art` y GitHub Copilot

**Duración estimada:** 20 minutos
**Resultado:** un visor interactivo en HTML con arte generativo animado (p5.js), creado por Copilot usando una Agent Skill.

## Requisitos previos

- Visual Studio Code con las extensiones **GitHub Copilot** y **GitHub Copilot Chat**, con sesión iniciada.
- Git instalado.
- Un navegador.
- Conexión a Internet (el visor carga p5.js desde un CDN).

## Paso 1: Crear el proyecto vacío

1. [WINDOWS] Abrí **CMD** o **PowerShell** y ejecutá:

```bat
mkdir C:\Temp\generative-art-demo
cd C:\Temp\generative-art-demo
mkdir .github\skills
```

2. Abrí la carpeta en VS Code:

```bat
code .
```

## Paso 2: Clonar el repositorio de Skills

1. En la terminal, cloná el repositorio de ejemplos de Anthropic en una carpeta conocida, fuera del proyecto:

```bat
git clone https://github.com/anthropics/skills.git C:\Temp\anthropic-skills
```

2. Verificá que la Skill esté en el repositorio clonado:

```bat
dir C:\Temp\anthropic-skills\skills\algorithmic-art
```

## Paso 3: Copiar la Skill al proyecto

1. Asegurate de estar parado en la carpeta del proyecto (`C:\Temp\generative-art-demo`) y copiá **la carpeta completa** de la Skill:

```bat
xcopy /E /I "C:\Temp\anthropic-skills\skills\algorithmic-art" ".github\skills\algorithmic-art"
```

> Hay que copiar la carpeta entera y no solo `SKILL.md`. La Skill le indica al agente que lea `templates/viewer.html` antes de generar el HTML, y sin esa plantilla el resultado se degrada.

## Paso 4: Verificar la estructura

1. En la terminal, listá el contenido copiado:

```bat
tree /F .github\skills
```

2. [TAB] En el **Explorer** de VS Code, confirmá que tengas esta estructura:

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

3. Abrí `SKILL.md` y revisá el encabezado YAML. Tiene que mostrar `name: algorithmic-art` y un campo `description`. Copilot usa esa descripción para decidir cuándo cargar la Skill.

## Paso 5: Recargar VS Code

1. [MENU] Presioná **Ctrl+Shift+P** y ejecutá **Developer: Reload Window**.
2. Si en el Paso 7 Copilot no detecta la Skill, [MENU] abrí **File > Preferences > Settings**, buscá `skills` y verificá que el soporte de Agent Skills esté habilitado. Esta opción puede variar según tu versión de VS Code.

## Paso 6: Abrir Copilot Chat en modo Agent

1. [TAB] Abrí el panel de **Copilot Chat** (Ctrl+Alt+I).
2. En el selector de modo, elegí **Agent**. Este modo es necesario para que Copilot pueda crear archivos en el proyecto.

## Paso 7: Ejecutar la Skill

1. Escribí el siguiente prompt en el chat:

```text
Usando la skill algorithmic-art, creá arte generativo basado en campos de flujo
y miles de partículas. Temática: corrientes oceánicas al atardecer. Guardá los
archivos dentro de una carpeta "art" en el proyecto.
```

2. Copilot debería trabajar en dos fases:
   - **Fase 1:** escribe una "filosofía algorítmica" en un archivo `.md` (un manifiesto de 4 a 6 párrafos del movimiento estético).
   - **Fase 2:** genera un visor `.html` y un `.js` con el algoritmo, partiendo de `templates/viewer.html`.
3. [DIALOG] Si Copilot pide confirmación para crear archivos o ejecutar comandos, aceptá.

> Si Copilot no usó la Skill por su cuenta, probá invocarla de forma explícita escribiendo `/algorithmic-art` al inicio del prompt.

## Paso 8: Ver el resultado

1. [TAB] En el Explorer, abrí la carpeta `art` y hacé clic derecho sobre el archivo `.html`.
2. [MENU] Elegí **Reveal in File Explorer**.
3. [BROWSER] Abrí el archivo con doble clic en tu navegador.
4. Verificá que veas:
   - Partículas animadas siguiendo un campo de flujo.
   - Una barra lateral con **Seed**, **Parameters** y **Actions**.

## Paso 9: Explorar la parte interactiva

1. Cambiá la **Seed** y observá cómo la misma lógica produce una composición distinta.
2. Mové los sliders de parámetros (cantidad de partículas, escala del ruido, etc.) y mirá el efecto en tiempo real.
3. Probá las opciones de **Actions** (por ejemplo, regenerar o guardar la imagen).

## Paso 10: Iterar con Copilot

1. Volvé al chat y pedí un cambio concreto:

```text
Cambiá la paleta de colores a tonos cálidos de atardecer y agregá un slider
para controlar el largo de la estela de las partículas.
```

2. [BROWSER] Recargá el `.html` en el navegador (F5) y comprobá que el nuevo control aparece.

## Validación del laboratorio

| Verificación | Resultado esperado |
|---|---|
| La carpeta de la Skill incluye `templates/` | Sí |
| Copilot generó un `.md` con la filosofía | Sí |
| El `.html` abre en el navegador y anima partículas | Sí |
| Cambiar la Seed produce una composición distinta | Sí |
| El slider agregado en el Paso 10 funciona | Sí |

## Problemas frecuentes

- **`git clone` dice que la carpeta ya existe:** borrá `C:\Temp\anthropic-skills` o ejecutá `git pull` dentro de esa carpeta para actualizarla.
- **Copilot no menciona ni usa la Skill:** verificá que la ruta sea exactamente `.github/skills/algorithmic-art/SKILL.md`, recargá la ventana y probá con `/algorithmic-art`.
- **El HTML abre en blanco:** abrí las herramientas de desarrollador del navegador (F12). Si falla la carga de p5.js, revisá tu conexión, porque se descarga desde un CDN.
- **El visor no tiene la barra lateral esperada:** es probable que Copilot haya generado el HTML desde cero en lugar de usar la plantilla. Pedile:

```text
Reconstruí el visor partiendo de templates/viewer.html
```

# Investigación: Git Branching

## Índice

1. [¿Qué es una rama en Git?](#1-qué-es-una-rama-en-git)
2. [¿Qué diferencia hay entre branch y fork?](#2-qué-diferencia-hay-entre-branch-y-fork)
3. [¿Qué es `main` y por qué se protege?](#3-qué-es-main-y-por-qué-se-protege)
4. [¿Qué es un commit y por qué es importante?](#4-qué-es-un-commit-y-por-qué-es-importante)
5. [¿Qué es push y qué relación tiene con GitHub?](#5-qué-es-push-y-qué-relación-tiene-con-github)
6. [¿Qué es un Pull Request?](#6-qué-es-un-pull-request)
7. [¿Qué es merge y qué podría salir mal?](#7-qué-es-merge-y-qué-podría-salir-mal)
8. [Buenas prácticas al trabajar con ramas](#8-buenas-prácticas-al-trabajar-con-ramas)

---

## 1. ¿Qué es una rama en Git?

📌 **¿Qué es una branch?**
Una rama (branch) en Git es una línea de trabajo independiente donde puedes hacer cambios sin afectar el resto del proyecto.

🎯 **¿Para qué sirve?**
Permite trabajar en tareas separadas sin mezclar el código, manteniendo el proyecto ordenado.

⚠️ **¿Qué problema resuelve?**
Evita que errores o cambios incompletos afecten la versión principal mientras se desarrolla algo nuevo.

🚫 **¿Por qué no se trabaja siempre en `main`?**
Porque `main` debe mantenerse estable. Cualquier error que se suba ahí afecta a todo el equipo de inmediato.

💡 **Ejemplo**
Tienes un sitio web funcionando en `main`. Quieres agregar un formulario de contacto.
- Creas una rama llamada `feature-formulario`
- Trabajas ahí sin tocar `main`
- Si algo falla, el proyecto principal no se ve afectado
- Cuando está listo, unes la rama a `main`

✅ **Conclusión**
Las ramas permiten trabajar de forma segura y ordenada. Son el mecanismo principal para que un equipo pueda desarrollar en paralelo sin pisarse el trabajo.

---

## 2. ¿Qué diferencia hay entre branch y fork?

📌 **¿Qué es una branch?**
Una rama que vive dentro del mismo repositorio. Se usa para separar tareas dentro de un proyecto al que ya tienes acceso.

📌 **¿Qué es un fork?**
Una copia completa de un repositorio que se guarda en tu propia cuenta de GitHub. El original no se toca.

🔍 **¿Cuándo se usa cada uno?**
- **Branch** → cuando trabajas en tu propio proyecto o en un equipo con acceso directo al repositorio.
- **Fork** → cuando quieres contribuir a un proyecto ajeno al que no tienes permiso de escritura.

🌐 **¿Por qué GitHub usa forks para proyectos ajenos?**
Porque no es seguro dar acceso de escritura a cualquiera. El fork permite proponer cambios sin arriesgar el proyecto original. El dueño decide si los acepta.

💡 **Ejemplo**
Encuentras un proyecto open source en GitHub con un error. No eres parte del equipo, así que:
- Haces fork → tienes tu propia copia
- Corriges el error en una rama dentro de tu fork
- Propones los cambios al dueño con un Pull Request

✅ **Conclusión**
Branch y fork no son lo mismo. La branch es un desvío dentro del mismo proyecto; el fork es llevarse una copia a tu cuenta. Cada uno responde a una situación distinta de colaboración.

---

## 3. ¿Qué es `main` y por qué se protege?

📌 **¿Qué representa `main`?**
Es la rama principal del proyecto. Contiene la versión oficial, estable y lista. Si el proyecto fuera un producto, `main` sería lo que está disponible para los usuarios.

🛡️ **¿Qué significa protegerla?**
En GitHub se puede configurar para que nadie pueda subir cambios directamente a `main`. Todo cambio debe pasar por una rama y ser aprobado mediante un Pull Request.

🚫 **¿Por qué no hacer cambios directos ahí?**
Porque no hay red de seguridad. En una rama puedes equivocarte y descartar todo. En `main`, el error queda expuesto para todo el equipo al instante.

⚠️ **¿Por qué mantenerla estable?**
Todo el equipo parte de `main` para crear nuevas ramas. Si `main` tiene errores, los tiene todo el proyecto.

💡 **Ejemplo**
Un desarrollador, con apuro, sube un cambio directo a `main` sin revisar. El sitio se cae. Todo el equipo se ve afectado. Si hubiera usado una rama y un Pull Request, alguien habría detectado el error antes.

✅ **Conclusión**
`main` es la versión oficial del proyecto y debe estar siempre en buen estado. Protegerla obliga al equipo a revisar antes de incorporar cualquier cambio.

---

## 4. ¿Qué es un commit y por qué es importante?

📌 **¿Qué es un commit?**
Un commit es una fotografía guardada del estado del proyecto en un momento específico. Registra qué cambió, quién lo hizo y cuándo, junto a un mensaje descriptivo.

🎯 **¿Para qué sirve?**
Permite llevar un historial detallado del proyecto y volver a cualquier punto anterior si algo sale mal.

✂️ **¿Por qué hacer commits pequeños?**
Porque son más fáciles de revisar y de entender. Si algo falla, es mucho más sencillo identificar cuál cambio específico introdujo el problema.

📖 **¿Cómo ayudan a entender la historia del proyecto?**
El historial de commits funciona como una bitácora. Cualquier persona puede leerlo y entender cómo evolucionó el proyecto paso a paso.

💡 **Ejemplo**
- ❌ Commit malo: `"cambios varios"`
- ✅ Commit bueno: `"feat: agregar validación de correo en formulario de registro"`

El segundo le dice exactamente a cualquier compañero qué se hizo y dónde.

✅ **Conclusión**
Un commit bien hecho es una herramienta de comunicación. Commits pequeños y descriptivos hacen que el historial sea útil, no solo un registro automático.

---

## 5. ¿Qué es push y qué relación tiene con GitHub?

📌 **¿Qué es local?**
Todo lo que existe en tu computador. Los cambios que haces con Git quedan guardados ahí primero, y nadie más puede verlos aún.

📌 **¿Qué es remoto?**
El servidor donde vive el repositorio compartido, generalmente GitHub. Es donde el equipo accede al proyecto desde cualquier lugar.

🚀 **¿Qué hace `git push`?**
Envía tus commits locales al repositorio remoto. Es el puente entre tu máquina y GitHub.

❓ **¿Por qué los cambios no aparecen en GitHub automáticamente?**
Porque Git trabaja primero de forma local. Te da control sobre qué y cuándo compartes. Nada se sube sin que tú lo ordenes explícitamente.

💡 **Ejemplo**
Redactas un correo. Mientras escribes, solo existe en tu pantalla. Cuando presionas "Enviar", recién llega al destinatario. El `push` es ese botón de enviar.

✅ **Conclusión**
Hacer commit no es suficiente para que el equipo vea tu trabajo. El `push` es el paso que lleva tus cambios de tu computador a GitHub, donde el resto del equipo puede acceder a ellos.

---

## 6. ¿Qué es un Pull Request?

📌 **¿Qué es un PR?**
Un Pull Request es una solicitud formal para incorporar los cambios de una rama al proyecto principal. Es decirle al equipo: *"terminé mi parte, revísenla y si está bien, únala al proyecto"*.

🤝 **¿Para qué sirve en trabajo colaborativo?**
Es el punto de control donde el equipo valida que los cambios estén correctos antes de aceptarlos. Deja registro de quién aprobó qué y cuándo.

🔍 **¿Qué permite revisar antes de hacer merge?**
- Si el código funciona correctamente
- Si sigue las convenciones del proyecto
- Si el mensaje del commit es claro
- Si no introduce errores nuevos

🚫 **¿Por qué no es solo "subir código"?**
Porque el PR no sube cambios directamente. Los propone. Solo cuando hay revisión y aprobación se hace el merge.

💡 **Ejemplo**
Ana termina de programar una nueva función. Abre un PR. Luis lo revisa, encuentra un error y lo comenta. Ana corrige. Luis aprueba. Recién entonces el cambio entra a `main`.

✅ **Conclusión**
El Pull Request convierte el trabajo individual en trabajo colectivo revisado. Es el mecanismo que evita que errores lleguen a la versión oficial del proyecto.

---

## 7. ¿Qué es merge y qué podría salir mal?

📌 **¿Qué es un merge?**
Es la acción de unir los cambios de una rama con otra. Generalmente se incorpora el trabajo de una rama secundaria a `main`. Cuando no hay contradicciones, Git lo hace automáticamente.

⚠️ **¿Qué es un conflicto de merge?**
Ocurre cuando dos personas modificaron las mismas líneas del mismo archivo en ramas distintas. Git no puede decidir cuál versión conservar y detiene el proceso para que un humano lo resuelva.

El archivo en conflicto queda marcado así:

```
<<<<<<< HEAD
versión de Ana
=======
versión de Luis
>>>>>>> feature-luis
```

Alguien debe elegir qué conservar o combinar ambas versiones manualmente.

🛠️ **¿Cómo puede reducirse?**
- Dividir bien el trabajo para que cada persona toque archivos distintos
- Hacer ramas cortas y merges frecuentes
- Comunicarse si dos personas van a editar lo mismo

💡 **Ejemplo**
Ana y Luis trabajan en el mismo archivo `styles.css`. Ana cambia el color del botón, Luis también. Al hacer merge, Git encuentra dos versiones del mismo lugar y genera conflicto.

✅ **Conclusión**
El merge es la operación que une el trabajo de las ramas. Los conflictos son normales y se resuelven, pero se previenen con buena organización y comunicación en el equipo.

---

## 8. Buenas prácticas al trabajar con ramas

📌 **Nombres de ramas claros**
El nombre debe describir qué tarea representa. Convención recomendada: `tipo-descripcion-breve`
- ✅ `feature-login`, `fix-error-navbar`, `docs-actualizar-readme`
- ❌ `rama1`, `prueba`, `mis-cambios`

📌 **Mensajes de commit descriptivos**
Usa prefijos que indiquen el tipo de cambio:
- `feat:` → nueva funcionalidad
- `fix:` → corrección de error
- `docs:` → cambio en documentación

Ejemplos:
- ✅ `feat: agregar formulario de contacto`
- ❌ `"arreglos"`, `"cambios varios"`

📌 **Ramas cortas, no eternas**
Cada tarea tiene su propia rama. Una rama que acumula semanas de trabajo sin mergearse genera más conflictos y es más difícil de revisar.

📌 **Nunca trabajar directo en `main`**
Todo cambio, por pequeño que sea, debe pasar por una rama y un Pull Request.

📌 **Revisar antes de mergear**
Nadie debería aprobar su propio PR. La revisión de otro detecta errores que quien escribió el código no ve por estar demasiado cerca de él.

💡 **Ejemplo de flujo ideal**
1. Crear rama `feature-registro`
2. Hacer commits pequeños y descriptivos
3. Abrir Pull Request
4. Un compañero revisa y aprueba
5. Merge a `main`
6. Eliminar la rama

✅ **Conclusión**
Los comandos de Git se aprenden rápido. Los hábitos de trabajo ordenado se construyen con práctica. Estos son los que distinguen a un equipo profesional de uno que constantemente rompe el proyecto.

---

## Glosario rápido

| Término | Significado |
|---|---|
| Repository | Carpeta del proyecto controlada por Git |
| Branch | Rama de trabajo independiente |
| Main | Rama principal y estable del proyecto |
| Fork | Copia del repositorio en otra cuenta |
| Commit | Punto guardado en el historial |
| Push | Subir cambios al repositorio remoto |
| Pull Request | Solicitud para incorporar cambios |
| Merge | Unión de cambios entre ramas |

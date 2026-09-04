# JustitIA

**Corrección calibrada contra tu propio criterio, y auditoría de equidad del lote.**

Aplicación de un único fichero HTML. No necesita instalación ni servidor: se abre en el
navegador y funciona con una clave de la API de OpenAI que se guarda solo en local.

👉 **[Abrir la aplicación](https://fborrasumh.github.io/justitia/)**

---

## Qué problema resuelve

Corregir un lote entero con el mismo criterio de principio a fin es difícil. El criterio
se mueve con el cansancio, con el orden en que llegan los trabajos y con el recuerdo del
anterior. Nadie puede ver ese desplazamiento en sí mismo.

JustitIA no reparte la corrección entre el profesor y la máquina, porque dos correctores
sobre un mismo lote es precisamente la desigualdad que se quiere evitar. Lo que hace es
otra cosa: aprende el criterio del profesor a partir de una muestra que él corrige, mide
cuánto se le parece, y solo entonces propone el resto.

## Cómo funciona

1. **Rúbrica.** Criterios con peso y descriptores. Se pueden redactar a mano o proponer
   desde el enunciado de la tarea.
2. **Lote.** Las entregas se barajan. Corregir en orden alfabético mete el cansancio
   dentro de la calibración como si fuera criterio.
3. **Calibración.** Por cada trabajo de la muestra, la máquina predice a ciegas y su
   predicción queda sellada. Después el profesor pone su nota. Solo entonces se abre la
   comparación. El orden no se puede saltar: ver la predicción antes sería firmarla en
   lugar de contrastarla.
4. **Corrección.** La máquina puntúa el lote completo. Sobre los trabajos ya corregidos
   vuelve a pasar con validación cruzada, dejando fuera el propio trabajo. Sobre el resto
   propone, y el profesor revisa por triaje.
5. **Equidad.** Cobertura del rango de notas, deriva del criterio a lo largo del orden de
   corrección, divergencias ordenadas por distancia y mapa de criterio por trabajo.
6. **Salida.** La nota la firma el profesor. La máquina propone y deja la cita literal
   que sostiene cada punto.

## Lo que mide

- **Error medio** entre la nota del profesor y la segunda lectura.
- **Sesgo global y por criterio**, para ver si la discrepancia es sistemática.
- **Parada adaptativa**: avisa cuando el acuerdo se estabiliza y no hace falta corregir
  más muestra, y dice qué falta cuando todavía no.
- **Deriva**: correlación entre el residuo y la posición en el orden de corrección.
- **Cobertura del rango**: si la muestra no ancla ningún suspenso, la máquina extrapola
  el extremo bajo y la app lo advierte.

## Modelos

`gpt-4o-mini` por defecto, y la familia `gpt-5.6` en sus variantes `luna`, `terra` y
`sol`. La llamada se adapta a cada familia. Cambiar de modelo a mitad de proyecto pide
confirmación, porque invalida el acuerdo ya medido.

## Protección de datos

Los trabajos de los estudiantes son datos personales. Antes de que nada salga del
navegador, la app sustituye nombres (incluidos los del nombre de archivo), correos, DNI,
NIE y números de expediente. El proyecto se guarda en IndexedDB, en el propio navegador.

El informe de deriva y divergencias se descarga aparte, con la advertencia de que es
diagnóstico interno del profesor y no prueba documental.

## Lo que no hace

No califica. Propone, justifica con evidencia anclada al texto, y espera la firma del
profesor responsable de la asignatura.

## Uso

Abrir `index.html` en el navegador, o usar la versión publicada. Hace falta una clave de
la API de OpenAI, que se guarda en `localStorage` y no viaja a ningún otro sitio.

## Autor

Fernando Borrás Rocher · Universidad Miguel Hernández de Elche
ORCID [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573)

Parte del catálogo [Herramientas IA para la academia](https://fborrasumh.github.io/ia/).

## Licencia

MIT

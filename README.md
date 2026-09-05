# NEXO CURRICULAR

### Constructor y acompañante del Programa Analítico y la Planeación Docente

**Versión:** 4.36.1  
**Tipo:** Aplicación web autocontenida en HTML  
**Uso:** Programa Analítico de Escuela · Programa Analítico de Grupo · Planeación Didáctica

---

## 1. ¿Qué es NEXO CURRICULAR?

NEXO CURRICULAR es una aplicación web diseñada para acompañar el desarrollo curricular de la escuela y su contextualización hacia los grupos y la planeación docente.

Su lógica parte de una premisa central:

> **La escuela decide; el docente contextualiza; la aplicación sugiere y acompaña.**

La aplicación organiza el trabajo en tres etapas articuladas:

1. **Programa Analítico de Escuela**
2. **Programa Analítico de Grupo**
3. **Planeación Didáctica**

La información construida en una etapa sirve como referente para las siguientes, buscando conservar la trazabilidad de las decisiones tomadas durante el proceso.

---

## 2. Flujo general

### Escuela

En esta etapa se concentra la información y las decisiones correspondientes al ámbito escolar.

Se trabaja con:

- realidad de la escuela;
- diagnóstico y contextualización;
- necesidades, características, intereses y fortalezas;
- referentes curriculares;
- decisiones colegiadas;
- contextualización curricular;
- elementos necesarios para construir el Programa Analítico de Escuela.

### Grupo

El Programa Analítico de Escuela constituye el referente curricular de partida.

El docente contextualiza la información a partir de la realidad específica de su grupo.

La aplicación puede presentar sugerencias y referentes para apoyar la toma de decisiones, pero estas no sustituyen la decisión docente.

### Planeación Didáctica

La planeación parte de las decisiones construidas previamente y busca mantener coherencia entre:

- diagnóstico;
- Programa Analítico de Escuela;
- Programa Analítico de Grupo;
- contenidos;
- Procesos de Desarrollo de Aprendizaje;
- ejes articuladores;
- actividades;
- propósitos;
- evaluación;
- contextualización del grupo.

---

## 3. Principio de funcionamiento

NEXO CURRICULAR no pretende sustituir el juicio profesional de la directora, docentes o colectivo escolar.

La aplicación funciona como:

- organizador;
- acompañante;
- repositorio de decisiones;
- generador de sugerencias contextualizadas;
- apoyo para mantener la coherencia entre documentos.

Las sugerencias generadas por la aplicación deben ser revisadas y, cuando corresponda, modificadas o rechazadas por quien toma la decisión curricular.

---

## 4. Entrada documental

La aplicación está diseñada para trabajar tomando como documento curricular de referencia el **Programa Analítico de Escuela**.

A partir de este documento se desarrolla la contextualización correspondiente al grupo y posteriormente la planeación didáctica.

La aplicación no pretende convertir automáticamente cualquier información importada en una decisión curricular definitiva.

---

## 5. Persistencia de información

La aplicación puede conservar información de trabajo mediante el almacenamiento disponible en el navegador.

Esto permite continuar trabajando después de cerrar o recargar la página, dependiendo del navegador y del origen desde el cual se ejecute la aplicación.

### Importante

Los datos almacenados pertenecen al entorno del navegador/origen desde el cual se utiliza la aplicación.

Por esta razón:

- una copia servida desde otro repositorio puede disponer de un almacenamiento independiente;
- abrir una copia diferente del HTML puede producir un entorno de datos diferente;
- borrar o modificar el repositorio de GitHub no equivale a borrar los datos almacenados previamente en un navegador.

---

## 6. Restablecer

La aplicación incorpora una función de **Restablecer** destinada a eliminar los datos de trabajo almacenados localmente por la aplicación.

El restablecimiento contempla, cuando las APIs correspondientes están disponibles:

- `localStorage`;
- `sessionStorage`;
- IndexedDB;
- Cache Storage;
- cookies accesibles al documento.

Después del borrado, la aplicación se recarga para evitar que información que permaneciera únicamente en memoria vuelva a aparecer.

### Qué NO hace Restablecer

Restablecer no elimina:

- el archivo `index.html`;
- el repositorio de GitHub;
- los archivos del repositorio;
- el código de la aplicación;
- los recursos curriculares incorporados dentro del propio HTML.

Su función es eliminar el **estado de trabajo almacenado por la aplicación en el navegador**.

---

## 7. Ejecución

NEXO CURRICULAR está desarrollado como una aplicación web contenida en un archivo HTML.

Puede utilizarse:

### Localmente

Descargando `index.html` y abriéndolo con un navegador compatible.

### Desde GitHub Pages

El archivo puede publicarse como página web estática mediante GitHub Pages.

La estructura más sencilla consiste en utilizar:

```text
index.html
```

---

## 8. Fuente curricular y funcionamiento sin conexión

La aplicación consulta el repositorio curricular externo **curriculo-primaria-nem**
y guarda una copia local en el navegador después de la primera descarga.

A partir de la versión 4.36.1:

- la copia local se usa primero, sin volver a descargar en cada apertura;
- **Actualizar desde GitHub** descarga de nuevo y reescribe esa copia local;
- si el repositorio no responde, la aplicación abre con la copia local existente;
- si falta alguno de los archivos complementarios (relaciones proyecto–contenido,
  ejes, fases), la aplicación abre igual y lo informa, en lugar de abortar la
  descarga completa. Los archivos indispensables son `version.json`, `grados.json`,
  `campos-formativos.json`, `contenidos.json` y `pdas.json`.

---

## 9. Alcance de "Restablecer" (versión 4.36.1)

**Restablecer elimina únicamente los datos de NEXO CURRICULAR**, identificados por
los prefijos `pa_`, `pa46_` y `nexo_` en `localStorage`, `sessionStorage`, cookies,
IndexedDB y Cache Storage.

Esto importa cuando la aplicación se publica en GitHub Pages: todos los repositorios
de una misma cuenta comparten el mismo origen de navegador, de modo que un borrado
sin acotar destruiría también los datos locales de las demás aplicaciones publicadas
bajo ese usuario. Las versiones anteriores borraban el origen completo.

---

## 10. Registro de correcciones de la versión 4.36.1

| # | Corrección |
|---|---|
| 1 | `pa43Remote()` invocaba `pa37FetchRemote()`, función inexistente: **Actualizar desde GitHub** fallaba siempre y dejaba una pantalla sin salida. Ahora usa el motor real de descarga. |
| 2 | La descarga de arranque no se guardaba nunca como copia local: la aplicación no funcionaba sin conexión y volvía a descargar 14 archivos en cada apertura. |
| 3 | `ReferenceError: pa413TraceabilityPanel is not defined` durante el arranque, por orden de carga entre bloques. Resuelto con resolución tardía en el despacho de pantallas. |
| 4 | **Restablecer** borraba todo el origen del navegador (ver sección 9). Acotado a claves propias. |
| 5 | El botón flotante «← Menú principal» evadía la advertencia de trabajo sin respaldar del Programa Analítico de Grupo. |
| 6 | Numeración del menú con dos pantallas «6.» y dos «12.». Renumerado 1–17. |
| 7 | Trece funciones sin ninguna referencia eliminadas, entre ellas `saveConstruccionV26`, que apuntaba a doce elementos del DOM ya inexistentes. Se eliminaron también un bucle sin cuerpo dentro del módulo de borrado, una clave duplicada en el despacho de `render()` y el shim `window.construction`. |
| 8 | Cuatro cifras de versión contradictorias (`4.34.0`, `4.35.0`, `28/28`, `15/28`) unificadas en una sola fuente de verdad. |
| 9 | `downloadJSON()` revocaba la URL del objeto antes de que iniciara la descarga. |
| 10 | Las portadas se guardaban como PNG RGBA de hasta 2.2 MB. Recomprimidas a WebP: **8.36 MB → 0.55 MB** (–93 %), determinante para abrir la aplicación desde la red de la escuela o desde el celular. |
| 11 | `pdf.js` declarado dos veces; listeners duplicados en `bind()`. |

---

## 11. Organización interna del archivo (consolidación v4.36.1)

Hasta la versión 4.34.0 el código vivía en **29 bloques `<script>`** acumulados por
capas históricas (`pa32`, `pa36`, `pa43`, `pa44`, `pa46`, `v47`, `v48`, `pa4.1x`),
donde una misma función podía estar definida en un bloque y sustituida en otro dos
mil líneas más abajo. De ahí nacieron los dos errores más graves de esa versión: un
parche corrigió la ruta de arranque del repositorio y dejó intacta la ruta del botón.

A partir de la 4.36.0 el archivo está organizado en **doce módulos nombrados por
dominio**, en el orden en que deben ejecutarse:

| Módulo | Contenido |
|---|---|
| `nexo-01-nucleo-escuela` | Estado, persistencia, repositorio curricular, 17 pantallas de Escuela, exportación DOCX |
| `nexo-02-portal-y-grupo-base` | Portal de las tres etapas, identidad institucional y escudo, base del Programa Analítico de Grupo |
| `nexo-03-planeacion-didactica` | Metodologías (ABPC, STEAM, ABP, AS) y construcción de la planeación |
| `nexo-04-portal-navegacion` | Salida al portal desde cualquiera de las tres etapas |
| `nexo-05-planeacion-exportacion` | Exportación de la planeación |
| `nexo-06-repositorio-curricular` | Copia local, descarga desde GitHub, arranque sin bloqueo |
| `nexo-07-grupo-y-ecosistema` | Sugerencias y decisiones de Grupo, capa documental del Ecosistema NEM |
| `nexo-08-ecosistema-y-autoria` | Ventana de autoría y fuentes documentales |
| `nexo-09-grupo-sesion-y-navegacion` | Sesión efímera de Grupo y botón universal de regreso |
| `nexo-10-capas-de-escuela` | Cierre escolar, biblioteca de proyectos, trazabilidad, auditoría avanzada, autoguardado mensual |
| `nexo-11-borrado-fuentes-y-version` | Restablecer acotado, política de fuentes RAW, versión |
| `nexo-12-arranque` | Única llamada a `pa43Start()`, al final del documento |

### Regla de mantenimiento

**Una capa nueva se agrega antes del módulo 12, nunca después.** El arranque es el
último script del documento a propósito: así ninguna pantalla se dibuja antes de que
existan todas las capas.

### Cadenas de sustitución vigentes

Seis funciones siguen redefiniéndose por diseño, y están documentadas en el mapa de
la cabecera del `index.html` y en el banner de cada módulo:

| Función | Cadena |
|---|---|
| `paReturnPortal` | define 02 → **sustituye** 04 → **envuelve** 09 |
| `pa43Clear` | define 06 → **envuelve** 11 |
| `paEnterGroup` | define 02 → **envuelve** 09 |
| `matrizEditar` | define 01 → **envuelve** 07 |
| `pa44Suggestions` | define 07 → **envuelve** 07 |
| `curriculumNotice` | define 06 → **envuelve** 07 |

*Sustituye* reemplaza sin llamar a la anterior; *envuelve* la conserva y la invoca.
Se eliminaron ocho definiciones que un bloque posterior sustituía por completo y que,
por tanto, nunca llegaban a ejecutarse: `curriculumNotice`, `reloadCurriculum`,
`loadCurriculum`, `paReturnPortal`, `paGroupGo`, `pa33Save`, `pa34Save` y
`pa36Exportar` en sus versiones originales. También se eliminó la duplicación literal
entre `pa43Apply()` y `paApplyCurriculumData()`.

**Ninguna otra función del archivo se redefine.** Cualquier redefinición nueva que no
aparezca en la tabla anterior debe considerarse un error de mantenimiento.

---

## 12. Paridad de las tres etapas (v4.36.1)

### 12.1 Persistencia

| Etapa | Clave local |
|---|---|
| Programa Analítico de Escuela | `pa_app_v14` |
| Programa Analítico de Grupo | `pa_group_v49` *(nuevo en 4.36.0)* |
| Planeación Didáctica | `pa_planning_v36` |

Hasta la 4.34.0, Grupo era la única etapa sin persistencia: guardaba una bandera en
memoria y el trabajo se perdía al cerrar la pestaña. Ahora las tres guardan igual y
las tres se borran igual con **Restablecer**.

### 12.2 Importador universal

Botón fijo **⬆ Continuar un documento**, visible en las tres etapas. Admite `.docx`
(el que mejor se reconoce, porque conserva las tablas), `.pdf`, `.txt` y los
respaldos `.json` de la propia aplicación.

Lo que reconoce y reconstruye dentro de la interfaz:

- **Escuela** — los cinco apartados de la Etapa 1 por etiqueta, la tabla mensual
  completa (Mes · Situación-problema · Valor del mes · Proyecto comunitario) y las
  tablas de matriz curricular (Fase · Campo · Contenido · PDA · Ejes), que entran al
  mes correspondiente.
- **Grupo** — grado, grupo, fase, periodo, situación, características, necesidades,
  intereses y fortalezas.
- **Planeación** — temporalidad, mes, periodo de evaluación, temática, campo,
  contenido, PDA, ejes, contexto, necesidad, propósito, metodología, proyecto,
  producto, destinatario, duración, libro, páginas, pregunta reto, metacognición y
  acuerdos.

Reglas del importador:

1. **No sobrescribe** lo ya capturado, salvo que se pida explícitamente con el
   segundo botón.
2. **No inventa.** Lo que no reconoce lo declara como no reconocido, para que se
   capture en la aplicación.
3. Los referentes traídos de una matriz entran **en estado pendiente y sin vínculo
   con el repositorio curricular**; hay que revisarlos en la Matriz curricular para
   recuperar su trazabilidad (PDA, ejes, proyectos). El importador lo advierte.

### 12.3 Aviso de datos institucionales

Antes de exportar desde cualquiera de las tres etapas, si faltan nombre de la
escuela, CCT, ciclo o escudo, la aplicación lo enumera y advierte que **esos espacios
quedarán vacíos en el formato**, y pide confirmación. El mismo aviso aparece en el
panel del importador.

### 12.4 Corrección adicional detectada al emparejar las etapas

`state`, `paGroup` y `paPlanning` se declaran con `let`, y una declaración `let` **no
crea propiedad en `window`**. Todo el código que escribía en `window.paGroup` —entre
otros, la restauración de respaldos del módulo 09— escribía en un objeto distinto del
que lee la interfaz: el respaldo se "importaba" sin que nada cambiara en pantalla. El
módulo 12 define accesores que hacen que `window.X` y la variable interna sean lo
mismo, con lo que esa restauración vuelve a funcionar.

---

## 13. Plantillas Word incrustadas (v4.36.1)

Hasta la versión 4.36.0 la aplicación **no incluía ninguna plantilla `.docx`**: la
exportación escribía sobre el archivo que el propio usuario importaba y, si nadie lo
había importado —o si se había usado Restablecer—, se detenía. Desde la 4.36.1 las dos
plantillas viajan **dentro del `index.html`**, codificadas en base64, y se siembran
solas en IndexedDB la primera vez que la aplicación abre.

### 13.1 Las dos plantillas

| Archivo | Etapas que la usan | Cómo se rellena |
|---|---|---|
| `plantilla-programa-analitico.docx` | **Escuela** y **Grupo** | Por reconocimiento de estructura: la aplicación clasifica las tablas del documento (contexto, panorama mensual, matriz curricular, bloque de cierre) y escribe en las celdas que corresponden. |
| `plantilla-planeacion-didactica.docx` | **Planeación Didáctica** | Por sustitución de marcadores `{{CAMPO}}` en el texto del documento. |

Es **una sola plantilla** para Escuela y Grupo, reutilizada en las dos etapas, tal
como se pidió.

### 13.2 Estructura de `plantilla-programa-analitico.docx`

- Portada con `{{ESCUDO_ESCUELA}}`, `{{ESCUELA}}`, `{{CCT}}`, `{{ZONA_ESCOLAR}}` y `{{CICLO_ESCOLAR}}`.
- Tabla de matrícula por grado (H/M y totales).
- **Etapa 1 · Lectura de la realidad**: tabla de dos columnas con las cinco etiquetas
  exactas que reconoce el motor (`CONTEXTO SOCIOEDUCATIVO DE LA ESCUELA`,
  `CONTEXTO INTERNO`, `CONTEXTO SOCIAL`, `APRENDIZAJES PRIORITARIOS`,
  `SABERES DE LA COMUNIDAD`).
- **Etapa 2 · Contextualización**: panorama de los once meses
  (`MES` · `SITUACIÓN-PROBLEMA` · `VALOR DEL MES` · `PROYECTO COMUNITARIO`).
- **Once pares** de tablas, uno por mes: la matriz curricular
  (`FASE` · `CAMPO FORMATIVO` · `CONTENIDO` · `PROCESOS DE DESARROLLO DE APRENDIZAJE` ·
  `EJES ARTICULADORES`), precedida por las filas `SITUACIÓN – PROBLEMA:` y
  `TEMPORALIDAD: <MES>`, seguida de la tabla de cierre de una sola columna
  (`CODISEÑO`, `ORIENTACIONES DIDÁCTICAS`, `SUGERENCIAS DE EVALUACIÓN`).

Al venir los once meses ya armados, la exportación **no necesita clonar** ninguna
tabla: cada mes escribe en su sitio.

### 13.3 Estructura de `plantilla-planeacion-didactica.docx`

Encabezado institucional, encuadre del periodo, secuencia didáctica ampliada
(`Momento` · `Secuencia Didáctica Ampliada` · `Recursos y Materiales` ·
`Evaluación Formativa + Ajustes DUA`), listado de recursos, instrumentos de
evaluación, rúbrica socioformativa, lista de cotejo, evidencias, metacognición y
acuerdos. Usa **65 marcadores**, todos con correspondencia comprobada en el mapa de
sustitución de `pa36ExportDocx`.

### 13.4 Almacenes separados por etapa

Se corrigió un choque que existía desde antes: **Escuela y Planeación escribían en la
misma base y la misma llave** (`pa_app_v14_templates` / `active`), de modo que importar
la plantilla de Planeación pisaba la del Programa Analítico y viceversa. Ahora:

| Almacén IndexedDB | Contenido |
|---|---|
| `pa_app_v14_templates` | Plantilla del Programa Analítico (Escuela y Grupo) |
| `pa_planning_v14_templates` | Plantilla de Planeación Didáctica |

`getPlanningTemplateBytes()` conserva un respaldo hacia el almacén antiguo, para no
perder la plantilla de quien ya la tenía importada.

### 13.5 Restablecer y las plantillas

Restablecer sigue borrando **todos los datos** del colectivo y también las bases de
plantillas —no hay excepciones frágiles en el borrado—, pero el módulo 12b vuelve a
sembrar las plantillas incrustadas en cuanto el borrado termina y, de nuevo, en cada
arranque. El resultado práctico: **después de Restablecer no queda ningún dato y la
exportación sigue funcionando**.

Cada escuela puede sustituir la plantilla por la suya propia en cualquier momento
(Escuela: pantalla «4. Importar Programa Analítico»; Planeación: pantalla
«11. Exportar a Word»). Ambas pantallas ofrecen además descargar la plantilla en
blanco.

---

## 14. Calibración del importador contra las plantillas reales (v4.36.1)

Al importar los documentos reales de la escuela aparecieron cuatro defectos que se
corrigieron:

1. **Desfase de posiciones en `porEtiquetas`.** Las etiquetas se buscaban sobre el
   texto normalizado —que colapsa cada racha de espacios y saltos de línea en uno
   solo— pero el recorte se hacía sobre el texto original con esas mismas posiciones.
   En un DOCX real, donde cada celda aporta un `\n\n`, el desfase crecía línea a línea
   y la Etapa 1 llegaba vacía o corrida. Ahora la normalización guarda de qué posición
   del texto original proviene cada carácter.
2. **«Género» se leía como «enero».** El mes se buscaba con `includes()`, y la
   situación-problema de marzo —*Familias: diversidad, discapacidad y equidad de
   género*— hacía que ese mes se escribiera sobre enero. El mes debe aparecer ahora
   como palabra completa. La corrección se aplicó también al exportador.
3. **Celdas combinadas en el panorama mensual.** En el documento real la columna
   «Proyecto comunitario» está combinada verticalmente, de modo que nueve de las once
   filas sólo traen tres celdas y se descartaban. Ahora se admiten y se arrastra el
   último proyecto leído, que es lo que significa una celda combinada.
4. **Apartados cuyo texto repite su propio encabezado** dejaban el valor vacío; ahora
   el límite del apartado avanza hasta encontrar contenido real.

Además, el importador reconoce dos estructuras nuevas:

- El **bloque de cierre de cada mes** (codiseño, orientaciones didácticas y
  sugerencias de evaluación) leído de la tabla de una sola columna y asociado al mes
  de la matriz anterior.
- Las **tablas de encabezado de la planeación** (`etiqueta | valor`), que el lector de
  texto plano no distinguía. Los recursos se depositan en `paPlanning.resources`, que
  es donde la interfaz los lee.

Resultado sobre el Programa Analítico real de la escuela: **11 de 11 meses** con
panorama, referentes curriculares y bloque de cierre; los siete apartados de la
Etapa 1 reconocidos.

---

## 15. Certificación de paridad de las tres etapas (v4.36.1)

| Criterio | Escuela | Grupo | Planeación |
|---|---|---|---|
| **Persistencia local** | ✓ `pa_app_v14` | ✓ `pa_group_v49` | ✓ `pa_planning_v36` |
| **Importación** (.docx/.pdf/.txt/.json) | ✓ | ✓ | ✓ |
| **Exportación a Word** | ✓ plantilla incrustada | ✓ misma plantilla | ✓ plantilla propia |
| **Aviso de datos institucionales** | ✓ | ✓ | ✓ |
| **Restablecer no inutiliza la exportación** | ✓ | ✓ | ✓ |

Las cuatro filas del encargo quedan cubiertas: la exportación a Word deja de ser el
punto pendiente.

### Pruebas ejecutadas antes de publicar

| Prueba | Resultado |
|---|---|
| Sintaxis de los 15 bloques `<script>` | 0 errores |
| Exportación de Escuela sobre la plantilla incrustada | 11/11 meses escritos, 0 clonaciones, 0 avisos, 14/14 comprobaciones |
| Exportación de Planeación sobre la plantilla incrustada | 18/18 comprobaciones, sin marcadores sin resolver |
| Ida y vuelta: exportar e importar de nuevo | 12/12 comprobaciones; no sobrescribe lo capturado |
| Importación de los dos documentos reales de la escuela | 11/11 meses; Etapa 1 completa |

---

## 16. Organización final del archivo (v4.36.1)

Quince bloques `<script>`, catorce de ellos con identificador de módulo:

```
nexo-01-nucleo-escuela ............ estado, motor DOCX y exportación de Escuela
nexo-02-portal-y-grupo-base ....... portal y base del Programa Analítico de Grupo
nexo-03-planeacion-didactica ...... modelo y pantallas de la Planeación
nexo-04-portal-navegacion ......... navegación entre etapas
nexo-05-planeacion-exportacion .... exportación de la Planeación a Word
nexo-06-repositorio-curricular .... repositorio curricular y caché local
nexo-07-grupo-y-ecosistema ........ Grupo y Ecosistema NEM
nexo-08-ecosistema-y-autoria ...... fuentes documentales y autoría
nexo-09-grupo-sesion-y-navegacion . sesión de Grupo y regreso al portal
nexo-10-capas-de-escuela .......... capas de trabajo de la Escuela
nexo-11-borrado-fuentes-y-version . borrado acotado y política de fuentes
nexo-12-paridad-tres-etapas ....... persistencia, importador universal y avisos
nexo-12a-plantillas-datos ......... las dos plantillas .docx en base64   ← nuevo
nexo-12b-plantillas-embebidas ..... siembra, almacenes separados y resiembra ← nuevo
nexo-13-arranque .................. primera pantalla (siempre el último)
```

**La regla de mantenimiento se conserva:** toda capa nueva se agrega antes de
`nexo-13-arranque`, nunca después.

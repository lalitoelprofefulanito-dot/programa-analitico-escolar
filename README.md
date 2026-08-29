# NEXO CURRICULAR

### Constructor y acompañante del Programa Analítico y la Planeación Docente

**Versión:** 4.34.0  
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

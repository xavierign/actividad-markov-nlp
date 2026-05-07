# Actividad: Introducción a Cadenas de Markov y Procesamiento de Lenguaje Natural (NLP) en Investigación Operativa

## Descripción General

Esta actividad introduce conceptos fundamentales de **cadenas de Markov** y **procesamiento de lenguaje natural (NLP)** aplicados a un texto literario. Utilizaremos el texto de "El crimen y el castigo" de Fyodor Dostoevsky para construir modelos probabilísticos que generen texto y analicen transiciones de palabras. La actividad está diseñada con niveles progresivos de dificultad, desde conceptos básicos hasta aplicaciones avanzadas.

**Objetivos de Aprendizaje:**
- Comprender qué son las cadenas de Markov y su aplicación en modelado probabilístico.
- Introducir técnicas básicas de NLP: tokenización, limpieza de texto y análisis de frecuencia.
- Aplicar modelos de Markov de diferentes órdenes para generar y completar texto.
- Reflexionar sobre aplicaciones en Investigación Operativa (e.g., modelado de procesos estocásticos).

**Tiempo Estimado:** 2 horas.  
**Entrega:** Respuestas en el foro del curso, completando frases específicas y adjuntando el enlace al notebook Jupyter con el código ejecutado.

**Archivos Necesarios:**
- `crimen_y_castigo.txt`: Texto limpio de la novela (descargado de Project Gutenberg).
- `actividad_markov.ipynb`: Notebook Jupyter con el código base.

## Conceptos Teóricos

### 1. Cadenas de Markov

Una **cadena de Markov** es un modelo matemático que describe una secuencia de eventos donde el estado futuro depende únicamente del estado actual, no del pasado (propiedad de Markov). Se usa en Investigación Operativa para modelar procesos estocásticos como colas, inventarios o decisiones secuenciales.

- **Estado:** En esta actividad, un "estado" es una palabra (o secuencia de palabras).
- **Transición:** Probabilidad de pasar de un estado a otro.
- **Matriz de Transición:** Tabla que resume las probabilidades entre estados.

#### Orden de la Cadena:
- **Orden 0:** Cada palabra es independiente (no usa contexto).
- **Orden 1:** La siguiente palabra depende solo de la anterior. Ejemplo: Si "el" precede a "amor" con probabilidad 0.1, entonces P(siguiente | "el") = 0.1 para "amor".
- **Orden 2:** Depende de las dos palabras anteriores. Mejora la coherencia.
- **Orden 3:** Depende de las tres anteriores. Más preciso, pero requiere más datos.

**Ejemplo Visual (Orden 1):**
```
Estado Actual: "el"
Transiciones:
- "amor" → 0.2
- "hombre" → 0.15
- "tiempo" → 0.1
...
```

**Aplicación en IO:** Modelar cadenas de suministro donde el estado es el nivel de inventario, y transiciones representan ventas/demandas.

### 2. Procesamiento de Lenguaje Natural (NLP) Básico

NLP es el campo que permite a las computadoras entender y procesar lenguaje humano. En esta actividad, usamos técnicas simples:

- **Tokenización:** Dividir el texto en unidades (palabras). Ejemplo: "El amor es ciego" → ["El", "amor", "es", "ciego"].
- **Limpieza:** Remover puntuación, convertir a minúsculas, eliminar stopwords (palabras comunes como "el", "la").
- **Análisis de Frecuencia:** Contar ocurrencias de palabras para identificar patrones.
- **Generación de Texto:** Usar probabilidades para crear frases nuevas basadas en el modelo.

**Herramientas:** Usamos Python con bibliotecas como NLTK (para tokenización) y estructuras de datos como diccionarios para transiciones.

## Instrucciones de la Actividad

1. **Descarga y Configuración:**
   - Clona este repositorio de GitHub.
   - Abre `actividad_markov.ipynb` en Jupyter Notebook o VS Code.
   - Asegúrate de tener Python instalado con las bibliotecas: `nltk`, `numpy`, `matplotlib`.

2. **Ejecuta las Celdas en Orden:**
   - **Celda 1:** Carga el texto de `crimen_y_castigo.txt`.
   - **Celda 2:** Preprocesa el texto (limpia y tokeniza). Responde: ¿Cuál es la palabra más frecuente?
   - **Celda 3:** Construye modelo Markov orden 1. Responde: Completa "el amor" con la palabra más probable.
   - **Celda 4:** Modelo orden 2. Responde: Completa "el amor" con 3 palabras.
   - **Celda 5:** Modelo orden 3 y generación. Responde: Genera 20 palabras a partir de "el amor es" y analiza la coherencia.

3. **Preguntas para el Foro:**
   - Publica tus respuestas a las preguntas anteriores.
   - Adjunta el enlace al notebook (e.g., GitHub Gist o repo personal).
   - Reflexión: ¿Cómo mejora la coherencia con órdenes mayores? ¿Ejemplos en IO?

## Figuras y Ejemplos

**Figura 1: Diagrama de Transición Orden 1**
```
[el] --> [amor] (0.2)
   |     |
   v     v
[hombre] [tiempo]
```
(Descripción: Flechas muestran probabilidades de transición desde "el").

**Ejemplo de Generación:**
- Orden 1: "el amor el hombre el tiempo" (poco coherente).
- Orden 3: "el amor es una pasión que consume el alma" (más natural).

## Recursos Adicionales
- [Documentación NLTK](https://www.nltk.org/)
- [Cadenas de Markov en Wikipedia](https://es.wikipedia.org/wiki/Cadena_de_M%C3%A1rkov)
- Si tienes dudas, consulta el foro del curso.

¡Disfruta explorando cómo la probabilidad modela el lenguaje!
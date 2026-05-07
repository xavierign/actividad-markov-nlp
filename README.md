# Actividad: Introducción a Cadenas de Markov y Procesamiento de Lenguaje Natural (NLP) en Investigación Operativa

## Descripción General

Esta actividad introduce conceptos fundamentales de **cadenas de Markov** y **procesamiento de lenguaje natural (NLP)** aplicados a un texto literario. Utilizaremos el texto de "El crimen y el castigo" de Fyodor Dostoevsky para construir modelos probabilísticos que generen texto y analicen transiciones de palabras.

**Objetivos de Aprendizaje:**
- Comprender qué son las cadenas de Markov y su aplicación en modelado probabilístico.
- Introducir técnicas básicas de NLP: tokenización, limpieza de texto y análisis de frecuencia.
- Aplicar modelos de Markov de diferentes órdenes para generar y completar texto.

**Entrega:** Respuestas en el foro del curso, completando frases específicas y adjuntando el enlace al notebook Jupyter con el código ejecutado.

**Archivos Necesarios:**
- `crimen_y_castigo.txt`: Texto limpio de la novela (descargado de Project Gutenberg).
- `actividad_markov.ipynb`: Notebook Jupyter con un esqueleto de código.

## Conceptos Teóricos

### 1. Cadenas de Markov

Un **proceso estocástico** es una colección de variables aleatorias indexadas por tiempo, donde el futuro depende del presente, no del pasado (propiedad de Markov). Una **cadena de Markov** es un tipo específico de proceso estocástico discreto en tiempo, usado en Investigación Operativa para modelar sistemas como colas, inventarios o decisiones secuenciales.

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

- **Tokenización:** Dividir el texto en unidades (palabras). Ejemplo: "El perdon es ciego" → ["El", "perdon", "es", "ciego"].
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
   - **Celda 2:** Preprocesa el texto (limpia y tokeniza). Responde: Top 5 palabras más frecuentes.
- **Celda 3:** Construye modelo Markov orden 1. Responde: Completa "el perdon" con 5 palabras.
- **Celda 4:** Modelo orden 2. Responde: Completa "el perdon" con 10 palabras.
- **Celda 5:** Modelo orden 3. Responde: Completa "el perdon" con 15 palabras.

3. **Preguntas para el Foro:**
   - Publica tus respuestas a las preguntas anteriores.
   - Adjunta el enlace al notebook.

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
- Orden 1: "el perdon el hombre el tiempo" (poco coherente).
- Orden 3: "el perdon es una decisión que transforma la vida" (más natural).

## Recursos Adicionales
- [Documentación NLTK](https://www.nltk.org/)
- [Cadenas de Markov en Wikipedia](https://es.wikipedia.org/wiki/Cadena_de_M%C3%A1rkov)
- Si tienes dudas, consulta el foro del curso.

¡Disfruta explorando cómo la probabilidad modela el lenguaje!
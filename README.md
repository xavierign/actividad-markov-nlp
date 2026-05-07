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

Un **proceso estocástico** es una colección de variables aleatorias indexadas en el tiempo, donde el valor futuro se modela con probabilidades y depende del estado presente. En una **cadena de Markov**, esa dependencia se restringe al estado actual o a un número limitado de estados anteriores.

- **Estado:** En esta actividad, un "estado" es una palabra o una secuencia de palabras.
- **Transición:** Es la probabilidad de pasar de un estado a otro.
- **Matriz de Transición:** Es una tabla que resume las probabilidades de cada posible salto entre estados.

#### Orden de la Cadena:
- **Orden 0:** Cada palabra se elige sin contexto. No hay dependencia entre estados.
- **Orden 1:** La siguiente palabra depende solo de la palabra anterior.
- **Orden 2:** La siguiente palabra depende de las dos palabras anteriores.
- **Orden 3:** La siguiente palabra depende de las tres palabras anteriores.

En general, a mayor orden, el modelo captura más contexto, pero también requiere más datos para estimar las probabilidades.

### Cómo construir un modelo de Markov

1. Tokenizar el texto en palabras limpias.
2. Para cada orden, contar las secuencias:
   - Orden 1: contar cuántas veces cada palabra sigue a la palabra actual.
   - Orden 2: contar cuántas veces cada palabra sigue a un par de palabras anteriores.
   - Orden 3: contar cuántas veces cada palabra sigue a una triple anterior.
3. Construir una tabla de transiciones usando diccionarios:
   - Para orden 1: `transiciones[palabra_actual].append(palabra_siguiente)`.
   - Para orden 2: `transiciones[(palabra_a, palabra_b)].append(palabra_siguiente)`.
4. Calcular probabilidades condicionales dividiendo el conteo de cada siguiente palabra por el total de ocurrencias del estado.
5. Generar texto seleccionando la siguiente palabra según esas probabilidades y avanzando el estado.

**Pseudocódigo:**
```
for i in range(len(tokens) - orden):
    estado = tokens[i:i+orden]
    siguiente = tokens[i+orden]
    transiciones[tuple(estado)].append(siguiente)

for estado, lista in transiciones.items():
    contar = Counter(lista)
    probabilidades[estado] = {sig: count/len(lista) for sig, count in contar.items()}
```

**Ejemplo Visual (Orden 1):**
```
Estado Actual: "el"
Transiciones:
- "perdón" → 0.2
- "hombre" → 0.15
- "tiempo" → 0.1
...
```

**Ejemplo en colas:** El estado puede ser el número de clientes en fila; la transición describe la probabilidad de que llegue un nuevo cliente o que se atienda uno.

**Ejemplo en inventarios:** El estado es la cantidad en stock; la transición describe la probabilidad de recibir inventario o vender unidades.

**Ejemplo de decisiones secuenciales:** En un proceso de control de producción, el estado puede ser el nivel de inventario y la transición depende de la demanda y las órdenes de reposición.

### 2. Procesamiento de Lenguaje Natural (NLP) Básico

NLP es el campo que permite a las computadoras entender y procesar lenguaje humano. En esta actividad, usamos técnicas simples:

- **Tokenización:** Dividir el texto en unidades (palabras). Ejemplo: "El perdón es ciego" → ["El", "perdón", "es", "ciego"].
- **Limpieza:** Remover puntuación, convertir a minúsculas, eliminar stopwords (palabras comunes como "el", "la").
- **Análisis de Frecuencia:** Contar ocurrencias de palabras para identificar patrones.
- **Generación de Texto:** Usar probabilidades para crear frases nuevas basadas en el modelo.

**Herramientas:** Usamos Python con bibliotecas como NLTK (para tokenización) y estructuras de datos como diccionarios para transiciones.

## Instrucciones de la Actividad

1. **Descarga y Configuración:**
   - Descarga el material y trabaja con los archivos localmente.
   - Abre `actividad_markov.ipynb` en Jupyter Notebook o VS Code.
   - Asegúrate de tener Python instalado con las bibliotecas: `nltk`, `numpy`, `matplotlib`.

2. **Ejecuta las Celdas en Orden:**
   - **Celda 1:** Carga el texto de `crimen_y_castigo.txt`.
   - **Celda 2:** Preprocesa el texto (limpia y tokeniza). Responde: Top 5 palabras más frecuentes.
   - **Celda 3:** Construye modelo Markov orden 1. Responde: Completa "el perdón" con 5 palabras.
   - **Celda 4:** Modelo orden 2. Responde: Completa "el perdón" con 10 palabras.
   - **Celda 5:** Modelo orden 3. Responde: Completa "el perdón" con 15 palabras.

3. **Preguntas para el Foro:**
   - Publica tus respuestas a las preguntas anteriores.
   - Adjunta el enlace al notebook.

## Figuras y Ejemplos

**Ejemplo de transición orden 1**

Imagina que el estado actual es la palabra "el". En un modelo de Markov de orden 1, la siguiente palabra se elige solo en función de la palabra actual.

- Si el modelo dice que "perdón" sigue a "el" con probabilidad 0.2, significa que el 20% de las veces la palabra siguiente es "perdón".
- Otras posibles continuaciones pueden ser "hombre", "tiempo", etc.

En forma de tabla, un fragmento de la matriz de transición sería:

| Estado actual | Siguiente palabra | Probabilidad |
|--------------|-------------------|--------------|
| el           | perdón            | 0.2          |
| el           | hombre            | 0.15         |
| el           | tiempo            | 0.1          |

Esto ayuda a entender cómo el modelo usa solo el estado presente para elegir la siguiente palabra.

**Ejemplo de Generación:**
- Orden 1: "el perdón el hombre el tiempo" (poco coherente).
- Orden 3: "el perdón es una decisión que transforma la vida" (más natural).

## Recursos Adicionales
- [Documentación NLTK](https://www.nltk.org/)
- [Cadenas de Markov en Wikipedia](https://es.wikipedia.org/wiki/Cadena_de_M%C3%A1rkov)
- Si tienes dudas, consulta el foro del curso.

¡Disfruta explorando cómo la probabilidad modela el lenguaje!
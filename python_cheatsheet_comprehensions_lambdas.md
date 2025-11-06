# Cheatsheet: List Comprehension y Lambdas en Python

> Basado en ejercicios de listas, diccionarios, sets y uso de `lambda` con `sorted`, `max` y `min`.

---

## 1. List Comprehension: Sintaxis básica

### 1.1. Forma general

```python
[expresion for variable in iterable]
[expresion for variable in iterable if condicion]
```

- **expresion**: lo que se añade a la nueva lista.
- **iterable**: lista, rango, tupla, diccionario, etc.
- **condicion** (opcional): filtra elementos.

Ejemplo (15.1): números divisibles por 2 y por 4 entre 2 y 50

```python
x = [n for n in range(2, 50) if n % 2 == 0 and n % 4 == 0]
```

---

## 2. Patrones típicos de List Comprehension

### 2.1. Transformar elementos

Multiplicar cada número por 10 (15.9 b):

```python
lista_diez = [n * 10 for n in range(1, 11)]
```

Convertir cadenas a mayúsculas (15.9 f):

```python
lst = ['Amol', 'Vijay', 'Vinay', 'Rahul', 'Sandeep']
lst_mayus = [nombre.upper() for nombre in lst]
```

Capitalizar palabras de una frase (15.5):

```python
python = "Es un lenguaje de progrmación muy popular en ML , NN, IA y GenAI"
resultado = " ".join([palabra.capitalize() for palabra in python.split()])
```

Convertir Fahrenheit a Celsius (15.9 g):

```python
fahrenheit = [32, 68, 86, 104, 212]
celsius = [(f - 32) * 5/9 for f in fahrenheit]
```

---

### 2.2. Filtrar elementos

Quedarse con los pares entre 10 y 30 (15.9 i):

```python
pares = [n for n in range(10, 30) if n % 2 == 0]
```

Separar positivos y negativos (15.9 e):

```python
lista_mezclada = [1, -5, 3, -10, 9, -2, 0]

positivos = [n for n in lista_mezclada if n >= 0]
negativos = [n for n in lista_mezclada if n < 0]
```

Eliminar tuplas vacías (15.4):

```python
lista = [(1, 2), (), (3, 4), (), (5,), (6, 7, 8), ()]
lista_limpia = [t for t in lista if t]
```

---

### 2.3. List comprehensions anidadas

Aplanar una matriz (15.2):

```python
mat = [[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]]
aplanada = [n for fila in mat for n in fila]
```

Generar lista de coordenadas (15.9 a):

```python
coordenadas = [(x, y) for x in range(1, 6) for y in range(1, 6)]
```

Matriz 2D de múltiplos (15.9 h):

```python
matriz_multiplos = [[(40 + (i * 5 + j) * 4) for j in range(5)] for i in range(4)]
```

Suma de matrices 3x4 (15.7):

```python
mat3_comprehension = [[mat1[i][j] + mat2[i][j] for j in range(len(mat1[0]))] for i in range(len(mat1))]
```

---

## 3. Set Comprehension

```python
{expresion for variable in iterable if condicion}
```

Ejemplo (15.3):

```python
import random
a = {random.randint(15, 45) for _ in range(10)}
mayores_30 = {n for n in a if n >= 30}
```

Nombres a mayúsculas (15.9 o):

```python
lst = ['Amol', 'Vijay', 'Vinay', 'Rahul', 'Sandeep']
lst_convert = {n.upper() for n in lst}
```

---

## 4. Dict Comprehension

```python
{clave_nueva: valor_nuevo for clave, valor in diccionario.items() if condicion}
```

Multiplicar valores y poner claves en mayúsculas (15.9 l):

```python
d1 = {'a': 1, 'b': 2, 'c': 3}
d1_convert = {k.upper(): v * 100 for k, v in d1.items()}
```

Capitalizar claves y elevar al cuadrado valores (15.9 n):

```python
d2 = {'AMOL': 20, 'ANIL': 12}
d2_convert = {k.capitalize(): v * v for k, v in d2.items()}
```

Dict comprehension complejo (15.6):

```python
resultado_final = {
    "".join(
        c for c in clave.lower() if c.isalnum() and c not in {'a','e','i','o','u'}
    ): (d["precio"], d["stock"], d["cat"])
    for clave, d in inventario.items()
    if d["stock"] > 0 and d["precio"] > 100
}
```

---

## 5. Lambdas: Funciones anónimas

```python
lambda parametros: expresion
```

Ejemplo:

```python
doble = lambda x: x * 2
```

---

## 6. Lambdas con `max`, `min`, `sorted`

### 6.1. Con diccionarios (15.10)

```python
datos = {'a': 10, 'b': 3, 'c': 25, 'd': 1}
valor_max = max(datos.items(), key=lambda x: x[1])
valor_min = min(datos.items(), key=lambda x: x[1])
```

### 6.2. Con listas

```python
palabras = ["Python", "es", "un", "lenguaje", "genial"]
ordenadas = sorted(palabras, key=lambda x: len(x))
```

Ordenar por última letra:

```python
nombres = ["Carlos", "Ana", "Beatriz", "David"]
ordenados = sorted(nombres, key=lambda x: x[-1])
```

### 6.3. Con tuplas

```python
productos = [('Café', 8), ('Azúcar', 3)]
ordenados_por_precio = sorted(productos, key=lambda x: x[1])
```

Máxima suma (BONUS 7):

```python
pares = [(1, 9), (5, 3), (2, 10)]
tupla_max = max(pares, key=lambda x: x[0] + x[1])
```

### 6.4. Con listas de diccionarios

```python
juegos = [
    {'titulo': 'Cyberpunk', 'puntuacion': 7.5},
    {'titulo': 'Zelda', 'puntuacion': 9.9}
]

max_juego = max(juegos, key=lambda x: x['puntuacion'])
ranking = sorted(juegos, key=lambda x: x['puntuacion'], reverse=True)
```

Orden por varios criterios (BONUS 5):

```python
inventario = [
    {'prod': 'Monitor', 'cat': 'Electrónica', 'precio': 150},
    {'prod': 'Teclado', 'cat': 'Periféricos', 'precio': 80}
]

ordenado = sorted(inventario, key=lambda x: (x['cat'], x['precio']))
```

### 6.5. Tratando `None` como último

```python
productos = [
    {'prod': 'Ratón Roto', 'stock': None},
    {'prod': 'Monitor', 'stock': 5}
]
ordenado = sorted(productos, key=lambda x: x['stock'] is None)
```

### 6.6. Ordenar diccionario por valor

```python
puntuaciones = {'jugador_1': 1500, 'jugador_3': 9000}
ranking = sorted(puntuaciones.items(), key=lambda x: x[1], reverse=True)
```

---

## 7. Resumen rápido

- **List comprehensions**
  - `[expr for x in iterable]`
  - `[expr for x in iterable if cond]`
  - Anidadas: `[expr for x in A for y in B]`
- **Set comprehensions**: `{expr for ...}`
- **Dict comprehensions**: `{k: v for ...}`
- **Lambda**: `lambda x: expr`
- **Usos comunes de `lambda`**: `sorted`, `max`, `min`, `map`, `filter`.

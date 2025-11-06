# Cheatsheet General de Python 🐍

> Resumen rápido de sintaxis, tipos, estructuras y control de flujo en Python.

---

## 1. Sintaxis básica

```python
# Comentarios
# Esto es un comentario de una línea

"""
Docstring o comentario multilínea
Útil para documentar funciones, clases, módulos
"""

# Asignación de variables
x = 10
y = 3.14
nombre = "Iñigo"
activo = True

# Mostrar por pantalla
print("Hola", nombre)

# Leer por teclado (siempre devuelve str)
entrada = input("Escribe algo: ")
```

---

## 2. Tipos básicos y conversiones

```python
# Tipos básicos
entero = 5              # int
decimal = 3.5           # float
cadena = "texto"        # str
booleano = True         # bool

type(entero)            # <class 'int'>

# Conversión de tipos (casting)
int("10")               # 10
float("3.14")           # 3.14
str(123)                # "123"
bool(0)                 # False, cualquier cosa distinta de 0 → True

# Operaciones con números
a = 7
b = 3
a + b    # 10
a - b    # 4
a * b    # 21
a / b    # 2.333...
a // b   # 2 (división entera)
a % b    # 1 (módulo)
a ** b   # 343 (potencia)
```

---

## 3. Operadores

```python
# Comparación → devuelven bool
x == y   # igual
x != y   # distinto
x < y
x <= y
x > y
x >= y

# Lógicos
cond = (x > 0) and (y > 0)
cond = (x > 0) or (y > 0)
cond = not (x > 0)

# Pertenencia
"py" in "python"        # True
3 in [1, 2, 3]          # True
```

---

## 4. Estructuras de datos

### 4.1 Listas (mutables, ordenadas)

```python
nums = [1, 2, 3]
mixta = [1, "hola", True]

nums[0]         # 1
nums[-1]        # último elemento

# Slicing
nums[0:2]       # [1, 2]
nums[:2]        # [1, 2]
nums[1:]        # [2, 3]
nums[:]         # copia

# Métodos importantes
nums.append(4)
nums.insert(1, 99)
nums.remove(2)      # borra la primera aparición de 2
valor = nums.pop()  # saca y devuelve el último
len(nums)           # longitud
sorted(nums)        # devuelve una lista ordenada (no modifica la original)
nums.sort()         # ordena in-place
```

### 4.2 Tuplas (inmutables, ordenadas)

```python
t = (1, 2, 3)
t[0]       # 1
# t[0] = 10 → ERROR (no se puede modificar)

# Desempaquetado
a, b, c = t
```

### 4.3 Diccionarios (clave-valor)

```python
persona = {
    "nombre": "Ana",
    "edad": 25,
    "ciudad": "Madrid"
}

persona["nombre"]      # "Ana"
persona["edad"] = 26   # modificar
persona["email"] = "ana@example.com"  # añadir

# Métodos útiles
persona.keys()         # dict_keys([...])
persona.values()       # dict_values([...])
persona.items()        # dict_items([(clave, valor), ...])

"edad" in persona      # True
persona.get("altura", 0)  # devuelve 0 si no existe la clave
```

### 4.4 Conjuntos (sets) (sin orden, sin duplicados)

```python
s = {1, 2, 2, 3}   # {1, 2, 3}
s.add(4)
s.remove(1)        # lanza error si no existe
s.discard(1)       # no lanza error

a = {1, 2, 3}
b = {3, 4, 5}
a | b      # unión → {1, 2, 3, 4, 5}
a & b      # intersección → {3}
a - b      # diferencia → {1, 2}
```

---

## 5. Control de flujo

### 5.1 Condicionales

```python
x = 10

if x > 0:
    print("positivo")
elif x == 0:
    print("cero")
else:
    print("negativo")
```

### 5.2 Bucles `while`

```python
i = 0
while i < 5:
    print(i)
    i += 1
else:
    print("Fin del while")
```

### 5.3 Bucles `for`

```python
for i in range(5):      # 0,1,2,3,4
    print(i)

for i in range(1, 6):   # 1 a 5
    print(i)

# Iterar listas
nombres = ["Ana", "Luis", "María"]
for nombre in nombres:
    print(nombre)

# Indice y valor a la vez
for i, nombre in enumerate(nombres):
    print(i, nombre)
```

### 5.4 `break`, `continue`, `pass`

```python
for i in range(10):
    if i == 5:
        break       # sale del bucle
    if i % 2 == 0:
        continue    # salta a la siguiente iteración
    print(i)

def funcion_sin_implementar():
    pass    # placeholder, no hace nada
```

---

## 6. Funciones

```python
def saludar(nombre):
    """Muestra un saludo por pantalla."""
    print(f"Hola, {nombre}")

saludar("Iñigo")

def potencia(base, exp=2):
    return base ** exp

potencia(3)      # 9
potencia(2, 3)   # 8

def sumar_todo(*args):
    return sum(args)

def mostrar_info(**kwargs):
    for clave, valor in kwargs.items():
        print(clave, "=", valor)
```

### Lambdas

```python
doble = lambda x: x * 2
numeros = [5, 2, 9, 1]
sorted(numeros, key=lambda x: -x)
```

---

## 7. Comprehensions

```python
cuadrados = [x**2 for x in range(10)]
pares = [x for x in range(10) if x % 2 == 0]
cuadrados_dict = {x: x**2 for x in range(5)}
cuadrados_set = {x**2 for x in range(5)}
```

---

## 8. Módulos e importaciones

```python
import math
from math import sqrt, pi
import math as m
from operaciones import sumar
```

---

## 9. Manejo de errores

```python
try:
    x = int(input("Número: "))
    resultado = 10 / x
except ZeroDivisionError:
    print("No se puede dividir entre cero")
except ValueError:
    print("Debes introducir un número entero")
else:
    print("Resultado =", resultado)
finally:
    print("Siempre se ejecuta")
```

---

## 10. Ficheros

```python
with open("datos.txt", "r", encoding="utf-8") as f:
    contenido = f.read()

with open("salida.txt", "w", encoding="utf-8") as f:
    f.write("Hola\n")
    f.write("Línea 2\n")
```

---

## 11. POO básica

```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad

    def saludar(self):
        print(f"Hola, soy {self.nombre}")

p = Persona("Ana", 25)
p.saludar()
```

### Herencia

```python
class Estudiante(Persona):
    def __init__(self, nombre, edad, curso):
        super().__init__(nombre, edad)
        self.curso = curso
```

---

## 12. Funciones útiles

```python
nombres = ["Ana", "Luis", "María"]
edades = [25, 30, 22]

for i, nombre in enumerate(nombres):
    print(i, nombre)

for nombre, edad in zip(nombres, edades):
    print(nombre, edad)

any([1, 0, 3])
all([1, 2, 3])
sorted(["python", "es", "genial"], key=len)
```

---

## 13. Módulos estándar

```python
import math, random, datetime, os, sys
from collections import Counter

random.randint(1, 10)
hoy = datetime.date.today()
contador = Counter("banana")
```

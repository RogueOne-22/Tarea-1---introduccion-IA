##Desarrollo tarea 1

<h1 align="center">🤖 Movimiento Aleatorio de un robot </h1>

  Este ejercicio implementa una simulación sencilla de un robot en una grid **3x3** (ajustable por código), En donde el objetivo es que el robot llegue a la posición final optimizando sus movimientos.

---

## 🎯 Objetivo
El robot debe alcanzar la meta en la menor cantidad de pasos posibles, tomando decisiones que maximicen la recompensa y evitando quedar bloqueado por falta de batería.

---

## ⚡ Estrategia del Robot

El robot sigue una **estrategia con aleatoriedad controlada**:
- Puede avanzar **arriba, abajo, izquierda o derecha**.  
- **Recarga:** la batería se reinicia al **100%**.  
- **Restricción de batería:**  
  - Si la batería es **> 20**, puede moverse (cada movimiento consume -10).  
  - Si la batería es **≤ 20**, no puede moverse y se le fuerza a recargar.  
-  En cada paso, la acción se elige de manera aleatoria entre las posibles (`adelante`, `atrás`, `izquierda`, `derecha`, `recargar`).  
-  Cuando alcanza la posición `(3, 3)`, el robot detiene la ejecución.  

---

## 🔋 Batería
- El valor inicial de batería se genera de manera **aleatoria** entre **10 y 100**, en intervalos de 15:  
  `10, 25, 40, 55, 70, 85, 100`.  
- Cada movimiento cuesta **10 unidades de batería**.  
---

## 🏆 Sistema de Recompensas
La recompensa está diseñada para guiar al robot hacia decisiones correctas:
- `+20` → Si alcanza el objetivo.  
- `+5` → Si decide recargar si la bateria no esta al limite.  
- `-1` → Si se mueve normalmente.  
- `-5` → Si intenta moverse con poca batería.  
- `-10` → Si intenta moverse sin batería.  

Esto obliga al robot a **aprender una estrategia**, aunque las acciones se eligen aleatoriamente.

## 🚦 Ejemplo de Ejecución
```phyton
Total de estados posibles: 63
Estado inicial del robot: {'posicion': (0, 0), 'bateria': 70, 'objetivo_alcanzado': False}
🔋 Batería recargada preventivamente al 100%
Paso 1: Acción = recargar, Estado = {'posicion': (0, 0), 'bateria': 85, 'objetivo_alcanzado': False}, Recompensa = 5
Paso 2: Acción = adelante, Estado = {'posicion': (1, 0), 'bateria': 70, 'objetivo_alcanzado': False}, Recompensa = -1
Paso 3: Acción = adelante, Estado = {'posicion': (2, 0), 'bateria': 55, 'objetivo_alcanzado': False}, Recompensa = -1
Paso 4: Acción = adelante, Estado = {'posicion': (3, 0), 'bateria': 40, 'objetivo_alcanzado': False}, Recompensa = -1
Paso 5: Acción = derecha, Estado = {'posicion': (3, 1), 'bateria': 25, 'objetivo_alcanzado': False}, Recompensa = -1
Paso 6: Acción = derecha, Estado = {'posicion': (3, 2), 'bateria': 10, 'objetivo_alcanzado': False}, Recompensa = -5
🔋 Batería recargada al 100%
Paso 7: Acción = recargar, Estado = {'posicion': (3, 2), 'bateria': 100, 'objetivo_alcanzado': False}, Recompensa = 5
Paso 8: Acción = derecha, Estado = {'posicion': (3, 3), 'bateria': 85, 'objetivo_alcanzado': True}, Recompensa = 20

✅ Simulación terminada: objetivo alcanzado en 8 pasos.

Recompensa total obtenida: 21

```
---

## 🚀 Posibles Mejoras
- Implementar aprendizaje por refuerzo para optimizar la recompensa a largo plazo.  
- Ampliar el tamaño de la grilla o introducir obstáculos.

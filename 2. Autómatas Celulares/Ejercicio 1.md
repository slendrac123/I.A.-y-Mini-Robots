## Escenario 1: Entorno del Hogar (AC 3D aislado)

| Característica | Definición |
| :-- | :-- |
| **Cuadrícula (espacio)** | Matriz **3D** `grid[z][y][x]` con capas por piso (`z=0` Piso 1, `z=1` Piso 2). Cada celda es un micro-espacio (habitación, sala, cocina, baño, escalera, patio). |
| **Estados posibles** | `Dormido (0)`, `Despierto-inactivo (1)`, `Activo (2)`, `Ausente (3)` |
| **Tiempo** | Discreto: `t = 0,1,2,...` (1 paso ≈ 1 minuto) |
| **Condición de frontera** | Fija: fuera del contorno de la casa siempre es `0` (aislamiento del exterior) |
| **Tipo de vecindad** | Moore **3D** (hasta 26 vecinos) con pesos de conectividad: `W=1` (puerta abierta), `W=0.5` (contacto vertical entre pisos), `W=0` (muro) |
| **Regla 1 (Mañana)** | Si una celda de **habitación** está en `Dormido` y `hora(t) ≥ 06:00`, pasa a `Despierto-inactivo`. |
| **Regla 2 (Interacción)** | Si una celda `Activo` está en una zona común (cocina, sala, pasillo), los vecinos conectados `Despierto-inactivo` pasan a `Activo`. |
| **Regla 3 (Escaleras)** | Si hay una celda de escalera activa en el otro piso, la escalera del piso actual se activa. |
| **Regla 4 (Ausencia)** | Si una celda está en `Activo` y `hora(t) ≥ 06:30`, pasa a `Ausente` (sale de casa). |
| **Regla 5 (Noche)** | Si una celda está en `Activo` y `hora(t) ≥ 22:00`, pasa a `Dormido`. |

---

## Escenario 2: Entorno Universitario (Campus 3D multicapa con atrayentes)

| Característica | Definición |
| :-- | :-- |
| **Cuadrícula (espacio)** | Matriz **3D** `Campus[z][y][x]`: `z=0` campus (caminos), `z>0` pisos de edificios (salones, pasillos, escaleras). |
| **Estados posibles** | `-1` = No transitable, `0` = Transitable vacío, `1` = Estudiante en tránsito, `2` = En clase, `3` = Aula destino (atrayente) |
| **Tiempo** | Discreto, sincronizado con el horario de clases |
| **Tipo de vecindad** | Moore **3D** (26 vecinos) |
| **Regla 1 (Activación del atrayente)** | Al iniciar la clase, el salón correspondiente cambia a estado `3`; el salón anterior vuelve a `0`. |
| **Regla 2 (Movimiento por gradiente)** | Una celda `1` se mueve al vecino transitable que minimice la distancia al atrayente `3` (incluye escaleras para cambiar de piso). |
| **Regla 3 (Congestión)** | Si varias celdas `1` intentan entrar a la misma celda (puertas/escaleras), solo una avanza; las demás esperan. |
| **Regla 4 (Llegada a clase)** | Si un `1` llega a una celda vecina del `3`, entra al aula y pasa a estado `2` (estático durante la clase). |
| **Regla 5 (Huecos)** | Al terminar la clase, `2 → 1` y el nuevo atrayente `3` es cafetería o biblioteca. |

---

## Escenario 3: Entorno de Transporte (Moto en tráfico multicarril)

| Característica | Definición |
| :-- | :-- |
| **Cuadrícula (espacio)** | Matriz **2D multicarril** `Vía[carril][posición]` con sub-carriles para permitir filtrado |
| **Estados posibles** | `-1` = Vacío, `(1, v)` = Carro con `v ∈ [0, V_max]`, `(2, v)` = Moto con `v ∈ [0, V_max]` |
| **Tiempo** | Discreto: cada paso representa un instante de conducción |
| **Tipo de vecindad** | Vecindad frontal (hacia adelante) + lateral (cambio de carril/filtrado) |
| **Regla 1 (Lane splitting)** | Si el frente está bloqueado y el sub-carril lateral está libre, la moto cambia de carril. |
| **Regla 2 (Aceleración)** | Si hay espacio libre adelante: `v → min(v + 1, V_max)`. |
| **Regla 3 (Frenado)** | Si la distancia `d` al vehículo de enfrente es menor que `v`, entonces `v → d - 1`. |
| **Regla 4 (Aleatoriedad)** | Con probabilidad `p`, `v → max(v - 1, 0)` (precaución, lluvia, huecos). |
| **Regla 5 (Movimiento)** | La moto avanza: `x → x + v`. |

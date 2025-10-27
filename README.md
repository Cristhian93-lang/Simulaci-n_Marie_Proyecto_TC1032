# Simulacion_Marie_Proyecto_TC1032

# Simulación del Sistema de Enfriamiento de un Motor Automotriz (MARIE.js)

## Descripción del Proyecto
Este programa simula el funcionamiento del sistema de enfriamiento de un motor de automóvil, desarrollado en el simulador MARIE.js.  
A medida que el motor incrementa su velocidad, también lo hace su temperatura, lo que activa un ventilador de enfriamiento con distintos niveles de potencia para mantener la temperatura dentro de límites seguros.

El objetivo del proyecto es modelar el control automático de la temperatura del motor en base a su velocidad y mostrar cómo la unidad de control lógico responde con distintos niveles del ventilador.

---

## Equipo ThermoFlow

- Cristhian Viery Maida Suarez – A01668790  
- Raúl Alejandro Momox Chávez – A01707900  
- Iker Rodríguez Amaro – A01712814  
- Gerardo Martínez Carbajal – A01713474  

---

## Funcionamiento General

1. El usuario ingresa la velocidad máxima del motor (`VelocidadMaxima`).
2. El sistema inicializa:
   - `VelocidadActual = 0`
   - `TemperaturaActual = 70°C`
3. En cada iteración:
   - La velocidad del motor aumenta en +10 unidades.
   - La temperatura del motor sube en +2°C.
   - Se evalúa la temperatura para determinar el estado del ventilador.
4. En cada ciclo, el programa muestra tres valores:
   - VelocidadActual  
   - TemperaturaActual  
   - EstadoVentilador  
5. La simulación se detiene cuando el motor alcanza su velocidad máxima.

---

## Estados del Ventilador

| Temperatura (°C) | Estado del Ventilador | Descripción |
|------------------:|:----------------------|:-------------|
| < 90              | 0 → Apagado           | El motor no requiere enfriamiento |
| 90–94             | 1 → Lento             | Se activa el ventilador lentamente |
| 95–99             | 2 → Rápido            | El ventilador aumenta la velocidad |
| ≥ 100             | 3 → Alarma            | Temperatura crítica, activar alarma |

---

## Variables Principales

| Variable | Descripción |
|-----------|--------------|
| `VelocidadMaxima` | Límite máximo de velocidad del motor |
| `VelocidadActual` | Velocidad actual del motor (aumenta cada ciclo) |
| `TemperaturaActual` | Temperatura actual del motor |
| `EstadoVentilador` | Nivel de potencia del ventilador (0–3) |
| `TempBase` | Temperatura inicial (70°C) |
| `IncrementoVelo` | Incremento de velocidad por iteración (+10) |
| `IncrementoTemp` | Incremento de temperatura por iteración (+2°C) |

---

## Lógica de Control del Ventilador

El control se basa en comparaciones (`Subt`) y condiciones (`Skipcond 800`):
Si TemperaturaActual ≥ 100 → Estado = 3 (Alarma)
Si TemperaturaActual ≥ 95 → Estado = 2 (Rápido)
Si TemperaturaActual ≥ 90 → Estado = 1 (Lento)
Si TemperaturaActual < 90 → Estado = 0 (Apagado)


De esta manera, el programa simula cómo el sistema de enfriamiento automotriz responde de forma escalonada a las condiciones térmicas del motor.

---

## Instrucciones MARIE utilizadas

| Instrucción | Descripción |
|--------------|--------------|
| `Input` | Solicita al usuario la velocidad máxima del motor |
| `Output` | Muestra valores en la consola (velocidad, temperatura, estado) |
| `Load` / `Store` | Carga y guarda valores en memoria |
| `Add` / `Subt` | Incrementa o compara valores |
| `Skipcond` | Evalúa condiciones lógicas del acumulador |
| `Jump` | Controla el flujo del programa |
| `Halt` | Detiene la ejecución |

---

## Cómo Ejecutarlo en MARIE.js

1. Abre el simulador [MARIE.js](https://marie.js.org/).  
2. Copia el contenido del archivo `.mas` en el editor.  
3. Da clic en **Assemble** y luego en **Run**.  
4. Ingresa la velocidad máxima del motor (por ejemplo, `100`).  
5. Observa cómo cambian los valores de velocidad, temperatura y estado del ventilador en la salida.

---

## Ejemplo de Salida

Input: 100
Output:
Velocidad: 10 Temperatura: 72 Estado: 0
Velocidad: 20 Temperatura: 74 Estado: 0
Velocidad: 30 Temperatura: 76 Estado: 0
Velocidad: 40 Temperatura: 78 Estado: 0
Velocidad: 50 Temperatura: 80 Estado: 0
Velocidad: 60 Temperatura: 82 Estado: 0
Velocidad: 70 Temperatura: 84 Estado: 0
Velocidad: 80 Temperatura: 86 Estado: 0
Velocidad: 90 Temperatura: 88 Estado: 1
Velocidad: 100 Temperatura: 90 Estado: 1

## Conceptos de Arquitectura MARIE aplicados

- **Memoria Principal:** Almacena todas las variables del sistema.  
- **Acumulador (AC):** Registra resultados temporales de operaciones aritméticas.  
- **Unidad de Control:** Gestiona los saltos condicionales (`Skipcond`) y bucles (`Jump`).  
- **Entrada/Salida:** Interacción con el usuario mediante `Input` y `Output`.  
- **Ciclo de instrucción:** `Fetch → Decode → Execute → Store`.

---

## Conclusión

Este proyecto demuestra cómo el lenguaje ensamblador MARIE puede utilizarse para simular el comportamiento de sistemas físicos de control automotriz, en este caso el sistema de enfriamiento de un motor de auto.  
El programa aplica condiciones lógicas y control por niveles, mostrando el principio del control térmico automático en los motores modernos.



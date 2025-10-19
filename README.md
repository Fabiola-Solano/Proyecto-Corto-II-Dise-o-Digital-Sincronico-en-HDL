# Proyecto Corto II Diseño Digital Sincronico en HDL
**Curso:** EL-3307 Diseño Lógico  
**Institución:** Instituto Tecnológico de Costa Rica  
**Semestre:** II Semestre 2025  
**Integrantes:**  
- José Andrés Acosta Sosa  
- Fabiola María Solano Guillén

---

## 1. Introducción

El presente proyecto tiene como objetivo implementar un sistema digital sincrónico utilizando SystemVerilog y una FPGA Tang Nano 9K. El sistema permite capturar dos números decimales positivos desde un teclado hexadecimal, realizar su suma aritmética sin signo y desplegar tanto los datos ingresados como el resultado en cuatro displays de 7 segmentos.  
Este trabajo integra conceptos de máquinas de estados (FSM), sincronización de señales, eliminación de rebotes, decodificación, multiplexación y diseño digital modular.

---

## 2. Objetivo general

Desarrollar un sistema digital sincrónico en HDL capaz de capturar, procesar y desplegar datos ingresados mediante un teclado hexadecimal utilizando una FPGA.

### Objetivos específicos

- Implementar la lectura y eliminación de rebotes de un teclado hexadecimal.  
- Capturar dos números decimales de hasta tres dígitos mediante una FSM de control.  
- Realizar la suma de ambos números en lógica digital.  
- Desplegar los datos y el resultado en cuatro displays de 7 segmentos.  
- Validar el sistema mediante simulaciones RTL y post-síntesis.  
- Analizar consumo de recursos, frecuencia máxima y funcionamiento final en FPGA.

---

## 3. Planteamiento del problema

Se requiere la construcción de un sistema digital que:  
a) Reciba dos números decimales usando un teclado hexadecimal (0–9, A–F).  
b) Elimine el rebote mecánico y sincronice las entradas con un reloj de 27 MHz.  
c) Almacene cada número mediante registros y permita operar en formato de calculadora tradicional.  
d) Sume ambos números sin signo.  
e) Muestre los números ingresados y el resultado en displays de 7 segmentos multiplexados.

---

## 4. Funcionamiento general del sistema

El sistema se divide en tres subsistemas principales:

### 4.1. Subsistema de lectura del teclado hexadecimal
- Barrido de columnas (scanning) y monitoreo de filas.  
- Eliminación de rebotes mediante filtros o contadores sincronizados.  
- Registro del dígito pulsado y control mediante FSM para:  
  - Ingreso del primer número  
  - Ingreso del segundo número  
  - Ejecución de la suma

*[Insertar aquí diagrama de bloques del lector de teclado]*

---

### 4.2. Subsistema de suma aritmética
- Recibe los dos operandos ya almacenados en registros.  
- Realiza la suma en binario utilizando operadores de SystemVerilog.  
- Entrega el resultado como bus de datos al subsistema de despliegue.

*[Insertar aquí diagrama del sumador y registros]*

---

### 4.3. Subsistema de despliegue en displays de 7 segmentos
- Decodificación BCD → 7 segmentos.  
- Multiplexación de 4 displays con cátodo común.  
- Uso de divisores de frecuencia para refresco visual (>200 Hz).

*[Insertar aquí diagrama del sistema de displays]*

---

## 5. Máquinas de Estados (FSM)

- FSM principal: controla inicio, ingreso del primer número, ingreso del segundo número y suma final.  
- Estados sugeridos:
  - `IDLE`  
  - `INPUT_A`  
  - `INPUT_B`  
  - `SUM`  
  - `DISPLAY_RESULT`

*[Insertar aquí diagrama FSM]*

---

## 6. Simulaciones

- Simulación del lector de teclado con señales de rebote.  
- Simulación del sumador con casos como: 000 + 000, 123 + 456, 999 + 001.  
- Verificación de la señal `clk_27MHz` y divisores de frecuencia.

*[Insertar capturas de waveform o archivos .vcd]*

---

## 7. Análisis de recursos y temporización

| Recurso            | Utilización |
|--------------------|-------------|
| LUTs               | (por completar) |
| Flip-Flops (FFs)   | (por completar) |
| Pines de E/S       | (por completar) |
| Frecuencia máxima  | ≥ 27 MHz requerida |

---

## 8. Problemas encontrados y soluciones aplicadas

| Problema | Solución aplicada |
|----------|--------------------|
| Rebote excesivo en teclas | Implementación de contador sinc. de 10–20 ms |
| Inestabilidad del multiplexado | Generación de reloj dividido estable |
| Captura incorrecta de dígitos | Añadir doble registro síncrono (FF) |

---

## 9. Referencias

- Pong P. Chu – *FPGA Prototyping by SystemVerilog Examples*  
- Andrew House – *Hex Keypad Explanation*  
- Wiki de Tang Nano 9K – David Medina  
- Manual DSO-X2002A Keysight (lógica digital y analizador)

---

## 10. Créditos

Proyecto realizado por:  
- **José Andrés Acosta Sosa**  
- **Fabiola María Solano Guillén**

---

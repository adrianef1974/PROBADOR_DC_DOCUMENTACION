# PRUEBA 01 — Flip-flop astable con dos BC817

## Objetivo
Multivibrador astable de dos transistores NPN BC817. Los LED deben encenderse alternadamente con 5 V CC.

## Componentes
| Ref. | Cant. | Valor / componente |
|---|---:|---|
| Q1, Q2 | 2 | BC817, NPN, SOT-23 |
| R1, R2 | 2 | 47 kΩ, 1/4 W — polarización de bases |
| R3, R4 | 2 | 1 kΩ, 1/4 W — limitación de corriente |
| C1, C2 | 2 | 10 µF, mínimo 10 V |
| LED1, LED2 | 2 | LED rojo estándar |
| C3 | 1 | 100 nF cerámico — desacoplo |
| J1 | 1 | Entrada +5 V y GND |

## Conexiones
- Q1: emisor a GND; colector al cátodo de LED1.
- LED1: ánodo a +5 V mediante R3 de 1 kΩ; cátodo al colector de Q1.
- Q2: emisor a GND; colector al cátodo de LED2.
- LED2: ánodo a +5 V mediante R4 de 1 kΩ; cátodo al colector de Q2.
- R1 de 47 kΩ entre +5 V y base de Q1.
- R2 de 47 kΩ entre +5 V y base de Q2.
- C1 de 10 µF entre colector de Q1 y base de Q2.
- C2 de 10 µF entre colector de Q2 y base de Q1.
- C3 de 100 nF entre +5 V y GND, cerca de los transistores.

### Polaridad de C1 y C2
Para electrolíticos, conectar el positivo hacia el colector y el negativo hacia la base opuesta. Verificar tensiones durante la puesta en marcha. También pueden usarse capacitores no polarizados.

## Esquema funcional (conexiones cruzadas)
```text
Rama 1: +5 V — R3 1 kΩ — ánodo LED1; cátodo LED1 — colector Q1
Rama 2: +5 V — R4 1 kΩ — ánodo LED2; cátodo LED2 — colector Q2
Q1 y Q2: emisores a GND
+5 V — R1 47 kΩ — base Q1
+5 V — R2 47 kΩ — base Q2
Colector Q1 — C1 10 µF — base Q2
Colector Q2 — C2 10 µF — base Q1
C3 100 nF entre +5 V y GND
```

## Funcionamiento esperado
Al encender, pequeñas diferencias hacen que un transistor conduzca primero. Su colector cae y el capacitor cruzado lleva momentáneamente baja la base del otro transistor. Luego el capacitor se carga a través de la resistencia de base y el estado cambia. Los LED alternan continuamente.

Con 47 kΩ y 10 µF, cada estado durará aproximadamente unas décimas de segundo; el tiempo real depende de los componentes y de la tensión.

## Comprobaciones
1. Alimentar con 5 V CC regulados y limitar la corriente de la fuente durante la primera prueba.
2. Comprobar el pinout del BC817 en la hoja de datos del fabricante exacto. No asumir el orden de patas sin verificarlo.
3. Comprobar que los emisores estén a GND y que no haya cortocircuitos entre +5 V y GND.
4. Medir los colectores: deben alternar entre nivel bajo y alto.
5. Si no oscila, revisar pinout, polaridad de C1/C2 y conexiones cruzadas.

## Simulación y archivos CAD
La topología puede simularse con SPICE usando un modelo compatible. Para una simulación fiel, importar el modelo SPICE del fabricante del BC817 elegido. Un NPN genérico sirve solo para comprobar la oscilación, no para validar corrientes o límites del transistor.

El archivo nativo de Proteus 9 y la simulación quedan pendientes de verificación en Proteus; este documento no afirma que esos archivos ya estén creados o validados.

**Estado:** diseño inicial documentado.
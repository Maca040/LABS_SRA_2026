# LAB_SRA_2026

Laboratorio de filtros de **Síntesis de Redes Activas** (FCEFyN, UNC), ciclo lectivo 2026.

## Integrantes
* Blanco, Luciano
* González, Macarena
* Narváez, Jenifer
* Román, Bianca

## Docentes
* Prof. Pablo Ferreyra
* Prof. César Reale
  
## Filtro implementado

Pasabajos Butterworth de orden 3, $W_n = 8900$ rad/s, con TL082 a ±15 V.
Plantilla: $A_p \le 1$ dB en 1 kHz y $A_s \ge 24$ dB en 4 kHz.
Cascada de una sección $R_3C_3$ + seguidor y una celda Sallen-Key de ganancia unitaria.

| Componente | Valor |
|---|---|
| $R_3$ | 11 kΩ (10 kΩ + 1 kΩ, 1 %) |
| $R_1 = R_2$ | 12 kΩ (5 %) |
| $C_1$, $C_2$, $C_3$ | 4,7 nF, 18 nF, 10 nF (poliéster, 5 %) |

**Medido:** 0,44 dB en 1 kHz, ≥ 24,6 dB en 4 kHz, $f_{-3\,\mathrm{dB}}$ = 1433 Hz (9004 rad/s).

## Estructura

```
LABS_SRA_2026/
├── NIVEL I/
│   ├── Esquematico/
│   ├── Fotos_laboratorio/
│   ├── Mediciones_Lab/
│   ├── Scripts/
│   ├── Simulacion_LTspice/
│   └── InformeFiltro_NIVEL1.pdf
├── NIVEL II/
│   ├── Script/
│   ├── SimulacionesLTspice/
│   ├── TablasObtenidas/
│   └── Nivel2TP_Filtro.pdf
└── README.md
```

### Nivel I: diseño, simulación y construcción

| Carpeta / archivo | Contenido |
|---|---|
| `Esquematico/` | Esquema del circuito. |
| `Scripts/` | Notebooks de diseño y análisis (tabla de abajo). |
| `Simulacion_LTspice/` | Simulación del pasabajos en LTspice. |
| `Fotos_laboratorio/` | Montaje y capturas del osciloscopio. |
| `Mediciones_Lab/` | Mediciones en CSV: componentes, barrido total, cada etapa, linealidad, escalón y continua. |
| `InformeFiltro_NIVEL1.pdf` | Informe del Nivel I. |

Notebooks de `Scripts/`, en orden de uso:

| Notebook | Contenido |
|---|---|
| `1_analisis_4casos` | Diseño matemático de los cuatro casos (SciPy). |
| `2_BodeAnalisis` | Magnitud, fase y retardo de grupo de las aproximaciones. |
| `4_Analisis_Circuital_Simbolico_Actualizado` | Análisis nodal simbólico, $H_c(s)$ vs $H_t(s)$ (SymPy). |
| `5_Componentes_y_Tolerancias` | Ventana de $W_n$, valores comerciales, tolerancias y verificación del TL082. |
| `6_Sensitividad` | Sensibilidades $S_x^{\omega_0}$ y $S_x^Q$, validación con ±1 %. |
| `8_Mediciones_Laboratorio` | Procesamiento de mediciones y contraste con el modelo. |

### Nivel II: análisis estadístico de tolerancias

Monte Carlo de 500 corridas en LTspice con cuatro combinaciones de tolerancias, comparado con la sensibilidad lineal.

| Carpeta / archivo | Contenido |
|---|---|
| `SimulacionesLTspice/` | Netlist `Filtro_MC.cir` y `.log` de las corridas. |
| `Script/` | Notebook y script de procesamiento de los `.log`. |
| `TablasObtenidas/` | Tablas y figuras de resultados. |
| `Nivel2TP_Filtro.pdf` | Informe del Nivel II. |

## Uso

Los notebooks instalan sus dependencias y están pensados para correr en **Google Colab**, sin configuración local.

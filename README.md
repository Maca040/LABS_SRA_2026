# LAB_SRA_2026
Repositorio correspondiente al laboratorio de filtros de la materia Síntesis de Redes Activas, ciclo lectivo 2026.

## Integrantes
* Blanco, Luciano
* González, Macarena
* Narváez, Jenifer
* Román, Bianca

## Docentes
* Prof. Pablo Ferreyra
* Prof. César Reale

## Contenido
El laboratorio comprende el desarrollo teórico, el diseño, las simulaciones de los circuitos y los scripts de procesamiento en Python.

## Estructura

| Carpeta / archivo | Contenido |
|---|---|
| `Scripts/1_analisis_4casos.ipynb` | Diseño matemático de los cuatro casos (SciPy). |
| `Scripts/2_BodeAnalisis.ipynb` | Comparación de aproximaciones: magnitud, fase y retardo de grupo. |
| `Scripts/4_Analisis_Circuital_Simbolico_Actualizado.ipynb` | Análisis nodal simbólico y comparación $H_c(s)$ vs $H_t(s)$ (SymPy). |
| `Scripts/5_Componentes_y_Tolerancias.ipynb` | Ventana de $W_n$, valores comerciales, tolerancias (peor caso y Monte Carlo), verificación del TL082 y valores esperados para el laboratorio. Genera `Figuras/respuesta_vs_plantilla.png`. |
| `Scripts/6_Sensitividad.ipynb` | Sensibilidades $S_x^{\omega_0}$ y $S_x^Q$ y validación con perturbaciones de ±1 %. |
| `Scripts/8_Mediciones_Laboratorio.ipynb` | Procesamiento de las mediciones y contraste con el modelo evaluado con los componentes medidos. Genera `Figuras/lab_bode_medido.png` y `Figuras/lab_etapas_medido.png`. |
| `Datos/` | Mediciones del laboratorio en CSV: componentes, barrido total, cada etapa, linealidad, escalón y verificaciones en continua. |
| `Esquematico/` | Esquemático completo del filtro (circuitikz, compilar con pdfLaTeX) y su imagen. |
| `Figuras/` | Figuras generadas por los notebooks. |
| `Fotos_laboratorio/` | Fotos del montaje y capturas del osciloscopio usadas en el informe. |
| `InformeFiltro.pdf` | Informe final. |

## Cómo reproducir los resultados

Requisitos: Python 3 con `numpy`, `scipy`, `pandas`, `matplotlib` y Jupyter.

```bash
pip install numpy scipy pandas matplotlib jupyter
cd Scripts
jupyter notebook
```

Los notebooks 5 y 8 leen los datos de `../Datos` y guardan las figuras en `../Figuras`, así que deben ejecutarse desde la carpeta `Scripts`. Los porcentajes de cumplimiento del Monte Carlo pueden variar unas décimas según la semilla aleatoria.

## Filtro implementado

Pasabajos Butterworth de orden 3, $W_n = 8900$ rad/s ($f_p = 1$ kHz con $A_p \le 1$ dB; $f_s = 4$ kHz con $A_s \ge 24$ dB). Cascada de una sección de primer orden ($R_3 C_3$ + seguidor) y una celda Sallen-Key con ganancia unitaria, con un TL082 alimentado a ±15 V.

| Componente | Valor |
|---|---|
| $R_3$ | 11 kΩ (10 kΩ + 1 kΩ en serie, 1 %) |
| $R_1 = R_2$ | 12 kΩ (5 %) |
| $C_1$, $C_2$, $C_3$ | 4,7 nF, 18 nF, 10 nF (poliéster, 5 %) |

Resultados medidos: atenuación de 0,44 dB en 1 kHz, al menos 24,6 dB en 4 kHz y frecuencia de −3 dB de 1433 Hz (9004 rad/s).

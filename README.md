# Monitoreo predictivo de máquinas industriales mediante Modelos Ocultos de Markov (HMM)

## 1. Descripción del proyecto

Este proyecto desarrolla una simulación de monitoreo de una máquina industrial mediante un **Modelo Oculto de Markov (HMM)**. Su propósito es estimar el estado de funcionamiento de una máquina a partir de observaciones de vibración y analizar cómo puede utilizarse esta información para apoyar las decisiones de mantenimiento.

El modelo considera tres estados internos que no se pueden observar directamente:

- **Sano:** la máquina funciona normalmente.
- **Desgaste:** la máquina presenta señales de deterioro.
- **Crítico:** la máquina presenta una condición que requiere atención.

También se consideran tres observaciones posibles:

- **Baja:** nivel bajo de vibración.
- **Media:** nivel medio de vibración.
- **Alta:** nivel alto de vibración.

## 2. Objetivo

Implementar y evaluar un Modelo Oculto de Markov para estimar los posibles estados de una máquina industrial a partir de observaciones de vibración, utilizando algoritmos probabilísticos y simulaciones.

Como mejora complementaria, se incorpora un sistema de alertas que transforma las probabilidades estimadas por el modelo en recomendaciones de mantenimiento.

## 3. Tecnologías utilizadas

- Python.
- Jupyter Notebook / Google Colab.
- NumPy.
- Pandas.
- Matplotlib.
- Algoritmos de Modelos Ocultos de Markov.

## 4. Metodología

El desarrollo del proyecto contempla los siguientes componentes:

### 4.1. Construcción del modelo HMM

Se definen los siguientes elementos:

- **Probabilidades iniciales (π):** representan la probabilidad inicial de cada estado.
- **Matriz de transición (A):** representa las probabilidades de pasar de un estado a otro.
- **Matriz de emisión (B):** representa las probabilidades de observar un determinado nivel de vibración según el estado de la máquina.

### 4.2. Algoritmos implementados

Se utilizan tres algoritmos principales:

- **Forward:** calcula las probabilidades de los estados ocultos teniendo en cuenta las observaciones recibidas.
- **Viterbi:** permite encontrar la secuencia de estados ocultos más probable.
- **Baum-Welch:** permite estimar los parámetros del modelo a partir de secuencias de observaciones.

### 4.3. Simulaciones y análisis

Se trabajan cuatro escenarios experimentales (E1, E2, E3 y E4), modificando las condiciones y parámetros del modelo.

Se realizan 500 simulaciones por escenario para analizar y comparar su comportamiento.

El análisis contempla medidas estadísticas como:

- Media.
- Desviación estándar.
- Valor mínimo y máximo.
- Intervalos de confianza del 95 %.
- Matriz de confusión.
- Retardo en la detección de estados críticos.

## 5. Mejora implementada: sistema de alertas de mantenimiento

Como aporte complementario, se desarrolla una función que utiliza las probabilidades calculadas mediante Forward para generar recomendaciones según la probabilidad de que la máquina se encuentre en estado Crítico.

Se establecen tres niveles de alerta:

| Probabilidad del estado Crítico | Recomendación |
|---|---|
| Menor al 30 % | Monitoreo normal |
| Desde 30 % y menor al 60 % | Programar inspección |
| Igual o superior al 60 % | Alerta de mantenimiento |

Estos umbrales son valores de referencia definidos para la simulación y no representan estándares industriales validados.

### Código de la mejora

```python
def generar_alerta(probabilidades):
    prob_critico = probabilidades[2]

    if prob_critico < 0.30:
        return "Monitoreo normal"
    elif prob_critico < 0.60:
        return "Programar inspeccion"
    else:
        return "Alerta de mantenimiento"
```

La función permite convertir los resultados probabilísticos del modelo en recomendaciones más fáciles de interpretar y utilizar como apoyo a la toma de decisiones.

## 6. Estructura del repositorio

La organización sugerida del proyecto es:

```text
monitoreo-industrial-hmm/
│
├── notebooks/
│   └── modelo_hmm.ipynb
│
├── resultados/
│   ├── graficas/
│   └── tablas/
│
├── documentos/
│   └── informe_actividad.pdf
│
├── evidencias/
│   └── capturas_resultados/
│
└── README.md
```

Los nombres y carpetas deben ajustarse a los archivos que realmente se incluyan en el repositorio.

## 7. Requisitos para ejecutar el proyecto

Se requiere tener instalado Python y las siguientes bibliotecas:

```bash
pip install numpy pandas matplotlib scipy scikit-learn
```

También se puede ejecutar el notebook desde Google Colab sin necesidad de instalar Python localmente.

## 8. Instrucciones de ejecución

1. Descargar o clonar el repositorio.
2. Abrir el notebook principal ubicado en la carpeta `notebooks`.
3. Verificar que las bibliotecas requeridas estén instaladas.
4. Ejecutar las celdas en orden.
5. Revisar las simulaciones, las gráficas y los resultados estadísticos.
6. Ejecutar la sección correspondiente al sistema de alertas para observar las recomendaciones generadas.

Para clonar el repositorio:

```bash
git clone URL_DEL_REPOSITORIO
```

## 9. Resultados esperados

Con el desarrollo del proyecto se busca:

- Estimar los estados internos de una máquina industrial mediante observaciones de vibración.
- Analizar el comportamiento del modelo en diferentes escenarios.
- Comparar los resultados obtenidos mediante los algoritmos Forward, Viterbi y Baum-Welch.
- Evaluar el comportamiento del modelo mediante medidas estadísticas.
- Generar recomendaciones de mantenimiento según la probabilidad estimada del estado Crítico.

## 10. Conclusiones

Los Modelos Ocultos de Markov permiten representar situaciones en las que el estado real de un sistema no es observable directamente, pero se cuenta con observaciones que ayudan a estimarlo.

Mediante las simulaciones y los algoritmos implementados es posible analizar diferentes condiciones de funcionamiento de una máquina industrial.

La mejora del sistema de alertas complementa el modelo al transformar las probabilidades obtenidas mediante Forward en recomendaciones de mantenimiento, facilitando la interpretación de los resultados y el apoyo a la toma de decisiones.

## 11. Autores

- [David Castro]
- [Santiago Henao]
- [Dilbani Enriquez]

## 12. Información académica

- **Institución:** IU Digital de Antioquia.
- **Programa:** Ingeniería en Desarrollo de Software y Datos.
- **Asignatura:** Simulación.
- **Actividad:** Módulo 2 – Actividad didáctica 2.
- **Tema:** Modelos Ocultos de Markov aplicados al monitoreo industrial.

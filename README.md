# Asociación entre la pendiente del segmento ST y la enfermedad cardíaca

Trabajo Práctico Final de **Bioestadística (16.43)**, Ingeniería Biomédica, Instituto Tecnológico de Buenos Aires (ITBA). Trabajo en equipo de 3 personas, junio de 2026.

**Informe completo (HTML):** `TP_Bioestadistica.html`. Descargalo y abrilo en el navegador, o activá GitHub Pages para verlo online (ver abajo).

## Pregunta de investigación (PICO)

En pacientes evaluados por riesgo cardiovascular, ¿se asocia una pendiente anormal del segmento ST (plana o descendente), frente a una normal o ascendente, con una mayor probabilidad de enfermedad cardíaca?

## Datos

[Heart Failure Prediction Dataset](https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction) (Kaggle, fedesoriano): 918 registros originales, 917 pacientes en el análisis final (507 con enfermedad cardíaca y 410 sin ella). Es un estudio observacional, transversal y de análisis secundario, por lo que los resultados describen asociaciones y no causalidad. Los derechos de los datos pertenecen a sus autores originales; consultá las condiciones de uso en la página de Kaggle.

## Métodos

- Depuración y descripción de la base (`tableone`).
- Normalidad (Shapiro-Wilk, Lilliefors, histogramas y QQ-plots) y cálculo de tamaño muestral y poder (`pwr`).
- Análisis univariado: t de Welch y Mann-Whitney para variables cuantitativas, tests de proporciones para categóricas.
- Regresión logística: modelo crudo (PICO), modelo saturado, evaluación de confusión, modelo final reducido, análisis de sensibilidad con colesterol e interacciones con sexo, edad y angina de esfuerzo.
- Diagnóstico y desempeño: VIF, Hosmer-Lemeshow, curvas ROC y AUC (`pROC`), matriz de confusión.

## Resultados principales

| Medida | Valor |
|---|---|
| OR crudo (ST anormal vs. normal) | 18,64 |
| OR ajustado (modelo final) | 9,25 |
| AUC del modelo final | 0,903 |
| AUC del modelo saturado | 0,930 |

Se prefirió el modelo reducido por parsimonia e interpretabilidad. Los detalles, supuestos, limitaciones y la discusión están en el informe.

## Cómo reproducirlo

1. Instalar [R](https://www.r-project.org/) y, opcionalmente, RStudio.
2. Clonar el repositorio y abrir `TP_Bioestadistica.Rmd` en la carpeta del proyecto (el `.Rmd` usa rutas relativas a `heart.csv` y a las imágenes).
3. Ejecutar *Knit* a HTML. El primer bloque instala los paquetes que falten: `dplyr`, `readr`, `stringr`, `ggplot2`, `tableone`, `broom`, `pROC`, `ResourceSelection`, `pwr`, `nortest`, `car`, `epitools`, `scales` y `knitr`.

```r
rmarkdown::render("TP_Bioestadistica.Rmd")
```

## Estructura

```
├── TP_Bioestadistica.Rmd           # código y texto del informe (R Markdown)
├── TP_Bioestadistica.html          # informe renderizado
├── heart.csv                       # dataset
├── causes_of_death_world.png       # figuras usadas en la introducción
├── causes_of_death_argentina.png
└── ejemplo_st.png
```

## Créditos de las figuras

Los gráficos de causas de muerte provienen de [Our World in Data](https://ourworldindata.org/causes-of-death) (datos del IHME, Global Burden of Disease), bajo licencia CC BY.

---

## Summary (EN)

Final project for the Biostatistics course at ITBA (Biomedical Engineering). We studied the association between **ST-segment slope** and **heart disease** using the public *Heart Failure Prediction* dataset (917 patients after cleaning), with a PICO framework, normality testing, univariate comparisons (Welch's t-test, Mann-Whitney) and **logistic regression** in R. The crude odds ratio was 18.64 and the adjusted odds ratio 9.25; the final model reached an **AUC of 0.903**. The analysis is fully reproducible with R Markdown.

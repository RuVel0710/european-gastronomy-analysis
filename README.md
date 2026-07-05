# 🍽️ European Gastronomy Analysis | Análisis de Gastronomía Europea

> Interactive Power BI dashboard analyzing 110,000+ restaurants across 31 European cities — comparing ratings, price levels, review reliability, and cuisine trends, with a focus on Dublin, Geneva, and Zurich.
> Dashboard interactivo en Power BI que analiza más de 110,000 restaurantes en 31 ciudades europeas — comparando calificaciones, precios, confiabilidad de reseñas y tendencias gastronómicas, con foco en Dublín, Ginebra y Zúrich.

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-01284C?style=for-the-badge)
![Power Query](https://img.shields.io/badge/Power_Query-217346?style=for-the-badge)

---

## 🇬🇧 English

### 📋 Project overview

Interactive Power BI dashboard built from TripAdvisor data covering **110,807 restaurants across 31 European cities**. The project follows the complete analytics workflow — data cleaning, modeling, DAX measures, and visualization — to answer business questions about Europe's dining scene, with special attention to three key cities: Dublin, Geneva, and Zurich.

### 🎯 Objectives

The dashboard explores three analytical angles:
- **European comparison** — how do cities compare on restaurant ratings, price, and variety?
- **Key cities focus** — how do Dublin, Geneva, and Zurich perform, and how reliable are their ratings?
- **Value for money** — does paying more actually mean better-rated food?

### 📊 Dataset

- **Source:** TripAdvisor European restaurants (31 cities) — Kaggle
- **Records:** 125,527 restaurants (110,807 unique after modeling)
- **Cities:** 31 European cities including Dublin, Geneva, Zurich, Paris, London, Rome, Barcelona, Vienna, and more
- **Columns:** name, city, cuisine style, ranking, rating, price range, number of reviews, reviews

### 🛠️ Tools & techniques

- **Power BI Desktop** — modeling and visualization
- **Power Query (M language)** — data cleaning and transformation
- **DAX** — calculated measures
- **Data visualization** — dark-themed two-page report

### ⚙️ Data preparation (Power Query)

Real-world data is messy — this dataset required careful cleaning, which is a core part of the analysis:

- Removed non-analytical columns (URL, internal ID, index)
- Filtered out invalid ratings (value of -1, meaning "unrated")
- Translated price symbols into readable categories ($ → Economico, $$-$$$ → Medio, $$$$ → Alto)
- Replaced missing review counts with 0
- Cleaned the cuisine field (removed brackets and quotes) and **split multiple cuisines into rows** for deeper analysis

### 🧮 Key DAX measures

| Measure | Purpose |
|---------|---------|
| `Total Restaurants` | Unique restaurant count using `DISTINCTCOUNT` |
| `Average Rating` | Average rating, ignoring blanks honestly |
| `Total Reviews` | Corrected with `SUMX(VALUES(...))` to avoid row-duplication inflation |
| `Avg Reviews per Restaurant` | Review volume normalized per restaurant |

> **Analytical note:** splitting cuisines into rows duplicated each restaurant, which inflated a naive `SUM` of reviews from ~12.8M to ~60M. This was corrected with `SUMX` over unique restaurants — a common trap when a table's structure is transformed.

### 🔍 Key findings

**1. European cities are remarkably even.** Average ratings range only from 3.87 (Milan) to 4.26 (Athens) — a 0.39-point spread. Every city sits around 4.0, meaning there is no "bad" dining city in the dataset.

**2. Dublin leads its Swiss peers in review engagement.** Among the key cities, Dublin (4.12), Zurich (4.05), and Geneva (3.99) have similar ratings and a similar number of restaurants (~1,500–1,960 each). However, Dublin averages **157 reviews per restaurant** vs. Zurich's 69 and Geneva's 57 — likely reflecting Dublin's more tourism- and commerce-driven, English-speaking market (though language and platform-usage culture may also play a role).

**3. Higher price shows a slight quality edge — but budget options are still excellent.** Average rating rises modestly with price (Alto 4.24 > Economico 4.16 > Medio 4.03). The spread is small (0.21 points), so diners on a budget still find great options. Note: this analysis covers the ~53% of restaurants that have a recorded price.

**4. Dietary flexibility dominates cuisine tags.** The most common tag is "Vegetarian Friendly" (30,000+ restaurants), ahead of any national cuisine, with "Vegan Options" and "Gluten Free Options" also in the top 6 — reflecting a real market trend toward inclusive dining. (These are self-assigned tags that stack onto many cuisines, which partly explains their prevalence.)

### ⚠️ Honest limitations

- **~38% of restaurants have no price data** — price analysis reflects the recorded subset only.
- **~25% have no cuisine style** listed.
- Cuisine tags are self-assigned on TripAdvisor and can overlap.
- Ratings may reflect *expectations relative to price* — expensive venues are judged more harshly, so cross-price comparisons carry that caveat.

### 📸 Dashboard

![European Gastronomy Dashboard](dashboard.png)

---

## 🇪🇸 Español

### 📋 Descripción del proyecto

Dashboard interactivo en Power BI construido con datos de TripAdvisor que cubren **110,807 restaurantes en 31 ciudades europeas**. El proyecto recorre el flujo completo de análisis —limpieza, modelado, medidas DAX y visualización— para responder preguntas de negocio sobre la escena gastronómica europea, con atención especial a tres ciudades clave: Dublín, Ginebra y Zúrich.

### 🎯 Objetivos

El dashboard explora tres ángulos:
- **Comparación europea** — ¿cómo se comparan las ciudades en calificación, precio y variedad?
- **Ciudades clave** — ¿cómo se desempeñan Dublín, Ginebra y Zúrich, y qué tan confiables son sus calificaciones?
- **Relación calidad-precio** — ¿pagar más significa realmente comer mejor?

### 📊 Dataset

- **Origen:** TripAdvisor European restaurants (31 ciudades) — Kaggle
- **Registros:** 125,527 restaurantes (110,807 únicos tras el modelado)
- **Ciudades:** 31 ciudades europeas incluyendo Dublín, Ginebra, Zúrich, París, Londres, Roma, Barcelona, Viena, y más
- **Columnas:** nombre, ciudad, estilo de cocina, ranking, calificación, rango de precio, número de reseñas, reseñas

### 🛠️ Herramientas y técnicas

- **Power BI Desktop** — modelado y visualización
- **Power Query (lenguaje M)** — limpieza y transformación
- **DAX** — medidas calculadas
- **Visualización** — reporte de dos páginas con tema oscuro

### ⚙️ Preparación de datos (Power Query)

Los datos reales son desordenados — este dataset requirió limpieza cuidadosa, que es parte central del análisis:

- Eliminación de columnas no analíticas (URL, ID interno, índice)
- Filtrado de calificaciones inválidas (valor -1, que significa "sin calificar")
- Traducción de símbolos de precio a categorías legibles ($ → Economico, $$-$$$ → Medio, $$$$ → Alto)
- Reemplazo de reseñas faltantes por 0
- Limpieza del campo de cocina (corchetes y comillas) y **separación de cocinas múltiples en filas** para análisis profundo

### 🧮 Medidas DAX clave

| Medida | Propósito |
|--------|-----------|
| `Total Restaurants` | Conteo de restaurantes únicos con `DISTINCTCOUNT` |
| `Average Rating` | Calificación promedio, ignorando vacíos honestamente |
| `Total Reviews` | Corregida con `SUMX(VALUES(...))` para evitar inflación por duplicación de filas |
| `Avg Reviews per Restaurant` | Volumen de reseñas normalizado por restaurante |

> **Nota analítica:** separar las cocinas en filas duplicó cada restaurante, lo que infló una suma ingenua de reseñas de ~12.8M a ~60M. Se corrigió con `SUMX` sobre restaurantes únicos — una trampa común cuando se transforma la estructura de una tabla.

### 🔍 Hallazgos clave

**1. Las ciudades europeas están muy parejas.** Las calificaciones promedio van solo de 3.87 (Milán) a 4.26 (Atenas) — un rango de 0.39 puntos. Todas rondan el 4.0; no hay ninguna "mala" ciudad gastronómica.

**2. Dublín lidera a sus pares suizas en participación de reseñas.** Entre las ciudades clave, Dublín (4.12), Zúrich (4.05) y Ginebra (3.99) tienen calificaciones y cantidad de restaurantes similares (~1,500–1,960 cada una). Sin embargo, Dublín promedia **157 reseñas por restaurante** vs. 69 de Zúrich y 57 de Ginebra — probablemente por su carácter más turístico y comercial, y su mercado angloparlante (aunque el idioma y la cultura de uso de la plataforma también pueden influir).

**3. Mayor precio muestra una ligera ventaja de calidad — pero las opciones económicas siguen siendo excelentes.** La calificación sube levemente con el precio (Alto 4.24 > Economico 4.16 > Medio 4.03). El rango es pequeño (0.21 puntos), así que quien tiene presupuesto ajustado encuentra grandes opciones. Nota: este análisis cubre el ~53% de restaurantes con precio registrado.

**4. La flexibilidad dietética domina las etiquetas de cocina.** La etiqueta más común es "Vegetarian Friendly" (más de 30,000 restaurantes), por encima de cualquier cocina nacional, con "Vegan Options" y "Gluten Free Options" también en el top 6 — reflejando una tendencia real hacia la gastronomía inclusiva. (Son etiquetas auto-asignadas que se suman a muchas cocinas, lo que explica en parte su prevalencia.)

### ⚠️ Limitaciones honestas

- **~38% de los restaurantes no tienen dato de precio** — el análisis de precio refleja solo el subconjunto registrado.
- **~25% no tienen estilo de cocina** listado.
- Las etiquetas de cocina son auto-asignadas en TripAdvisor y pueden superponerse.
- Las calificaciones pueden reflejar *expectativas relativas al precio* — a los locales caros se les exige más, así que las comparaciones entre precios llevan esa salvedad.

### 📸 Dashboard

![Dashboard de Gastronomía Europea](dashboard.png)

---

## 👤 Autor | Author

**Jorge Rubén Velazquez Davila**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/rubvel/)

📜 Microsoft Data Analyst Professional Certificate (edX) · 2026

---

*Proyecto de portafolio · Portfolio project*

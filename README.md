# 🛍️ ¿Cuál es el mejor momento del año para comprar?

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/TU_USUARIO/TU_REPOSITORIO/blob/main/Analisis_Mercado_Alkosto.ipynb)

Proyecto académico de **Análisis de Mercados de Productos** — Alkosto, Bogotá, Colombia.

---

## 🤔 ¿Qué es esto?

Imagina que eres un **detective de ofertas** 🕵️. Tu misión es descubrir, para tres productos distintos,
**en qué mes del año conviene más comprarlos**. Este cuaderno reúne pistas reales y públicas de internet,
las organiza y, al final, te entrega una recomendación por producto, explicada paso a paso.

Los tres productos investigados son:

| Producto | ¿Por qué se eligió? |
|---|---|
| 📺 Televisor de 32 pulgadas | Producto electrónico de consumo masivo, tamaño de entrada |
| 💻 Computador de gama baja | Producto de tecnología con alta rotación y sensibilidad al precio |
| 📱 iPhone | Producto premium, fuertemente ligado al dólar y a lanzamientos anuales |

El archivo principal del proyecto es:

```
Analisis_Mercado_Alkosto.ipynb
```

---

## 🧠 ¿Cómo funciona la investigación, en palabras simples?

El cuaderno junta **tres pistas**, como si armara un rompecabezas 🧩, y las combina para dar una
recomendación final:

1. 🔎 **Qué tanto busca la gente cada producto en Google**, mes a mes, durante los últimos 5 años.
   Cuando menos personas buscan algo, es más probable que las tiendas ofrezcan descuentos para
   atraer compradores.
2. 💵 **Cuánto vale el dólar en pesos colombianos**, porque los tres productos se fabrican en el
   exterior y se pagan en dólares. Un dólar "barato" en pesos suele ser una buena señal para comprar
   productos importados.
3. 🎉 **Las fechas de descuentos oficiales en Colombia**: Día sin IVA, Black Friday, Cyber Monday,
   Hot Sale y la temporada de Navidad.

Con esas tres pistas juntas, el cuaderno arma una tabla final con el **mes recomendado por producto**,
la razón detrás de esa recomendación y un nivel de confianza (alto, si coincide con un evento oficial
de descuentos; medio, si se basa solo en el patrón de búsquedas).

---

## 🧰 ¿Qué necesito para usarlo?

Solo dos cosas:

1. Una cuenta de **Google** (la misma de Gmail).
2. Un navegador de internet.

No es necesario instalar nada en tu computador: todo se ejecuta en la nube, igual que cuando ves un
video en YouTube sin necesidad de descargarlo. ☁️

---

## 🚀 ¿Cómo lo uso?

### Opción A: El botón azul (la más rápida)

Haz clic en el botón **"Abrir en Colab"** de la parte superior de este documento. Te llevará directo
al cuaderno, listo para ejecutarse.

### Opción B: Subirlo manualmente

1. Entra a **Google Colab**: [https://colab.research.google.com](https://colab.research.google.com)
2. Ve a **Archivo → Subir cuaderno**.
3. Selecciona el archivo `Analisis_Mercado_Alkosto.ipynb` descargado de este repositorio.
4. Ejecuta cada celda de código con el botón ▶️, de arriba hacia abajo.
5. Al final obtendrás gráficas, una tabla de recomendaciones y un reporte de conclusiones.

> 💡 Para ejecutar todo el cuaderno de una sola vez, usa el menú **"Entorno de ejecución" → "Ejecutar todas"**.

---

## 📦 ¿De dónde vienen los datos?

Este proyecto usa exclusivamente **fuentes públicas, gratuitas y sin necesidad de registro**:

| Fuente | Qué aporta | Actualización |
|---|---|---|
| [Google Trends](https://trends.google.com) (vía la librería `pytrends`) | Interés de búsqueda por producto en Colombia | Prácticamente en tiempo real |
| [Frankfurter API](https://frankfurter.dev) (proveedor Banco de la República) | Tasa de cambio histórica USD → COP | Diaria |
| Calendario comercial colombiano | Fechas conocidas de descuentos (Día sin IVA, Black Friday, etc.) | Información pública de referencia |

> 🧩 **Dato curioso:** para el peso colombiano, Frankfurter usa como fuente al **Banco de la República**,
> que es ni más ni menos que el banco central de nuestro propio país. Por eso el cuaderno le pide a la
> API específicamente los datos que vienen de esa fuente (`providers=BANREP`).

---

## ⚠️ Importante — límites honestos de este análisis

Este cuaderno **no tiene acceso a los precios reales, exactos y en tiempo real de Alkosto**, porque esa
información es privada y no existe una base de datos pública y gratuita que la ofrezca. En su lugar, se
usan **señales indirectas pero verídicas** (demanda de búsqueda, tipo de cambio y calendario oficial de
descuentos) para construir una **predicción razonada**, no una promesa de precio.

Además, el cuaderno está diseñado para **nunca inventar datos**: si alguna fuente pública falla al
momento de ejecutar (por ejemplo, por una caída temporal del servicio), el análisis correspondiente se
omite con un aviso claro, en lugar de rellenarse con cifras ficticias.

👉 Antes de comprar cualquiera de estos productos, verifica siempre el precio vigente directamente en
Alkosto (tienda física o página web).

---

## 🗂️ Estructura del proyecto

```
📁 analisis-mercado-alkosto/
 ├── 📄 Analisis_Mercado_Alkosto.ipynb   # El cuaderno principal del proyecto
 ├── 📄 requirements.txt                  # Librerías necesarias para ejecutarlo fuera de Colab
 └── 📄 README.md                         # Este documento
```

### 📃 Sobre el `requirements.txt`

Es la lista de "ingredientes" (librerías de Python) que el cuaderno necesita para funcionar. Si usas el
botón de Colab, no necesitas hacer nada con este archivo, ya que el propio cuaderno las instala en su
primera celda. Si en algún momento quieres ejecutar el proyecto en tu computador, instala todo de una
vez con:

```bash
pip install -r requirements.txt
```

---

## 🛠️ Herramientas utilizadas

- **Python** 🐍 — lenguaje de programación del proyecto.
- **pandas** — organización y análisis de datos en forma de tablas.
- **numpy** — cálculos numéricos.
- **matplotlib** — generación de gráficas.
- **pytrends** — consulta no oficial y pública de Google Trends.
- **requests** — solicitudes HTTP a las APIs públicas utilizadas.

---

## 📚 Metodología, en resumen

1. Se descarga el interés de búsqueda histórico (5 años) de cada producto en Colombia.
2. Se calcula el promedio de interés por mes, identificando el mes de menor demanda para cada producto.
3. Se descarga el histórico de la tasa de cambio USD/COP (2 años) y se calcula su promedio mensual.
4. Se construye un calendario con los eventos comerciales conocidos en Colombia.
5. Se combinan las tres señales para generar una recomendación de compra por producto, con su
   justificación y un nivel de confianza.
6. Se genera un reporte final con conclusiones adicionales sobre el comportamiento de cada categoría.

---

## ✨ Autor

Proyecto elaborado por **Will**, estudiante de Análisis de Mercados de Productos, como entrega
académica para Alkosto (Bogotá, Colombia).

---

## 📜 Licencia

Proyecto de uso académico y educativo. Su reutilización y adaptación con fines de aprendizaje está
permitida.

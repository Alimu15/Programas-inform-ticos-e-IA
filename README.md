# 🧠 Reto 1: Matriz de Decisión Arquitectónica

![Status](https://img.shields.io/badge/Estado-Completado-success)
![Area](https://img.shields.io/badge/Area-IA%20%2F%20Big%20Data-blue)
![Role](https://img.shields.io/badge/Rol-Arquitecto%20de%20Software-orange)

## 1. Contexto previo (Mentalidad de Arquitecto)

Para este ejercicio, he seleccionado el **Escenario A**. Sin embargo, he analizado los tres para entender los trade-offs:

* 🎯 **Escenario A (Elegido):** Entrenar + API. Lo vital es el *Ecosistema de IA* y la *Facilidad de Despliegue*.
* 🔍 **Escenario B:** Exploración/EDA. Lo vital es la *Productividad* y Visualización (R suele ser fuerte aquí).
* 🌊 **Escenario C:** Streaming/Producción Masiva. Lo vital es *Concurrencia y Latencia* (Territorio de Java/Go).

---

## 2. La Matriz de Decisión

| Criterio 📏 | Peso ⚖️ | 🐍 Python | 📊 R | ☕ Java | 🟢 Node |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Ecosistema IA/ML** | **5** | 5 | 4 | 2 | 2 |
| Productividad / Prototipado | **4** | 5 | 4 | 2 | 3 |
| Rendimiento / Latencia | **3** | 2 | 1 | 5 | 4 |
| Concurrencia / Servicios | **3** | 3 | 1 | 5 | 5 |
| Integración Big Data | **3** | 4 | 3 | 4 | 2 |
| **Despliegue y Portabilidad** | **5** | 5 | 2 | 4 | 4 |
| Mantenibilidad / Tipado | **3** | 3 | 2 | 5 | 3 |
| Talento disponible | **4** | 5 | 2 | 4 | 4 |
| **TOTAL PONDERADO** 🏆 | **-** | **126** | **75** | **111** | **100** |

---

## 3. Justificación de Puntuaciones

### 🧠 1. Ecosistema IA/ML
* **Peso (5):** 🔴 **CRÍTICO.** Sin librerías de entrenamiento, no hay proyecto.
* **Python (5):** Líder absoluto (PyTorch, Scikit, HuggingFace).
* **R (4):** Fuerte en estadística, pero débil para Deep Learning moderno en producción.
* **Java/Node (2):** Librerías antiguas, wrappers lentos o inexistentes.

### 🚀 2. Productividad / Prototipado
* **Peso (4):** 🟠 **ALTO.** En IA necesitas probar y fallar muy rápido.
* **Python (5):** Código conciso, ideal para iterar rápido.
* **R (4):** Muy rápido para limpieza de datos, lento para lógica de backend.
* **Java (2):** Muy verboso (boilerplate).
* **Node (3):** Rápido para web, tedioso para matemáticas.

### ⚡ 3. Rendimiento / Latencia
* **Peso (3):** 🟡 **MEDIO.** Importante, pero las librerías de Python usan C por debajo.
* **Python (2):** Lento nativamente.
* **R (1):** Muy lento y consume mucha RAM.
* **Java (5):** Compilado y optimizado (JVM).
* **Node (4):** Motor V8 muy rápido.

### 🌐 4. Concurrencia / I-O / Servicios
* **Peso (3):** 🟡 **MEDIO.** Cuello de botella suele ser CPU, no I/O.
* **Python (3):** Limitado por el GIL (Global Interpreter Lock).
* **R (1):** "Single-threaded". Se bloquea con múltiples usuarios.
* **Java/Node (5):** Manejo de hilos robusto o asincronía excelente.

### 💾 5. Integración Big Data
* **Peso (3):** 🟡 **MEDIO.** Necesario para cargar datos.
* **Python (4):** PySpark es el estándar.
* **R (3):** Conectores existentes pero menos maduros.
* **Java (4):** Nativo (Hadoop/Spark son Java/Scala).
* **Node (2):** Conectores débiles para empresas.

### 🐳 6. Despliegue y Portabilidad
* **Peso (5):** 🔴 **CRÍTICO.** El objetivo es "Desplegar API".
* **Python (5):** Docker + Pip es el estándar cloud.
* **R (2):** Difícil gestión de dependencias.
* **Java/Node (4):** Contenedores robustos y ligeros.

### 🛠️ 7. Mantenibilidad / Tipado
* **Peso (3):** 🟡 **MEDIO.** Prioridad: funcionalidad vs perfección a largo plazo.
* **Python (3):** Dinámico (riesgo de errores), mitigable con Type Hints.
* **R (2):** Caótico.
* **Java (5):** Estricto y seguro.
* **Node (3):** Débil (JavaScript).

### 👥 8. Talento disponible
* **Peso (4):** 🟠 **ALTO.** Necesitas equipo híbrido (IA + Backend).
* **Python (5):** Todo perfil de datos lo domina.
* **R (2):** Perfiles estadísticos, no de ingeniería.
* **Java/Node (4):** Muchos programadores, pero sin base de IA.

---

## 🏆 Conclusión Final

> Viendo los resultados de la matriz, **Python gana de calle con 126 puntos**. Sinceramente, creo que es la única opción lógica porque, aunque Java tenga mejor rendimiento bruto, si intentase hacer esto en otro lenguaje perdería semanas reinventando la rueda o buscando librerías.
>
> En Python tengo todo el ecosistema (Pandas, PyTorch, Scikit) listo para prototipar y validar el modelo desde el primer día, que es lo prioritario en este escenario.
>
> **¿El Riesgo?** La velocidad en producción. Sé que Python tiene el problema del GIL y no gestiona la concurrencia real tan bien como Java; si la API recibe un pico enorme de tráfico, podría saturarse rápidamente. **¿La Solución?** Desplegaría usando servidores asíncronos eficientes como *Uvicorn*. Si el proyecto escala mucho en el futuro, plantearía una estrategia híbrida: entrenar cómodo en Python y luego exportar el modelo (vía **ONNX**) para ejecutarlo en un servidor de alto rendimiento.

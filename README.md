# Programas-inform-ticos-e-IA
# Reto 1 ALM

1. Contexto previo (Mentalidad de Arquitecto)
Aunque elijo el escenario A, tengo en cuenta estos aspectos necesarios para cada escenario:
•	Escenario A (Entrenar + API): Lo vital es el Ecosistema de IA (librerías) y la Facilidad de Despliegue (crear la API rápido)

•	Escenario B (Exploración/EDA): Lo vital es la Productividad (escribir poco código) y Visualización de datos. (R suele ser fuerte)

•	Escenario C (Streaming/Producción Masiva): Lo vital es la Concurrencia, Latencia y Tipado. (Aquí Java, Go o Scala)


Tabla:
Criterio	Peso (1–5)	Python (1–5)	R (1–5)	Java (1–5)	Node (1–5)
Ecosistema IA/ML (librerías, comunidad)	5	5	4	2	2
Productividad / prototipado	4	5	4	2	3
Rendimiento / latencia	3	2	1	5	4
Concurrencia / I-O / servicios	3	3	1	5	5
Integración Big Data (Spark, conectores)	3	4	3	4	2
Despliegue y portabilidad	5	5	2	4	4
Mantenibilidad / tipado / tooling	3	3	2	5	3
Talento disponible (equipo)	4	5	2	4	4
TOTAL ponderado		126	75	111	100

Explicación Breve para cada puntuación:

1. Ecosistema IA/ML
•	Peso (5): CRÍTICO. Sin librerías de entrenamiento, no hay proyecto
•	Python (5): Líder absoluto (PyTorch, Scikit, HuggingFace)
•	R (4): Fuerte en estadística, pero débil para Deep Learning moderno en producción
•	Java (2): Librerías antiguas o abandonadas, no se usa para investigar
•	Node (2): Inmaduro. Solo wrappers lentos o experimentales.
2. Productividad / Prototipado
•	Peso (4): ALTO. En IA necesitas probar y fallar muy rápido
•	Python (5): Código conciso, ideal para iterar rápido
•	R (4): Muy rápido para limpieza de datos, lento para lógica de backend
•	Java (2): Muy verboso y lento de escribir (boilerplate)
•	Node (3): Rápido para web, tedioso para matemáticas
3. Rendimiento / Latencia
•	Peso (3): MEDIO. Importante, pero las librerías de Python usan C por debajo
•	Python (2): Lento nativamente, aceptable gracias a librerías optimizadas
•	R (1): Muy lento y devora memoria RAM
•	Java (5): Compilado y optimizado, máxima velocidad
•	Node (4): Motor V8 muy rápido para ejecución
4. Concurrencia / I-O / Servicios
•	Peso (3): MEDIO. La API debe atender usuarios, pero el cuello de botella es la CPU
•	Python (3): Limitado por el Global Interpreter Lock en multihilo
•	R (1): "Single-threaded". Se bloquea con múltiples usuarios
•	Java (5): Manejo de hilos robusto y real
•	Node (5): Excelente manejo asíncrono (Non-blocking I/O)
5. Integración Big Data
•	Peso (3): MEDIO. Necesario para cargar datos de entrenamiento
•	Python (4): PySpark es el estándar de la industria
•	R (3): Conectores existentes, pero menos maduros
•	Java (4): Nativo (Hadoop y Spark están hechos en Java/Scala)
•	Node (2): Conectores débiles para ecosistemas empresariales
6. Despliegue y Portabilidad
•	Peso (5): CRÍTICO. El objetivo es Desplegar API
•	Python (5): Docker + Pip es el estándar cloud actual
•	R (2): Difícil gestión de dependencias en servidor
•	Java (4): Los .jar son robustos y fáciles de mover
•	Node (4): Muy ligero y fácil de contenerizar
7. Mantenibilidad / Tipado
•	Peso (3): MEDIO. Priorizamos funcionalidad rápida sobre código perfecto a largo plazo
•	Python (3): Tipado dinámico (riesgo de errores), mitigable con hints
•	R (2): Tipado caótico e inconsistente
•	Java (5): Tipado estático estricto, código muy seguro
•	Node (3): Tipado débil (JavaScript), propenso a errores
8. Talento disponible
•	Peso (4): ALTO. Necesitas equipo capaz de unir IA + Backend
•	Python (5): Todo perfil de datos domina Python
•	R (2): Perfiles estadísticos, no saben hacer APIs
•	Java (4): Muchos programadores, pocos saben de IA
•	Node (4): Muchos web devs, nulo conocimiento de IA

Conclusión de la tabla:
Tras realizar la matriz de decisión ponderada, el lenguaje ganador para el Escenario A es Python, imponiéndose a Java y Node.js como la opción más viable para emplear en este escenario
Conclusión del ejercicio:
Viendo los resultados de la tabla, Python gana con 126 puntos. Sinceramente, es la única opción lógica porque, aunque Java sea más rápido, si intento hacer esto en otro lenguaje me pasaría semanas buscando librerías de IA que funcionen, mientras que en Python tengo todo (Pandas, PyTorch) listo para usar y prototipar rápido
El mayor riesgo que veo es que Python no es famoso por su velocidad; sé que tiene problemas de concurrencia (el famoso GIL) y si mi API recibe muchísimas visitas de golpe, podría saturarse. Para solucionarlo sin volvernos locos, usaría servidores eficientes como Uvicorn, o plantearía una estrategia híbrida: entrenar cómodo en Python y luego exportar el modelo (usando ONNX) para que corra en un servidor más rápido como Java o Go si el proyecto crece mucho.

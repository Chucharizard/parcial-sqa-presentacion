# Guion de exposición individual

Tiempo previsto: 6 minutos y 30 segundos, incluida la demo. Las nueve diapositivas sirven de apoyo. Ensayar el guion y explicar las ideas con palabras propias.

## 0:00–0:20 / Objetivo

Presentamos las pruebas del inventario en Spring Boot. El objetivo fue comprobar sus operaciones con pruebas unitarias y funcionales, y organizar el trabajo de cinco integrantes mediante GitHub. Voy a explicar el proceso, mostrar los resultados y terminar con una demo.

## 0:20–1:00 / Plan y alcance

Partimos de las historias de categorías y productos. Por ejemplo: como usuario quiero registrar un producto con una categoría válida. De ahí salen un caso exitoso y otro con una categoría inexistente. Probamos dos controladores porque reciben las solicitudes, dos servicios porque contienen la lógica y tres utilidades porque comprimen imágenes y generan Excel. El plan incluye entradas, pasos y resultados esperados. Usamos JUnit y Mockito para las pruebas unitarias, y Postman con la API y MySQL para las funcionales.

## 1:00–1:30 / Trabajo colaborativo

Organizamos un sprint de dos días y repartimos los módulos como se ve aquí. Tyler llevó el seguimiento y todos tuvimos tareas de testing. GitHub muestra los 16 issues cerrados: once historias y cinco tareas de prueba. Los cinco PR están aprobados y fusionados. Algunas descripciones todavía conservan un estado anterior, "En revisión", aunque sus criterios están marcados y los issues aparecen cerrados. En la demo mostraré ese recorrido en el repositorio.

## 1:30–2:00 / Apoyo de IA

Usamos IA para generar pruebas y scripts, apoyar su ejecución y preparar la documentación. El equipo definió el alcance, repartió las tareas y fue pidiendo ajustes. También autorizó las entregas y revisiones. La comprobación quedó respaldada por las ejecuciones de Maven y Postman, y el reporte de JaCoCo. Nos corresponde entender y explicar lo entregado.

## 2:00–2:50 / Mockito y calidad de las pruebas

Este ejemplo muestra cómo usamos Mockito. Simulamos que el repositorio no encuentra una categoría y llamamos al método real del servicio. Con una assertion comprobamos la respuesta 404, y con verifyNoInteractions comprobamos que no se use el repositorio de productos. Así verificamos tanto la respuesta como que no intente guardar. También hay casos exitosos, errores y comprobaciones del contenido de imágenes y archivos Excel. La ejecución integrada dio 106 pruebas en 14 clases, sin fallos. Ese total incluye pruebas unitarias y algunas de integración heredadas, como el DAO con H2 y la carga del contexto.

## 2:50–3:30 / Cobertura

JaCoCo reportó 97,3 por ciento de líneas, 79,3 de instrucciones y 35,1 de ramas. Las líneas indican qué código se ejecutó y las ramas muestran las alternativas recorridas en las decisiones. Los dos controladores y los dos servicios tienen todas sus líneas cubiertas. En el global quedan alternativas sin cubrir. El rango sugerido de 85 a 95 por ciento se supera en líneas. La consigna no especifica una única métrica, por eso mostramos las tres.

## 3:30–4:00 / Ambiente e incidencia

Las pruebas funcionales usaron MySQL en Docker y la API en el puerto 8080. Estas capturas muestran el contenedor activo y una respuesta de categorías. Al preparar el entorno, Docker falló por un archivo temporal de arranque al que no podía acceder. Apartamos esos archivos conservando una copia, reiniciamos y comprobamos el contenedor y la API. La incidencia y su solución están en el informe.

## 4:00–4:40 / Pruebas funcionales

La colección tiene 46 solicitudes. La ejecutamos con Newman, que permite correr colecciones de Postman. Hubo 45 solicitudes ejecutadas y 177 comprobaciones aprobadas, sin fallos. Una limpieza condicional se omitió porque ya no quedaban registros pendientes. Comprobamos el CRUD, búsquedas, respuestas de error y descargas Excel. La copia utilizada ajusta una variable de los scripts y utiliza las imágenes de prueba previstas. Conservamos la colección original y documentamos los ajustes.

## 4:40–6:30 / Demo y conclusión

DEMO, aproximadamente 1 minuto 40 segundos:
1. GitHub: mostrar una tarea, su rama y el PR integrado; los 16 issues aparecen cerrados y los cinco PR aprobados y fusionados (20 segundos).
2. En el proyecto, ejecutar .\mvnw.cmd verify. Mientras termina, mostrar el caso de Mockito explicado antes. Mostrar el resumen y abrir target/site/jacoco/index.html (45 segundos).
3. Con Docker y la API ya activos, ejecutar la colección en Postman y mostrar sus resultados. Las rutas de las imágenes deben estar configuradas (35 segundos).

CIERRE, 10 segundos:
El informe reúne el plan, los casos, la incidencia y las instrucciones para repetir las pruebas. Las ejecuciones registradas pasaron y la cobertura de ramas muestra dónde se puede seguir mejorando.

ANTES DE EXPONER:
Ensayar la duración en la laptop. Dejar las dependencias descargadas, las pestañas listas, Docker y la API activos. Si una ejecución tarda más, indicar que sigue en curso y distinguirla del reporte guardado. El resultado de una nueva corrida puede variar si cambia la colección o los datos.

SEGUIMIENTO AL CORTE DEL INFORME:
La colección de Postman y sus imágenes todavía deben compartirse junto al proyecto. Varias descripciones de historias aún muestran el texto antiguo "En revisión"; el estado de GitHub está cerrado, y las casillas aparecen completas. Conviene limpiar ese texto de seguimiento antes de presentar la página de issues.

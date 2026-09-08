# NutriFit - Clinical Dashboard

Sistema integral de administracion clinica y nutricional desarrollado como una Single Page Application (SPA). La plataforma esta disenada para optimizar el tiempo en consulta mediante el manejo de expedientes clinicos, generacion automatizada de planes de alimentacion y evaluacion antropometrica en tiempo real.

## Caracteristicas Principales

* **Expediente Clinico Integral:** Gestion completa de pacientes (CRUD) que incluye datos personales, historia clinica (AHF, APP, estilo de vida) y antropometria avanzada (pliegues ISAK, circunferencias y formulas de Palafox).
* **Calculo Dietosintetico Automatico:** Motor de distribucion automatizada basado en el Sistema Mexicano de Alimentos Equivalentes (SMAE). Genera combinaciones exactas de porciones segun metas de calorias y macronutrientes.
* **Agenda de Consultas:** Modulo de calendario interactivo para programar citas y vincular enlaces de videollamadas.
* **Dieta Rapida:** Generador de menus de 7 dias adaptados a la dieta mexicana, con funcionalidad de exportacion directa a formatos PDF y PNG.
* **Calculos Rapidos Reactivos:** Herramienta de estimacion inmediata de IMC, GEB, GET y distribucion de macronutrientes sin necesidad de guardar el expediente.
* **Evaluacion Pediatrica:** Modulo de seguimiento de crecimiento infantil con generacion dinamica de curvas de percentiles (Peso, Talla e IMC para la edad) basadas en estandares de la OMS/CDC.
* **Catalogos Personalizados:** Bases de datos independientes para registrar alimentos comerciales propios, estandarizar recetas y guardar plantillas de dietas predefinidas.

## Tecnologias Utilizadas

* **Frontend:** HTML5, Vanilla JavaScript (ES6 Modules), CSS3.
* **Framework UI:** Bootstrap 5.
* **Iconografia:** Flaticon UIcons (Solid Straight).
* **Graficos y Visualizacion:** Chart.js (Curvas pediatricas), FullCalendar (Agenda).
* **Exportacion de Documentos:** html2canvas, jsPDF.
* **Backend y Base de Datos:** Firebase / Cloud Firestore (NoSQL).

## Estructura de Base de Datos (Firestore)

El proyecto utiliza un modelo relacional basado en las siguientes colecciones principales:

* `pacientes`: Utiliza el correo electronico como llave primaria (Document ID) para evitar duplicados. Almacena objetos anidados para datos personales, historia clinica y antropometria.
  * Subcoleccion `mediciones_pediatricas`: Almacena el historial cronologico para el renderizado de curvas de crecimiento.
* `citas`: Documentos vinculados al ID del paciente que alimentan la interfaz de FullCalendar.
* `menus`: Registra la distribucion de equivalentes (SMAE) y macros totales, enlazados al paciente.
* `mis_alimentos`, `mis_recetas`, `mis_dietas`: Colecciones de catalogos gestionadas por el usuario.

## Instalacion y Configuracion

1. Clonar el repositorio del proyecto.
2. Crear un proyecto en Firebase y habilitar Cloud Firestore.
3. Configurar las reglas de seguridad de Firestore para proteger las colecciones y subcolecciones.
4. Obtener las credenciales web de Firebase (objeto `firebaseConfig`) y reemplazar los valores en la etiqueta `<script type="module">` dentro del archivo `index.html`.
5. Ejecutar el archivo `index.html` mediante un servidor local (por ejemplo, Live Server) para habilitar el uso correcto de los modulos ES6 y las importaciones desde CDN.

## Autor

Desarrollado por Erick Aguila Martinez.

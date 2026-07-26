# Automatización Avanzada de Procesos con Microsoft Copilot Studio

Capacitación práctica orientada al diseño, construcción, prueba y publicación de un agente en Microsoft Copilot Studio aplicado a procesos de auditoría interna.

Durante el curso, los participantes crearán el **Agente Auditor de Controles**, configurarán instrucciones y un tema de revisión, construirán un modelo de datos en Microsoft Dataverse, habilitarán la búsqueda mediante Quick Find e índice, conectarán el Servidor MCP de Microsoft Dataverse para consultar información gobernada, automatizarán el registro de revisiones mediante un workflow y publicarán el agente en Microsoft Teams.

El caso de uso incluye trazabilidad en Dataverse, consulta de controles y criterios de auditoría, validación de entradas, detección de excepciones y generación de archivos CSV en SharePoint.

## Estructura

- `CapituloXX/README.md`: guía práctica completa de cada capítulo.
- `Datos/`: archivos CSV, evidencias sintéticas y casos de evaluación.
- `images/`: capturas de pantalla de la práctica.
- `Recursos/`: archivos ZIP de skill.
- `SETUP.md`: preparación del entorno que debe completar el centro de instrucción.

## Lista de laboratorios

### Capítulo 1

- [Práctica 1 — Definir usuarios, entradas, salidas, reglas y alcance del agente auditor](Capitulo01/README.md)
  - **Descripción:** Los participantes diseñarán el canvas funcional del Agente Auditor de Controles. Definirán los usuarios, las entradas requeridas, las salidas esperadas, las reglas de excepción, las restricciones de seguridad y el alcance del caso de uso.
  - **Duración estimada:** 15 min

### Capítulo 2

- [Práctica 2 — Crear el agente base, configurar instrucciones y probar escenarios de auditoría con control de alcance](Capitulo02/README.md)
  - **Descripción:** Los participantes crearán la solución `LAB_Agente_Auditor`, el agente base y sus instrucciones generales. También configurarán el sitio de SharePoint, las bibliotecas del laboratorio y las reglas de alcance y seguridad del agente.
  - **Duración estimada:** 20 min

### Capítulo 3

- [Práctica 3 — Crear un tema de revisión de control con variables, entidades, condiciones y rutas de excepción](Capitulo03/README.md)
  - **Descripción:** Los participantes crearán el tema de revisión y configurarán las variables necesarias para recopilar los nueve campos del proceso. También establecerán validaciones, condiciones, rutas de excepción y confirmación previa al registro.
  - **Duración estimada:** 20 min

### Capítulo 4

- [Práctica 4 — Configurar conocimiento y datos estructurados para responder consultas de auditoría con sustento](Capitulo04/README.md)
  - **Descripción:** Los participantes crearán las tablas `Responsables`, `Controles`, `CriteriosAuditoria` y `Revisiones`, configurarán las longitudes de sus columnas e importarán los datos sintéticos. También habilitarán Búsqueda de Dataverse, Quick Find, el índice de búsqueda y el Servidor MCP de Microsoft Dataverse para consultar información sustentada.
  - **Duración estimada:** 30 min

### Capítulo 5

- [Práctica 5 — Crear un workflow como herramienta para registrar una revisión y devolver confirmación o alertar excepción](Capitulo05/README.md)
  - **Descripción:** Los participantes construirán `RegistrarRevisionAuditoria`. El workflow recibirá los datos confirmados por el agente, registrará exactamente una fila en `Revisiones`, identificará si existe una excepción y generará un archivo CSV en SharePoint cuando se requiera seguimiento.
  - **Duración estimada:** 20 min

### Capítulo 6

- [Práctica 6 — Ejecutar matriz de pruebas del agente auditor y ajustar instrucciones, temas, conocimiento o workflow](Capitulo06/README.md)
  - **Descripción:** Los participantes importarán `Datos/CasosEvaluacion.csv` y ejecutarán escenarios relacionados con controles válidos e inexistentes, seguridad, validación de datos, consulta de Dataverse y ejecución del workflow. Según los resultados, ajustarán instrucciones, tema, Servidor MCP o automatización.
  - **Duración estimada:** 25 min

### Capítulo 7

- [Práctica 7 — Ejecutar una revisión completa desde Teams con consulta de conocimiento, registro automatizado y salida final](Capitulo07/README.md)
  - **Descripción:** Los participantes publicarán el agente en Microsoft Teams y ejecutarán el caso de uso completo: consulta del control mediante Dataverse MCP, recopilación y confirmación de datos, ejecución del workflow, creación del registro en Dataverse y generación de una exportación cuando exista una excepción.
  - **Duración estimada:** 20 min

## Flujo funcional del laboratorio

```text
Usuario en Copilot Studio o Teams
  -> Agente Auditor de Controles
  -> Consulta de controles y criterios mediante Dataverse MCP
  -> Tema de revisión de control
  -> Validación y confirmación de los datos
  -> Workflow RegistrarRevisionAuditoria
  -> Registro en Dataverse
  -> Exportación CSV en SharePoint cuando existe excepción
  -> Respuesta final al usuario
```

## Duración total

**150 minutos — 2 horas y 30 minutos de práctica.**

## Flujo de colaboración

- Trabajar en `changes_course`.
- Crear Pull Request hacia `main`.
- Realizar el merge mediante `Squash and merge`.

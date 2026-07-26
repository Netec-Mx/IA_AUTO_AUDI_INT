# SETUP — Aprovisionamiento previo del laboratorio

Este documento es exclusivamente para el centro de instrucción o la persona que administra el tenant. Debe completarse antes de que los participantes abran el capítulo 1.

El aprovisionador **no debe** crear la solución, el publicador, el agente, las tablas, los datos, el sitio SharePoint, las bibliotecas, las conexiones ni los workflows. Esos elementos forman parte de las prácticas y los construye cada participante.

## 1. Licencias y capacidad

Asigne a cada participante:

- acceso a Microsoft Copilot Studio mediante licencia o Trial;
- una licencia que permita utilizar Power Apps, Power Automate y Microsoft Dataverse en el entorno asignado;
- SharePoint Online;
- Microsoft Teams.

La cuenta debe permitir:

- crear y publicar agentes;
- utilizar Microsoft Dataverse;
- crear workflows y referencias de conexión;
- utilizar los conectores Microsoft Dataverse y SharePoint;
- publicar y abrir el agente en Microsoft Teams.

Una cuenta Trial permite crear y probar el agente, pero puede imponer restricciones de publicación, capacidad o caducidad.

## 2. Crear y asignar un entorno por participante

Prepare un entorno aislado con Dataverse para cada participante.

También puede asignar un entorno por pareja cuando ambos trabajen sobre la misma solución y utilicen una sola cuenta como creadora principal.

No utilice un único entorno compartido por todo el grupo, porque las prácticas crean soluciones, tablas, agentes, conexiones y workflows con los mismos nombres.

1. Abra el Centro de administración de Power Platform.
2. Cree o seleccione un entorno de tipo **Developer** con Dataverse.
3. Use el nombre:

   `Dev One - <alias>`

   Ejemplo:

   `Dev One - juanl`

4. Configure el idioma base en español.
5. Asigne el entorno al participante.
6. Verifique que la cuenta puede seleccionar el mismo entorno en:
   - Microsoft Copilot Studio;
   - Power Apps;
   - Power Automate.
7. No cree dentro del entorno los componentes del laboratorio.

## 3. Asignar roles mínimos

Cada participante debe tener en su entorno:

- `Environment Maker`;
- `System Customizer`;
- `Basic User`.

`Environment Maker` permite crear soluciones, agentes, flujos y conexiones.

`System Customizer` permite crear y modificar tablas, columnas, vistas y otros componentes de Dataverse.

`Basic User` proporciona el acceso básico requerido para utilizar Dataverse.

Puede asignar temporalmente `System Administrator` en un entorno aislado de laboratorio cuando sea necesario para resolver permisos, pero no es obligatorio si los tres roles anteriores están correctamente configurados.

## 4. Habilitar la experiencia de Copilot Studio

1. Confirme que Microsoft Copilot Studio está disponible para las cuentas del laboratorio.
2. Abra Copilot Studio con una cuenta de prueba.
3. Seleccione el entorno `Dev One - <alias>`.
4. Verifique que la creación de agentes está disponible.
5. Confirme que la interfaz del agente muestra:
   - **Build**;
   - **Preview**;
   - **Evaluate**;
   - **Monitor**.
6. No cree el agente del participante.

La solución y el agente se crean durante las prácticas.

## 5. Habilitar Dataverse Search y el Servidor MCP

Esta configuración debe completarse antes de la práctica 4.

### Dataverse Search

1. Abra el Centro de administración de Power Platform.
2. Seleccione **Manage > Environments**.
3. Abra el entorno `Dev One - <alias>`.
4. Seleccione **Settings > Product > Features**.
5. Localice **Dataverse Search**.
6. Active:

   **Active search indexing to support Dataverse intelligence (Work IQ) in AI and agent experiences**

7. Guarde los cambios.
8. Espere a que la búsqueda quede aprovisionada.

El participante configurará en la práctica 4 las vistas de Búsqueda rápida y agregará las tablas correspondientes al índice.

### Servidor MCP de Microsoft Dataverse

1. En la misma página **Settings > Product > Features**, localice **Dataverse Model Context Protocol**.
2. Confirme que está activada la opción:

   **Allow MCP clients to interact with Dataverse MCP server**

3. Guarde cualquier cambio.
4. Verifique con una cuenta de prueba que, en Copilot Studio, aparece:

   **Build > Tools > Add a tool > Model Context Protocol > Microsoft Dataverse MCP Server**

5. No agregue ni configure el servidor MCP dentro del agente del participante.

La conexión y configuración del Servidor MCP se realizan en la práctica 4.

## 6. Permitir conectores y creación de conexiones

1. Compruebe que la política DLP permite que estos conectores trabajen en el mismo grupo de datos empresariales:
   - Microsoft Dataverse;
   - SharePoint.
2. Permita que cada participante cree conexiones personales con su cuenta del laboratorio.
3. Permita la creación de referencias de conexión dentro de soluciones.
4. No cree conexiones compartidas para el ejercicio, salvo que la política del centro lo exija.
5. No habilite conectores personales, de redes sociales o no requeridos por el laboratorio.

Las conexiones y referencias de conexión las crea o autoriza el participante durante la práctica 5.

## 7. Permitir la creación de sitios SharePoint

Cada participante construirá su sitio y sus bibliotecas en la práctica 2.

Antes de la sesión:

1. Confirme que la cuenta tiene licencia de SharePoint Online.
2. Confirme que la creación de sitios de equipo por autoservicio está permitida o que existe un mecanismo inmediato de aprobación.
3. Asigne a cada participante un alias único, por ejemplo `juanl`.
4. El participante utilizará el alias para crear un sitio con un nombre sin colisiones:

   `LaboratorioAuditoriaInterna-<alias>`

5. Confirme que el participante podrá:
   - ser propietario del sitio;
   - crear bibliotecas;
   - cargar archivos;
   - crear vínculos HTTPS;
   - crear archivos desde Power Automate.
6. No cree el sitio, las bibliotecas ni cargue los archivos.

Si el tenant impide la creación de sitios, entregue antes del laboratorio un sitio vacío y exclusivo al participante. El participante continuará creando las bibliotecas y cargando los archivos durante la práctica.

## 8. Preparar Teams y distribución

1. Verifique que Microsoft Teams está habilitado para las cuentas.
2. Confirme que las aplicaciones de Power Platform están permitidas en el Centro de administración de Teams.
3. Verifique que el canal de Teams y Microsoft 365 aparece en las opciones de publicación de Copilot Studio.
4. Permita que el participante:
   - publique el agente;
   - agregue el canal;
   - instale o abra el agente en Teams.
5. No publique ni instale previamente el agente del participante.

## 9. Entregar los archivos del laboratorio

Prepare los archivos antes de la sesión en la máquina virtual o equipo asignado.

### Opción A — Descargar desde GitHub

1. Confirme que Git está instalado.
2. Abra PowerShell.
3. Ejecute:

```powershell
cd C:\
mkdir Laboratorios
cd Laboratorios
git clone <URL_DEL_REPOSITORIO> IA_AUTO_AUDI_INT
cd IA_AUTO_AUDI_INT
```

4. Confirme que existen:
   - `README.md`;
   - `SETUP.md`;
   - `manifest.json`;
   - `Datos`;
   - `Capitulo01` a `Capitulo07`;
   - `images`.

### Opción B — Entregar el archivo ZIP

1. Copie el archivo ZIP del laboratorio en la máquina virtual.
2. Extraiga el contenido en:

   `C:\Laboratorios\IA_AUTO_AUDI_INT`

3. Confirme la misma estructura de carpetas.
4. No modifique los archivos CSV, las evidencias ni los README antes de entregarlos.

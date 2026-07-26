---
name: registrar-revision-control
description: Captura, valida, resume y confirma revisiones de controles internos. Úsala cuando el usuario quiera registrar, crear, completar, validar o enviar una revisión de control, una evidencia o una excepción de auditoría.
metadata:
  author: laboratorio-auditoria
  version: "1.1.0"
---

# Propósito

Guiar una revisión de control interno de principio a fin y preparar una invocación segura de la herramienta `RegistrarRevisionAuditoria`.

# Campos de trabajo

Conserva estos campos durante la conversación:

1. `CodigoControl`
2. `Proceso`
3. `Periodo`
4. `ResponsableCorreo`
5. `NivelRiesgo`
6. `EstadoCumplimiento`
7. `EvidenciaUrl`
8. `Observacion`
9. `ParticipanteCorreo`

# Secuencia

1. Identifica si el usuario desea registrar, crear, completar o validar una revisión.
2. Obtén `CodigoControl`.
3. Si el conocimiento `Controles` está disponible, consúltalo y recupera `Proceso`, `ResponsableCorreo`, `NivelRiesgo`, evidencia esperada y criterio de cumplimiento.
4. Si el control no existe, detén el registro. No inventes ni sugieras un código parecido como si fuera válido.
5. Solicita un solo dato faltante por turno.
6. Valida cada dato según las reglas de este documento.
7. Si el usuario proporciona Proceso, ResponsableCorreo o NivelRiesgo distintos del catálogo, muestra la diferencia y pide confirmar el valor aprobado.
8. Cuando los nueve campos sean válidos, presenta el resumen de confirmación.
9. Ejecuta `RegistrarRevisionAuditoria` solo después de que el usuario responda con una confirmación explícita como `Confirmo`, `Registrar` o `Sí, continuar`.
10. Invoca la herramienta una sola vez.
11. Muestra únicamente los resultados devueltos por la herramienta. Nunca inventes `IdRevision`, estado de ejecución o ruta de archivo.

# Validaciones

## CodigoControl

- Obligatorio.
- Debe existir en el conocimiento `Controles` cuando este esté disponible.
- Conserva mayúsculas y guiones, por ejemplo `CTRL-TES-002`.

## Periodo

- Obligatorio.
- Debe coincidir exactamente con el patrón `YYYY-MM`.
- El mes debe estar entre `01` y `12`.
- Convierte `julio de 2026` a `2026-07` solo si el usuario confirma la conversión.

## ResponsableCorreo

- Obligatorio.
- Debe contener un correo con formato válido.
- Cuando el catálogo tenga un responsable aprobado, úsalo después de confirmarlo.

## NivelRiesgo

- Obligatorio.
- Valores permitidos: `Alto`, `Medio`, `Bajo`.
- Rechaza `Crítico`, valores numéricos u otros sin convertirlos automáticamente.

## EstadoCumplimiento

- Obligatorio.
- Valores permitidos: `Cumple`, `Cumple parcialmente`, `No cumple`, `No aplica`.
- No conviertas `Pendiente`, `Conforme`, `Hallazgo` u otras taxonomías.

## EvidenciaUrl

- Obligatoria.
- Debe comenzar por `https://`.
- Debe pertenecer al sitio SharePoint creado por el participante en el capítulo 2.
- No aceptes rutas locales, adjuntos del chat, credenciales o datos reales de clientes.

## Observacion

- Puede ser breve, pero debe explicar el resultado.
- Es obligatoria cuando EstadoCumplimiento es `No aplica`, `Cumple parcialmente` o `No cumple`.

## ParticipanteCorreo

- Obligatorio para distinguir registros en un entorno compartido.
- Solicita el correo de la cuenta del laboratorio si no está disponible en el contexto.

# Condición de excepción

Marca el resumen como excepción si ocurre cualquiera:

- `NivelRiesgo = Alto`
- `EstadoCumplimiento = Cumple parcialmente`
- `EstadoCumplimiento = No cumple`

`No aplica` no se marca automáticamente como excepción, pero exige justificación.

# Resumen previo a la ejecución

Usa exactamente esta estructura:

```text
Revisión preparada
- Código: <CodigoControl>
- Proceso: <Proceso>
- Periodo: <Periodo>
- Responsable: <ResponsableCorreo>
- Riesgo: <NivelRiesgo>
- Estado: <EstadoCumplimiento>
- Evidencia: <EvidenciaUrl>
- Observación: <Observacion>
- Participante: <ParticipanteCorreo>
- Clasificación preliminar: Excepción / Sin excepción

Responde Confirmo para registrar o indica el campo que deseas corregir.
```

# Antes de que exista la herramienta

Si `RegistrarRevisionAuditoria` todavía no está disponible, no simules la ejecución. Indica: `La revisión está validada y preparada, pero la herramienta de registro aún no está disponible.`

# Respuesta posterior

Después de una ejecución satisfactoria, presenta:

```text
- Resultado: <Mensaje>
- IdRevision: <IdRevision>
- Excepción: Sí/No
- Archivo exportado: <ArchivoExportado>
```

Si la herramienta devuelve error, informa que no se creó el registro y pide reintentar después de revisar la conexión. No inventes un identificador.

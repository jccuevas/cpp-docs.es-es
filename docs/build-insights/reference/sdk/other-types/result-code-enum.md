---
title: Enumeración RESULT_CODE
description: El C++ SDK de Build insights RESULT_CODE referencia de enumeración.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RESULT_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ee563d148b3456b288bc418255ec46f8cbade7ec
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333951"
---
# <a name="result_code-enum"></a>Enumeración RESULT_CODE

::: moniker range="<=vs-2015"

El C++ SDK de Build Insights es compatible con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

En la enumeración `RESULT_CODE` se describen las condiciones de éxito y error.

## <a name="members"></a>Miembros

| Name | Valor | Descripción |
|--|--|--|
| `RESULT_CODE_SUCCESS` | 0 (0x00000000) | La operación se realizó correctamente. |
| `RESULT_CODE_FAILURE_ANALYSIS_ERROR` | 1 (0x00000001) | Una de las funciones de devolución de llamada en [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) o [RELOG_DESCRIPTOR](relog-descriptor-struct.md) devolvió el valor de `CALLBACK_CODE_ANALYSIS_FAILURE`. Este valor es un miembro de la enumeración [CALLBACK_CODE](callback-code-enum.md) . |
| `RESULT_CODE_FAILURE_CANCELLED` | 2 (0x00000002) | Una de las funciones de devolución de llamada en [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) o [RELOG_DESCRIPTOR](relog-descriptor-struct.md) devolvió el valor de `CALLBACK_CODE_ANALYSIS_CANCEL`. Este valor es un miembro de la enumeración [CALLBACK_CODE](callback-code-enum.md) . |
| `RESULT_CODE_FAILURE_INVALID_INPUT_LOG_FILE` | 3 (0x00000003) | El seguimiento de eventos de entrada para Windows (ETW) especificado no es válido. |
| `RESULT_CODE_FAILURE_INVALID_OUTPUT_LOG_FILE` | 4 (0x00000004) | El seguimiento ETW de salida especificado no es válido. |
| `RESULT_CODE_FAILURE_MISSING_ANALYSIS_CALLBACK` | 5 (0x00000005) | La estructura de [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) no se ha inicializado correctamente. |
| `RESULT_CODE_FAILURE_MISSING_RELOG_CALLBACK` | 6 (0x00000006) | La estructura de [RELOG_CALLBACKS](relog-callbacks-struct.md) no se ha inicializado correctamente. |
| `RESULT_CODE_FAILURE_OPEN_INPUT_TRACE` | 7 (0x00000007) | No se pudo abrir el seguimiento ETW de entrada. |
| `RESULT_CODE_FAILURE_PROCESS_TRACE` | 8 (0x00000008) | Se produjo un error al procesar el seguimiento ETW de entrada. |
| `RESULT_CODE_FAILURE_START_RELOGGER` | 9 (0x00000009) | Se produjo un error al intentar iniciar la sesión de registro. |
| `RESULT_CODE_FAILURE_DROPPED_EVENTS` | 10 (0x0000000A) | En el seguimiento de ETW de entrada faltan eventos importantes. |
| `RESULT_CODE_FAILURE_UNSUPPORTED_OS` | 11 (0x0000000B) | Está utilizando C++ Build Insights en una versión no compatible de Windows. |
| `RESULT_CODE_FAILURE_INVALID_TRACING_SESSION_NAME` | 12 (0x0000000C) | El nombre de sesión proporcionado no es válido. |
| `RESULT_CODE_FAILURE_INSUFFICIENT_PRIVILEGES` | 13 (0x0000000D) | Esta operación requiere privilegios de administrador. |
| `RESULT_CODE_FAILURE_GENERATE_GUID` | 14 (0x0000000E) | Se produjo un error al generar un GUID. |
| `RESULT_CODE_FAILURE_OBTAINING_TEMP_DIRECTORY` | 15 (0x0000000F) | Error al intentar determinar la ruta de acceso del directorio temporal. |
| `RESULT_CODE_FAILURE_CREATE_TEMPORARY_DIRECTORY` | 16 (0x00000010) | Error al intentar crear un directorio temporal para la sesión de seguimiento que se está iniciando. |
| `RESULT_CODE_FAILURE_START_SYSTEM_TRACE` | 17 (0x00000011) | Se produjo un error al intentar iniciar el seguimiento del sistema. |
| `RESULT_CODE_FAILURE_START_MSVC_TRACE` | 18 (0x00000012) | Se produjo un error al intentar iniciar el seguimiento de MSVC. |
| `RESULT_CODE_FAILURE_STOP_MSVC_TRACE` | 19 (0x00000013) | Se produjo un error al intentar detener el seguimiento de MSVC. |
| `RESULT_CODE_FAILURE_STOP_SYSTEM_TRACE` | 20 (0x00000014) | Se produjo un error al intentar iniciar el seguimiento del sistema. |
| `RESULT_CODE_FAILURE_SESSION_DIRECTORY_RESOLUTION` | 21 (0x00000015) | Se detuvo un seguimiento, pero no se encuentra el directorio temporal de la sesión de seguimiento. |
| `RESULT_CODE_FAILURE_MSVC_TRACE_FILE_NOT_FOUND` | 22 (0x00000016) | No se encuentra el archivo de seguimiento para el seguimiento de MSVC que se está deteniendo. |
| `RESULT_CODE_FAILURE_MERGE_TRACES` | 23 (0x00000017) | Se produjo un error al combinar seguimientos mediante el control de seguimiento de kernel. |
| `RESULT_CODE_FAILURE_UNKNOWN_ERROR` | 24 (0x00000018) | Se produjo un error desconocido. |

::: moniker-end

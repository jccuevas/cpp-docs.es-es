---
title: 'Referencia: comandos de vcperf'
description: Referencia de la utilidad de línea de comandos vcperf. exe.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b85320ce4517eb41410c59a11bd79553405b8402
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333885"
---
# <a name="reference-vcperf-commands"></a>Referencia: comandos de vcperf

::: moniker range="<=vs-2017"

Las C++ herramientas de Build Insights están disponibles en Visual Studio 2019. Para ver la documentación de esa versión, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

En este artículo se enumeran y describen los comandos disponibles en *vcperf. exe*y cómo usarlos.

## <a name="commands-to-start-and-stop-traces"></a>Comandos para iniciar y detener seguimientos

*IMPORTANTE: todos los comandos siguientes requieren privilegios administrativos.*

| Opción           | Argumentos y descripción |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | Indica a *vcperf. exe* que inicie un seguimiento con el nombre de sesión determinado. Solo puede haber una sesión activa a la vez en un equipo determinado. <br/><br/> Si se especifica la opción `/nocpusampling`, *vcperf. exe* no recopila ejemplos de la CPU. Impide el uso de la vista uso de CPU (muestreado) en el analizador de rendimiento de Windows, pero hace que los seguimientos recopilados sean más pequeños. <br/><br/> Una vez iniciado el seguimiento, *vcperf. exe* vuelve inmediatamente. Los eventos se recopilan en todo el sistema para todos los procesos que se ejecutan en la máquina. Esto significa que no es necesario compilar el proyecto desde el mismo símbolo del sistema que el que se usó para ejecutar *vcperf. exe*. Por ejemplo, puede compilar el proyecto desde Visual Studio. |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | Detiene el seguimiento identificado por el nombre de sesión determinado. Ejecuta un paso de procesamiento posterior en el seguimiento para generar un archivo visible en el analizador de rendimiento de Windows (WPA). Para obtener la mejor experiencia de visualización, use una versión de WPA que C++ incluya el complemento Build Insights. Para obtener más información, consulte Introducción [a C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). El parámetro `<outputFile.etl>` especifica dónde se debe guardar el archivo de salida. |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | Detiene el seguimiento identificado por el nombre de sesión determinado y escribe los datos sin procesar y sin procesar en el archivo de salida especificado. El archivo resultante no está diseñado para verlo en WPA. <br/><br/> En ocasiones, el paso posterior al procesamiento implicado en el comando `/stop` puede ser largo. Puede usar el comando `/stopnoanalyze` para retrasar este paso posterior al procesamiento. Use el comando `/analyze` cuando esté listo para generar un archivo visible en el analizador de rendimiento de Windows. |

## <a name="miscellaneous-commands"></a>Comandos varios

| Opción     | Argumentos y descripción |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | Acepta un archivo de seguimiento sin procesar generado por el comando `/stopnoanalyze`. Ejecuta un paso posterior al procesamiento en este seguimiento para generar un archivo visible en el analizador de rendimiento de Windows. Para obtener la mejor experiencia de visualización, use una versión de WPA que C++ incluya el complemento Build Insights. Para obtener más información, consulte Introducción [a C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). |

## <a name="see-also"></a>Vea también

[Introducción a la C++ información de compilación](/cpp/build-insights/get-started-with-cpp-build-insights)\
[Tutorial: aspectos básicos del analizador de rendimiento de Windows](/cpp/build-insights/tutorials/wpa-basics)\
[Referencia: vistas del analizador de rendimiento de Windows](wpa-views.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end

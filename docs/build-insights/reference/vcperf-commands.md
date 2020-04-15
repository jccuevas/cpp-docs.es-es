---
title: 'Referencia: comandos vcperf'
description: Referencia para la utilidad de línea de comandos vcperf.exe.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9d3b0a9dbdfe922dc87f91006441e1f65d54c8a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323254"
---
# <a name="reference-vcperf-commands"></a>Referencia: comandos vcperf

::: moniker range="<=vs-2017"

Las herramientas de C++ Build Insights están disponibles en Visual Studio 2019. Para ver la documentación de esa versión, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range="vs-2019"

En este artículo se enumeran y describen los comandos disponibles en *vcperf.exe*y cómo usarlos.

## <a name="commands-to-start-and-stop-traces"></a>Comandos para iniciar y detener trazas

*IMPORTANTE: todos los siguientes comandos requieren privilegios administrativos.*

| Opción           | Argumentos y descripción |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | Indica a *vcperf.exe* que inicie un seguimiento con el nombre de sesión especificado. Solo puede haber una sesión activa a la vez en una máquina determinada. <br/><br/> Si `/nocpusampling` se especifica la opción, *vcperf.exe* no recopila muestras de CPU. Impide el uso de la vista Uso de CPU (muestreado) en el Analizador de rendimiento de Windows, pero hace que los seguimientos recopilados sean más pequeños. <br/><br/> Una vez que se inicia el seguimiento, *vcperf.exe* devuelve inmediatamente. Los eventos se recopilan en todo el sistema para todos los procesos que se ejecutan en la máquina. Esto significa que no es necesario compilar el proyecto desde el mismo símbolo del sistema que el que usó para ejecutar *vcperf.exe*. Por ejemplo, puede compilar el proyecto desde Visual Studio. |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | Detiene el seguimiento identificado por el nombre de sesión especificado. Ejecuta un paso de postprocesamiento en el seguimiento para generar un archivo visible en El Analizador de rendimiento de Windows (WPA). Para obtener la mejor experiencia de visualización, utilice una versión de WPA que incluya el complemento C++ Build Insights. Para obtener más información, consulte [Introducción a C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). El `<outputFile.etl>` parámetro especifica dónde guardar el archivo de salida. |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | Detiene el seguimiento identificado por el nombre de sesión especificado y escribe los datos sin procesar en el archivo de salida especificado. El archivo resultante no está destinado a ser visto en WPA. <br/><br/> El paso de postprocesamiento `/stop` implicado en el comando a veces puede ser largo. Puede utilizar `/stopnoanalyze` el comando para retrasar este paso de postprocesamiento. Utilice `/analyze` el comando cuando esté listo para generar un archivo visible en el Analizador de rendimiento de Windows. |

## <a name="miscellaneous-commands"></a>Comandos varios

| Opción     | Argumentos y descripción |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | Acepta un archivo de seguimiento `/stopnoanalyze` sin procesar generado por el comando. Ejecuta un paso de postprocesamiento en este seguimiento para generar un archivo visible en el Analizador de rendimiento de Windows. Para obtener la mejor experiencia de visualización, utilice una versión de WPA que incluya el complemento C++ Build Insights. Para obtener más información, consulte [Introducción a C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights). |

## <a name="see-also"></a>Consulte también

[Comience con C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights)\
[Tutorial: Conceptos básicos de Windows Performance Analyzer](/cpp/build-insights/tutorials/wpa-basics)\
[Referencia: Vistas de Windows Performance Analyzer](wpa-views.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end

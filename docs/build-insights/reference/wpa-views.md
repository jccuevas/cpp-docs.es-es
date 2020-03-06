---
title: 'Referencia: vistas del analizador de rendimiento de Windows'
description: Referencia de C++ las vistas de Build Insights disponibles en el analizador de rendimiento de Windows.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eb3e20ed3ca4231b10efaf36310f6fbc0f5980bf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333897"
---
# <a name="reference-windows-performance-analyzer-views"></a>Referencia: vistas del analizador de rendimiento de Windows

::: moniker range="<=vs-2017"

Las C++ herramientas de Build Insights están disponibles en Visual Studio 2019. Para ver la documentación de esa versión, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

En este artículo se proporcionan detalles sobre cada C++ una de las vistas de Build Insights disponibles en el analizador de rendimiento de Windows (WPA). Use esta página para buscar:

- descripciones de columnas de datos; etc
- valores preestablecidos disponibles para cada vista, incluido el uso previsto y el modo de visualización preferido.

Si no está familiarizado con WPA, se recomienda que primero se familiarice con los [aspectos básicos de WPA C++ para la información de compilación](/cpp/build-insights/tutorials/wpa-basics).

## <a name="build-explorer"></a>Build Explorer

La vista del explorador de compilaciones se usa para:

- Diagnostique problemas de paralelismo,
- determinar si el tiempo de compilación está dominado por el análisis, la generación de código o la vinculación, y
- Identifique los cuellos de botella y las actividades de compilación largas.

### <a name="build-explorer-view-data-columns"></a>Columnas de datos de la vista del explorador de compilaciones

| Nombre de columna | Descripción |
|-|-|
| BuildTimelineDescription | Una descripción textual de la escala de tiempo en la que se produce la actividad o propiedad actual. |
| BuildTimelineId          | Identificador de base cero para la escala de tiempo en la que se produce la actividad o propiedad actual. |
| Componente                | Componente que se va a compilar o vincular cuando se emitió el evento actual. El valor de esta columna es *\<invocación X Info\>* cuando no hay ningún componente asociado a este evento. X es un identificador numérico único para la invocación que se está ejecutando en el momento en que se emitió el evento. Este identificador es el mismo que el de la columna ID. de invocación para este evento. |
| Recuento                    | El número de actividades o propiedades representadas por esta fila de datos. Este valor es siempre 1 y solo es útil en escenarios de agregación cuando se agrupan varias filas. |
| ExclusiveCPUTime         | Cantidad de tiempo de CPU en milisegundos utilizado por esta actividad. El tiempo invertido en las actividades secundarias no se incluye en esta cantidad. |
| ExclusiveDuration        | Duración de milisegundos de la actividad. La duración de las actividades secundarias no se incluye en esta cantidad. |
| InclusiveCPUTime         | La cantidad de tiempo de CPU en milisegundos usada por esta actividad y todas las actividades secundarias. |
| InclusiveDuration        | Duración en milisegundos de esta actividad, incluidas todas las actividades secundarias. |
| InvocationDescription    | Una descripción textual de la invocación en la que se produjo este evento. La descripción incluye si es *cl. exe* o *Link. exe*y un identificador de invocación numérico único. Si es aplicable, incluye la ruta de acceso completa al componente compilado o vinculado durante la invocación. En el caso de las invocaciones que no compilan ningún componente, o para los que compilan varios componentes, la ruta de acceso está en blanco. El identificador de invocación es el mismo que el de la columna de invocación. |
| Vocación             | Identificador numérico único para la invocación en la que se produjo este evento. |
| Name                     | Nombre de la actividad o propiedad representada por este evento. |
| Tiempo                     | Marca de tiempo que identifica Cuándo se produjo el evento. |
| Herramienta                     | Herramienta que se ejecuta cuando se produjo este evento. El valor de esta columna es CL o link. |
| Tipo                     | Tipo del evento actual. Este valor es Activity o Property. |
| Valor                    | Si el evento actual es una propiedad, esta columna contiene su valor. Esta columna se deja en blanco cuando el evento actual es una actividad. |

### <a name="build-explorer-view-presets"></a>Valores preestablecidos de vista del explorador de compilaciones

| Nombre preestablecido           | Modo de vista preferido | Modo de uso |
|-----------------------|---------------------|------------|
| Estadísticas de actividad   | Gráfico o tabla       | Use este valor preestablecido para ver las estadísticas agregadas de todas las actividades del explorador de compilaciones. En el modo de tabla, observe de un vistazo si la compilación está dominada por el análisis, la generación de código o el enlazador. Las duraciones agregadas para cada actividad se ordenan en orden descendente. Profundice expandiendo el nodo superior para encontrar fácilmente las invocaciones que tardan más tiempo en estas actividades principales. Si lo desea, puede ajustar la configuración de WPA para mostrar los promedios u otros tipos de agregaciones. En el modo de gráfico, vea cuando cada actividad está activa durante la compilación. |
| Invocaciones           | Grafo               | Desplácese hacia abajo a través de una lista de invocaciones en la vista de gráfico ordenadas por hora de inicio. Puede usarlo junto con la vista CPU (muestreada) para buscar las invocaciones que se alinean con zonas de uso de CPU bajas. Detectar problemas de paralelismo. |
| Propiedades de invocación | Table               | Buscar rápidamente información clave sobre una invocación de un compilador o vinculador determinado. Determine la versión, el directorio de trabajo o la línea de comandos completa que se usa para invocarlo. |
| Escalas de tiempo             | Grafo               | Vea un gráfico de barras de cómo se ejecutó la compilación en paralelo. Identificar problemas de paralelismo y cuellos de botella de un vistazo. Configure WPA para asignar significados diferentes a las barras según sus necesidades. Elija descripciones de invocación como la última columna agrupada para ver un gráfico de barras codificadas en color de todas las invocaciones. Le ayuda a identificar rápidamente los culpables que consumen tiempo. A continuación, acerque y elija el nombre de la actividad como la última columna agrupada para ver las partes más largas. |

## <a name="files"></a>Files

La vista archivos se utiliza para:

- Determine qué encabezados se incluyen con más frecuencia y
- ayudarle a decidir qué incluir en un encabezado precompilado (PCH).

### <a name="files-view-data-columns"></a>Columnas de datos de la vista archivos

| Nombre de columna              | Descripción |
|--------------------------|-------------|
| ActivityName             | La actividad en curso cuando se emitió este evento de archivo. Actualmente, este valor siempre se está *analizando*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Componente                | * |
| Recuento                    | * |
| Profundidad                    | Posición de base cero del árbol de inclusión en el que se encuentra este archivo. El recuento empieza en la raíz del árbol de inclusión. Un valor de 0 normalmente corresponde a un archivo. c/. cpp. |
| ExclusiveDuration        | * |
| IncludedBy               | Ruta de acceso completa del archivo que incluía el archivo actual. |
| IncludedPath             | Ruta de acceso completa del archivo actual. |
| InclusiveDuration        | * |
| Vocación             | * |
| StartTime                | Marca de tiempo que representa la hora a la que se emitió el evento de archivo actual. |
| Herramienta                     | * |

\* el valor de esta columna es el mismo que en la vista del [Explorador de compilaciones](#build-explorer-view-data-columns) .

### <a name="files-view-presets"></a>Valores preestablecidos de vista de archivos

| Nombre preestablecido | Modo de vista preferido | Modo de uso |
|-------------|---------------------|------------|
| Estadísticas  | Table               | Vea qué archivos tenían el mayor tiempo de análisis agregado mirando la lista en orden descendente. Utilice esta información como ayuda para reestructurar los encabezados o para decidir qué incluir en el PCH. |

## <a name="functions"></a>Funciones

La vista funciones se usa para identificar las funciones con una hora de generación de código excesivamente larga.

### <a name="functions-view-data-columns"></a>Columnas de datos de la vista funciones

| Nombre de columna              | Descripción |
|--------------------------|-------------|
| ActivityName             | La actividad en curso cuando se emitió este evento de función. Actualmente, este valor siempre es *CodeGeneration*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Componente                | * |
| Recuento                    | * |
| Duración                 | La duración de la actividad de generación de código para esta función. |
| FunctionName             | Nombre de la función que se está sometiendo a la generación de código. |
| Vocación             | * |
| StartTime                | Marca de tiempo que representa Cuándo se emitió el evento de función actual. |
| Herramienta                     | * |

\* el valor de esta columna es el mismo que en la vista del [Explorador de compilaciones](#build-explorer-view-data-columns) .

### <a name="functions-view-presets"></a>Valores preestablecidos de vista de funciones

| Nombre preestablecido | Modo de vista preferido | Modo de uso |
|-------------|---------------------|------------|
| Estadísticas  | Table               | Vea qué funciones tenían el mayor tiempo de generación de código agregado mirando la lista en orden descendente. Pueden sugerir el lugar en el que el código sobreutiliza la palabra clave **__forceinline** o que algunas funciones pueden ser demasiado grandes. |
| Escalas de tiempo   | Grafo               | Eche un vistazo a este gráfico de barras para conocer la ubicación y la duración de las funciones que tardan más tiempo en generarse. Vea si se alinean con cuellos de botella en la vista del explorador de compilaciones. Si lo hacen, tome las medidas adecuadas para reducir su tiempo de generación de código y beneficiarse de los tiempos de compilación. |

## <a name="see-also"></a>Vea también

[Introducción a la C++ información de compilación](/cpp/build-insights/get-started-with-cpp-build-insights)\
[Referencia: comandos de vcperf](vcperf-commands.md)\
[Tutorial: aspectos básicos del analizador de rendimiento de Windows](/cpp/build-insights/tutorials/wpa-basics)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end

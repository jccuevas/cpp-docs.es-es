---
title: 'Referencia: Vistas de Windows Performance Analyzer'
description: Referencia para las vistas de C++ Build Insights disponibles en el Analizador de rendimiento de Windows.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b54b1b76d83b77ec7b8d8d3309d81ed9eb2db2d0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323235"
---
# <a name="reference-windows-performance-analyzer-views"></a>Referencia: Vistas de Windows Performance Analyzer

::: moniker range="<=vs-2017"

Las herramientas de C++ Build Insights están disponibles en Visual Studio 2019. Para ver la documentación de esta versión, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range="vs-2019"

En este artículo se proporcionan detalles sobre cada una de las vistas de C++ Build Insights disponibles en Windows Performance Analyzer (WPA). Utilice esta página para encontrar:

- descripciones de columnas de datos; Y
- ajustes preestablecidos disponibles para cada vista, incluido su uso previsto y el modo de visualización preferido.

Si es nuevo en WPA, le recomendamos que primero se familiarice con los [conceptos básicos de WPA para C++ Build Insights](/cpp/build-insights/tutorials/wpa-basics).

## <a name="build-explorer"></a>Explorador de compilaciones

La vista Explorador de compilación se utiliza para:

- diagnosticar problemas de paralelismo,
- determinar si el tiempo de compilación está dominado por el análisis, la generación de código o la vinculación, y
- identificar cuellos de botella y actividades de construcción inusualmente largas.

### <a name="build-explorer-view-data-columns"></a>Crear columnas de datos de vista del Explorador

| Nombre de columna | Descripción |
|-|-|
| BuildTimelineDescription | Una descripción textual de la línea de tiempo en la que se produce la actividad o propiedad actual. |
| BuildTimelineId          | Identificador de base cero para la línea de tiempo en la que se produce la actividad o propiedad actual. |
| Componente                | El componente que se compila o vincula cuando se emite el evento actual. El valor de esta columna es * \<Invocation X Info\> * cuando no hay ningún componente asociado a este evento. X es un identificador numérico único para la invocación que se ejecuta en el momento en que se emitió el evento. Este identificador es el mismo que el de la columna InvocationId para este evento. |
| Count                    | El número de actividades o propiedades representadas por esta fila de datos. Este valor siempre es 1 y solo es útil en escenarios de agregación cuando se agrupan varias filas. |
| ExclusiveCPUTime         | La cantidad de tiempo de CPU en milisegundos utilizado por esta actividad. El tiempo dedicado a las actividades infantiles no está incluido en esta cantidad. |
| ExclusiveDuration        | La duración de milisegundos de la actividad. La duración de las actividades secundarias no está incluida en esta cantidad. |
| InclusiveCPUTime         | La cantidad de tiempo de CPU en milisegundos utilizado por esta actividad y todas las actividades secundarias. |
| InclusiveDuration        | Duración de milisegundos de esta actividad, incluidas todas las actividades secundarias. |
| InvocationDescription    | Una descripción textual de la invocación en la que se produjo este evento. La descripción incluye si fue *cl.exe* o *link.exe,* y un identificador de invocación numérico único. Si procede, incluye la ruta de acceso completa al componente compilado o vinculado durante la invocación. Para las invocaciones que no crean ningún componente, o para las que crean varios componentes, la ruta de acceso está en blanco. El identificador de invocación es el mismo que el de la columna InvocationId. |
| InvocationId             | Un identificador numérico único para la invocación en la que se produjo este evento. |
| Nombre                     | El nombre de la actividad o propiedad representada por este evento. |
| Time                     | Una marca de tiempo que identifica cuándo se produjo el evento. |
| Herramienta                     | La herramienta que se ejecuta cuando se produjo este evento. El valor de esta columna es CL o Link. |
| Tipo                     | El tipo del evento actual. Este valor es Activity o Property. |
| Value                    | Si el evento actual es una propiedad, esta columna contiene su valor. Esta columna se deja en blanco cuando el evento actual es una actividad. |

### <a name="build-explorer-view-presets"></a>Crear ajustes preestablecidos de vista del Explorador

| Nombre preestablecido           | Modo de vista preferido | Modo de uso |
|-----------------------|---------------------|------------|
| Estadísticas de actividad   | Gráfico / Tabla       | Utilice este ajuste preestablecido para ver las estadísticas agregadas de todas las actividades del Explorador de compilación. En el modo de tabla, indique de un vistazo si la compilación está dominada por el análisis, la generación de código o el vinculador. Las duraciones agregadas para cada actividad se ordenan en orden descendente. Profundice expandiendo el nodo superior para encontrar fácilmente qué invocaciones toman más tiempo para estas actividades principales. Si lo desea, puede ajustar la configuración wpa para mostrar promedios u otros tipos de agregaciones. En el modo gráfico, vea cuándo cada actividad está activa durante la compilación. |
| Invocaciones           | Grafo               | Desplácese hacia abajo por una lista de invocaciones en la vista de gráfico ordenadas por hora de inicio. Puede usarlo junto con la vista CPU (muestreada) para buscar invocaciones que se alineen con zonas de uso de CPU bajas. Detectar problemas de paralelismo. |
| Propiedades de invocación | Tabla               | Encuentre rápidamente información clave sobre una invocación determinada del compilador o del vinculador. Determine su versión, el directorio de trabajo o la línea de comandos completa utilizada para invocarla. |
| Escalas de tiempo             | Grafo               | Vea un gráfico de barras de cómo se paralizó la compilación. Identifique los problemas de paralelismo y los cuellos de botella de un vistazo. Configure WPA para asignar diferentes significados a las barras de acuerdo a sus necesidades. Elija las descripciones de invocación como la última columna agrupada para ver un gráfico de barras codificado por colorde todas sus invocaciones. Le ayuda a identificar rápidamente a los culpables que consumen mucho tiempo. A continuación, haga zoom y elija el nombre de la actividad como la última columna agrupada para ver las partes más largas. |

## <a name="files"></a>Archivos

La vista Archivos se utiliza para:

- determinar qué encabezados se incluyen con más frecuencia, y
- ayudarle a decidir qué incluir en un encabezado precompilado (PCH).

### <a name="files-view-data-columns"></a>Los archivos ven columnas de datos

| Nombre de columna              | Descripción |
|--------------------------|-------------|
| ActivityName             | La actividad en curso cuando se emitió este evento de archivo. Actualmente, este valor siempre es *Análisis*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Componente                | * |
| Count                    | * |
| Profundidad                    | La posición de base cero en el árbol de inclusión en el que se encuentra este archivo. El recuento comienza en la raíz del árbol de inclusión. Un valor de 0 normalmente corresponde a un archivo .c/.cpp. |
| ExclusiveDuration        | * |
| IncluidoPor               | La ruta de acceso completa del archivo que incluía el archivo actual. |
| IncludedPath             | La ruta de acceso completa del archivo actual. |
| InclusiveDuration        | * |
| InvocationId             | * |
| StartTime                | Una marca de tiempo que representa la hora en la que se emitió el evento de archivo actual. |
| Herramienta                     | * |

\*El valor de esta columna es el mismo que en la vista Explorador de [compilación.](#build-explorer-view-data-columns)

### <a name="files-view-presets"></a>Los archivos visualizan los ajustes preestablecidos

| Nombre preestablecido | Modo de vista preferido | Modo de uso |
|-------------|---------------------|------------|
| Estadísticas  | Tabla               | Vea qué archivos tenían el tiempo de análisis agregado más alto mirando la lista en orden descendente. Utilice esta información para ayudarle a reestructurar sus encabezados o decidir qué incluir en su PCH. |

## <a name="functions"></a>Functions

La vista Funciones se utiliza para identificar funciones con un tiempo de generación de código excesivamente largo.

### <a name="functions-view-data-columns"></a>Las funciones ven columnas de datos

| Nombre de columna              | Descripción |
|--------------------------|-------------|
| ActivityName             | La actividad en curso cuando se emitió este evento de función. Actualmente, este valor siempre es *CodeGeneration*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Componente                | * |
| Count                    | * |
| Duration                 | La duración de la actividad de generación de código para esta función. |
| FunctionName             | El nombre de la función que pasa por la generación de código. |
| InvocationId             | * |
| StartTime                | Una marca de tiempo que representa cuándo se emitió el evento de función actual. |
| Herramienta                     | * |

\*El valor de esta columna es el mismo que en la vista Explorador de [compilación.](#build-explorer-view-data-columns)

### <a name="functions-view-presets"></a>Las funciones visualizan los ajustes preestablecidos

| Nombre preestablecido | Modo de vista preferido | Modo de uso |
|-------------|---------------------|------------|
| Estadísticas  | Tabla               | Vea qué funciones tenían el mayor tiempo de generación de código agregado mirando la lista en orden descendente. Pueden sugerir dónde el código utiliza en exceso la palabra clave **__forceinline** o que algunas funciones pueden ser demasiado grandes. |
| Escalas de tiempo   | Grafo               | Observe este gráfico de barras para conocer la ubicación y la duración de las funciones que tardan más tiempo en generarse. Compruebe si se alinean con los cuellos de botella en la vista Explorador de compilación. Si lo hacen, tome las medidas adecuadas para reducir su tiempo de generación de código y beneficiar sus tiempos de compilación. |

## <a name="see-also"></a>Consulte también

[Comience con C++ Build Insights](/cpp/build-insights/get-started-with-cpp-build-insights)\
[Referencia: comandos vcperf](vcperf-commands.md)\
[Tutorial: Conceptos básicos de Windows Performance Analyzer](/cpp/build-insights/tutorials/wpa-basics)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end

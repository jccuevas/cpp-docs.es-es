---
title: 'C++Información de compilación: aspectos básicos del analizador de rendimiento de Windows'
description: Tutorial sobre cómo completar operaciones básicas en el analizador de rendimiento de Windows.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4bd91698561175d876b7a3351a0ed6e85ef73a35
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633211"
---
# <a name="c-build-insights-windows-performance-analyzer-basics"></a>C++Información de compilación: aspectos básicos del analizador de rendimiento de Windows

::: moniker range="<=vs-2017"

Las C++ herramientas de Build Insights están disponibles en Visual Studio 2019. Para ver la documentación de esa versión, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

El C++ uso eficaz de Build Insights requiere cierto conocimiento del analizador de rendimiento de Windows (WPA). Este artículo le ayudará a familiarizarse con las operaciones comunes de WPA. Para obtener más información sobre cómo usar WPA, consulte la documentación del [analizador de rendimiento de Windows](/windows-hardware/test/wpt/windows-performance-analyzer) .

## <a name="change-the-view-mode"></a>Cambiar el modo de vista

WPA ofrece dos modos de vista básicos para explorar los seguimientos:

- modo de gráfico y
- modo de tabla.

Puede cambiar entre ellos mediante los iconos de modo de vista en la parte superior del panel de vista:

![Cambiar entre el modo de gráfico y el modo de tabla.](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>Seleccionar valores preestablecidos

La C++ mayoría de las vistas de WPA de Build Insights tienen varios valores preestablecidos para elegir. Puede seleccionar el valor preestablecido que desee mediante el menú desplegable de la parte superior del panel Vista:

![Seleccionar un valor preestablecido.](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>Acercar y alejar

Algunos seguimientos de compilación son tan grandes que es difícil de tomar los detalles. Para acercar un área que le interese, haga clic con el botón derecho en el gráfico y seleccione **zoom**. Siempre puede volver a la configuración anterior seleccionando **Deshacer zoom**. En esta imagen se muestra un ejemplo del uso de una selección y el comando **zoom** para acercar una sección del gráfico:

![Acercar un gráfico.](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>Agrupar por columnas diferentes

Puede personalizar la forma en que se muestra el seguimiento. Haga clic en el icono de engranaje en la parte superior de un panel de vista y reorganice las columnas en el editor de vistas del explorador de compilaciones. Las columnas que se encuentran por encima de la línea amarilla en este cuadro de diálogo son las que están agrupadas por las filas de datos. La columna situada justo encima de la línea amarilla es especial: en la vista gráfico, se muestra en las barras coloreadas.

En esta imagen se muestra un gráfico de barras de ejemplo de una invocación de vínculo. Usamos el icono de engranaje para abrir el cuadro de diálogo Editor de vistas del explorador de compilaciones. A continuación, se arrastran las entradas de la columna componente y nombre por encima de la línea amarilla. La configuración se cambia para aumentar el nivel de detalle y para ver lo que sucede realmente dentro del enlazador:

![Acercar un gráfico.](media/wpa-grouping.gif)

## <a name="see-also"></a>Vea también

[Introducción a la C++ información de compilación](get-started-with-cpp-build-insights.md)\
\ de [referencia de vcperf. exe](vcperf-reference.md)
[Referencia](wpa-views-reference.md) de las vistas del analizador de rendimiento de Windows\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end

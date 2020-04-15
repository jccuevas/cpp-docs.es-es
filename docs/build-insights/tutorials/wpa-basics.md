---
title: 'Tutorial: Conceptos básicos de Windows Performance Analyzer'
description: Tutorial sobre cómo completar operaciones básicas en el Analizador de rendimiento de Windows.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ae1050b9389527a12f5bdbea6d695c0f20510127
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323401"
---
# <a name="tutorial-windows-performance-analyzer-basics"></a>Tutorial: Conceptos básicos de Windows Performance Analyzer

::: moniker range="<=vs-2017"

Las herramientas de C++ Build Insights están disponibles en Visual Studio 2019. Para ver la documentación de esta versión, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range="vs-2019"

El uso eficaz de C++ Build Insights requiere cierto conocimiento de Windows Performance Analyzer (WPA). Este artículo le ayuda a familiarizarse con las operaciones WPA comunes. Para obtener más información sobre cómo utilizar WPA, consulte la documentación [de Windows Performance Analyzer.](/windows-hardware/test/wpt/windows-performance-analyzer)

## <a name="change-the-view-mode"></a>Cambiar el modo de vista

WPA ofrece dos modos de vista básicos para que usted explore sus trazas:

- modo gráfico, y
- modo de tabla.

Puede cambiar entre ellos mediante los iconos de modo de vista en la parte superior del panel de vista:

![Cambio entre el modo gráfico y el modo de tabla.](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>Seleccionar ajustes preestablecidos

La mayoría de las vistas WPA de C++ Build Insights tienen varios ajustes preestablecidos para que pueda elegir. Puede seleccionar el ajuste preestablecido que desee mediante el menú desplegable en la parte superior del panel de vista:

![Selección de un ajuste preestablecido.](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>Acercar y alejar

Algunos trazos de construcción son tan grandes que es difícil de averiguar los detalles. Para acercar un área que le interese, haga clic con el botón derecho en el gráfico y seleccione **Zoom**. Siempre puede volver a la configuración anterior seleccionando **Deshacer zoom**. Esta imagen muestra un ejemplo del uso de una selección y el comando **Zoom** para acercar una sección del gráfico:

![Acercamiento a un gráfico.](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>Agrupar por diferentes columnas

Puede personalizar la forma en que se muestra el seguimiento. Haga clic en el icono de engranaje en la parte superior de un panel de vista y reorganice las columnas en el Editor de vistas del Explorador de compilación. Las columnas que se encuentran encima de la línea amarilla en este cuadro de diálogo son las que se agrupan las filas de datos. La columna situada justo encima de la línea amarilla es especial: en la vista de gráfico, se muestra en las barras de color.

Esta imagen muestra un gráfico de barras de ejemplo de una invocación de vínculo. Usamos el icono de engranaje para abrir el cuadro de diálogo Editor de vistas del Explorador de compilación. A continuación, arrastramos las entradas de columna Componente y Nombre por encima de la línea amarilla. La configuración se cambia para aumentar el nivel de detalle, y para ver lo que realmente sucedió dentro del vinculador:

![Acercamiento a un gráfico.](media/wpa-grouping.gif)

## <a name="see-also"></a>Consulte también

[Tutorial: vcperf y Windows Performance Analyzer](vcperf-and-wpa.md)\
[Referencia: comandos vcperf](/cpp/build-insights/reference/vcperf-commands)\
[Referencia: Vistas de Windows Performance Analyzer](/cpp/build-insights/reference/wpa-views)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end

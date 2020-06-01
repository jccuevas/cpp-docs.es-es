---
title: Introducción a C++ Build Insights
description: Información general sobre C++ Build Insights.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28d7e0758ea521af424129c546297fc97e3d6659
ms.sourcegitcommit: 8c8ed02a6f3bcb5ee008e3fe30ba7595d7c4c922
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2020
ms.locfileid: "83759230"
---
# <a name="get-started-with-c-build-insights"></a>Introducción a C++ Build Insights

::: moniker range="<=vs-2017"

Las herramientas de C++ Build Insights están disponibles en Visual Studio 2019. Para ver la documentación de esa versión, establezca el control de selector **Versión** de Visual Studio para este artículo en Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range="vs-2019"

C++ Build Insights es una colección de herramientas que proporciona mayor visibilidad en la cadena de herramientas de Microsoft Visual C++ (MSVC). Las herramientas recopilan datos sobre las compilaciones de C++ y se presentan en un formato que puede ayudarlo a responder a preguntas comunes, como las siguientes:

- ¿Las compilaciones están lo suficientemente paralelizadas?
- ¿Qué debería incluir en mi encabezado precompilado (PCH)?
- ¿Hay un cuello de botella específico en el que me deba centrar para aumentar la velocidad de compilación?

Los componentes principales de esta tecnología son estos:

- *vcperf.exe*, una utilidad de línea de comandos que puede usar para recopilar seguimientos de las compilaciones.
- Una extensión de Windows Performance Analyzer (WPA) que permite ver los seguimientos de compilaciones en WPA.
- El SDK de C++ Build Insights, un kit de desarrollo de software para crear sus propias herramientas que consuman datos de C++ Build Insights.

## <a name="documentation-sections"></a>Secciones de la documentación

[Tutorial: vcperf y Windows Performance Analyzer](tutorials/vcperf-and-wpa.md)\
Obtenga información sobre cómo recopilar seguimientos de compilaciones de los proyectos de C++ y cómo verlos en WPA.

[Tutorial: Aspectos básicos de las herramientas de rendimiento de Windows](tutorials/wpa-basics.md)\
Descubra sugerencias de WPA útiles para analizar los seguimientos de compilaciones.

[SDK de C++ Build Insights](reference/sdk/overview.md)\
Información general sobre el SDK de C++ Build Insights.

## <a name="articles"></a>Artículos

Lea estos artículos del blog oficial del equipo de C++ para obtener más información sobre C++ Build Insights:

[Introducción a C++ Build Insights](https://devblogs.microsoft.com/cppblog/introducing-c-build-insights/)

[Análisis de las compilaciones mediante programación con el SDK de C++ Build Insights](https://devblogs.microsoft.com/cppblog/analyze-your-builds-programmatically-with-the-c-build-insights-sdk/)

[Búsqueda de cuellos de botella de compilación con C++ Build Insights](https://devblogs.microsoft.com/cppblog/finding-build-bottlenecks-with-cpp-build-insights/)

[Compilaciones más rápidas con las sugerencias de PCH de C++ Build Insights](https://devblogs.microsoft.com/cppblog/faster-builds-with-pch-suggestions-from-c-build-insights/)

::: moniker-end

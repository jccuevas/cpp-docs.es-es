---
title: Introducción a C++ Build Insights
description: Una visión general de alto nivel de C++ Build Insights.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3a75dfe3bf1263cce53d70b764607cad4eec86d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325717"
---
# <a name="get-started-with-c-build-insights"></a>Introducción a C++ Build Insights

::: moniker range="<=vs-2017"

Las herramientas de C++ Build Insights están disponibles en Visual Studio 2019. Para ver la documentación de esa versión, establezca el control Selector de **versiones** de Visual Studio para este artículo en Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end
::: moniker range="vs-2019"

C++ Build Insights es una colección de herramientas que proporciona una mayor visibilidad de la cadena de herramientas de Microsoft Visual C++ (MSVC). Las herramientas recopilan datos sobre sus compilaciones de C++ y los presentan en un formato que puede ayudarle a responder preguntas comunes, como:

- ¿Están mis construcciones suficientemente paralelizadas?
- ¿Qué debo incluir en mi encabezado precompilado (PCH)?
- ¿Hay un cuello de botella específico en el que deba centrarme para aumentar mis velocidades de compilación?

Los principales componentes de esta tecnología son:

- *vcperf.exe*, una utilidad de línea de comandos que puede utilizar para recopilar seguimientos para sus compilaciones,
- una extensión de Windows Performance Analyzer (WPA) que le permite ver las trazas de compilación en WPA, y
- el SDK de C++ Build Insights, un kit de desarrollo de software para crear sus propias herramientas que consumen datos de C++ Build Insights.

Haga clic en los enlaces a continuación para comenzar rápidamente con estos componentes:

[Tutorial: vcperf y Windows Performance Analyzer](tutorials/vcperf-and-wpa.md)\
Aprenda a recopilar seguimientos de compilación para sus proyectos C++ y cómo verlos en WPA.

[Tutorial: Conceptos básicos de rendimiento de Windows](tutorials/wpa-basics.md)\
Descubra consejos útiles de WPA para analizar sus trazas de compilación.

[C++ Build Insights SDK](reference/sdk/overview.md)\
Descripción general del SDK de C++ Build Insights.

::: moniker-end

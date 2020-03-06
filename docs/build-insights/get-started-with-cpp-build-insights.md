---
title: Introducción a C++ Build Insights
description: Información general de alto nivel sobre C++ la información de compilación.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2a5799fecc885b96f4278e0f5077662ce5fd7c8f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332012"
---
# <a name="get-started-with-c-build-insights"></a>Introducción a C++ Build Insights

::: moniker range="<=vs-2017"

Las C++ herramientas de Build Insights están disponibles en Visual Studio 2019. Para ver la documentación de esa versión, establezca el control selector de versión de Visual Studio para este artículo en Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

C++Build Insights es una colección de herramientas que proporciona mayor visibilidad en la cadena de herramientas C++ de Microsoft Visual (MSVC). Las herramientas recopilan datos sobre C++ las compilaciones y la presentan en un formato que puede ayudarle a responder a preguntas comunes, como:

- ¿Las compilaciones son suficientemente paralelas?
- ¿Qué debo incluir en mi encabezado precompilado (PCH)?
- ¿Hay un cuello de botella específico en el que se debe centrar para aumentar la velocidad de compilación?

Los componentes principales de esta tecnología son:

- *vcperf. exe*, una utilidad de línea de comandos que puede usar para recopilar seguimientos de las compilaciones.
- una extensión del analizador de rendimiento de Windows (WPA) que le permite ver los seguimientos de la compilación en WPA.
- el C++ SDK de Build Insights, un kit de desarrollo de software para crear sus propias herramientas C++ que consumen datos de Build Insights.

Haga clic en los vínculos siguientes para empezar a trabajar rápidamente con estos componentes:

[Tutorial: vcperf y el analizador de rendimiento de Windows](tutorials/vcperf-and-wpa.md)\
Obtenga información sobre cómo recopilar seguimientos C++ de compilación para los proyectos y cómo verlos en WPA.

[Tutorial: aspectos básicos del rendimiento de Windows](tutorials/wpa-basics.md)\
Descubra sugerencias de WPA útiles para analizar los seguimientos de la compilación.

\ del [SDK de Build Insights C++ ](reference/sdk/overview.md)
Información general sobre el C++ SDK de Build Insights.

::: moniker-end

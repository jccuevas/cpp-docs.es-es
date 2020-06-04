---
title: Error irrecuperable C1001
ms.date: 11/04/2016
f1_keywords:
- C1001
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
ms.openlocfilehash: e1255578883c8d2bc278184a02575a0a51ed9b6c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204963"
---
# <a name="fatal-error-c1001"></a>Error irrecuperable C1001

> ERROR interno del compilador ( *archivo*de archivo del compilador, *número*de línea)

El compilador no puede generar código correcto para una construcción, a menudo debido a la combinación de una expresión determinada y una opción de optimización, o a un problema en el análisis. Si el archivo del compilador enumerado tiene un segmento de ruta de acceso UTC o C2, es probable que se trate de un error de optimización. Si el archivo tiene un segmento de ruta de acceso cxxfe o C1XX, o es MSC1. cpp, es probable que se trate de un error del analizador. Si el archivo denominado es cl. exe, no hay otra información disponible.

A menudo se puede corregir un problema de optimización quitando una o más opciones de optimización. Para determinar qué opción está en el error, quite las opciones de una en una y vuelva a compilar hasta que el mensaje de error salga. Las opciones más comúnmente responsables son [/og (optimizaciones globales)](../../build/reference/og-global-optimizations.md) y [/OI (generar funciones intrínsecas)](../../build/reference/oi-generate-intrinsic-functions.md). Una vez que determine qué opción de optimización es responsable, puede deshabilitarla en torno a la función en la que se produce el error mediante la pragma [Optimize](../../preprocessor/optimize.md) y seguir usando la opción para el resto del módulo. Para obtener más información sobre las opciones de optimización, consulte [prácticas recomendadas de optimización](../../build/optimization-best-practices.md).

Si las optimizaciones no son responsables del error, intente volver a escribir la línea en la que se ha generado el error o varias líneas de código que rodean esa línea. Para ver el código de la forma en que el compilador lo ve después del preprocesamiento, puede usar la opción [/p (Preprocesar para un archivo)](../../build/reference/p-preprocess-to-a-file.md) .

Para obtener más información sobre cómo aislar el origen del error y cómo notificar un error interno del compilador a Microsoft, vea [Cómo notificar un problema con C++ el conjunto de herramientas visual](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

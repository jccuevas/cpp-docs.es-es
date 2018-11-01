---
title: Error irrecuperable C1001
ms.date: 11/04/2016
f1_keywords:
- C1001
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
ms.openlocfilehash: ee0796260ac17613568912f0de235e9a1fd0702e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513898"
---
# <a name="fatal-error-c1001"></a>Error irrecuperable C1001

> INTERNO ERROR(compiler file *file*, line *number*) del compilador

El compilador no puede generar código correcto para una construcción, a menudo debido a la combinación de una expresión determinada y una opción de optimización o un problema en el análisis. Si el archivo del compilador aparece tiene una hora utc o segmento de ruta de acceso de C2, probablemente es un error de optimización. Si el archivo tiene un segmento de ruta de acceso cxxfe o c1xx o es msc1.cpp, probablemente es un error del analizador. Si el archivo llamado cl.exe, no hay ninguna otra información.

A menudo puede corregir un problema de optimización mediante la eliminación de una o varias opciones de optimización. Para determinar qué opción es erróneo, quitar opciones de una en un momento y vuelva a compilar hasta que el mensaje de error desaparece. Las opciones que normalmente son [/Og (optimizaciones globales)](../../build/reference/og-global-optimizations.md) y [/Oi (generar funciones intrínsecas)](../../build/reference/oi-generate-intrinsic-functions.md). Una vez que determine que es responsable de qué opción de optimización, puede deshabilitarlo en torno a la función donde se produce el error mediante el uso de la [optimizar](../../preprocessor/optimize.md) pragma y seguir usando la opción para el resto del módulo. Para obtener más información acerca de las opciones de optimización, vea [recomendaciones de optimización](../../build/reference/optimization-best-practices.md).

Si las optimizaciones no son responsables del error, intente volver a escribir la línea donde se notifica el error, o varias líneas de código que rodea esa línea. Para ver el código tal y como ve en el compilador tras el preprocesamiento, puede usar el [/P (Preprocesar para un archivo)](../../build/reference/p-preprocess-to-a-file.md) opción.

Para obtener más información sobre cómo aislar la causa del error y cómo notificar un error interno del compilador a Microsoft, consulte [cómo notificar un problema con el conjunto de herramientas de Visual C++](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md).
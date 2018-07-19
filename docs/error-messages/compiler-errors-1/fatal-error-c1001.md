---
title: Error irrecuperable C1001 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1001
dev_langs:
- C++
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f605dd7e4892c4a8b57e544ed857257be72f020d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199033"
---
# <a name="fatal-error-c1001"></a>Error irrecuperable C1001

> INTERNO ERROR(compiler file *file*, line *number*) compilador  
  
El compilador no puede generar código correcto para una construcción, a menudo debido a la combinación de una expresión y una opción de optimización o un problema en el análisis. Si el archivo del compilador aparecen tiene una hora utc o segmento de ruta de acceso de C2, probablemente es un error de optimización. Si el archivo tiene un segmento de ruta de acceso cxxfe o c1xx o es msc1.cpp, probablemente es un error del analizador. Si el archivo denominado es cl.exe, no hay ninguna otra información.  

A menudo puede corregir un problema de optimización mediante la eliminación de una o varias opciones de optimización. Para determinar qué opción es erróneo, quitar opciones de una en una hora y vuelva a compilar hasta que el mensaje de error desaparece. Las opciones que normalmente son [/Og (optimizaciones globales)](../../build/reference/og-global-optimizations.md) y [/Oi (generar funciones intrínsecas)](../../build/reference/oi-generate-intrinsic-functions.md). Una vez que determine qué opción de optimización es responsable, puede deshabilitar torno a la función donde se produce el error mediante el uso de la [optimizar](../../preprocessor/optimize.md) pragma y seguir usando la opción para el resto del módulo. Para obtener más información acerca de las opciones de optimización, vea [recomendaciones de optimización](../../build/reference/optimization-best-practices.md).

Si las optimizaciones no son responsables del error, intente volver a escribir la línea donde se notifica el error o varias líneas de código que rodea esa línea. Para ver el código tal y como ve en el compilador tras el preprocesamiento, puede usar el [/P (Preprocesar para un archivo)](../../build/reference/p-preprocess-to-a-file.md) opción.

Para obtener más información acerca de cómo aislar el origen del error y cómo informar de un error interno del compilador a Microsoft, consulte [cómo notificar un problema con el conjunto de herramientas de Visual C++](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md).
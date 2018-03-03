---
title: "Optimizar el código | Documentos de Microsoft"
ms.custom: 
ms.date: 12/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4306f825b9925dbdcdc994d287a2c4287ea7bfc2
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="optimizing-your-code"></a>Optimizar el código

Al optimizar un archivo ejecutable, puede lograr un equilibrio entre la velocidad de ejecución rápida y tamaño de código pequeño. Este tema describen algunos de los mecanismos proporcionados por Visual C++ para ayudarle a optimizar el código.

## <a name="language-features"></a>Características del lenguaje

Los temas siguientes describen algunas de las características de optimización en el lenguaje C o C++.

[Directivas pragma y palabras clave de optimización](../../build/reference/optimization-pragmas-and-keywords.md)  
Una lista de palabras clave y directivas pragma que puede usar en el código para mejorar el rendimiento.

[Opciones del compilador por categoría](../../build/reference/compiler-options-listed-by-category.md)  
Una lista de **/O** opciones del compilador que específicamente afectan al tamaño de velocidad o el código de ejecución.

[Declarador de referencia a un valor R: &&](../../cpp/rvalue-reference-declarator-amp-amp.md)  
Referencias a valor r admiten la implementación de *semántica de transferencia de*. Si puede mejorar significativamente el movimiento semántica se usa para implementar las bibliotecas de plantillas, el rendimiento de las aplicaciones que usan las plantillas.

### <a name="the-optimize-pragma"></a>La directiva pragma optimize

Si una sección optimizada del código origina errores o ralentiza la ejecución, puede utilizar el [optimizar](../../preprocessor/optimize.md) pragma para desactivar la optimización en esa sección.

Inserte el código entre dos directivas pragma, como se muestra aquí:

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>Prácticas recomendadas de programación

Verá mensajes de advertencia adicionales al compilar el código con la optimización. Este comportamiento es el esperado porque algunas advertencias solo están relacionadas con el código optimizado. Puede evitar muchos problemas de optimización si tiene en cuenta estas advertencias.

Paradójicamente, la optimización de un programa para acelerar el proceso podría provocar código se ejecuten más lentamente. Esto es porque algunas optimizaciones para acelerar el proceso de aumentar el tamaño del código. Por ejemplo, las funciones de inclusión elimina la sobrecarga de llamadas a función. Sin embargo, la inclusión demasiado código podría hacer que su programa tan grande que aumente el número de página de memoria virtual errores. Por lo tanto, la velocidad obtenida al eliminar las llamadas a funciones puede perderse del intercambio de memoria.

Los temas siguientes tratan sobre prácticas recomendadas de programación.

[Sugerencias para mejorar código en el que la velocidad de ejecución es importante](../../build/reference/tips-for-improving-time-critical-code.md)  
Técnicas de codificación mejor pueden mejorar el rendimiento. Este tema sugieren técnicas de codificación que le ayudarán a asegurarse de que las partes del código crítico en el tiempo se ejecutan correctamente.

[Procedimientos recomendados para la optimización](../../build/reference/optimization-best-practices.md)  
Proporciona directrices generales sobre la mejor manera de optimizar la aplicación.

## <a name="debugging-optimized-code"></a>Depurar código optimizado

Dado que la optimización puede cambiar el código creado por el compilador, se recomienda depurar la aplicación y medir su rendimiento y, a continuación, optimizar el código.

Los temas siguientes proporcionan información básica sobre cómo depurar.

- [Depurar en Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)

- [Problemas comunes al crear versiones de lanzamiento](../../build/reference/common-problems-when-creating-a-release-build.md)

Los temas siguientes proporcionan información más avanzada sobre cómo se depuran.

- [Cómo: Depurar código optimizado](/visualstudio/debugger/how-to-debug-optimized-code)

- [Por qué los números de punto flotante pierden precisión](../../build/reference/why-floating-point-numbers-may-lose-precision.md)

Los temas siguientes proporcionan información acerca de cómo optimizar generar, cargar y ejecutar el código.

- [Mejorar el rendimiento del compilador](../../build/reference/improving-compiler-throughput.md)

- [Uso de un nombre de función sin () no genera código](../../build/reference/using-function-name-without-parens-produces-no-code.md)

- [Optimización de un ensamblado insertado](../../assembler/inline/optimizing-inline-assembly.md)

- [Especificación de optimización del compilador para un proyecto ATL](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [¿Qué técnicas de optimización debo usar para mejorar el rendimiento de la aplicación cliente al cargarlas?](../../build/dll-frequently-asked-questions.md#mfc_optimization)

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](../../build/reference/c-cpp-building-reference.md)  

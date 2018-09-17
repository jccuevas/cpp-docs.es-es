---
title: Optimización del código | Microsoft Docs
ms.custom: ''
ms.date: 12/28/2017
ms.technology:
- cpp-tools
ms.topic: reference
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
ms.workload:
- cplusplus
ms.openlocfilehash: 180586f55ea57100286c3c598ac62eb83107d7c9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714381"
---
# <a name="optimizing-your-code"></a>Optimización del código

Al optimizar un archivo ejecutable, puede lograr un equilibrio entre velocidad de ejecución rápida y el tamaño de código pequeño. En este tema se describe algunos de los mecanismos que ofrece Visual C++ para ayudarle a optimizar el código.

## <a name="language-features"></a>Características del lenguaje

Los temas siguientes describen algunas de las características de optimización en el lenguaje de C o C++.

[Directivas pragma de optimización y las palabras clave](../../build/reference/optimization-pragmas-and-keywords.md) una lista de palabras clave y pragmas que puede usar en el código para mejorar el rendimiento.

[Compilador Options Listed by Category](../../build/reference/compiler-options-listed-by-category.md) una lista de **/O** opciones del compilador que afectan específicamente al tamaño de código o la velocidad de ejecución.

[Declarador de referencia rvalue: & &](../../cpp/rvalue-reference-declarator-amp-amp.md) referencias a valor r admiten la implementación de *semántica de transferencia*. Si puede mejorar significativamente el movimiento semántica se usa para implementar las bibliotecas de plantillas, el rendimiento de las aplicaciones que usan esas plantillas.

### <a name="the-optimize-pragma"></a>La pragma optimize

Si una sección de código optimizada provoca una ralentización o errores, puede usar el [optimizar](../../preprocessor/optimize.md) pragma para desactivar la optimización en esa sección.

Incluya el código entre dos directivas pragma, como se muestra aquí:

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>Prácticas recomendadas de programación

Es posible que observe mensajes de advertencia adicionales al compilar el código con la optimización. Se espera este comportamiento porque algunas advertencias solo se relacionan con el código optimizado. Puede evitar muchos problemas de optimización si tiene en cuenta estas advertencias.

Paradójicamente, la optimización de un programa para acelerar el proceso podría provocar código se ejecute más lentamente. Esto es porque algunas optimizaciones de velocidad de aumentar el tamaño del código. Por ejemplo, las funciones de inserción elimina la sobrecarga de llamadas de función. Sin embargo, inserción demasiado código podría hacer que su programa tan grande que aumente el número de página de memoria virtual errores. Por lo tanto, la velocidad obtenida al eliminar las llamadas de función puede perderse para intercambio de memoria.

Los temas siguientes describen las prácticas recomendadas de programación.

[Sugerencias para mejorar el código crítico en el tiempo](../../build/reference/tips-for-improving-time-critical-code.md) mejores técnicas de codificación puede producir un mejor rendimiento. Este tema sugieren técnicas de codificación que pueden ayudar a asegurarse de que las partes del código crítico en el tiempo se realizan satisfactoriamente o no.

[Recomendaciones de optimización](../../build/reference/optimization-best-practices.md) proporciona directrices generales sobre la mejor manera de optimizar la aplicación.

## <a name="debugging-optimized-code"></a>Depurar código optimizado

Como optimización puede cambiar el código creado por el compilador, se recomienda depurar la aplicación y medir su rendimiento y, a continuación, optimice el código.

Los temas siguientes proporcionan información básica sobre cómo depurar.

- [Depurar en Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)

- [Problemas comunes al crear versiones de lanzamiento](../../build/reference/common-problems-when-creating-a-release-build.md)

Los temas siguientes proporcionan información más avanzada sobre cómo depurar.

- [Cómo: Depurar código optimizado](/visualstudio/debugger/how-to-debug-optimized-code)

- [Por qué los números de punto flotante pierden precisión](../../build/reference/why-floating-point-numbers-may-lose-precision.md)

Los temas siguientes proporcionan información acerca de cómo optimizar la creación, cargar y ejecutar su código.

- [Mejorar el rendimiento del compilador](../../build/reference/improving-compiler-throughput.md)

- [Uso de un nombre de función sin () no genera código](../../build/reference/using-function-name-without-parens-produces-no-code.md)

- [Optimización de un ensamblado insertado](../../assembler/inline/optimizing-inline-assembly.md)

- [Especificación de optimización del compilador para un proyecto ATL](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [¿Qué técnicas de optimización debo usar para mejorar el rendimiento de la aplicación cliente al cargar?](../../build/dll-frequently-asked-questions.md#mfc_optimization)

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](../../build/reference/c-cpp-building-reference.md)

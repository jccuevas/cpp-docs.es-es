---
title: Optimizar el código
ms.date: 05/06/2019
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
ms.openlocfilehash: f44fb734c8441e10b656c5326c8df4bf6879499a
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220180"
---
# <a name="optimizing-your-code"></a>Optimización del código

Al optimizar un archivo ejecutable, puede lograr un equilibrio entre velocidad de ejecución rápida y el tamaño de código pequeño. En este tema se describe algunos de los mecanismos que proporciona Visual Studio para ayudarle a optimizar el código.

## <a name="language-features"></a>Características del lenguaje

Los temas siguientes describen algunas de las características de optimización en el lenguaje de C o C++.

[Las palabras clave y directivas pragma de optimización](optimization-pragmas-and-keywords.md) \
Una lista de palabras clave y pragmas que puede usar en el código para mejorar el rendimiento.

[Opciones del compilador por categoría](reference/compiler-options-listed-by-category.md) \
Una lista de **/O** opciones del compilador que afectan específicamente al tamaño de código o la velocidad de ejecución.

[Declarador de referencia rvalue: & &](../cpp/rvalue-reference-declarator-amp-amp.md) \
Referencias a valor r admiten la implementación de *semántica de transferencia*. Si puede mejorar significativamente el movimiento semántica se usa para implementar las bibliotecas de plantillas, el rendimiento de las aplicaciones que usan esas plantillas.

### <a name="the-optimize-pragma"></a>La pragma optimize

Si una sección de código optimizada provoca una ralentización o errores, puede usar el [optimizar](../preprocessor/optimize.md) pragma para desactivar la optimización en esa sección.

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

[Sugerencias para mejorar código crítico en el tiempo](tips-for-improving-time-critical-code.md) \
Mejor codificación técnicas puede ofrecer un mejor rendimiento. Este tema sugieren técnicas de codificación que pueden ayudar a asegurarse de que las partes del código crítico en el tiempo se realizan satisfactoriamente o no.

[Recomendaciones de optimización](optimization-best-practices.md) \
Proporciona directrices generales sobre la mejor manera de optimizar la aplicación.

## <a name="debugging-optimized-code"></a>Depurar código optimizado

Como optimización puede cambiar el código creado por el compilador, se recomienda depurar la aplicación y medir su rendimiento y, a continuación, optimice el código.

Los temas siguientes proporcionan información sobre cómo depurar la versión se basa.

- [Depurar en Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)

- [Cómo: Depurar código optimizado](/visualstudio/debugger/how-to-debug-optimized-code)

- [Por qué los números de punto flotante pierden precisión](why-floating-point-numbers-may-lose-precision.md)


Los temas siguientes proporcionan información acerca de cómo optimizar la creación, cargar y ejecutar su código.

- [Mejorar el rendimiento del compilador](improving-compiler-throughput.md)

- [Uso de un nombre de función sin () no genera código](using-function-name-without-parens-produces-no-code.md)

- [Optimización de un ensamblado insertado](../assembler/inline/optimizing-inline-assembly.md)

- [Especificación de optimización del compilador para un proyecto ATL](../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [¿Qué técnicas de optimización debo usar para mejorar el rendimiento de la aplicación cliente al cargar?](../build/dll-frequently-asked-questions.md#mfc_optimization)


## <a name="in-this-section"></a>En esta sección

[Las palabras clave y directivas pragma de optimización](optimization-pragmas-and-keywords.md) \
[Mejorar el rendimiento del compilador](improving-compiler-throughput.md) \
[Por qué los números de punto flotante pierden precisión](why-floating-point-numbers-may-lose-precision.md) \
[Representación de punto flotante de IEEE](ieee-floating-point-representation.md) \
[Sugerencias para mejorar código crítico en el tiempo](tips-for-improving-time-critical-code.md) \
[Nombre de función sin () No genera código](using-function-name-without-parens-produces-no-code.md) \
[Recomendaciones de optimización](optimization-best-practices.md) \
[Optimizaciones guiadas por perfil](profile-guided-optimizations.md) \
[Variables de entorno para las optimizaciones guiadas por perfil](environment-variables-for-profile-guided-optimizations.md) \
[PgoAutoSweep](pgoautosweep.md) \
[pgomgr](pgomgr.md) \
[pgosweep](pgosweep.md) \
[Cómo: Combinación de varios perfiles PGO en un solo perfil](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)

## <a name="see-also"></a>Vea también

[Referencia de compilación de C/C++](reference/c-cpp-building-reference.md)

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
ms.openlocfilehash: 00356cf50ca8e50c80e8a1142adf654816490c9b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078493"
---
# <a name="optimizing-your-code"></a>Optimizar el código

Mediante la optimización de un archivo ejecutable, puede lograr un equilibrio entre la velocidad de ejecución rápida y el pequeño tamaño del código. En este tema se describen algunos de los mecanismos que Visual Studio proporciona para ayudarle a optimizar el código.

## <a name="language-features"></a>Características del lenguaje

En los temas siguientes se describen algunas de las características de optimización delC++ lenguaje C/.

[Pragmas y palabras clave de optimización](optimization-pragmas-and-keywords.md) \
Una lista de palabras clave y pragmas que puede usar en el código para mejorar el rendimiento.

[Opciones del compilador enumeradas por categoría](reference/compiler-options-listed-by-category.md) \
Lista de opciones del compilador **/o** que afectan específicamente a la velocidad de ejecución o al tamaño del código.

[Declarador de referencia de valor r: & &](../cpp/rvalue-reference-declarator-amp-amp.md) \
Las referencias rvalue admiten la implementación de la *semántica de transferencia de movimiento*. Si se usa la semántica de movimiento para implementar bibliotecas de plantillas, el rendimiento de las aplicaciones que usan esas plantillas puede mejorar significativamente.

### <a name="the-optimize-pragma"></a>Pragma Optimize

Si una sección optimizada de código provoca errores o una ralentización, puede usar la pragma [Optimize](../preprocessor/optimize.md) para desactivar la optimización de esa sección.

Incluya el código entre dos pragmas, como se muestra aquí:

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>Prácticas de programación

Es posible que vea mensajes de advertencia adicionales al compilar el código con optimización. Este comportamiento es el esperado porque algunas advertencias solo se relacionan con el código optimizado. Puede evitar muchos problemas de optimización si tiene en cuentan estas advertencias.

Paradójicamente, la optimización de un programa para la velocidad puede hacer que el código se ejecute más lentamente. Esto se debe a que algunas optimizaciones de velocidad aumentan el tamaño del código. Por ejemplo, las funciones de inclusión eliminan la sobrecarga de las llamadas a funciones. Sin embargo, si se alinea demasiado código, puede que el programa sea tan grande que aumente el número de errores de página de memoria virtual. Por lo tanto, la velocidad obtenida al eliminar las llamadas de función puede perderse en el intercambio de memoria.

En los temas siguientes se tratan los procedimientos recomendados de programación.

[Sugerencias para mejorar el código crítico en el tiempo](tips-for-improving-time-critical-code.md) \
Mejorar las técnicas de codificación puede mejorar el rendimiento. En este tema se sugieren técnicas de programación que pueden ayudarle a asegurarse de que las partes del código que se ejecutan en un momento crítico se ejecuten correctamente.

[Prácticas recomendadas de optimización](optimization-best-practices.md) \
Proporciona instrucciones generales sobre la optimización de la aplicación.

## <a name="debugging-optimized-code"></a>Depuración de código optimizado

Dado que la optimización podría cambiar el código creado por el compilador, se recomienda depurar la aplicación y medir su rendimiento y, a continuación, optimizar el código.

En los temas siguientes se proporciona información sobre cómo depurar las compilaciones de versión.

- [Depurar en Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)

- [Cómo: Depurar código optimizado](/visualstudio/debugger/how-to-debug-optimized-code)

- [Por qué los números de punto flotante pierden precisión](why-floating-point-numbers-may-lose-precision.md)

En los temas siguientes se proporciona información sobre cómo optimizar la compilación, la carga y la ejecución del código.

- [Mejorar el rendimiento del compilador](improving-compiler-throughput.md)

- [Uso de un nombre de función sin () no genera código](using-function-name-without-parens-produces-no-code.md)

- [Optimización de un ensamblado insertado](../assembler/inline/optimizing-inline-assembly.md)

- [Especificación de optimización del compilador para un proyecto ATL](../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [¿Qué técnicas de optimización debo usar para mejorar el rendimiento de la aplicación cliente al cargar?](../build/dll-frequently-asked-questions.md#mfc_optimization)

## <a name="in-this-section"></a>En esta sección

[Pragmas y palabras clave de optimización](optimization-pragmas-and-keywords.md) \
[Mejorar el rendimiento del Compilador](improving-compiler-throughput.md) \
[Por qué los números de punto flotante pueden perder precisión](why-floating-point-numbers-may-lose-precision.md) \
[Representación de punto flotante de IEEE](ieee-floating-point-representation.md) \
[Sugerencias para mejorar el código crítico en el tiempo](tips-for-improving-time-critical-code.md) \
[El uso de un nombre de función sin () no genera código](using-function-name-without-parens-produces-no-code.md) \
[Prácticas recomendadas de optimización](optimization-best-practices.md) \
[Optimizaciones guiadas por perfiles](profile-guided-optimizations.md) \
[Variables de entorno para las optimizaciones guiadas por perfiles](environment-variables-for-profile-guided-optimizations.md) \
 \ [PgoAutoSweep](pgoautosweep.md)
[pgomgr](pgomgr.md) \
[pgosweep](pgosweep.md) \
[Cómo: Combinar varios perfiles PGO en un solo perfil](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)

## <a name="see-also"></a>Consulte también

[Referencia de compilación de C/C++](reference/c-cpp-building-reference.md)

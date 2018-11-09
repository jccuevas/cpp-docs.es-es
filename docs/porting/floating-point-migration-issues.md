---
title: Problemas de migración de punto flotante
ms.date: 05/17/2017
ms.assetid: 36a1b552-2f2b-4919-bc9d-c17f42434954
ms.openlocfilehash: ea34f1eb8e8bd528273da5d7d18cd545cd22de37
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530876"
---
# <a name="floating-point-migration-issues"></a>Problemas de migración de punto flotante

A veces, al actualizar los proyectos a una versión más reciente de Visual Studio, observará que los resultados de determinadas operaciones de punto flotante han cambiado. Esto suele deberse a una de dos razones: los cambios en la generación de código que aprovechan mejor el procesador disponible, o bien las correcciones de errores o los cambios en los algoritmos usados en las funciones matemáticas de la biblioteca de tiempo de ejecución de C (CRT). En general, los nuevos resultados son correctos dentro de los límites especificados por el estándar del lenguaje. Siga leyendo para averiguar lo que ha cambiado y, si es importante, cómo conseguir los mismos resultados que obtenía antes con sus funciones.

## <a name="new-math-functions-and-universal-crt-changes"></a>Nueva funciones matemáticas y cambios de CRT universal

La mayoría de las funciones matemáticas de CRT han estado disponibles en Visual Studio durante años, pero a partir de Visual Studio 2013 se incluyen todas las funciones necesarias en ISO C99. Estas funciones se implementan para equilibrar el rendimiento con exactitud. Dado que es posible que producir el resultado redondeado correctamente en todos los casos sea excesivamente costoso, estas funciones están diseñadas para generar con eficacia una buena aproximación al resultado redondeado correctamente. En la mayoría de los casos, el resultado producido se encuentra dentro de una unidad de menor precisión +/-1, o *ulp*, del resultado redondeado correctamente, aunque puede haber casos en los que la falta de precisión sea mayor. Si antes usaba una biblioteca matemática diferente para obtener estas funciones, los cambios en los resultados pueden deberse a diferencias en la implementación.

Cuando las funciones matemáticas se movieron a CRT universal en Visual Studio 2015, se usaron algunos algoritmos nuevos y se corrigieron varios errores en la implementación de las funciones nuevas que se introdujeron en Visual Studio 2013. Estos cambios pueden producir diferencias detectables en los resultados de los cálculos de punto flotante que usan estas funciones. Las funciones con errores eran erf, exp2, remainder, remquo, scalbln y scalbn, y sus variantes float y long double.  Otros cambios introducidos en Visual Studio 2015 han corregido los problemas relacionados con la conservación de la información del estado de la excepción y la palabra de estado del punto flotante en las funciones _clear87, _clearfp, fegetenv, fesetenv y feholdexcept.

## <a name="processor-differences-and-compiler-flags"></a>Diferencias de procesador y marcas de compilador

Muchas de las funciones de la biblioteca matemática de punto flotante tienen implementaciones diferentes para distintas arquitecturas de CPU. Por ejemplo, puede que el CRT x86 de 32 bits tenga una implementación distinta que el CRT x64 de 64 bits. Además, algunas de las funciones pueden tener varias implementaciones para una determinada arquitectura de CPU. La implementación más eficaz se selecciona dinámicamente en tiempo de ejecución en función de los conjuntos de instrucciones compatibles con la CPU. Por ejemplo, en el CRT x86 de 32 bits, algunas funciones tienen una implementación x87 y una implementación SSE2. Cuando se ejecuta en una CPU que admite SSE2, se usa la implementación SSE2 más rápida. Cuando se ejecuta en una CPU que no admite SSE2, se usa la implementación x87 más lenta. Puede ver esto al migrar código antiguo, ya que la opción predeterminada de arquitectura del compilador x86 ha cambiado a [/arch:SSE2](../build/reference/arch-x86.md) en Visual Studio 2012. Dado que es posible que diferentes implementaciones de las funciones de la biblioteca matemática usen distintas instrucciones de CPU y distintos algoritmos para generar sus resultados, puede que las funciones generen diferentes resultados en diferentes plataformas. En la mayoría de los casos, los resultados se encuentran dentro de +/-1 ulp del resultado redondeado correctamente, pero los resultados reales pueden variar de una CPU a otra.

Las mejoras en la corrección de la generación de código en diferentes modos de punto flotante en Visual Studio también pueden afectar a los resultados de las operaciones de punto flotante cuando el código antiguo se compara con el código nuevo, incluso si se usan las mismas marcas de compilador. Por ejemplo, es posible que el código generado por Visual Studio 2010 cuando se ha especificado [/fp:precise](../build/reference/fp-specify-floating-point-behavior.md) (valor predeterminado) o `/fp:strict` no haya propagado correctamente los valores no numéricos (NaN) intermedios en las expresiones. Por lo tanto, podría darse que algunas expresiones que generaban un resultado numérico en compiladores antiguos ahora generen correctamente un resultado NaN. También podría ver algunas diferencias debido a que las optimizaciones de código habilitadas para `/fp:fast` ahora aprovechan más características del procesador. Estas optimizaciones pueden usar menos instrucciones, pero podrían afectar a los resultados generados porque se han quitado algunas operaciones intermedias que antes eran visibles.

## <a name="how-to-get-identical-results"></a>Cómo obtener resultados idénticos

En la mayoría de los casos, los cambios de punto flotante en los compiladores y las bibliotecas más recientes producen un comportamiento más rápido o más correcto, o ambos. Incluso podría constatar un mejor rendimiento energético del procesador cuando las instrucciones SSE2 reemplazan a las instrucciones x87. A pesar de todo, si tiene código que debe replicar con precisión el comportamiento de punto flotante de un compilador antiguo, considere la posibilidad de usar funciones de compatibilidad nativa con múltiples versiones de Visual Studio y compile el proyecto afectado con el conjunto de herramientas antiguo. Para obtener más información, vea [Use native multi-targeting in Visual Studio to build old projects](use-native-multi-targeting.md) (Usar compatibilidad nativa con múltiples versiones en Visual Studio para compilar proyectos antiguos).

## <a name="see-also"></a>Vea también

[Actualizar proyectos desde versiones anteriores de Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Información general sobre posibles problemas de actualización (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Historial de cambios en Visual C++ 2003-2015](visual-cpp-change-history-2003-2015.md)
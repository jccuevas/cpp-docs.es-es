---
title: Paralelización y vectorización automáticas
ms.date: 11/04/2016
ms.assetid: ec71583a-287b-4599-8767-1d255e080fe3
ms.openlocfilehash: adc0dd9346cc2850b02e01804e26044c367f2d14
ms.sourcegitcommit: fcc3aeb271449f8be80348740cffef39ba543407
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "82538615"
---
# <a name="auto-parallelization-and-auto-vectorization"></a>Paralelización y vectorización automáticas

El paralelizador automático y el vectorizador automático se han diseñado para proporcionar mejoras automáticas de rendimiento de los bucles en el código.

## <a name="auto-parallelizer"></a>Paralelizador automático

El modificador de compilador [/QPAR](../build/reference/qpar-auto-parallelizer.md) habilita la *paralelización automática* de bucles en el código. Cuando se especifica este marcador sin cambiar el código existente, el compilador evalúa el código para buscar los bucles que podrían beneficiarse de la paralelización. Dado que podría encontrar bucles que no hacen mucho trabajo y, por tanto, no se beneficiarán de la paralelización, y debido a que cada paralelización innecesaria puede acaparar un grupo de subprocesos o producir sincronización adicional u otro procesamiento que tendería a disminuir el rendimiento en lugar de mejorarlo, el compilador es conservador en la selección de los bucles que ejecuta en paralelo. Por ejemplo, considere el siguiente ejemplo en el que el límite superior del bucle no se conoce en tiempo de compilación:

```cpp
void loop_test(int u) {
   for (int i=0; i<u; ++i)
      A[i] = B[i] * C[i];
}
```

Dado que `u` puede ser un valor pequeño, el compilador no paralelizará automáticamente este bucle. Sin embargo, es posible que el usuario todavía desee paralelizarlo porque sabe que `u` siempre será grande. Para habilitar la paralelización automática, especifique [#pragma bucle (hint_parallel (n))](../preprocessor/loop.md), donde `n` es el número de subprocesos que se van a paralelizar. En el ejemplo siguiente, el compilador intentará paralelizar el bucle entre 8 subprocesos.

```cpp
void loop_test(int u) {
#pragma loop(hint_parallel(8))
   for (int i=0; i<u; ++i)
      A[i] = B[i] * C[i];
}
```

Como con todas las [directivas pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md), también se admite `__pragma(loop(hint_parallel(n)))` la sintaxis de pragma alternativa.

Hay algunos bucles que el compilador no puede paralelizar aunque lo desee. Este es un ejemplo:

```cpp
#pragma loop(hint_parallel(8))
for (int i=0; i<upper_bound(); ++i)
    A[i] = B[i] * C[i];
```

La función `upper_bound()` puede cambiar cada vez que se la llama. Dado que el límite superior no puede conocerse, el compilador puede emitir un mensaje de diagnóstico que explica por qué no se puede paralelizar este bucle. En el ejemplo siguiente se muestra un bucle que se puede paralelizar, un bucle que no se puede paralelizar, la sintaxis del compilador que se usa en el símbolo del sistema y la salida del compilador para cada opción de línea de comandos:

```cpp
int A[1000];
void test() {
#pragma loop(hint_parallel(0))
    for (int i=0; i<1000; ++i) {
        A[i] = A[i] + 1;
    }

    for (int i=1000; i<2000; ++i) {
        A[i] = A[i] + 1;
    }
}
```

La compilación con este comando:

`cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-report:1`

produce este resultado:

```Output
--- Analyzing function: void __cdecl test(void)
d:\myproject\mytest.cpp(4) : loop parallelized
```

La compilación con este comando:

`cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-report:2`

produce este resultado:

```Output
--- Analyzing function: void __cdecl test(void)
d:\myproject\mytest.cpp(4) : loop parallelized
d:\myproject\mytest.cpp(4) : loop not parallelized due to reason '1008'
```

Observe la diferencia en la salida entre las dos opciones diferentes de [/QPAR-Report (nivel de informe de paralelizador automático automática)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md) . `/Qpar-report:1` genera mensajes del paralelizador solo para los bucles que se paralelizan correctamente. `/Qpar-report:2` genera mensajes del paralelizador para las paralelizaciones de bucles correctas e incorrectas.

Para obtener más información sobre los códigos de motivo y los mensajes, consulte [vectorizador automático and paralelizador automático messages](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

## <a name="auto-vectorizer"></a>Vectorizador automático

El vectorizador automático analiza los bucles del código y usa los registros y las instrucciones de vector en el equipo de destino para ejecutarlos si puede. Esto puede mejorar el rendimiento del código. El compilador tiene como destino las instrucciones SSE2, AVX y AVX2 de los procesadores Intel o AMD, o las instrucciones de neón en los procesadores ARM, según el conmutador [/Arch](../build/reference/arch-minimum-cpu-architecture.md) .

El vectorizador automático puede generar instrucciones diferentes de las que especifica el modificador `/arch`. Estas instrucciones estarán protegidas por una comprobación en tiempo de ejecución para asegurarse de que código se ejecuta correctamente. Por ejemplo, cuando se compila `/arch:SSE2`, se pueden emitir instrucciones SSE4.2. Una comprobación en tiempo de ejecución comprueba que SSE4.2 está disponible en el procesador de destino y salta a una versión no SSE4.2 del bucle si el procesador no admite las instrucciones.

De forma predeterminada, se habilita el vectorizador automático. Si desea comparar el rendimiento del código con la vectorización, puede usar [#pragma bucle (no_vector)](../preprocessor/loop.md) para deshabilitar la vectorización de cualquier bucle determinado.

```cpp
#pragma loop(no_vector)
for (int i = 0; i < 1000; ++i)
   A[i] = B[i] + C[i];
```

Como con todas las [directivas pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md), también se admite `__pragma(loop(no_vector))` la sintaxis de pragma alternativa.

Al igual que con la paralelizador automático automática, puede especificar la opción de línea de comandos [/qvec-Report (el nivel de informe de vectorizador automático automática)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md) para notificar solo`/Qvec-report:1`bucles con vectores correctos (o bucles`/Qvec-report:2`con vectores correctos y sin éxito).

Para obtener más información sobre los códigos de motivo y los mensajes, consulte [vectorizador automático and paralelizador automático messages](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

Para ver un ejemplo en el que se muestra cómo funciona vectorizador automático en la práctica, vea [Project Austin, parte 2 de 6: Página de rizo](https://devblogs.microsoft.com/cppblog/project-austin-part-2-of-6-page-curling/)

## <a name="see-also"></a>Consulte también

[realizar](../preprocessor/loop.md)<br/>
[Programación en paralelo en código nativo](/archive/blogs/nativeconcurrency)<br/>
[/Qpar (Paralelizador automático)](../build/reference/qpar-auto-parallelizer.md)<br/>
[/Qpar/report (Nivel de información de paralelizador automático)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)<br/>
[/Qvec-report (Nivel de información de vectorizador automático)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)<br/>
[Mensajes del vectorizador y paralelizador](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)

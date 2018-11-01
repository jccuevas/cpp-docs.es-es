---
title: Paralelización y vectorización automáticas
ms.date: 11/04/2016
ms.assetid: ec71583a-287b-4599-8767-1d255e080fe3
ms.openlocfilehash: 06ab255e7769bfa56d5a8d22cdbe19d415ce6b31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618353"
---
# <a name="auto-parallelization-and-auto-vectorization"></a>Paralelización y vectorización automáticas

El paralelizador automático y el vectorizador automático se han diseñado para proporcionar mejoras automáticas de rendimiento de los bucles en el código.

## <a name="auto-parallelizer"></a>Paralelizador automático

El [/Qpar](../build/reference/qpar-auto-parallelizer.md) permite el modificador del compilador *paralelización automática* de bucles del código. Cuando se especifica este marcador sin cambiar el código existente, el compilador evalúa el código para buscar los bucles que podrían beneficiarse de la paralelización. Dado que podría encontrar bucles que no hacen mucho trabajo y, por tanto, no se beneficiarán de la paralelización, y debido a que cada paralelización innecesaria puede acaparar un grupo de subprocesos o producir sincronización adicional u otro procesamiento que tendería a disminuir el rendimiento en lugar de mejorarlo, el compilador es conservador en la selección de los bucles que ejecuta en paralelo. Por ejemplo, considere el siguiente ejemplo en el que el límite superior del bucle no se conoce en tiempo de compilación:

```cpp
void loop_test(int u) {
   for (int i=0; i<u; ++i)
      A[i] = B[i] * C[i];
}
```

Dado que `u` puede ser un valor pequeño, el compilador no paralelizará automáticamente este bucle. Sin embargo, es posible que el usuario todavía desee paralelizarlo porque sabe que `u` siempre será grande. Para habilitar la paralelización automática, especifique [#pragma loop(hint_parallel(n))](../preprocessor/loop.md), donde `n` es el número de subprocesos a paralelizar. En el ejemplo siguiente, el compilador intentará paralelizar el bucle entre 8 subprocesos.

```cpp
void loop_test(int u) {
#pragma loop(hint_parallel(8))
   for (int i=0; i<u; ++i)
      A[i] = B[i] * C[i];
}
```

Como ocurre con todos los [directivas pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md), la sintaxis de la directiva pragma alternativa `__pragma(loop(hint_parallel(n)))` también es compatible.

Hay algunos bucles que el compilador no puede paralelizar aunque lo desee. Por ejemplo:

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

Tenga en cuenta la diferencia entre los dos diferentes [/qpar-Report (nivel de información de Paralelizador automático)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md) opciones. `/Qpar-report:1` genera mensajes del paralelizador solo para los bucles que se paralelizan correctamente. `/Qpar-report:2` genera mensajes del paralelizador para las paralelizaciones de bucles correctas e incorrectas.

Para obtener más información sobre los códigos de motivo y mensajes, vea [mensajes del Vectorizador y Paralelizador](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

## <a name="auto-vectorizer"></a>Vectorizador automático

El vectorizador automático analiza los bucles del código y usa los registros y las instrucciones de vector en el equipo de destino para ejecutarlos si puede. Esto puede mejorar el rendimiento del código. El compilador tiene como destino las instrucciones SSE2, AVX y AVX2 en procesadores Intel o AMD, o las instrucciones NEON en procesadores ARM, según la [/arch](../build/reference/arch-minimum-cpu-architecture.md) cambie.

El vectorizador automático puede generar instrucciones diferentes de las que especifica el modificador `/arch`. Estas instrucciones estarán protegidas por una comprobación en tiempo de ejecución para asegurarse de que código se ejecuta correctamente. Por ejemplo, cuando se compila `/arch:SSE2`, se pueden emitir instrucciones SSE4.2. Una comprobación en tiempo de ejecución comprueba que SSE4.2 está disponible en el procesador de destino y salta a una versión no SSE4.2 del bucle si el procesador no admite las instrucciones.

De forma predeterminada, se habilita el vectorizador automático. Si desea comparar el rendimiento del código sometido a la vectorización, puede usar [#pragma Loop (no_vector)](../preprocessor/loop.md) para deshabilitar la vectorización de un bucle concreto.

```cpp
#pragma loop(no_vector)
for (int i = 0; i < 1000; ++i)
   A[i] = B[i] + C[i];
```

Como ocurre con todos los [directivas pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md), la sintaxis de la directiva pragma alternativa `__pragma(loop(no_vector))` también es compatible.

Como en el Paralelizador automático, se puede especificar el [/Qvec-report (nivel de información de Vectorizador automático)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md) la opción de línea de comandos para notificar correctamente solo los bucles vectorizados:`/Qvec-report:1`, o ambos correctamente y los bucles vectorizados correctamente:`/Qvec-report:2`).

Para obtener más información sobre los códigos de motivo y mensajes, vea [mensajes del Vectorizador y Paralelizador](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

Para obtener un ejemplo que muestra cómo funciona el vectorizador en la práctica, consulte [proyecto Austin, parte 2 de 6: volver una página](http://blogs.msdn.com/b/vcblog/archive/2012/09/27/10348494.aspx)

## <a name="see-also"></a>Vea también

[loop](../preprocessor/loop.md)<br/>
[Programación en paralelo en código nativo](http://go.microsoft.com/fwlink/p/?linkid=263662)<br/>
[/Qpar (Paralelizador automático)](../build/reference/qpar-auto-parallelizer.md)<br/>
[/Qpar/report (Nivel de información de paralelizador automático)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)<br/>
[/Qvec/report (Nivel de información de vectorizador automático)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)<br/>
[Mensajes del vectorizador y paralelizador](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)
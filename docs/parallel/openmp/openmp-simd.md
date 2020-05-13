---
title: Extensión SIMD
ms.date: 03/20/2019
helpviewer_keywords:
- SIMD
- OpenMP in Visual C++, new features
- explicit parallelization, new features
ms.openlocfilehash: 0a7f1142a3a432628795341f4885b76a5c144990
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366452"
---
# <a name="simd-extension"></a>Extensión SIMD

Visual C++ actualmente es compatible con el estándar OpenMP 2.0, sin embargo, Visual Studio 2019 también ahora ofrece funcionalidad SIMD.

> [!NOTE]
> Para utilizar SIMD, `-openmp:experimental` compile con el conmutador que habilita `-openmp` funciones OpenMP adicionales que no están disponibles cuando se utiliza el conmutador.
>
> El `-openmp:experimental` interruptor `-openmp`subsume, lo que significa que todas las características de OpenMP 2.0 están incluidas en su uso.

Para obtener más información, vea [Extensión DE SIMD a C++ OpenMP en Visual Studio](https://devblogs.microsoft.com/cppblog/simd-extension-to-c-openmp-in-visual-studio/).

## <a name="openmp-simd-in-visual-c"></a>OpenMP SIMD en Visual C++

OpenMP SIMD, introducido en el estándar OpenMP 4.0, se dirige a la fabricación de bucles aptos para vectores. Mediante el `simd` uso de la directiva antes de un bucle, el compilador puede omitir las dependencias vectoriales, hacer que el bucle sea lo más apto para vectores como sea posible y respetar la intención de los usuarios de que varias iteraciones de bucle se ejecuten simultáneamente.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Visual C++ proporciona pragmas de bucle `#pragma vector` `#pragma ivdep`no OpenMP similares como y, sin embargo, con OpenMP SIMD, el compilador puede hacer más, como:

- Siempre se permite ignorar las dependencias vectoriales actuales.
- `/fp:fast`se habilita dentro del bucle.
- Los bucles externos y los bucles con llamadas de función son aptos para vectores.
- Los bucles anidados se pueden combinar en un bucle y hacer que sean aptos para vectores.
- Aceleración `#pragma omp for simd` híbrida con para permitir vectores de grano grueso y de grano fino.  

Para bucles basados en vectores, el compilador permanece en silencio a menos que utilice un modificador de registro de soporte vectorial:

```cmd
    cl -O2 -openmp:experimental -Qvec-report:2 mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(96) : info C5001: Omp simd loop vectorized
```

Para bucles no aptos para vectores, el compilador emite cada mensaje:

```cmd
    cl -O2 -openmp:experimental mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
```

### <a name="clauses"></a>Cláusulas

La directiva SIMD de OpenMP también puede tomar las siguientes cláusulas para mejorar la compatibilidad con vectores:

|Directiva|Descripción|
|---|---|
|`simdlen(length)`|Especifique el número de carriles vectoriales.|
|`safelen(length)`|Especifique la distancia de dependencia vectorial.|
|`linear(list[ : linear-step]`)|La asignación lineal de la variable de inducción de bucle a la suscripción de matriz.|
|`aligned(list[ : alignment])`|La alineación de los datos.|
|`private(list)`|Especifique la privatización de datos.|
|`lastprivate(list)`|Especifique la privatización de datos con el valor final de la última iteración.|
|`reduction(reduction-identifier:list)`|Especifique operaciones de reducción personalizadas.|
|`collapse(n)`|Nido de bucle de fusión.|

> [!NOTE]
> El compilador analiza e ignora las cláusulas SIMD no eficaces con una advertencia.
>
> Por ejemplo, el uso del código siguiente emite una advertencia:
>
> ```c
>    #pragma omp simd simdlen(8)
>    for (i = 0; i < count; i++)
>    {
>        a[i] = a[i-1] + 1;
>        b[i] = *c + 1;
>        bar(i);
>    }
> ```
>
> ```Output
>    warning C4849: OpenMP 'simdlen' clause ignored in 'simd' directive
> ```

### <a name="example"></a>Ejemplo
  
La directiva SIMD de OpenMP proporciona a los usuarios una manera de dictar el compilador hacer bucles aptos para vectores. Al anotar un bucle con la directiva OpenMP SIMD, los usuarios tienen la intención de ejecutar varias iteraciones de bucle simultáneamente.

Por ejemplo, el siguiente bucle se anota con la directiva OpenMP SIMD. No hay un paralelismo perfecto entre las iteraciones de bucle, ya que hay una dependencia hacia atrás de a[i] a[i-1], pero debido a la directiva SIMD el compilador todavía puede empaquetar iteraciones consecutivas de la primera instrucción en una instrucción vectorial y ejecutarlas en paralelo.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Por lo tanto, la siguiente forma vectorial transformada del bucle es **legal** porque el compilador mantiene el comportamiento secuencial de cada iteración de bucle original. En otras `a[i]` palabras, `a[-1]` `b[i]` se `a[i]` ejecuta después `bar` de , es después y la llamada a sucede en último lugar.

```c
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        b[i:i+3] = *c + 1;
        bar(i);
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

No es **legal** mover la `*c` referencia de memoria fuera del `a[i]` `b[i]`bucle si puede alias con o . Tampoco es legal reordenar las instrucciones dentro de una iteración original si rompe la dependencia secuencial. Por ejemplo, el siguiente bucle transformado no es legal:

```c
    c = b;
    t = *c;
    for (i = 0; i < count; i+=4)
    {
        a[i:i+3] = a[i-1:i+2] + 1;
        bar(i);            // illegal to reorder if bar[i] depends on b[i]
        b[i:i+3] = t + 1;  // illegal to move *c out of the loop
        bar(i+1);
        bar(i+2);
        bar(i+3);
    }
```

## <a name="see-also"></a>Consulte también

[/openmp (Habilitar la compatibilidad con OpenMP 2.0)](../../build/reference/openmp-enable-openmp-2-0-support.md)<br/>

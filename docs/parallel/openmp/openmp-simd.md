---
title: Extensión SIMD
ms.date: 03/20/2019
helpviewer_keywords:
- SIMD
- OpenMP in Visual C++, new features
- explicit parallelization, new features
ms.openlocfilehash: 52402aa553c6d68d3073aba26ecac7b784522ee9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363276"
---
# <a name="simd-extension"></a>Extensión SIMD

Visual C++ actualmente es compatible con el estándar OpenMP 2.0, sin embargo, Visual Studio de 2019 ahora también ofrece funcionalidad SIMD.

> [!NOTE]
> Para usar SIMD, compile con el `-openmp:experimental` conmutador que permite características adicionales de OpenMP no está disponible cuando se usa el `-openmp` cambie.
>
> El `-openmp:experimental` conmutador incluye a `-openmp`, lo que significa que todas las características de OpenMP 2.0 están incluidas en su uso.

Para obtener más información, consulte [extensión SIMD C++ OpenMP en Visual Studio](https://devblogs.microsoft.com/cppblog/simd-extension-to-c-openmp-in-visual-studio/).

## <a name="openmp-simd-in-visual-c"></a>SIMD OpenMP en VisualC++

OpenMP SIMD, introducido en 4.0 OpenMP estándar, destinos realizar bucles compatible con el vector. Mediante el uso de la `simd` Directiva antes de un bucle, el compilador puede omitir las dependencias de vector, hacer que el bucle como vector fáciles como sea posible y respeta la intención de los usuarios tienen varias iteraciones del bucle ejecutar simultáneamente.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Visual C++ proporciona pragmas de bucle no OpenMP similar como `#pragma vector` y `#pragma ivdep`; sin embargo, con OpenMP SIMD, el compilador puede hacer más, como:

- Siempre puede pasar por alto las dependencias de vector presente.
- `/fp:fast` se habilita en el bucle.
- Bucles externos y los bucles con las llamadas de función son compatible con el vector.
- Bucles anidados pueden combinan en un bucle y realiza compatible con el vector.
- Aceleración de híbrido con `#pragma omp for simd` para habilitar los vectores de subprocesamiento múltiple y detallados generales.  

Compatible con el vector de bucles for, el compilador sigue siendo silencioso a menos que use un modificador de registro de vectores de soporte técnico:

```cmd
    cl -O2 -openmp:experimental -Qvec-report:2 mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(96) : info C5001: Omp simd loop vectorized
```

Compatible con vector bucles for, el compilador emite cada uno un mensaje:

```cmd
    cl -O2 -openmp:experimental mycode.cpp
```

```Output
    mycode.cpp(84) : info C5002: Omp simd loop not vectorized due to reason '1200'
    mycode.cpp(90) : info C5002: Omp simd loop not vectorized due to reason '1200'
```

### <a name="clauses"></a>Cláusulas

La directiva de OpenMP SIMD también puede realizar las siguientes cláusulas para mejorar la compatibilidad con el vector:

|Directiva|Descripción|
|---|---|
|`simdlen(length)`|Especifique el número de pistas de vector.|
|`safelen(length)`|Especificar la distancia de dependencia del vector.|
|`linear(list[ : linear-step]`)|La asignación de variable de inducción de bucle lineal a suscripción de la matriz.|
|`aligned(list[ : alignment])`|La alineación de datos.|
|`private(list)`|Especifique privatización en modo datos.|
|`lastprivate(list)`|Especifique privatización en modo datos con el valor final de la última iteración.|
|`reduction(reduction-identifier:list)`|Especificar las operaciones de reducción personalizada.|
|`collapse(n)`|Anidamiento de bucle de fusión.|

> [!NOTE]
> Cláusulas SIMD efectivo no se analizan y se omite el compilador con una advertencia.
>
> Por ejemplo, use los siguientes problemas de código una advertencia:
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
  
La directiva de OpenMP SIMD proporciona a los usuarios una forma de indicar el compilador marca bucles vector fáciles. La anotación de un bucle con la directiva de OpenMP SIMD, los usuarios desean tener ejecutar simultáneamente varias iteraciones del bucle.

Por ejemplo, el siguiente bucle está anotado con la directiva de OpenMP SIMD. No hay ningún paralelismo perfecta entre las iteraciones del bucle porque no hay una dependencia con versiones anteriores de una [i] a una [i-1], pero debido a la directiva SIMD que se podrá empaquetar iteraciones consecutivas de la primera instrucción en una sola instrucción de vector y ejecutar el compilador ellos en paralelo.

```c
    #pragma omp simd
    for (i = 0; i < count; i++)
    {
        a[i] = a[i-1] + 1;
        b[i] = *c + 1;
        bar(i);
    }
```

Por lo tanto, es el siguiente formulario transformado del bucle **legal** porque el compilador mantiene el comportamiento de cada iteración del bucle original secuencial. En otras palabras, `a[i]` se ejecuta después de `a[-1]`, `b[i]` después `a[i]` y la llamada a `bar` ocurre por última vez.

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

Tiene **no legal** para mover la referencia de memoria `*c` fuera del bucle si es posible que sea alias con `a[i]` o `b[i]`. También, no es legal para reordenar las instrucciones dentro de una iteración original Si interrumpe la dependencia secuencial. Por ejemplo, el siguiente bucle transformado no es legal:

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

## <a name="see-also"></a>Vea también

[/openmp (Habilitar la compatibilidad con OpenMP 2.0)](../../build/reference/openmp-enable-openmp-2-0-support.md)<br/>

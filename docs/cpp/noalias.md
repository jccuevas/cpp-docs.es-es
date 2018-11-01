---
title: noalias
ms.date: 02/09/2018
f1_keywords:
- noalias_cpp
helpviewer_keywords:
- noalias __declspec keyword
- __declspec keyword [C++], noalias
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
ms.openlocfilehash: 2eceffd10f97615859918991320ceebf577d094c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447130"
---
# <a name="noalias"></a>noalias

**Específicos de Microsoft**

**noalias** significa que una llamada de función no modifica ni hacer referencia a estado global visible y solo modifica la memoria designada *directamente* por los parámetros de puntero (direccionamientos indirectos de primer nivel).

Si una función está anotada como **noalias**, el optimizador puede suponer que, además de los parámetros, direccionamientos indirectos de primer nivel solo de los parámetros de puntero se hace referencia o modifican dentro de la función. El estado global visible es el conjunto de todos los datos que no están definidos o a los que no se hace referencia fuera del ámbito de la compilación, y su dirección no se toma. El ámbito de la compilación es todos los archivos de origen ([/LTCG (generación de código de tiempo de vínculo)](../build/reference/ltcg-link-time-code-generation.md) compilaciones) o un archivo de origen único (que no sean de **/LTCG** compilar).

El **noalias** anotación solo se aplica en el cuerpo de la función anotada. Al marcar una función como **__declspec (noalias)** no afecta a los alias de los punteros devueltos por la función.

Para la anotación de otro que puede afectar al uso de alias, vea [__declspec (Restrict)](../cpp/restrict.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra el uso de **__declspec (noalias)**.

Cuando la función `multiply` que se anota los accesos a memoria **__declspec (noalias)**, indica al compilador que esta función no modifica el estado global, excepto a través de los punteros en su lista de parámetros.

```C
// declspec_noalias.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1/k++;
    return a;
}

__declspec(noalias) void multiply(float * a, float * b, float * c)
{
    int i, j, k;

    for (j=0; j<P; j++)
        for (i=0; i<M; i++)
            for (k=0; k<N; k++)
                c[i * P + j] =
                          a[i * N + k] *
                          b[k * P + j];
}

int main()
{
    float * a, * b, * c;

    mempool = (float *) malloc(sizeof(float) * (M*N + N*P + M*P));

    if (!mempool)
    {
        puts("ERROR: Malloc returned null");
        exit(1);
    }

    memptr = mempool;
    a = init(M, N);
    b = init(N, P);
    c = init(M, P);

    multiply(a, b, c);
}
```

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[__declspec(restrict)](../cpp/restrict.md)

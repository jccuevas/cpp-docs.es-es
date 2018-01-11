---
title: rand_s | Microsoft Docs
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: rand_s
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords: rand_s
dev_langs: C++
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, cryptographically secure
- random numbers, generating
- rand_s function
- numbers, pseudorandom
- cryptographically secure random numbers
- pseudorandom numbers
- numbers, generating pseudorandom
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d5fde51ee8fb65426166d9d5d2e7d6e5873dd6e8
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2018
---
# <a name="rands"></a>rand_s

Genera un número pseudoaleatorio. Se trata de una versión más segura de la función [rand](../../c-runtime-library/reference/rand.md), con mejoras de seguridad, como se describe en [características de seguridad en CRT](../../c-runtime-library/security-features-in-the-crt.md). 

## <a name="syntax"></a>Sintaxis

```C
errno_t rand_s(unsigned int* randomValue);
```

### <a name="parameters"></a>Parámetros

*randomValue*  
Un puntero a un entero que contenga el valor generado.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto, código de error en caso contrario. Si el puntero de entrada _randomValue_ es un puntero nulo, la función invoca un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve `EINVAL` y establece en `errno` en `EINVAL`. Si se produce un error en la función por cualquier otro motivo, *_randomValue_ se establece en 0.

## <a name="remarks"></a>Comentarios

La función `rand_s` escribe un entero pseudoaleatorio comprendido entre 0 y `UINT_MAX` en el puntero de entrada. La función `rand_s` usa el sistema operativo para generar números aleatorios criptográficamente seguros. No usa el valor de inicialización generado por la función [srand](../../c-runtime-library/reference/srand.md) ni afecta a la secuencia de números aleatorios usada por `rand`.

La función `rand_s` requiere que la constante `_CRT_RAND_S` se defina antes de la declaración de inclusión de la función que se debe declarar, como se indica en el ejemplo siguiente:

```C
#define _CRT_RAND_S
#include <stdlib.h>
```

`rand_s` depende de la API [RtlGenRandom](http://msdn.microsoft.com/library/windows/desktop/aa387694), que solo está disponible en Windows XP y en versiones posteriores.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`rand_s`|\<stdlib.h>|

Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_rand_s.c
// This program illustrates how to generate random
// integer or floating point numbers in a specified range.

// Remembering to define _CRT_RAND_S prior
// to inclusion statement.
#define _CRT_RAND_S

#include <stdlib.h>
#include <stdio.h>
#include <limits.h>

int main( void )
{
    int             i;
    unsigned int    number;
    double          max = 100.0;
    errno_t         err;

    // Display 10 random integers in the range [ 1,10 ].
    for( i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %u\n", (unsigned int) ((double)number /
                       ((double) UINT_MAX + 1 ) * 10.0) + 1);
    }

    printf_s("\n");

    // Display 10 random doubles in [0, max).
    for (i = 0; i < 10;i++ )
    {
        err = rand_s( &number );
        if (err != 0)
        {
            printf_s("The rand_s function failed!\n");
        }
        printf_s( "  %g\n", (double) number / 
                          ((double) UINT_MAX + 1) * max );
    }
}
```

### <a name="sample-output"></a>Resultados del ejemplo

```Output
10
4
5
2
8
2
5
6
1
1

32.6617
29.4471
11.5413
6.41924
20.711
60.2878
61.0094
20.1222
80.9192
65.0712
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)  
[rand](../../c-runtime-library/reference/rand.md)  
[srand](../../c-runtime-library/reference/srand.md)  

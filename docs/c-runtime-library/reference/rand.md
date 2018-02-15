---
title: rand | Microsoft Docs
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- rand
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
f1_keywords:
- rand
dev_langs:
- C++
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5fecd9079de1ae846d83847eb299890d62c29d17
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="rand"></a>rand

Genera un número pseudoaleatorio mediante un algoritmo conocido y reproducible totalmente. Una versión más mediante programación segura de esta función está disponible; vea [rand_s](../../c-runtime-library/reference/rand-s.md). Números generan por `rand` no son criptográficamente segura. Para más seguros criptográficamente generación de números aleatorios, use `rand_s` o las funciones se declaran en la biblioteca estándar de C++ en [ \<aleatorio >](../../standard-library/random.md).

## <a name="syntax"></a>Sintaxis

```C
int rand( void );
```

## <a name="return-value"></a>Valor devuelto

`rand` devuelve un número pseudoaleatorio, como se describe arriba. No se devuelve ningún error.

## <a name="remarks"></a>Comentarios

La función `rand` devuelve un entero pseudoaleatorio comprendido entre 0 y `RAND_MAX` (32767). Use la función [srand](../../c-runtime-library/reference/srand.md) para inicializar el generador de números pseudoaleatorios antes de llamar a `rand`.

El `rand` función genera una secuencia conocida y no es adecuado para su uso como una función criptográfica. Para más seguros criptográficamente generación de números aleatorios, use `rand_s` o las funciones se declaran en la biblioteca estándar de C++ en [ \<aleatorio >](../../standard-library/random.md). Para obtener más información sobre los aspectos negativos de `rand()` y ver cómo `<random>` los aborda, vea [este vídeo](http://go.microsoft.com/fwlink/?LinkId=397615).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`rand`|\<stdlib.h>|

Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.

## <a name="example"></a>Ejemplo

```C
// crt_rand.c
// This program seeds the random-number generator
// with the time, then exercises the rand function.
//

#include <stdlib.h>
#include <stdio.h>
#include <time.h>

void SimpleRandDemo( int n )
{
   // Print n random numbers.
   int i;
   for( i = 0; i < n; i++ )
      printf( "  %6d\n", rand() );
}

void RangedRandDemo( int range_min, int range_max, int n )
{
   // Generate random numbers in the half-closed interval
   // [range_min, range_max). In other words,
   // range_min <= random number < range_max
   int i;
   for ( i = 0; i < n; i++ )
   {
      int u = (double)rand() / (RAND_MAX + 1) * (range_max - range_min)
            + range_min;
      printf( "  %6d\n", u);
   }
}

int main( void )
{
   // Seed the random-number generator with the current time so that
   // the numbers will be different every time we run.
   srand( (unsigned)time( NULL ) );

   SimpleRandDemo( 10 );
   printf("\n");
   RangedRandDemo( -100, 100, 10 );
}
```

```Output
22036
18330
11651
27464
18093
 3284
11785
14686
11447
11285

   74
   48
   27
   65
   96
   64
   -5
  -42
  -55
   66
```

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)  
[srand](../../c-runtime-library/reference/srand.md)  
[rand_s](../../c-runtime-library/reference/rand-s.md)  
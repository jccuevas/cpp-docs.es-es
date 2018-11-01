---
title: rand
ms.date: 1/02/2018
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
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 67e128fc4adea345807a2d59078a00e3c4bd1f07
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440734"
---
# <a name="rand"></a>rand

Genera un número pseudoaleatorio mediante un algoritmo muy conocido y completamente reproducible. Una versión más mediante programación segura de esta función está disponible; consulte [rand_s](rand-s.md). Los números generan por **rand** no son seguras criptográficamente. Para más seguros criptográficamente generación de números aleatorios, utilice [rand_s](rand-s.md) o las funciones se declaran en la biblioteca estándar de C++ en [ \<aleatorio >](../../standard-library/random.md).

## <a name="syntax"></a>Sintaxis

```C
int rand( void );
```

## <a name="return-value"></a>Valor devuelto

**RAND** devuelve un número pseudoaleatorio, como se ha descrito anteriormente. No se devuelve ningún error.

## <a name="remarks"></a>Comentarios

El **rand** función devuelve un entero pseudoaleatorio entre 0 y **RAND_MAX** (32767). Use la [srand](srand.md) función para inicializar el generador de números pseudoaleatorios antes de llamar a **rand**.

El **rand** función genera una secuencia conocida y no es adecuado para su uso como una función criptográfica. Para más seguros criptográficamente generación de números aleatorios, utilice [rand_s](rand-s.md) o las funciones se declaran en la biblioteca estándar de C++ en [ \<aleatorio >](../../standard-library/random.md). Para obtener información acerca de cuál es el problema con **rand** y cómo \<aleatorio > aborda estas desventajas, vea este vídeo titulado [rand considera perjudicial](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**rand**|\<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[srand](srand.md)<br/>
[rand_s](rand-s.md)<br/>

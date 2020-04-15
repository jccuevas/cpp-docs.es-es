---
title: rand
ms.date: 4/2/2020
api_name:
- rand
- _o_rand
api_location:
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rand
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 944c512d0102b459afc2924ef7515311e46cd43c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338158"
---
# <a name="rand"></a>rand

Genera un número pseudoaleatorio mediante un algoritmo conocido y totalmente reproducible. Una versión más segura mediante programación de esta función está disponible; ver [rand_s](rand-s.md). Los números generados por **rand** no son criptográficamente seguros. Para una generación de números aleatorios más segura criptográficamente, utilice [rand_s](rand-s.md) o las funciones declaradas en la biblioteca estándar C++ en [ \<>aleatorios. ](../../standard-library/random.md)

## <a name="syntax"></a>Sintaxis

```C
int rand( void );
```

## <a name="return-value"></a>Valor devuelto

**rand** devuelve un número pseudoaleatorio, como se describió anteriormente. No se devuelve ningún error.

## <a name="remarks"></a>Observaciones

La función **rand** devuelve un entero pseudoaleatorio en el intervalo 0 a **RAND_MAX** (32767). Utilice la función [srand](srand.md) para sembrar el generador de números pseudoaleatorios antes de llamar a **rand**.

La función **rand** genera una secuencia conocida y no es adecuada para su uso como función criptográfica. Para una generación de números aleatorios más segura criptográficamente, utilice [rand_s](rand-s.md) o las funciones declaradas en la biblioteca estándar C++ en [ \<>aleatorios. ](../../standard-library/random.md) Para obtener información sobre lo que \<está mal con **rand** y cómo> al azar aborda estas deficiencias, vea este video titulado [rand Considered Harmful](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**Rand**|\<stdlib.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Consulte también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[srand](srand.md)<br/>
[rand_s](rand-s.md)<br/>

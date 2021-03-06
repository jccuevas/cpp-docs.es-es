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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 8f2a4d00310671e8ba80055e38e479e348562ac2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919528"
---
# <a name="rand"></a>rand

Genera un número pseudoaleatorios mediante un algoritmo conocido y totalmente reproducible. Hay disponible una versión más segura mediante programación de esta función; vea [rand_s](rand-s.md). Los números generados por **Rand** no son seguros criptográficamente. Para obtener una generación de números aleatorios criptográficamente segura, use [rand_s](rand-s.md) o las funciones declaradas en la biblioteca estándar de C++ en [ \<>aleatorios ](../../standard-library/random.md).

## <a name="syntax"></a>Sintaxis

```C
int rand( void );
```

## <a name="return-value"></a>Valor devuelto

**Rand** devuelve un número pseudoaleatorios, tal como se ha descrito anteriormente. No se devuelve ningún error.

## <a name="remarks"></a>Observaciones

La función **Rand** devuelve un entero pseudoaleatorio en el intervalo de 0 a **RAND_MAX** (32767). Utilice la función [srand](srand.md) para inicializar el generador de números pseudoaleatorios antes de llamar a **Rand**.

La función **Rand** genera una secuencia conocida y no es adecuada para su uso como una función criptográfica. Para obtener una generación de números aleatorios criptográficamente segura, use [rand_s](rand-s.md) o las funciones declaradas en la biblioteca estándar de C++ en [ \<>aleatorios ](../../standard-library/random.md). Para obtener información acerca de lo que **rand** es el problema \<con rand y cómo el> aleatorio soluciona estas deficiencias, vea este vídeo titulado [Rand considerado perjudicial](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**rand**|\<stdlib.h>|

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

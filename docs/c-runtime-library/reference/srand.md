---
title: srand
ms.date: 4/2/2020
api_name:
- srand
- _o_srand
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
- srand
helpviewer_keywords:
- random starting point
- random starting point, setting
- random numbers, generating
- srand function
- numbers, pseudorandom
- numbers, random
- pseudorandom numbers
- starting points, setting random
- starting points
ms.openlocfilehash: 3f6f97ad9a3bd0d7e4e88ad1797d369f012bbe5e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913594"
---
# <a name="srand"></a>srand

Establece el valor de inicialización inicial para el generador de números pseudoaleatorios utilizado por la función **Rand** .

## <a name="syntax"></a>Sintaxis

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>Parámetros

*seed*<br/>
Valor de inicialización para la generación de números pseudoaleatorios

## <a name="remarks"></a>Observaciones

La función **srand** establece el punto de partida para generar una serie de enteros pseudoaleatorios en el subproceso actual. Para reinicializar el generador y crear la misma secuencia de resultados, llame a la función **srand** y use de nuevo el mismo argumento de *inicialización* . Cualquier otro valor de *SEED* establece el generador en un punto inicial diferente en la secuencia pseudoaleatorio. **Rand** recupera los números pseudoaleatorios que se generan. Si se llama a **Rand** antes de cualquier llamada a **srand** , se genera la misma secuencia que si se llama a **srand** con la *inicialización* pasada como 1.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [rand](rand.md).

## <a name="see-also"></a>Consulta también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>

---
title: srand
ms.date: 01/02/2018
apiname:
- srand
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
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: d74ae4cbec5a76df48bb2b56acab7329e6cf8aa5
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927407"
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

*propagación*<br/>
Valor de inicialización para la generación de números pseudoaleatorios

## <a name="remarks"></a>Comentarios

La función **srand** establece el punto de partida para generar una serie de enteros pseudoaleatorios en el subproceso actual. Para reinicializar el generador y crear la misma secuencia de resultados, llame a la función **srand** y use de nuevo el mismo argumento de *inicialización* . Cualquier otro valor de *SEED* establece el generador en un punto inicial diferente en la secuencia pseudoaleatorio. **Rand** recupera los números pseudoaleatorios que se generan. Si se llama a **Rand** antes de cualquier llamada a **srand** , se genera la misma secuencia que si se llama a **srand** con la *inicialización* pasada como 1.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [rand](rand.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>

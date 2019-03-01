---
title: srand
ms.date: 1/02/2018
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
ms.openlocfilehash: 6545d4eba6c17fd55bb2b8cf23fb0319d1c96bee
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/01/2019
ms.locfileid: "57209826"
---
# <a name="srand"></a>srand

Establece el valor de inicialización inicial para el generador de números pseudoaleatorio utilizado por el **rand** función.

## <a name="syntax"></a>Sintaxis

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>Parámetros

*seed*<br/>
Valor de inicialización para la generación de números pseudoaleatorios

## <a name="remarks"></a>Comentarios

El **srand** función establece el punto de partida para generar una serie de enteros pseudoaleatorios en el subproceso actual. Para reinicializar el generador para crear la misma secuencia de resultados, llame a la **srand** funcionar y utilizar el mismo *inicialización* nuevo argumento. Cualquier otro valor para *inicialización* establece el generador en otro punto de partida en la secuencia pseudoaleatoria. **RAND** recupera los números pseudaleatorios que se generan. Una llamada a **rand** antes de cualquier llamada a **srand** genera la misma secuencia que una llamada a **srand** con *inicialización* pasa como 1.

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

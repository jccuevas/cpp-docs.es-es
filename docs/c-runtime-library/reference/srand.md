---
title: srand | Microsoft Docs
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- srand
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7972ddfe6ae9c1d591bdbd4cc5e208d78e826037
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107562"
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

*Valor de inicialización*<br/>
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

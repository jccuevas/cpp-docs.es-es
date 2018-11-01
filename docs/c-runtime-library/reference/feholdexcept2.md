---
title: feholdexcept
ms.date: 04/05/2018
apiname:
- feholdexcept
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- feholdexcept
- fenv/feholdexcept
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
ms.openlocfilehash: 26097398b9f9d498ab4c56690dc9c6cbb950bafb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525744"
---
# <a name="feholdexcept"></a>feholdexcept

Guarda el entorno actual de punto flotante en el objeto especificado, borra las marcas de estado de punto flotante y, si es posible, coloca el entorno de punto flotante en modo continuo.

## <a name="syntax"></a>Sintaxis

```C
int feholdexcept(
   fenv_t *penv
);
```

### <a name="parameters"></a>Parámetros

*penv*<br/>
Puntero a un **fenv_t** objeto que contiene una copia del entorno de punto flotante.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si y solo si la función es capaz de activar correctamente el control de excepciones de punto flotante continuo.

## <a name="remarks"></a>Comentarios

El **feholdexcept** función se utiliza para almacenar el estado del entorno de punto flotante actual en el **fenv_t** objeto señalado por *penv*y para establecer el entorno No interrumpa la ejecución en excepciones de punto flotante. Esto se conoce como modo continuo.  Este modo continúa hasta que el entorno se restaura mediante [fesetenv](fesetenv1.md) o [feupdateenv](feupdateenv.md).

Puede usar esta función al principio de una subrutina que tenga que ocultar una o varias excepciones de punto flotante del autor de llamada. Para notificar una excepción, simplemente puede borrar las excepciones no deseadas mediante [feclearexcept,](feclearexcept1.md) y luego finalice el modo continuo con una llamada a **feupdateenv**.

Para usar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulta [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**feholdexcept**|\<fenv.h>|\<cfenv>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[fesetenv](fesetenv1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>

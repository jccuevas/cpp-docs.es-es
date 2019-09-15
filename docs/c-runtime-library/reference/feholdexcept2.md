---
title: feholdexcept
ms.date: 04/05/2018
api_name:
- feholdexcept
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- feholdexcept
- fenv/feholdexcept
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
ms.openlocfilehash: bd55a4ed627d731f7246d589d4b74b4173e31d4e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941185"
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
Puntero a un objeto **fenv_t** que contiene una copia del entorno de punto flotante.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si y solo si la función puede activar correctamente el control de excepciones de punto flotante no detenido.

## <a name="remarks"></a>Comentarios

La función **feholdexcept** se usa para almacenar el estado del entorno de punto flotante actual en el objeto **fenv_t** al que apunta *penv*, y para establecer el entorno para que no interrumpa la ejecución en las excepciones de punto flotante. Esto se conoce como modo continuo.  Este modo continúa hasta que el entorno se restaura mediante [fesetenv](fesetenv1.md) o [feupdateenv](feupdateenv.md).

Puede usar esta función al principio de una subrutina que tenga que ocultar una o varias excepciones de punto flotante del autor de llamada. Para notificar una excepción, simplemente puede borrar las excepciones no deseadas mediante [feclearexcept](feclearexcept1.md) y, a continuación, finalizar el modo sin interrupción con una llamada a **feupdateenv**.

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

---
title: fegetexceptflag
ms.date: 04/05/2018
api_name:
- fegetexceptflag
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
- fegetexceptflag
- fenv/fegetexceptflag
helpviewer_keywords:
- fegetexceptflag function
ms.assetid: 2d28f0ca-70c9-4cff-be8b-3d876eacde71
ms.openlocfilehash: 3d3bf59b28a464dc163dc027b867e890c3c8797b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941232"
---
# <a name="fegetexceptflag"></a>fegetexceptflag

Almacena el estado actual de las marcas de excepción de punto flotante especificadas.

## <a name="syntax"></a>Sintaxis

```C
int fegetexceptflag(
   fexcept_t* pstatus,
   int excepts
);
```

### <a name="parameters"></a>Parámetros

*pstatus*<br/>
Un puntero a un objeto **fexcept_t** que contiene los valores actuales de las marcas de excepción especificadas por *excepts*.

*excepts*<br/>
Marcas de excepción de punto flotante que se van a almacenar en *pstatus*.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, devuelve 0. De lo contrario, devuelve un valor distinto de cero.

## <a name="remarks"></a>Comentarios

La función **fegetexceptflag** almacena el estado actual de las marcas de estado de excepción de punto flotante especificadas por *excepts* en el objeto **fexcept_t** al que apunta *pstatus*.  *pstatus* debe apuntar a un objeto **fexcept_t** válido o el comportamiento posterior es indefinido. La función **fegetexceptflag** admite estas macros de excepción, definidas \<en fenv. h >:

|Macro de excepción|DESCRIPCIÓN|
|---------------------|-----------------|
|FE_DIVBYZERO|Se ha producido un error de singularidad o de polo en una operación de punto flotante anterior; se ha creado un valor infinito.|
|FE_INEXACT|Se ha forzado la función a redondear el resultado almacenado de una operación de punto flotante anterior.|
|FE_INVALID|Se ha producido un error de dominio en una operación de punto flotante anterior.|
|FE_OVERFLOW|Se ha producido un error de intervalo; el resultado de una operación de punto flotante anterior era demasiado grande para representarse.|
|FE_UNDERFLOW|El resultado de una operación de punto flotante anterior era demasiado pequeño para representarlo con completa precisión; se ha creado un valor no normalizado.|
|FE_ALLEXCEPT|Operación OR bit a bit de todas las excepciones de punto flotante admitidas.|

El argumento *excepts* puede ser cero, una de las macros de excepción de punto flotante admitidas o la operación OR bit a bit de dos o más de las macros. El efecto de cualquier otro valor de argumento es indefinido.

Para usar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulta [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**fegetexceptflag**|\<fenv.h>|\<cfenv>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>

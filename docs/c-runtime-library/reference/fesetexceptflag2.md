---
title: fesetexceptflag
ms.date: 04/05/2018
api_name:
- fesetexceptflag
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
- fesetexceptflag
- fenv/fesetexceptflag
helpviewer_keywords:
- fesetexceptflag function
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
ms.openlocfilehash: b16de7ea54b5f1df21b6626febe773c8cef556f5
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972147"
---
# <a name="fesetexceptflag"></a>fesetexceptflag

Establece las marcas de estado de punto flotante especificadas en el entorno actual de punto flotante.

## <a name="syntax"></a>Sintaxis

```C
int fesetexceptflag(
     const fexcept_t *pstatus,
     int excepts
);
```

### <a name="parameters"></a>Parameters

*pstatus*<br/>
Puntero a un objeto **fexcept_t** que contiene los valores en los que se van a establecer las marcas de estado de excepción. Es posible que el objeto se haya establecido mediante una llamada anterior a [fegetexceptflag](fegetexceptflag2.md).

*excepts*<br/>
Marcas de estado de excepción de punto flotante que se establecen.

## <a name="return-value"></a>Valor devuelto

Si todas las marcas de estado de excepción especificadas se establecen correctamente, devuelve 0. De lo contrario, devuelve un valor distinto de cero.

## <a name="remarks"></a>Notas

La función **fesetexceptflag** establece el estado de las marcas de estado de excepción de punto flotante especificadas por, *excepto* los valores correspondientes establecidos en el objeto de **fexcept_t** al que apunta *pstatus*.  No genera las excepciones. El puntero *pstatus* debe apuntar a un objeto **fexcept_t** válido o el comportamiento posterior es indefinido. La función **fesetexceptflag** admite estos valores de macro de excepción en *excepts*, que se definen en \<fenv. h >:

|Macro de excepción|Descripción|
|---------------------|-----------------|
|FE_DIVBYZERO|Se ha producido un error de singularidad o de polo en una operación de punto flotante anterior; se ha creado un valor infinito.|
|FE_INEXACT|Se ha forzado la función a redondear el resultado almacenado de una operación de punto flotante anterior.|
|FE_INVALID|Se ha producido un error de dominio en una operación de punto flotante anterior.|
|FE_OVERFLOW|Se ha producido un error de intervalo; el resultado de una operación de punto flotante anterior era demasiado grande para representarse.|
|FE_UNDERFLOW|El resultado de una operación de punto flotante anterior era demasiado pequeño para representarlo con completa precisión; se ha creado un valor no normalizado.|
|FE_ALL_EXCEPT|Operación OR bit a bit de todas las excepciones de punto flotante admitidas.|

El argumento *excepts* puede ser cero, una de las macros de excepción de punto flotante admitidas o la operación OR bit a bit de dos o más de las macros. El efecto de cualquier otro valor de argumento es indefinido.

Para usar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulta [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Requisitos de

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**fesetexceptflag**|\<fenv.h>|\<cfenv>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[fegetexceptflag](fegetexceptflag2.md)<br/>

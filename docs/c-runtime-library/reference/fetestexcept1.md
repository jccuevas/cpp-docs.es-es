---
title: fetestexcept
ms.date: 04/05/2018
api_name:
- fetestexcept
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
- fetestexcept
- fenv/fetestexcept
helpviewer_keywords:
- fetestexept function
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
ms.openlocfilehash: 61a68b4569d52b550da3fad12c077b82bb067fa9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941007"
---
# <a name="fetestexcept"></a>fetestexcept

Determina cuáles de las marcas de estado de excepción de punto flotante están establecidas actualmente.

## <a name="syntax"></a>Sintaxis

```C
int fetestexcept(
   int excepts
);
```

### <a name="parameters"></a>Parámetros

*excepts*<br/>
Operación OR bit a bit de las marcas de estado de punto flotante que se van a probar.

## <a name="return-value"></a>Valor devuelto

Si se ejecuta correctamente, devuelve una máscara de bits que contiene una operación OR bit a bit de las macros de excepción de punto flotante que se corresponden con las marcas de estado de excepción actualmente establecidas. Devuelve 0 si no se establece ninguna de las excepciones.

## <a name="remarks"></a>Comentarios

Use la función fetestexcept para determinar las excepciones que ha generado una operación de punto flotante. Use el parámetro *excepts* para especificar qué marcas de estado de excepción se van a probar. La función **fetestexcept** usa estas macros de excepción definidas \<en fenv. h > en *excepto* en y el valor devuelto:

|Macro de excepción|DESCRIPCIÓN|
|---------------------|-----------------|
|FE_DIVBYZERO|Se ha producido un error de singularidad o de polo en una operación de punto flotante anterior; se ha creado un valor infinito.|
|FE_INEXACT|Se ha forzado la función a redondear el resultado almacenado de una operación de punto flotante anterior.|
|FE_INVALID|Se ha producido un error de dominio en una operación de punto flotante anterior.|
|FE_OVERFLOW|Se ha producido un error de intervalo; el resultado de una operación de punto flotante anterior era demasiado grande para representarse.|
|FE_UNDERFLOW|El resultado de una operación de punto flotante anterior era demasiado pequeño para representarlo con completa precisión; se ha creado un valor no normalizado.|
|FE_ALLEXCEPT|Operación OR bit a bit de todas las excepciones de punto flotante admitidas.|

El argumento *excepts* especificado puede ser 0, una de las macros de excepción de punto flotante admitidas o la operación OR bit a bit de dos o más de las macros. El efecto de cualquier otro valor de argumento, *excepto* , es indefinido.

Para usar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulta [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**fetestexcept**|\<fenv.h>|\<cfenv>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feraiseexcept](feraiseexcept.md)<br/>

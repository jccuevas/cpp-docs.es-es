---
title: fetestexcept | Documentos de Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- fetestexcept
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
- fetestexcept
- fenv/fetestexcept
dev_langs:
- C++
helpviewer_keywords:
- fetestexept function
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0450fcaddf8ca05484d0b2bd122ff006eb8355f1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397403"
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

Use la función fetestexcept para determinar las excepciones que ha generado una operación de punto flotante. Use la *excepts* parámetro para especificar qué marcas de estado de excepción para probar. El **fetestexcept** función usa estas macros de excepción definidas en \<fenv.h > en *excepts* y el valor devuelto:

|Macro de excepción|Descripción|
|---------------------|-----------------|
|FE_DIVBYZERO|Se ha producido un error de singularidad o de polo en una operación de punto flotante anterior; se ha creado un valor infinito.|
|FE_INEXACT|Se ha forzado la función a redondear el resultado almacenado de una operación de punto flotante anterior.|
|FE_INVALID|Se ha producido un error de dominio en una operación de punto flotante anterior.|
|FE_OVERFLOW|Se ha producido un error de intervalo; el resultado de una operación de punto flotante anterior era demasiado grande para representarse.|
|FE_UNDERFLOW|El resultado de una operación de punto flotante anterior era demasiado pequeño para representarlo con completa precisión; se ha creado un valor no normalizado.|
|FE_ALLEXCEPT|Operación OR bit a bit de todas las excepciones de punto flotante admitidas.|

Especificado *excepts* argumento puede ser 0, una de las macros de excepción de punto flotante admitidos o bit a bit o de dos o más de las macros. El efecto de cualquier otro *excepts* el valor del argumento es indefinido.

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

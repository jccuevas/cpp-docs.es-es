---
title: feraiseexcept
ms.date: 04/05/2018
api_name:
- feraiseexcept
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
api_type:
- HeaderDef
f1_keywords:
- feraiseexcept
- fenv/feraiseexcept
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
ms.openlocfilehash: 40ff315c179a6b62a3073d4f07e4e6a6d1c1acab
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941126"
---
# <a name="feraiseexcept"></a>feraiseexcept

Genera las excepciones de punto flotante especificadas.

## <a name="syntax"></a>Sintaxis

```C
int feraiseexcept(
   int excepts
);
```

### <a name="parameters"></a>Parámetros

*excepts*<br/>
Excepciones de punto flotante que se generan.

## <a name="return-value"></a>Valor devuelto

Si todas las excepciones especificadas se generan correctamente, devuelve 0.

## <a name="remarks"></a>Comentarios

La función **feraiseexcept** intenta generar las excepciones de punto flotante especificadas por *excepts*.   La función **feraiseexcept** admite estas macros de excepción, definidas \<en fenv. h >:

|Macro de excepción|DESCRIPCIÓN|
|---------------------|-----------------|
|FE_DIVBYZERO|Se ha producido un error de singularidad o de polo en una operación de punto flotante anterior; se ha creado un valor infinito.|
|FE_INEXACT|Se ha forzado la función a redondear el resultado almacenado de una operación de punto flotante anterior.|
|FE_INVALID|Se ha producido un error de dominio en una operación de punto flotante anterior.|
|FE_OVERFLOW|Se ha producido un error de intervalo; el resultado de una operación de punto flotante anterior era demasiado grande para representarse.|
|FE_UNDERFLOW|El resultado de una operación de punto flotante anterior era demasiado pequeño para representarlo con completa precisión; se ha creado un valor no normalizado.|
|FE_ALLEXCEPT|Operación OR bit a bit de todas las excepciones de punto flotante admitidas.|

El argumento *excepts* puede ser cero, uno de los valores de macro de excepción o la operación OR bit a bit de dos o más de las macros de excepción admitidas. Si una de las macros de excepción es FE_OVERFLOW o FE_UNDERFLOW, es posible que se genere la excepción FE_INEXACT como efecto secundario.

Para usar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulta [fenv_access](../../preprocessor/fenv-access.md).

**Específico de Microsoft:** Las excepciones especificadas en *excepts* se generan en el orden FE_INVALID, FE_DIVBYZERO, FE_OVERFLOW, FE_UNDERFLOW, FE_INEXACT. Sin embargo, FE_INEXACT se puede generar cuando se genera FE_OVERFLOW o FE_UNDERFLOW, aunque no se especifique en *excepts*. **Fin de Específicos de Microsoft**

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|*feraiseexcept*|\<fenv.h>|\<cfenv>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>

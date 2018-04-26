---
title: feraiseexcept | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- feraiseexcept
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
apitype: HeaderDef
f1_keywords:
- feraiseexcept
- fenv/feraiseexcept
dev_langs:
- C++
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 93414d09b898212e3748c1de510796b401b6aa56
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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

El **feraiseexcept** función intenta generar las excepciones de punto flotante especificadas por *excepts*.   El **feraiseexcept** función admite estas macros de excepción, definidas en \<fenv.h >:

|Macro de excepción|Descripción|
|---------------------|-----------------|
|FE_DIVBYZERO|Se ha producido un error de singularidad o de polo en una operación de punto flotante anterior; se ha creado un valor infinito.|
|FE_INEXACT|Se ha forzado la función a redondear el resultado almacenado de una operación de punto flotante anterior.|
|FE_INVALID|Se ha producido un error de dominio en una operación de punto flotante anterior.|
|FE_OVERFLOW|Se ha producido un error de intervalo; el resultado de una operación de punto flotante anterior era demasiado grande para representarse.|
|FE_UNDERFLOW|El resultado de una operación de punto flotante anterior era demasiado pequeño para representarlo con completa precisión; se ha creado un valor no normalizado.|
|FE_ALLEXCEPT|Operación OR bit a bit de todas las excepciones de punto flotante admitidas.|

El *excepts* argumento puede ser cero, uno de los valores de macros de excepción, o bit a bit o de dos o más de las macros de excepción admitidos. Si una de las macros de excepción es FE_OVERFLOW o FE_UNDERFLOW, es posible que se genere la excepción FE_INEXACT como efecto secundario.

Para usar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulta [fenv_access](../../preprocessor/fenv-access.md).

**Specific de Microsoft:** las excepciones especificadas en *excepts* se generan en el orden FE_INVALID, FE_DIVBYZERO, FE_OVERFLOW, FE_UNDERFLOW, FE_INEXACT. Sin embargo, FE_INEXACT se puede producir cuando se produzca FE_OVERFLOW o FE_UNDERFLOW, incluso si no se especifica en *excepts*. **Fin de Específicos de Microsoft**

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

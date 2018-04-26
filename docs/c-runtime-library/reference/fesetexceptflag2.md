---
title: fesetexceptflag | Documentos de Microsoft
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
- fesetexceptflag
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
- fesetexceptflag
- fenv/fesetexceptflag
dev_langs:
- C++
helpviewer_keywords:
- fesetexceptflag function
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ec9be76fd0d860385ac53cfc70ea89d00ae2b1ef
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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

### <a name="parameters"></a>Parámetros

*pstatus*<br/>
Puntero a un **fexcept_t** que contiene los valores para establecer marcas de estado de la excepción en el objeto. Es posible que el objeto se haya establecido mediante una llamada anterior a [fegetexceptflag](fegetexceptflag2.md).

*excepts*<br/>
Marcas de estado de excepción de punto flotante que se establecen.

## <a name="return-value"></a>Valor devuelto

Si todas las marcas de estado de excepción especificadas se establecen correctamente, devuelve 0. De lo contrario, devuelve un valor distinto de cero.

## <a name="remarks"></a>Comentarios

El **fesetexceptflag** función establece el estado de los indicadores de estado de excepción de punto flotante especificado por *excepts* con los correspondientes valores establecidos el **fexcept_t** objeto señalado por *pstatus*.  No genera las excepciones. El *pstatus* puntero debe señalar a válido **fexcept_t** objeto o posterior comportamiento es indefinido. El **fesetexceptflag** función admite estos valores de macros de excepción en *excepts*, definida en \<fenv.h >:

|Macro de excepción|Descripción|
|---------------------|-----------------|
|FE_DIVBYZERO|Se ha producido un error de singularidad o de polo en una operación de punto flotante anterior; se ha creado un valor infinito.|
|FE_INEXACT|Se ha forzado la función a redondear el resultado almacenado de una operación de punto flotante anterior.|
|FE_INVALID|Se ha producido un error de dominio en una operación de punto flotante anterior.|
|FE_OVERFLOW|Se ha producido un error de intervalo; el resultado de una operación de punto flotante anterior era demasiado grande para representarse.|
|FE_UNDERFLOW|El resultado de una operación de punto flotante anterior era demasiado pequeño para representarlo con completa precisión; se ha creado un valor no normalizado.|
|FE_ALLEXCEPT|Operación OR bit a bit de todas las excepciones de punto flotante admitidas.|

El *excepts* argumento puede ser cero, una de las macros de excepción de punto flotante admitidos o bit a bit o de dos o más de las macros. El efecto de cualquier otro valor de argumento es indefinido.

Para usar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulta [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**fesetexceptflag**|\<fenv.h>|\<cfenv>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[fegetexceptflag](fegetexceptflag2.md)<br/>

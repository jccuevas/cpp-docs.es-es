---
title: feupdateenv | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- feupdateenv
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
- feupdateenv
- fenv/feupdateenv
dev_langs:
- C++
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1d88284717aec7a19c936d7ed8d87da96006d7ed
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="feupdateenv"></a>feupdateenv

Guarda las excepciones de punto flotante generadas actualmente, restaura el estado del entorno de punto flotante especificado y luego genera las excepciones de punto flotante guardadas.

## <a name="syntax"></a>Sintaxis

```C
int feupdateenv(
   const fenv_t* penv
);
```

### <a name="parameters"></a>Parámetros

*penv*<br/>
Puntero a un **fenv_t** objeto que contiene un entorno de punto flotante como conjunto mediante una llamada a [fegetenv](fegetenv1.md) o [feholdexcept](feholdexcept2.md). También puede especificar el entorno de punto flotante de inicio predeterminado mediante la macro FE_DFL_ENV.

## <a name="return-value"></a>Valor devuelto

Devuelve 0 si todas las acciones se completan correctamente. De lo contrario, devuelve un valor distinto de cero.

## <a name="remarks"></a>Comentarios

El **feupdateenv** función realiza varias acciones. En primer lugar, almacena las marcas de estado de excepción de punto flotante actuales en el almacenamiento automático. A continuación, Establece el entorno de punto flotante actual desde el valor almacenado en el **fenv_t** objeto señalado por *penv*. Si *penv* no **FE_DFL_ENV** o no apunta a válido **fenv_t** objeto posterior comportamiento es indefinido. Por último, **feupdateenv** genera las excepciones de punto flotante almacenadas de forma local.

Para usar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulta [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**feupdateenv**|\<fenv.h>|\<cfenv>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>

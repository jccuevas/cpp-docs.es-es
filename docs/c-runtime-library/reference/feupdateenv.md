---
title: feupdateenv
ms.date: 04/05/2018
api_name:
- feupdateenv
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
- feupdateenv
- fenv/feupdateenv
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
ms.openlocfilehash: 8f40cab42e4a89b1fc5a100587b11b0e2aeeb55c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940988"
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
Puntero a un objeto **fenv_t** que contiene un entorno de punto flotante establecido por una llamada a [fegetenv](fegetenv1.md) o [feholdexcept](feholdexcept2.md). También puede especificar el entorno de punto flotante de inicio predeterminado mediante la macro FE_DFL_ENV.

## <a name="return-value"></a>Valor devuelto

Devuelve 0 si todas las acciones se completan correctamente. De lo contrario, devuelve un valor distinto de cero.

## <a name="remarks"></a>Comentarios

La función **feupdateenv** realiza varias acciones. En primer lugar, almacena las marcas de estado de excepción de punto flotante actuales en el almacenamiento automático. A continuación, establece el entorno de punto flotante actual a partir del valor almacenado en el objeto **fenv_t** al que apunta *penv*. Si *penv* no es **FE_DFL_ENV** o no apunta a un objeto **fenv_t** válido, el comportamiento posterior es indefinido. Por último, **feupdateenv** genera las excepciones de punto flotante almacenadas localmente.

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

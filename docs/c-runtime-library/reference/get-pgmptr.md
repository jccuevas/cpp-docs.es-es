---
title: _get_pgmptr
ms.date: 11/04/2016
api_name:
- _get_pgmptr
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
- get_pgmptr
- _get_pgmptr
helpviewer_keywords:
- get_pgmptr function
- _get_pgmptr function
- pgmptr global variable
- _pgmptr global variable
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
ms.openlocfilehash: 4f9a3b19cc7eb1870b87ec46b7923987ec646e32
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955762"
---
# <a name="_get_pgmptr"></a>_get_pgmptr

Obtiene el valor actual de la variable global **_pgmptr** .

## <a name="syntax"></a>Sintaxis

```C
errno_t _get_pgmptr(
   char **pValue
);
```

### <a name="parameters"></a>Parámetros

*pValue*<br/>
Puntero a una cadena que se va a rellenar con el valor actual de la variable **_pgmptr** .

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error. Si *pValue* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** en **EINVAL** y devuelve **EINVAL**.

## <a name="remarks"></a>Comentarios

Solo llame a **_get_pgmptr** si el programa tiene un punto de entrada estrecho, como **Main ()** o **winmain ()** . La variable global **_pgmptr** contiene la ruta de acceso completa al ejecutable asociado con el proceso. Para obtener más información, consulte [_pgmptr, _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_pgmptr**|\<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[_get_wpgmptr](get-wpgmptr.md)<br/>

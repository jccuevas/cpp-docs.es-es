---
title: _get_wpgmptr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _get_wpgmptr
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
- get_wpgmptr
- _get_wpgmptr
dev_langs:
- C++
helpviewer_keywords:
- _wpgmptr global variable
- get_wpgmptr function
- wpgmptr global variable
- _get_wpgmptr function
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 23ebeed5b6710a7c8032f75b8677b09f8f96c84a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="getwpgmptr"></a>_get_wpgmptr

Obtiene el valor actual de la **_wpgmptr** (variable global).

## <a name="syntax"></a>Sintaxis

```C
errno_t _get_wpgmptr( 
   wchar_t **pValue 
);
```

### <a name="parameters"></a>Parámetros

*pValue*<br/>
Un puntero a una cadena que se rellenará con el valor actual de la **_wpgmptr** variable.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error. Si *pValue* es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve **EINVAL**.

## <a name="remarks"></a>Comentarios

Solo llame a **_get_wpgmptr** si el programa tiene un punto de entrada extensa, como **wmain()** o **wWinMain()**. El **_wpgmptr** (variable global) contiene la ruta de acceso completa al ejecutable asociado con el proceso como una cadena de caracteres anchos. Para obtener más información, consulte [_pgmptr, _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_wpgmptr**|\<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[_get_pgmptr](get-pgmptr.md)<br/>

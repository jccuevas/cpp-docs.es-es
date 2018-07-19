---
title: _get_doserrno | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_doserrno
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
- _get_doserrno
- get_doserrno
dev_langs:
- C++
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7cef2c068fad2f18cb1d11d33e551588800cb64
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399574"
---
# <a name="getdoserrno"></a>_get_doserrno

Obtiene el valor de error devuelto por el sistema operativo antes de que se traduce en un **errno** valor.

## <a name="syntax"></a>Sintaxis

```C
errno_t _get_doserrno( 
   int * pValue 
);
```

### <a name="parameters"></a>Parámetros

*pValue*<br/>
Un puntero a un entero que se rellenará con el valor actual de la **_doserrno** macro global.

## <a name="return-value"></a>Valor devuelto

Si **_get_doserrno** se realiza correctamente, devuelve cero; en caso contrario, devuelve un código de error. Si *pValue* es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve **EINVAL**.

## <a name="remarks"></a>Comentarios

El **_doserrno** macro global está establecida en cero durante la inicialización de CRT, antes de proceso comienza la ejecución. Se establece en el valor de error de sistema operativo devuelto por una llamada de función de nivel de sistema que devuelve un error de sistema operativo, y nunca se restablece a cero durante la ejecución. Al escribir código para comprobar el valor de error devuelto por una función, desactive siempre **_doserrno** utilizando [_set_doserrno](set-doserrno.md) antes de la llamada de función. Porque otra llamada de función sobrescriba **_doserrno**, compruebe el valor mediante el uso de **_get_doserrno** inmediatamente después de la llamada de función.

Se recomienda [_get_errno](get-errno.md) en lugar de **_get_doserrno** para códigos de error portátil.

Los valores posibles de **_doserrno** se definen en \<errno.h >.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h>, \<cerrno> (C++)|

**_get_doserrno** es una extensión de Microsoft. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>

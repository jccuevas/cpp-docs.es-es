---
title: _get_doserrno
ms.date: 11/04/2016
api_name:
- _get_doserrno
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
- _get_doserrno
- get_doserrno
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
ms.openlocfilehash: 2810ead8bdd7d6c77cb2b55f4f97371bfc9751e6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956037"
---
# <a name="_get_doserrno"></a>_get_doserrno

Obtiene el valor de error devuelto por el sistema operativo antes de traducirlo a un valor **errno** .

## <a name="syntax"></a>Sintaxis

```C
errno_t _get_doserrno(
   int * pValue
);
```

### <a name="parameters"></a>Parámetros

*pValue*<br/>
Un puntero a un entero que se va a rellenar con el valor actual de la macro global **_doserrno** .

## <a name="return-value"></a>Valor devuelto

Si **_get_doserrno** se ejecuta correctamente, devuelve cero; Si se produce un error, devuelve un código de error. Si *pValue* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** en **EINVAL** y devuelve **EINVAL**.

## <a name="remarks"></a>Comentarios

La macro global **_doserrno** se establece en cero durante la inicialización de CRT, antes de que comience la ejecución del proceso. Se establece en el valor de error de sistema operativo devuelto por una llamada de función de nivel de sistema que devuelve un error de sistema operativo, y nunca se restablece a cero durante la ejecución. Al escribir código para comprobar el valor de error devuelto por una función, borre siempre **_doserrno** mediante [_set_doserrno](set-doserrno.md) antes de la llamada de función. Dado que otra llamada de función puede sobrescribir **_doserrno**, compruebe el valor mediante **_get_doserrno** inmediatamente después de la llamada de función.

Se recomienda [_get_errno](get-errno.md) en lugar de **_get_doserrno** para los códigos de error portables.

Los valores posibles de **_doserrno** se definen \<en errno. h >.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h>, \<cerrno> (C++)|

**_get_doserrno** es una extensión de Microsoft. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>

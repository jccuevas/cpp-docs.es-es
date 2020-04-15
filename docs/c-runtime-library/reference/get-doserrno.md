---
title: _get_doserrno
ms.date: 4/2/2020
api_name:
- _get_doserrno
- _o__get_doserrno
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 2d5d4e224b39e9fa597e12975d27fa5720fbfbc7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345253"
---
# <a name="_get_doserrno"></a>_get_doserrno

Obtiene el valor de error devuelto por el sistema operativo antes de que se traduzca en un valor **errno.**

## <a name="syntax"></a>Sintaxis

```C
errno_t _get_doserrno(
   int * pValue
);
```

### <a name="parameters"></a>Parámetros

*pValue*<br/>
Puntero a un entero que se va a rellenar con el valor actual de la **_doserrno** macro global.

## <a name="return-value"></a>Valor devuelto

Si **_get_doserrno** se realiza correctamente, devuelve cero; si se produce un error, devuelve un código de error. Si *pValue* es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno en** **EINVAL** y devuelve **EINVAL**.

## <a name="remarks"></a>Observaciones

La macro global **_doserrno** se establece en cero durante la inicialización de CRT, antes de que comience la ejecución del proceso. Se establece en el valor de error de sistema operativo devuelto por una llamada de función de nivel de sistema que devuelve un error de sistema operativo, y nunca se restablece a cero durante la ejecución. Al escribir código para comprobar el valor de error devuelto por una función, desactive siempre **_doserrno** mediante [_set_doserrno](set-doserrno.md) antes de la llamada de función. Dado que otra llamada de función puede sobrescribir **_doserrno**, compruebe el valor mediante **_get_doserrno** inmediatamente después de la llamada de función.

Recomendamos [_get_errno](get-errno.md) en lugar de **_get_doserrno** para códigos de error portátiles.

Los valores **_doserrno** posibles de \<_doserrno se definen en errno.h>.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h>, \<cerrno> (C++)|

**_get_doserrno** es una extensión de Microsoft. Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>

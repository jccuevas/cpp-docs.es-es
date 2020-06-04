---
title: _get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler
ms.date: 4/2/2020
api_name:
- _get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- _o__get_invalid_parameter_handler
- _o__get_thread_local_invalid_parameter_handler
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_invalid_parameter_handler
- stdlib/_get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- stdlib/_get_thread_local_invalid_parameter_handler
helpviewer_keywords:
- _get_thread_local_invalid_parameter_handler function
- _get_invalid_parameter_handler function
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
ms.openlocfilehash: 27e42c9f3f570b24df8fa2a26798b3dc3fa326b3
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909896"
---
# <a name="_get_invalid_parameter_handler-_get_thread_local_invalid_parameter_handler"></a>_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler

Obtiene la función a la que se llama cuando CRT detecta un argumento no válido.

## <a name="syntax"></a>Sintaxis

```C
_invalid_parameter_handler _get_invalid_parameter_handler(void);
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);
```

## <a name="return-value"></a>Valor devuelto

Un puntero a la función de controlador de parámetros no válidos establecida actualmente o un puntero nulo si no se ha establecido ninguna.

## <a name="remarks"></a>Observaciones

La función **_get_invalid_parameter_handler** obtiene el controlador global de parámetros no válidos que se ha establecido actualmente. Devuelve un puntero nulo si no se ha establecido ningún controlador global de parámetros no válidos. Del mismo modo, el **_get_thread_local_invalid_parameter_handler** obtiene el controlador de parámetros no válidos local del subproceso del subproceso en el que se llama o un puntero nulo si no se ha establecido ningún controlador. Para obtener información sobre cómo establecer controladores de parámetros no válidos globales y locales para el subproceso, consulte [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

El puntero de función de controlador de parámetros no válidos devuelto tiene el siguiente tipo:

```C
typedef void (__cdecl* _invalid_parameter_handler)(
    wchar_t const*,
    wchar_t const*,
    wchar_t const*,
    unsigned int,
    uintptr_t
    );
```

Para obtener información sobre el controlador de parámetros no válidos, consulte el prototipo en [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_invalid_parameter_handler**, **_get_thread_local_invalid_parameter_handler**|C: \<stdlib.h><br /><br /> C++: \<cstdlib> o \<stdlib.h>|

Las funciones **_get_invalid_parameter_handler** y **_get_thread_local_invalid_parameter_handler** son específicas de Microsoft. Para obtener información sobre la compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Versiones de funciones de CRT con seguridad mejorada](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>

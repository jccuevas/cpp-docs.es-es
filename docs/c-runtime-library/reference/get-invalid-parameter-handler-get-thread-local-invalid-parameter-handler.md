---
title: _get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler
ms.date: 11/04/2016
api_name:
- _get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
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
- _get_invalid_parameter_handler
- stdlib/_get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- stdlib/_get_thread_local_invalid_parameter_handler
helpviewer_keywords:
- _get_thread_local_invalid_parameter_handler function
- _get_invalid_parameter_handler function
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
ms.openlocfilehash: 534590fed77fe06149db892d98ba0e555297ac7c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955834"
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

## <a name="remarks"></a>Comentarios

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

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_invalid_parameter_handler**, **_get_thread_local_invalid_parameter_handler**|C: \<stdlib.h><br /><br /> C++: \<cstdlib> o \<stdlib.h>|

Las funciones **_get_invalid_parameter_handler** y **_get_thread_local_invalid_parameter_handler** son específicas de Microsoft. Para obtener información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Versiones de funciones de CRT con seguridad mejorada](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>

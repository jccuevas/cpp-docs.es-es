---
title: _get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
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
- _get_invalid_parameter_handler
- stdlib/_get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- stdlib/_get_thread_local_invalid_parameter_handler
dev_langs:
- C++
helpviewer_keywords:
- _get_thread_local_invalid_parameter_handler function
- _get_invalid_parameter_handler function
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a3e4df593e027c77909f6d3d1ea7c7a106799a9
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="getinvalidparameterhandler-getthreadlocalinvalidparameterhandler"></a>_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler

Obtiene la función a la que se llama cuando CRT detecta un argumento no válido.

## <a name="syntax"></a>Sintaxis

```C
_invalid_parameter_handler _get_invalid_parameter_handler(void);
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);
```

## <a name="return-value"></a>Valor devuelto

Un puntero a la función de controlador de parámetros no válidos establecida actualmente o un puntero nulo si no se ha establecido ninguna.

## <a name="remarks"></a>Comentarios

El **_get_invalid_parameter_handler** función obtiene establecidos actualmente el controlador de parámetros no válidos global. Devuelve un puntero nulo si no se ha establecido ningún controlador global de parámetros no válidos. De forma similar, el **_get_thread_local_invalid_parameter_handler** Obtiene el controlador de parámetros no válidos locales del subproceso actual del subproceso se llama en o un puntero nulo si se ha establecido ningún controlador. Para obtener información sobre cómo establecer controladores de parámetros no válidos globales y locales para el subproceso, consulte [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

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

El **_get_invalid_parameter_handler** y **_get_thread_local_invalid_parameter_handler** funciones son específicas de Microsoft. Para obtener información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Versiones de funciones de CRT con seguridad mejorada](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>

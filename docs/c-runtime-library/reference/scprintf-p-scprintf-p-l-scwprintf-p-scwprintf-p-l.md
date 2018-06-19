---
title: _scprintf_p, _scprintf_p_l, _scwprintf_p, _scwprintf_p_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _scwprintf_p
- _scprintf_p_l
- _scwprintf_p_l
- _scprintf_p
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
apitype: DLLExport
f1_keywords:
- _scwprintf_p_l
- _sctprintf_p
- scprintf_p_l
- scprintf_p
- _sctprintf_p_l
- scwprintf_p
- _scprintf_p_l
- scwprintf_p_l
- _scprintf_p
- _scwprintf_p
dev_langs:
- C++
helpviewer_keywords:
- sctprintf_p_l function
- _scwprintf_p_l function
- scprintf_p_l function
- _scprintf_p function
- _scprintf_p_l function
- scprintf_p function
- sctprintf_p function
- _scwprintf_p function
- _sctprintf_p function
- scwprintf_p function
- scwprintf_p_l function
- _sctprintf_p_l function
ms.assetid: 8390d1e1-2826-47a4-851f-6635a88087cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2120eaaee5acfa3628650b5df1f03448ee282a91
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407189"
---
# <a name="scprintfp-scprintfpl-scwprintfp-scwprintfpl"></a>_scprintf_p, _scprintf_p_l, _scwprintf_p, _scwprintf_p_l

Devuelve el número de caracteres de la cadena con formato, con la capacidad de especificar el orden en que se usan los parámetros en dicha cadena.

## <a name="syntax"></a>Sintaxis

```C
int _scprintf_p(
   const char *format [,
   argument] ...
);
int _scprintf_p_l(
   const char *format,
   locale_t locale [,
   argument] ...
);
int _scwprintf_p (
   const wchar_t *format [,
   argument] ...
);
int _scwprintf_p _l(
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>Parámetros

*format*<br/>
Cadena de control de formato.

*Argumento*<br/>
Argumentos opcionales.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve el número de caracteres que se generarían si la cadena se fuera a imprimir o enviar a un archivo o búfer mediante los códigos de formato especificados. El valor devuelto no incluye el carácter nulo de finalización. **_scwprintf_p** realiza la misma función para los caracteres anchos.

La diferencia entre **_scprintf_p** y **_scprintf** es que **_scprintf_p** admite parámetros posicionales, lo que permite especificar el orden en que los argumentos se utilizan en la cadena de formato. Para obtener más información, consulte [printf_p (Parámetros de posición)](../../c-runtime-library/printf-p-positional-parameters.md).

Si *formato* es un **NULL** se invoca el puntero, el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1 y establecen **errno** a **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Cada *argumento* (si existe) se convierten según la especificación de formato correspondiente de *formato*. El formato consta de caracteres ordinarios y tiene el mismo formato y función que el *formato* argumento para [printf](printf-printf-l-wprintf-wprintf-l.md).

Las versiones de estas funciones con el **_l** sufijo son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.

> [!IMPORTANT]
> Asegúrese de que *format* no es una cadena definida por el usuario.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sctprintf_p**|**_scprintf_p**|**_scprintf_p**|**_scwprintf_p**|
|**_sctprintf_p_l**|**_scprintf_p_l**|**_scprintf_p_l**|**_scwprintf_p_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_scprintf_p**, **_scprintf_p_l**|\<stdio.h>|
|**_scwprintf_p**, **_scwprintf_p_l**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_scprintf, _scprintf_l, _scwprintf, _scwprintf_l](scprintf-scprintf-l-scwprintf-scwprintf-l.md)<br/>
[_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l](printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)<br/>

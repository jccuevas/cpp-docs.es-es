---
title: _ltoa_s, _ltow_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _ltoa_s
- _ltow_s
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
- _ltow_s
- _ltoa_s
- ltoa_s
- ltow_s
dev_langs:
- C++
helpviewer_keywords:
- converting integers
- _ltoa_s function
- ltow_s function
- long integer conversion to string
- converting numbers, to strings
- ltoa_s function
- _ltow_s function
ms.assetid: d7dc61ea-1ccd-412d-b262-555a58647386
caps.latest.revision: ''
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 181f03752a16f64329eb94ae0cd8fac091fa2987
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2018
---
# <a name="ltoas-ltows"></a>_ltoa_s, _ltow_s
Convierte un entero largo en cadena. Estas son versiones de [_ltoa, _ltow](../../c-runtime-library/reference/ltoa-ltow.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t _ltoa_s(  
    long value,  
    char *str,  
    size_t sizeOfstr,  
    int radix   
);  
errno_t _ltow_s(  
    long value,  
    wchar_t *str,  
    size_t sizeOfstr,  
    int radix   
);  
template <size_t size>  
errno_t _ltoa_s(  
    long value,  
    char (&str)[size],  
    int radix   
); // C++ only  
template <size_t size>  
errno_t _ltow_s(  
    long value,  
    wchar_t (&str)[size],  
    int radix   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 `value`  
 Número que se va a convertir.  
  
 `str`  
 Búfer de la cadena resultante.  
  
 `sizeOfstr`  
 Tamaño de `str` en bytes para `_ltoa_s` o en palabras para `_ltow_s`.  
  
 `radix`  
 Base de `value`.  
  
## <a name="return-value"></a>Valor devuelto  
 Cero si la función se realizó correctamente o si fue un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La función `_ltoa_s` convierte los dígitos de `value` en una cadena de caracteres terminada en un valor nulo y almacena el resultado (hasta 33 bytes) en `str`. El `radix` especifica el argumento de la base de `value`, que debe estar comprendido entre 2 y 36. Si `radix` es igual a 10 y `value` es negativo, el primer carácter de la cadena almacenada es el signo menos (-). `_ltow_s` es una versión con caracteres anchos de `_ltoa_s`; el segundo argumento de `_ltow_s` es una cadena de caracteres anchos.  
  
 Si `str` es un puntero `NULL` o `sizeOfstr` es menor o igual que cero, estas funciones invocan un controlador de parámetros no válidos, tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1 y establecen `errno` en `EINVAL`; si `value` o `str` están fuera del intervalo de un entero largo, estas funciones devuelven -1 y establecen `errno` en `ERANGE`.  
  
 En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_ltot_s`|`_ltoa_s`|`_ltoa_s`|`_ltow_s`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_ltoa_s`|\<stdlib.h>|  
|`_ltow_s`|\<stdlib.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [_itoa, _i64toa, _ui64toa, _itow, _i64tow, _ui64tow](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)   
 [_ultoa, _ultow](../../c-runtime-library/reference/ultoa-ultow.md)   
 [_ultoa_s, _ultow_s](../../c-runtime-library/reference/ultoa-s-ultow-s.md)
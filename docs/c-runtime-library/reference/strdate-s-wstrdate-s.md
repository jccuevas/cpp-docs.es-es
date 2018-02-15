---
title: _strdate_s, _wstrdate_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _strdate_s
- _wstrdate_s
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _strdate_s
- wstrdate_s
- _wstrdate_s
- strdate_s
- _tstrdate_s
dev_langs:
- C++
helpviewer_keywords:
- dates, copying
- tstrdate_s function
- wstrdate_s function
- _tstrdate_s function
- strdate_s function
- copying dates
- _strdate_s function
- _wstrdate_s function
ms.assetid: d41d8ea9-e5ce-40d4-864e-1ac29b455991
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e71476fbb1810505f0b50a04d20f6235ff727c92
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="strdates-wstrdates"></a>_strdate_s, _wstrdate_s
Copia la fecha actual del sistema en un búfer. Se trata de versiones de [_strdate, _wstrdate](../../c-runtime-library/reference/strdate-wstrdate.md) que incluyen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t _strdate_s(  
   char *buffer,  
   size_t numberOfElements  
);  
errno_t _wstrdate_s(  
   wchar_t *buffer,  
   size_t numberOfElements  
);  
template <size_t size>  
errno_t _strdate_s(  
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
errno_t _wstrdate_s(  
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `buffer`  
 Puntero a un búfer que se rellenará con la cadena de fecha con formato.  
  
 [in] `numberOfElements`  
 Tamaño del búfer.  
  
## <a name="return-value"></a>Valor devuelto  
 Cero si es correcto. Si se produce un error, el valor devuelto es un código de error. Los códigos de error se definen en ERRNO.H; consulte la tabla siguiente para ver los errores exactos generados por esta función. Para obtener más información sobre los códigos de error, vea [errno](../../c-runtime-library/errno-constants.md).  
  
## <a name="error-conditions"></a>Condiciones de error  
  
|`buffer`|`numberOfElements`|Volver|Contenido de `buffer`|  
|--------------|------------------------|------------|--------------------------|  
|`NULL`|(cualquiera)|`EINVAL`|No modificado|  
|No es `NULL` (apunta al búfer válido)|0|`EINVAL`|No modificado|  
|No es `NULL` (apunta al búfer válido)|0 < `numberOfElements` < 9|`EINVAL`|Cadena vacía|  
|No es `NULL` (apunta al búfer válido)|`numberOfElements` >= 9|0|Fecha actual con el formato especificado en la sección de comentarios|  
  
## <a name="security-issues"></a>Problemas de seguridad  
 Si se pasa un valor distinto de `NULL` no válido para el búfer, se producirá una infracción de acceso si el parámetro `numberOfElements` es mayor que 9.  
  
 Si se pasan valores de un tamaño que es mayor que el tamaño real de `buffer`, se producirá una saturación en el búfer.  
  
## <a name="remarks"></a>Comentarios  
 Estas funciones proporcionan versiones más seguras de `_strdate` y `_wstrdate`. La función `_strdate_s` copia la fecha del sistema actual en el búfer señalado por `buffer` con el formato `mm`/`dd`/`yy`, donde `mm` son dos dígitos que representan el mes, `dd` son dos dígitos que representan el día y `yy` son los dos últimos dígitos del año. Por ejemplo, la cadena `12/05/99` representa el 5 de diciembre de 1999. El búfer debe tener una longitud mínima de 9 caracteres.  
  
 `_wstrdate_s` es una versión con caracteres anchos de `_strdate_s`; el argumento y el valor devuelto de `_wstrdate_s` son cadenas de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.  
  
 Si `buffer` es un puntero `NULL` o si `numberOfElements` es inferior a 9 caracteres, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1 y establecen `errno` en `EINVAL` si el búfer es `NULL` o si `numberOfElements` es menor o igual a 0, o bien establecen `errno` en `ERANGE` si `numberOfElements` es inferior a 9.  
  
 En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mapping"></a>Asignación de rutina de texto genérico:  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstrdate_s`|`_strdate_s`|`_strdate_s`|`_wstrdate_s`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_strdate`|\<time.h>|  
|`_wstrdate`|\<time.h> o \<wchar.h>|  
|`_strdate_s`|\<time.h>|  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [time](../../c-runtime-library/reference/time-time32-time64.md).  
  
## <a name="see-also"></a>Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime, _mktime32, _mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)
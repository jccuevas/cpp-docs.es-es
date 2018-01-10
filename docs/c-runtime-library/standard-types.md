---
title: "Tipos estándar | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __time64_t
- _diskfree_t
- _CRT_DUMP_CLIENT
- _fsize_t
- __timeb64
- File
- __utimeb64
- jmp_buf
- __finddata64_t
- _wfinddata_t
- _finddata_t
- utimbuf64
- wint_t
- wctrans_t
- wctype_t
- _HFILE
- _secerr_handler_func
- clock_t
- fpos_t
- _dev_t
- time64_t
- wfinddata64_t
- stat64
- ldiv_t
- _EXCEPTION_POINTERS
- terminate_function
- size_t
- timeb64
- tm
- _HEAPINFO
- unexpected_function
- _CrtMemState
- _se_translator_function
- sig_atomic_t
- _CRT_REPORT_HOOK
- _complex
- _w_finddatai64_t
- _timeb
- _onexit_t
- _RTC_ErrorNumber
- lconv
- _PNH
- _off_t
- ptrdiff_t
- time_t
- _FPIEEE_RECORD
- _exception
- __w_finddata64_t
- __stat64
- _utimbuf
- __utimbuf64
- div_t
- _CRT_ALLOC_HOOK
- int8_t
- uint8_t
- int16_t
- uint16_t
- int32_t
- uint32_t
- int64_t
- int_least8_t
- uint_least8_t
- int_least16_t
- uint_least16_t
- int_least32_t
- uint_least32_t
- int_least64_t
- uint_least64_t
- int_fast8_t
- uint_fast8_t
- int_fast16_t
- uint_fast16_t
- int_fast32_t
- uint_fast32_t
- int_fast64_t
- uint_fast64_t
- intmax_t
- uintmax_t
dev_langs: C++
helpviewer_keywords:
- __timeb64 type
- tm type
- clock_t type
- intptr_t type
- diskfree_t type
- wctype_t type
- CRT_DUMP_CLIENT type
- sig_atomic_t type
- _PNH type
- time_t type
- wfinddata_t type
- timeb64
- CRT, standard types
- wint_t type
- _RTC_ErrorNumber type
- _diskfree_t type
- _dev_t type
- _wfinddata_t type
- HFILE type
- __utimbuf64 type
- div_t type
- _onexit_t type
- _secerr_handler_func type
- FPIEEE_RECORD type
- HEAPINFO type
- PNH type
- _CRT_ALLOC_HOOK type
- _se_translater_function type
- va_list type
- wctrans_t type
- secerr_handler_func type
- _locale_t type
- timeb type
- lconv type
- utimbuf type
- dev_t type
- unexpected_function typedef
- _complex type
- _off_t type
- off_t type
- RTC_ErrorNumber type
- _FPIEEE_RECORD type
- exception type
- _CRT_REPORT_HOOK type
- _HEAPINFO type
- ldiv_t type
- terminate_function type
- uintptr_t type
- _CRT_DUMP_CLIENT type
- _utimbuf type
- wfinddatai64_t type
- fpos_t type
- wchar_t type
- CRT_ALLOC_HOOK type
- _HFILE type
- __time64_t type
- _timeb type
- CrtMemState type
- __finddata64_t type
- _exception type
- stat type
- onexit_t type
- FILE constant
- _stat type
- finddata_t type
- __wfinddata64_t type
- ptrdiff_t type
- complex types
- _wfinddatai64_t type
- _EXCEPTION_POINTERS type
- jmp_buf type
- se_translater_function type
- size_t type
- EXCEPTION_POINTERS type
- __stat64 type
- _fsize_t type
- CRT_REPORT_HOOK type
- _finddata_t type
ms.assetid: 23312dd2-4a6a-4d70-9b48-2a5d0d8c9f28
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4fd51f03d9a4134ee7193d5aede410bb541cd19f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="standard-types"></a>Tipos estándar
La biblioteca en tiempo de ejecución de Microsoft define los siguientes tipos y definiciones de tipo estándar.  
  
### <a name="fixed-width-integral-types-stdinth"></a>Tipos enteros de ancho fijo (stdint.h)  
  
|nombre|Tipo integrado equivalente|  
|----------|-------------------------------|  
|int8\_t, uint8\_t|signed char, unsigned char|  
|int16\_t, uint16\_t|short, unsigned short|  
|int32\_t, uint32\_t|int, unsigned int|  
|int64\_t, uint64\_t|long long, unsigned long long|  
|int_least8_t, uint_least8_t|signed char, unsigned char|  
|int_least16_t, uint_least16_t|short, unsigned short|  
|int_least32_t, uint_least32_t|int, unsigned int|  
|int_least64_t, uint_least64_t|long long, unsigned long long|  
|int_fast8_t, uint_fast8_t|signed char, unsigned char|  
|int_fast16_t, uint_fast16_t|int, unsigned int|  
|int_fast32_t, uint_fast32_t|int, unsigned int|  
|int_fast64_t, uint_fast64_t|long long, unsigned long long|  
|intmax_t, uintmax_t|long long, unsigned long long|  
  
|Tipo|Description|Declarado en|  
|----------|-----------------|-----------------|  
|`clock_t` (long)|Almacena valores de hora. Usado por [clock](../c-runtime-library/reference/clock.md).|TIME.H|  
|`_complex` (estructura)|Almacena partes reales e imaginarias de números complejos. Usado por [_cabs](../c-runtime-library/reference/cabs.md).|MATH.H|  
|`_CRT_ALLOC_HOOK`|Definición de tipo para la función de enlace definida por el usuario. Se usa en [_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md).|CRTDBG.H|  
|`_CRT_DUMP_CLIENT`,<br /><br /> `_CRT_DUMP_CLIENT_M`|Definición de tipo para una función de devolución de llamada a la que se llamará en [_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md).|CRTDBG.H|  
|`_CrtMemState` (estructura)|Proporciona información sobre el estado actual del montón de depuración en tiempo de ejecución de C.|CRTDBG.H|  
|`_CRT_REPORT_HOOK`,<br /><br /> `_CRT_REPORT_HOOKW`,<br /><br /> `_CRT_REPORT_HOOKW_M`|Definición de tipo para una función de devolución de llamada a la que se llamará en [_CrtDbgReport](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).<br /><br /> Los parámetros para esta función son: tipo de informe, mensaje de salida y el valor devuelto de la función de devolución de llamada.|CRTDBG.H|  
|`dev_t`, `_dev_t` corto o entero sin signo|Representa identificadores de dispositivo.|SYS\TYPES.H|  
|`_diskfree_t` (estructura)|Contiene información sobre una unidad de disco. Utilizado por [_getdiskfree](../c-runtime-library/reference/getdiskfree.md)**.**|DOS.H y DIRECT.H|  
|Estructuras de `div_t`, `ldiv_t` y `lldiv_t`|Almacena los valores devueltos por [div](../c-runtime-library/reference/div.md), [ldiv](../c-runtime-library/reference/ldiv-lldiv.md) y [lldiv](../c-runtime-library/reference/ldiv-lldiv.md), respectivamente.|STDLIB.H|  
|Entero de `errno_t`|Se usa para un tipo de valor devuelto o un parámetro de la función que se ocupa de los códigos de error de `errno`.|STDDEF.H,<br /><br /> CRTDEFS.H|  
|`_exception` (estructura)|Almacena información de error para [_matherr](../c-runtime-library/reference/matherr.md).|MATH.H|  
|`_EXCEPTION_POINTERS`|Contiene un registro de excepciones. Para más información, vea [EXCEPTION_POINTERS](http://msdn.microsoft.com/library/windows/desktop/ms679331).|FPIEEE.H|  
|`FILE` (estructura)|Almacena información sobre el estado actual del flujo; se usa en todas las operaciones de E/S de flujo.|STDIO.H|  
|Estructuras de `_finddata_t`, `_wfinddata_t`, `_finddata32_t`, `_wfinddata32_t`, `_finddatai64_t`, `_wfinddatai64_t`, `__finddata64_t`, `__wfinddata64_t`, `__finddata32i64_t`, `__wfinddata32i64_t`, `__finddata64i32_t` y `__wfinddata64i32_t`|Almacena información de atributos de archivo devuelta por [_findfirst, _wfindfirst y por funciones relacionadas](../c-runtime-library/reference/findfirst-functions.md) y [_findnext, _wfindnext y por funciones relacionadas](../c-runtime-library/reference/findnext-functions.md). Vea [Funciones de búsqueda de nombre de archivo](../c-runtime-library/filename-search-functions.md) para obtener información sobre los miembros de la estructura.|IO.H, WCHAR.H|  
|`_FPIEEE_RECORD` (estructura)|Contiene información sobre la excepción de punto flotante del IEEE; [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md) la pasa al controlador de interceptaciones definido por el usuario.|FPIEEE.H|  
|`fpos_t` (entero largo, `__int64` o estructura, según la plataforma de destino)|Usado por [fgetpos](../c-runtime-library/reference/fgetpos.md) y [fsetpos](../c-runtime-library/reference/fsetpos.md) para registrar información que identifica de forma única cada posición dentro de un archivo.|STDIO.H|  
|`_fsize_t` (entero largo sin signo)|Se usa para representar el tamaño de un archivo.|IO.H,<br /><br /> WCHAR.H|  
|`_HEAPINFO` (estructura)|Contiene información sobre la siguiente entrada de montón para [_heapwalk](../c-runtime-library/reference/heapwalk.md).|MALLOC.H|  
|`_HFILE` (void*)|Identificador de archivo del sistema operativo.|CRTDBG.H|  
|`imaxdiv_t`|Tipo de valor devuelto por la función [imaxdiv](../c-runtime-library/reference/imaxdiv.md), que contiene el cociente y el resto.|inttypes.h|  
|`ino_t`, `_ino_t` (entero corto sin signo)|Se usa para devolver información de estado.|WCHAR.H|  
|`intmax_t`|Tipo entero con signo que puede representar cualquier valor de cualquier tipo de entero con signo.|stdint.h|  
|`intptr_t` (entero largo o `__int64`, según la plataforma de destino)|Almacena un puntero (o identificador) en las plataformas de Win32 y Win64.|STDDEF.H y otros archivos de inclusión|  
|Matriz `jmp_buf`|Usado por [setjmp](../c-runtime-library/reference/setjmp.md) y [longjmp](../c-runtime-library/reference/longjmp.md) para guardar y restaurar el entorno del programa.|SETJMP.H|  
|`lconv` (estructura)|Contiene reglas de formato para valores numéricos en distintos países o regiones. Usado por [localeconv](../c-runtime-library/reference/localeconv.md).|LOCALE.H|  
|`_LDOUBLE`,<br /><br /> `_LONGDOUBLE`,<br /><br /> `_LDBL12` (doble largo o matriz de caracteres sin signo)|Se usa para representar un valor doble largo.|STDLIB.H|  
|`_locale_t` (estructura)|Almacena valores de la configuración regional actual. Se usa en todas las bibliotecas en tiempo de ejecución de C específicas de la configuración regional.|CRTDEF.H|  
|`mbstate_t`|Realiza el seguimiento del estado de una conversión de caracteres multibyte.|WCHAR.H|  
|Entero largo de `off_t`, `_off_t`|Representa el valor de desplazamiento de archivo.|WCHAR.H, SYS\TYPES.H|  
|`_onexit_t`,<br /><br /> Puntero `_onexit_m_t`|Devuelto por [_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md).|STDLIB.H|  
|Puntero `_PNH` a función|Tipo de argumento de [_set_new_handler](../c-runtime-library/reference/set-new-handler.md).|NEW.H|  
|`ptrdiff_t` (entero largo o `__int64`, según la plataforma de destino)|Resultado de la resta de dos punteros.|CRTDEFS.H|  
|`_purecall_handler`,<br /><br /> `_purecall_handler_m`|Definición de tipo para una función de devolución de llamada que se llama cuando se llama a una función virtual pura. Usada por [_get_purecall_handler, _set_purecall_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md). Una función `_purecall_handler` debe tener un tipo de valor devuelto void.|STDLIB.H|  
|Definición de tipo de `_RTC_error_fn`|Definición de tipo para una función que controla las comprobaciones de errores en tiempo de ejecución. Se usa en [_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md).|RTCAPI.H|  
|Definición de tipo de `_RTC_error_fnW`|Definición de tipo para una función que controla las comprobaciones de errores en tiempo de ejecución. Se usa en [_RTC_SetErrorFuncW](../c-runtime-library/reference/rtc-seterrorfuncw.md).|RTCAPI.H|  
|Enumeración `_RTC_ErrorNumber`|Define condiciones de error para [_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md) y [_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md).|RTCAPI.H|  
|`_se_translator_function`|Definición de tipo para una función de devolución de llamada que convierte una excepción. El primer parámetro es el código de excepción y el segundo es el registro de la excepción. Usada por [_set_se_translator](../c-runtime-library/reference/set-se-translator.md).|EH.H|  
|Entero de `sig_atomic_t`|Tipo de objeto que se puede modificar como entidad atómica, incluso en presencia de interrupciones asincrónicas; se usa con [signal](../c-runtime-library/reference/signal.md).|SIGNAL.H|  
|`size_t` (__int64 sin signo o entero sin signo, según la plataforma de destino)|Resultado del operador de `sizeof`.|CRTDEFS.H y otros archivos de inclusión|  
|`_stat` (estructura)|Contiene información de estado de archivo devuelta por [_stat](../c-runtime-library/reference/stat-functions.md) y [_fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md).|SYS\STAT.H|  
|`__stat64` (estructura)|Contiene información de estado de archivo devuelta por [_fstat64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md), [_stat64](../c-runtime-library/reference/stat-functions.md) y [_wstat64](../c-runtime-library/reference/stat-functions.md).|SYS\STAT.H|  
|`_stati64` (estructura)|Contiene información de estado de archivo devuelta por [_fstati64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md), [_stati64](../c-runtime-library/reference/stat-functions.md) y [_wstati64](../c-runtime-library/reference/stat-functions.md).|SYS\STAT.H|  
|Definición de tipo de `terminate_function`|Definición de tipo para una función de devolución de llamada a la que se llama cuando se llama a [terminate](../c-runtime-library/reference/terminate-crt.md). Usada por [set_terminate](../c-runtime-library/reference/set-terminate-crt.md).|EH.H|  
|`time_t` (__int64 o entero largo)|Representa valores de hora en [mktime](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [time](../c-runtime-library/reference/time-time32-time64.md), [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) y [gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md). Número de segundos desde el 1 de enero de 1970, 0:00 UTC. Si se define _USE_32BIT_TIME_T, `time_t` es un entero largo. Si no se define, es un entero de 64 bits.|TIME.H,<br /><br /> SYS\STAT.H,<br /><br /> SYS\TIMEB.H|  
|`__time32_t` (entero largo)|Representa valores de hora en [mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) y [localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md).|CRTDEFS.H, SYS\STAT.H,<br /><br /> SYS\TIMEB.H|  
|`__time64_t` (`__int64`)|Representa valores de hora en [mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [_ctime64, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md) y [_time64](../c-runtime-library/reference/time-time32-time64.md).|TIME.H,<br /><br /> SYS\STAT.H,<br /><br /> SYS\TIMEB.H|  
|`_timeb` (estructura)|Usado por [_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md) y [_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) para almacenar la hora del sistema actual.|SYS\TIMEB.H|  
|`__timeb32` (estructura)|Usado por [_ftime, _ftime32, _ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) y [_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) para almacenar la hora del sistema actual.|SYS\TIMEB.H|  
|`__timeb64` (estructura)|Usado por [_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) y [_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) para almacenar la hora del sistema actual.|SYS\TIMEB.H|  
|`tm` (estructura)|Usado por [asctime, _wasctime](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s, _wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md), [gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime_s, _gmtime32_s, _gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md), [localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime_s, _localtime32_s, _localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), [mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md) y [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para almacenar y recuperar información de hora.|TIME.H|  
|`uintmax_t`|Tipo entero sin signo que puede representar cualquier valor de cualquier tipo de entero sin signo.|stdint.h|  
|`uintptr_t` (entero largo o `__int64`, según la plataforma de destino)|Entero sin signo o una versión __int64 sin signo de `intptr_t`.|STDDEF.H y otros archivos de inclusión|  
|`unexpected_function`|Definición de tipo para una función de devolución de llamada a la que se llama cuando se llama a [unexpected](../c-runtime-library/reference/unexpected-crt.md). Usada por [set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md).|EH.H|  
|`_utimbuf` (estructura)|Almacena las horas de acceso a archivos y su modificación usadas por [_utime, _wutime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) y [_futime, _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md) para cambiar las fechas de modificación del archivo.|SYS\UTIME.H|  
|`_utimbuf32` (estructura)|Almacena las horas de acceso a archivos y su modificación usadas por [_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) y [_futime, _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md) para cambiar las fechas de modificación del archivo.|SYS\UTIME.H|  
|`__utimbuf64` (estructura)|Usado por [_utime64, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) y [_futime64](../c-runtime-library/reference/futime-futime32-futime64.md) para almacenar la hora actual.|SYS\UTIME.H|  
|`va_list` (estructura)|Se usa para contener la información que necesitan las macros [va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) y [va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). La función a la que se llama declara la variable de tipo `va_list` que se puede pasar como argumento a otra función.|STDARG.H,<br /><br /> CRTDEFS.H|  
|carácter ancho de `wchar_t`|Útil para escribir programas portables para mercados internacionales.|STDDEF.H, STDLIB.H,<br /><br /> CRTDEFS.H,<br /><br /> SYS\STAT.H|  
|Entero de `wctrans_t`|Representa asignaciones de caracteres específicas de la configuración regional.|WCTYPE.H|  
|Entero de `wctype_t`|Puede representar todos los caracteres del juego de caracteres de cualquier idioma.|WCHAR.H,<br /><br /> CRTDEFS.H|  
|Entero de `wint_t`|Tipo de objeto de datos que puede contener cualquier carácter ancho o valor final de archivo ancho.|WCHAR.H,<br /><br /> CRTDEFS.H|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la biblioteca en tiempo de ejecución de C](../c-runtime-library/c-run-time-library-reference.md)

---
title: "Tipos est&#225;ndar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__time64_t"
  - "_diskfree_t"
  - "_CRT_DUMP_CLIENT"
  - "_fsize_t"
  - "__timeb64"
  - "File"
  - "__utimeb64"
  - "jmp_buf"
  - "__finddata64_t"
  - "_wfinddata_t"
  - "_finddata_t"
  - "utimbuf64"
  - "wint_t"
  - "wctrans_t"
  - "wctype_t"
  - "_HFILE"
  - "_secerr_handler_func"
  - "clock_t"
  - "fpos_t"
  - "_dev_t"
  - "time64_t"
  - "wfinddata64_t"
  - "stat64"
  - "ldiv_t"
  - "_EXCEPTION_POINTERS"
  - "terminate_function"
  - "size_t"
  - "timeb64"
  - "tm"
  - "_HEAPINFO"
  - "unexpected_function"
  - "_CrtMemState"
  - "_se_translator_function"
  - "sig_atomic_t"
  - "_CRT_REPORT_HOOK"
  - "_complex"
  - "_w_finddatai64_t"
  - "_timeb"
  - "_onexit_t"
  - "_RTC_ErrorNumber"
  - "lconv"
  - "_PNH"
  - "_off_t"
  - "ptrdiff_t"
  - "time_t"
  - "_FPIEEE_RECORD"
  - "_exception"
  - "__w_finddata64_t"
  - "__stat64"
  - "_utimbuf"
  - "__utimbuf64"
  - "div_t"
  - "_CRT_ALLOC_HOOK"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__finddata64_t (tipo)"
  - "__stat64 (tipo)"
  - "__time64_t (tipo)"
  - "__timeb64 (tipo)"
  - "__utimbuf64 (tipo)"
  - "__wfinddata64_t (tipo)"
  - "_complex (tipo)"
  - "_CRT_ALLOC_HOOK (tipo)"
  - "_CRT_DUMP_CLIENT (tipo)"
  - "_CRT_REPORT_HOOK (tipo)"
  - "_dev_t (tipo)"
  - "_diskfree_t (tipo)"
  - "_exception (tipo)"
  - "_EXCEPTION_POINTERS (tipo)"
  - "_finddata_t (tipo)"
  - "_FPIEEE_RECORD (tipo)"
  - "_fsize_t (tipo)"
  - "_HEAPINFO (tipo)"
  - "_HFILE (tipo)"
  - "_locale_t (tipo)"
  - "_off_t (tipo)"
  - "_onexit_t (tipo)"
  - "_PNH (tipo)"
  - "_RTC_ErrorNumber (tipo)"
  - "_se_translater_function (tipo)"
  - "_secerr_handler_func (tipo)"
  - "_stat (tipo)"
  - "_timeb (tipo)"
  - "_utimbuf (tipo)"
  - "_wfinddata_t (tipo)"
  - "_wfinddatai64_t (tipo)"
  - "clock_t (tipo)"
  - "tipos complejos"
  - "CRT, tipos estándar"
  - "CRT_ALLOC_HOOK (tipo)"
  - "CRT_DUMP_CLIENT (tipo)"
  - "CRT_REPORT_HOOK (tipo)"
  - "CrtMemState (tipo)"
  - "dev_t (tipo)"
  - "diskfree_t (tipo)"
  - "div_t (tipo)"
  - "tipo de excepción"
  - "EXCEPTION_POINTERS (tipo)"
  - "FILE (constante)"
  - "finddata_t (tipo)"
  - "FPIEEE_RECORD (tipo)"
  - "fpos_t (tipo)"
  - "HEAPINFO (tipo)"
  - "HFILE (tipo)"
  - "intptr_t (tipo)"
  - "jmp_buf (tipo)"
  - "lconv (tipo)"
  - "ldiv_t (tipo)"
  - "off_t (tipo)"
  - "onexit_t (tipo)"
  - "PNH (tipo)"
  - "ptrdiff_t (tipo)"
  - "RTC_ErrorNumber (tipo)"
  - "se_translater_function (tipo)"
  - "secerr_handler_func (tipo)"
  - "sig_atomic_t (tipo)"
  - "size_t (tipo)"
  - "stat (tipo)"
  - "terminate_function (tipo)"
  - "time_t (tipo)"
  - "timeb (tipo)"
  - "timeb64"
  - "tm (tipo)"
  - "uintptr_t (tipo)"
  - "unexpected_function (typedef)"
  - "utimbuf (tipo)"
  - "va_list (tipo)"
  - "wchar_t (tipo)"
  - "wctrans_t (tipo)"
  - "wctype_t (tipo)"
  - "wfinddata_t (tipo)"
  - "wfinddatai64_t (tipo)"
  - "wint_t (tipo)"
ms.assetid: 23312dd2-4a6a-4d70-9b48-2a5d0d8c9f28
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# Tipos est&#225;ndar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La biblioteca en tiempo de ejecución de Microsoft define los siguientes tipos y definiciones de tipo estándar.  
  
### Tipos enteros de ancho fijo \(stdint.h\)  
  
|Nombre|Tipo integrado equivalente|  
|------------|--------------------------------|  
|int8\_t, uint8\_t|signed char, unsigned char|  
|int16\_t, int16\_t|short, unsigned short|  
|int32\_t, uint32\_t|int, unsigned int|  
|int64\_t, int64\_t|long long, unsigned long long|  
|int\_least8\_t, uint\_least8\_t|signed char, unsigned char|  
|int\_least16\_t, uint\_least16\_t|short, unsigned short|  
|int\_least32\_t, uint\_least32\_t|int, unsigned int|  
|int\_least64\_t, uint\_least64\_t|long long, unsigned long long|  
|int\_fast8\_t, uint\_fast8\_t|signed char, unsigned char|  
|int\_fast16\_t, uint\_fast16\_t|int, unsigned int|  
|int\_fast32\_t, uint\_fast32\_t|int, unsigned int|  
|int\_fast64\_t, uint\_fast64\_t|long long, unsigned long long|  
|intmax\_t, uintmax\_t|long long, unsigned long long|  
  
|Tipo|Descripción|Declarado en|  
|----------|-----------------|------------------|  
|`clock_t` \(long\)|Almacena valores de hora. Usado por [clock](../c-runtime-library/reference/clock.md).|TIME.H|  
|`_complex` \(estructura\)|Almacena partes reales e imaginarias de números complejos. Usado por [\_cabs](../c-runtime-library/reference/cabs.md).|MATH.H|  
|`_CRT_ALLOC_HOOK`|Definición de tipo para la función de enlace definida por el usuario.  Se usa en [\_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md).|CRTDBG.H|  
|`_CRT_DUMP_CLIENT`,<br /><br /> `_CRT_DUMP_CLIENT_M`|Definición de tipo para una función de devolución de llamada al que se llamará en [\_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md).|CRTDBG.H|  
|`_CrtMemState` \(estructura\)|Proporciona información sobre el estado actual del montón de depuración en tiempo de ejecución de C.|CRTDBG.H|  
|`_CRT_REPORT_HOOK`,<br /><br /> `_CRT_REPORT_HOOKW`,<br /><br /> `_CRT_REPORT_HOOKW_M`|Definición de tipo para una función de devolución de llamada a la que se llamará en [\_CrtDbgReport](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).<br /><br /> Los parámetros para esta función son: tipo de informe, mensaje de salida y el valor devuelto de la función de devolución de llamada.|CRTDBG.H|  
|`dev_t`, `_dev_t` corto o entero sin signo|Representa identificadores de dispositivo.|SYS\\TYPES.H|  
|`_diskfree_t` estructura|Contiene información sobre una unidad de disco.  Utilizado por [\_getdiskfree](../c-runtime-library/reference/getdiskfree.md)**.**|DOS.H y DIRECT.H|  
|Estructuras de `div_t`, `ldiv_t` y `lldiv_t`|Almacena los valores devueltos por [div](../c-runtime-library/reference/div.md), [ldiv](../c-runtime-library/reference/ldiv-lldiv.md) y [lldiv](../c-runtime-library/reference/ldiv-lldiv.md), respectivamente.|STDLIB.H|  
|Entero de `errno_t`|Se usa para un tipo de valor devuelto o un parámetro de la función que se ocupa de los códigos de error de `errno`.|STDDEF.H,<br /><br /> CRTDEFS.H|  
|`_exception` \(estructura\)|Almacena información de error para [\_matherr](../c-runtime-library/reference/matherr.md).|MATH.H|  
|`_EXCEPTION_POINTERS`|Contiene un registro de excepciones.  Para obtener más información, vea [EXCEPTION\_POINTERS](http://msdn.microsoft.com/library/windows/desktop/ms679331).|FPIEEE.H|  
|`FILE` estructura|Almacena información sobre el estado actual del flujo; se usa en todas las operaciones de E\/S de flujo.|STDIO.H|  
|Estructuras de `_finddata_t`, `_wfinddata_t`, `_finddata32_t`, `_wfinddata32_t`, `_finddatai64_t`, `_wfinddatai64_t`, `__finddata64_t`, `__wfinddata64_t`, `__finddata32i64_t`, `__wfinddata32i64_t`, `__finddata64i32_t` y `__wfinddata64i32_t`|Almacena información de atributos de archivo devuelta por [\_findfirst, \_wfindfirst y funciones relacionadas](../c-runtime-library/reference/findfirst-functions.md) y [\_findnext, \_wfindnext y funciones relacionadas](../c-runtime-library/reference/findnext-functions.md).  Vea [Funciones de búsqueda de nombre de archivo](../c-runtime-library/filename-search-functions.md) para obtener información sobre los miembros de la estructura.|IO.H, WCHAR.H|  
|`_FPIEEE_RECORD` estructura|Contiene información sobre la excepción de punto flotante del IEEE;  [\_fpieee\_flt](../c-runtime-library/reference/fpieee-flt.md) la pasa al controlador de interceptaciones definido por el usuario.|FPIEEE.H|  
|`fpos_t` \(entero largo, `__int64` o estructura, según la plataforma de destino\)|Usado por [fgetpos](../c-runtime-library/reference/fgetpos.md) y [fsetpos](../c-runtime-library/reference/fsetpos.md) para registrar información que identifica de forma única cada posición dentro de un archivo.|STDIO.H|  
|`_fsize_t` \(entero largo sin signo\)|Se usa para representar el tamaño de un archivo.|IO.H,<br /><br /> WCHAR.H|  
|`_HEAPINFO` \(estructura\)|Contiene información sobre la siguiente entrada del montón para [\_heapwalk](../c-runtime-library/reference/heapwalk.md).|MALLOC.H|  
|`_HFILE` \(void\*\)|Identificador de archivo del sistema operativo.|CRTDBG.H|  
|`imaxdiv_t`|Tipo de valor devuelto por la función [imaxdiv](../c-runtime-library/reference/imaxdiv.md) , que contiene el cociente y el resto.|inttypes.h|  
|`ino_t`, `_ino_t` \(entero corto sin signo\)|Se usa para devolver información de estado.|WCHAR.H|  
|`intmax_t`|Tipo entero con signo que puede representar cualquier valor de cualquier tipo de entero con signo.|stdint.h|  
|`intptr_t` \(entero largo o `__int64`, según la plataforma de destino\)|Almacena un puntero \(o identificador\) en las plataformas de Win32 y Win64.|STDDEF.H y otros archivos de inclusión|  
|Matriz `jmp_buf`|Usado por [setjmp](../c-runtime-library/reference/setjmp.md) y [longjmp](../c-runtime-library/reference/longjmp.md) para guardar y restaurar el entorno del programa.|SETJMP.H|  
|`lconv` \(estructura\)|Contiene reglas de formato para valores numéricos en distintos países o regiones.  Usado por [localeconv](../c-runtime-library/reference/localeconv.md).|LOCALE.H|  
|`_LDOUBLE`,<br /><br /> `_LONGDOUBLE`,<br /><br /> `_LDBL12` \(doble largo o matriz de caracteres sin signo\)|Se usa para representar un valor doble largo.|STDLIB.H|  
|`_locale_t` \(estructura\)|Almacena valores de la configuración regional actual. Se usa en todas las bibliotecas en tiempo de ejecución de C específicas de la configuración regional.|CRTDEF.H|  
|`mbstate_t`|Realiza el seguimiento del estado de una conversión de caracteres multibyte.|WCHAR.H|  
|Entero largo de `off_t`, `_off_t`|Representa el valor de desplazamiento de archivo.|WCHAR.H, SYS\\TYPES.H|  
|`_onexit_t`,<br /><br /> Puntero `_onexit_m_t`|Devuelto por [\_onexit, \_onexit\_m](../c-runtime-library/reference/onexit-onexit-m.md).|STDLIB.H|  
|Puntero `_PNH` a función|Tipo de argumento de [\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md).|NEW.H|  
|`ptrdiff_t` \(entero largo o `__int64`, según la plataforma de destino\)|Resultado de la resta de dos punteros.|CRTDEFS.H|  
|`_purecall_handler`,<br /><br /> `_purecall_handler_m`|Definición de tipo para una función de devolución de llamada que se llama cuando se llama a una función virtual pura.  Usado por [\_get\_purecall\_handler, \_set\_purecall\_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md).  Una función `_purecall_handler` debe tener un tipo de valor devuelto void.|STDLIB.H|  
|Definición de tipo de `_RTC_error_fn`|Definición de tipo para una función que controla las comprobaciones de errores en tiempo de ejecución.  Se usa en [\_RTC\_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md).|RTCAPI.H|  
|Definición de tipo de `_RTC_error_fnW`|Definición de tipo para una función que controla las comprobaciones de errores en tiempo de ejecución.  Se usa en [\_RTC\_SetErrorFuncW](../c-runtime-library/reference/rtc-seterrorfuncw.md).|RTCAPI.H|  
|Enumeración `_RTC_ErrorNumber`|Define condiciones de error para [\_RTC\_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md) y [\_RTC\_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md).|RTCAPI.H|  
|`_se_translator_function`|Definición de tipo para una función de devolución de llamada que convierte una excepción.  El primer parámetro es el código de excepción y el segundo es el registro de la excepción.  Usado por [\_set\_se\_translator](../c-runtime-library/reference/set-se-translator.md).|EH.H|  
|Entero de `sig_atomic_t`|Tipo de objeto que se puede modificar como entidad atómica, incluso en presencia de interrupciones asincrónicas; se usa con [signal](../c-runtime-library/reference/signal.md).|SIGNAL.H|  
|`size_t` \(\_\_int64 sin signo o entero sin signo, según la plataforma de destino\)|Resultado del operador de  `sizeof`.|CRTDEFS.H y otros archivos de inclusión|  
|`_stat` \(estructura\)|Contiene información de estado de archivo devuelta por [\_stat](../c-runtime-library/reference/stat-functions.md) y [\_fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md).|SYS\\STAT.H|  
|`__stat64` \(estructura\)|Contiene información de estado de archivo devuelta por [\_fstat64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md), [\_stat64](../c-runtime-library/reference/stat-functions.md) y [\_wstat64](../c-runtime-library/reference/stat-functions.md).|SYS\\STAT.H|  
|`_stati64` \(estructura\)|Contiene información de estado de archivo devuelta por [\_fstati64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md), [\_stati64](../c-runtime-library/reference/stat-functions.md) y [\_wstati64](../c-runtime-library/reference/stat-functions.md).|SYS\\STAT.H|  
|Definición de tipo de `terminate_function`|Definición de archivo para una función de devolución de llamada a la que se llama cuando se llama a [terminate](../c-runtime-library/reference/terminate-crt.md).  Usado por [set\_terminate](../c-runtime-library/reference/set-terminate-crt.md).|EH.H|  
|`time_t` \(\_\_int64 o entero largo\)|Representa valores de hora en [mktime](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [time](../c-runtime-library/reference/time-time32-time64.md), [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime\_s, \_ctime32\_s, \_ctime64\_s, \_wctime\_s, \_wctime32\_s, \_wctime64\_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) y [gmtime, \_gmtime32, \_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md).  Número de segundos desde el 1 de enero de 1970, 0:00 UTC.  Si se define \_USE\_32BIT\_TIME\_T, `time_t` es un entero largo.  Si no se define, es un entero de 64 bits.|TIME.H,<br /><br /> SYS\\STAT.H,<br /><br /> SYS\\TIMEB.H|  
|`__time32_t` \(entero largo\)|Representa valores de hora en [mktime, \_mktime32, \_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime\_s, \_ctime32\_s, \_ctime64\_s, \_wctime\_s, \_wctime32\_s, \_wctime64\_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [gmtime, \_gmtime32, \_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) y [localtime, \_localtime32, \_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md).|CRTDEFS.H, SYS\\STAT.H,<br /><br /> SYS\\TIMEB.H|  
|`__time64_t` \(`__int64`\)|Representa valores de hora en [mktime, \_mktime32, \_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [\_ctime64, \_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime\_s, \_ctime32\_s, \_ctime64\_s, \_wctime\_s, \_wctime32\_s, \_wctime64\_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [\_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [\_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md) y [\_time64](../c-runtime-library/reference/time-time32-time64.md).|TIME.H,<br /><br /> SYS\\STAT.H,<br /><br /> SYS\\TIMEB.H|  
|`_timeb` \(estructura\)|Usado por [\_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md) y [\_ftime\_s, \_ftime32\_s, \_ftime64\_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) para almacenar la hora del sistema actual.|SYS\\TIMEB.H|  
|`__timeb32` \(estructura\)|Usado por [\_ftime, \_ftime32, \_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) y [\_ftime\_s, \_ftime32\_s, \_ftime64\_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) para almacenar la hora del sistema actual.|SYS\\TIMEB.H|  
|`__timeb64` \(estructura\)|Usado por [\_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) y [\_ftime\_s, \_ftime32\_s, \_ftime64\_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) para almacenar la hora del sistema actual.|SYS\\TIMEB.H|  
|`tm` \(estructura\)|Usado por [asctime, \_wasctime](../c-runtime-library/reference/asctime-wasctime.md), [asctime\_s, \_wasctime\_s](../c-runtime-library/reference/asctime-s-wasctime-s.md), [gmtime, \_gmtime32, \_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime\_s, \_gmtime32\_s, \_gmtime64\_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md), [localtime, \_localtime32, \_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime\_s, \_localtime32\_s, \_localtime64\_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), [mktime, \_mktime32, \_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md) y [strftime, wcsftime, \_strftime\_l, \_wcsftime\_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para almacenar y recuperar información de hora.|TIME.H|  
|`uintmax_t`|Tipo entero sin signo que puede representar cualquier valor de cualquier tipo de entero sin signo.|stdint.h|  
|`uintptr_t` \(entero largo o `__int64`, según la plataforma de destino\)|Entero sin signo o una versión \_\_int64 sin signo de `intptr_t`.|STDDEF.H y otros archivos de inclusión|  
|`unexpected_function`|Definición de archivo para una función de devolución de llamada a la que se llama cuando se llama a [unexpected](../c-runtime-library/reference/unexpected-crt.md).  Usado por [set\_unexpected](../c-runtime-library/reference/set-unexpected-crt.md).|EH.H|  
|`_utimbuf` \(estructura\)|Almacena las horas de acceso a archivos y su modificación usadas por [\_utime, \_wutime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) y [\_futime, \_futime32, \_futime64](../c-runtime-library/reference/futime-futime32-futime64.md) para cambiar las fechas de modificación del archivo.|SYS\\UTIME.H|  
|`_utimbuf32` \(estructura\)|Almacena las horas de acceso a archivos y su modificación usadas por [\_utime, \_utime32, \_utime64, \_wutime, \_wutime32, \_wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) y [\_futime, \_futime32, \_futime64](../c-runtime-library/reference/futime-futime32-futime64.md) para cambiar las fechas de modificación del archivo.|SYS\\UTIME.H|  
|`__utimbuf64` \(estructura\)|Usado por [\_utime64, \_wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) y [\_futime64](../c-runtime-library/reference/futime-futime32-futime64.md) para almacenar la hora actual.|SYS\\UTIME.H|  
|`va_list` \(estructura\)|Se usa para contener la información que necesitan las macros [va\_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) y [va\_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md).  La función a la que se llama declara la variable de tipo `va_list` que se puede pasar como argumento a otra función.|STDARG.H,<br /><br /> CRTDEFS.H|  
|carácter ancho de `wchar_t`|Útil para escribir programas portables para mercados internacionales.|STDDEF.H, STDLIB.H,<br /><br /> CRTDEFS.H,<br /><br /> SYS\\STAT.H|  
|Entero de `wctrans_t`|Representa asignaciones de caracteres específicas de la configuración regional.|WCTYPE.H|  
|Entero de `wctype_t`|Puede representar todos los caracteres del juego de caracteres de cualquier idioma.|WCHAR.H,<br /><br /> CRTDEFS.H|  
|Entero de `wint_t`|Tipo de objeto de datos que puede contener cualquier carácter ancho o valor final de archivo ancho.|WCHAR.H,<br /><br /> CRTDEFS.H|  
  
## Vea también  
 [Referencia de la biblioteca en tiempo de ejecución de C](../c-runtime-library/c-run-time-library-reference.md)
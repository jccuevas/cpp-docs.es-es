---
title: "_strdate_s, _wstrdate_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strdate_s"
  - "_wstrdate_s"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_strdate_s"
  - "wstrdate_s"
  - "_wstrdate_s"
  - "strdate_s"
  - "_tstrdate_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "fechas, copiar"
  - "tstrdate_s (función)"
  - "wstrdate_s (función)"
  - "_tstrdate_s (función)"
  - "strdate_s (función)"
  - "copiar fechas"
  - "_strdate_s (función)"
  - "_wstrdate_s (función)"
ms.assetid: d41d8ea9-e5ce-40d4-864e-1ac29b455991
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strdate_s, _wstrdate_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Copie la fecha actual del sistema a un búfer.  Éstas son versiones de [\_strdate, \_wstrdate](../../c-runtime-library/reference/strdate-wstrdate.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
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
  
#### Parámetros  
 \[out\] `buffer`  
 Un puntero a un búfer que se completará con la cadena de fecha con formato.  
  
 \[in\] `numberOfElements`  
 Tamaño del búfer.  
  
## Valor devuelto  
 Cero si correctamente.  El valor devuelto es un código de error si hay un error.  Los códigos de error se definen en ERRNO.H; vea la tabla siguiente para los errores exactos generados por esta función.  Para obtener más información sobre los códigos de error, vea [errno](../../c-runtime-library/errno-constants.md).  
  
## Condiciones de error  
  
|`buffer`|`numberOfElements`|Devolución|Contenido de `buffer`|  
|--------------|------------------------|----------------|---------------------------|  
|`NULL`|\(ninguno\)|`EINVAL`|No modificado|  
|No `NULL` \(del búfer válido\)|0|`EINVAL`|No modificado|  
|No `NULL` \(del búfer válido\)|0 \< `numberOfElements` \< 9|`EINVAL`|Cadena vacía|  
|No `NULL` \(del búfer válido\)|`numberOfElements` \>\= 9|0|Fecha actual con formato como se especifica en las notas|  
  
## Problemas de seguridad  
 El paso de no un valor no válido de `NULL` para el búfer producirá una infracción de acceso si el parámetro de `numberOfElements` es mayor que 9.  
  
 Pasar valores para el tamaño que es mayor que el tamaño real de `buffer` dará lugar a la saturación del búfer.  
  
## Comentarios  
 Estas funciones proporcionan versiones más seguras de `_strdate` y de `_wstrdate`.  La función de `_strdate_s` copia la fecha actual del sistema en el búfer indicada por `buffer`, `mm`con formato\/`dd`\/`yy`, donde dos dígitos `mm` que representan el mes, `dd` es dos dígitos que representan el día, y `yy` es los dos últimos dígitos del año.  Por ejemplo, la cadena `12/05/99` representa el 5 de diciembre de 1999.  El búfer debe ser por lo menos de 9 caracteres.  
  
 `_wstrdate_s` es una versión con caracteres anchos de `_strdate_s`; el argumento y el valor devuelto de `_wstrdate_s` son cadenas de caracteres anchos.  Por lo demás, estas funciones se comportan exactamente igual.  
  
 Si `buffer` es un puntero de `NULL` , o si `numberOfElements` es menos de 9 caracteres, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven \-1 y `errno` establecido en `EINVAL` si el búfer es `NULL` o si `numberOfElements` es menor o igual que 0, o conjunto `errno` a `ERANGE` si `numberOfElements` es menor que 9.  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer \(lo que elimina la necesidad de especificar un argumento de tamaño\) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignación de rutina de texto genérico:  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tstrdate_s`|`_strdate_s`|`_strdate_s`|`_wstrdate_s`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_strdate`|\<time.h\>|  
|`_wstrdate`|\<time.h o\> wchar.h \<\>|  
|`_strdate_s`|\<time.h\>|  
  
## Ejemplo  
 Vea el ejemplo para [tiempo](../../c-runtime-library/reference/time-time32-time64.md).  
  
## Equivalente en .NET Framework  
 [System::DateTime::Parse](https://msdn.microsoft.com/en-us/library/system.datetime.parse.aspx)  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime\_s, \_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime\_s, \_ctime32\_s, \_ctime64\_s, \_wctime\_s, \_wctime32\_s, \_wctime64\_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [gmtime\_s, \_gmtime32\_s, \_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime, \_mktime32, \_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)
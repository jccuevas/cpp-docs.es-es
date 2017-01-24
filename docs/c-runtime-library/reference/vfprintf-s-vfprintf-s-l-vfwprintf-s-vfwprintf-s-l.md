---
title: "vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "vfwprintf_s"
  - "_vfprintf_s_l"
  - "vfprintf_s"
  - "_vfwprintf_s_l"
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
apitype: "DLLExport"
f1_keywords: 
  - "_vftprintf_s"
  - "vfwprintf_s"
  - "vfprintf_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_vfprintf_s_l (función)"
  - "_vftprintf_s (función)"
  - "_vftprintf_s_l (función)"
  - "_vfwprintf_s_l (función)"
  - "texto con formato [C++]"
  - "vfprintf_s (función)"
  - "vfprintf_s_l (función)"
  - "vftprintf_s_l (función)"
  - "vfwprintf_s (función)"
  - "vfwprintf_s_l (función)"
ms.assetid: eab6f563-46e2-4806-963f-2b23f339ecdc
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe un resultado con formato mediante un puntero a una lista de argumentos.  Estas versiones de [vfprintf, \_vfprintf\_l, vfwprintf, \_vfwprintf\_l](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
int vfprintf_s(  
   FILE *stream,  
   const char *format,  
   va_list argptr   
);  
int _vfprintf_s_l(  
   FILE *stream,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int vfwprintf_s(  
   FILE *stream,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vfwprintf_s_l(  
   FILE *stream,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura `FILE`.  
  
 `format`  
 Especificación de formato.  
  
 `argptr`  
 Puntero a la lista de argumentos.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
 Para obtener más información, vea [Especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## Valor devuelto  
 `vfprintf_s` y `vfwprintf_s` devuelven el número de caracteres escritos, sin incluir el carácter de terminación nulo, o un valor negativo si se produce un error de salida.  Si `stream` o `format` es un puntero NULL, o si la cadena de formato contiene caracteres de formato no válidos, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, las funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
 Para obtener información sobre estos y otros códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Cada una de estas funciones toma un puntero a una lista de argumentos y, a continuación, aplica formato a los datos determinados y los escribe en `stream`.  
  
 Estas funciones se diferencian de las versiones de no Secure sólo en que las versiones seguras comprobar que la cadena de `format` contiene caracteres de formato válidos.  
  
 `vfwprintf_s` es la versión de caracteres anchos de `vfprintf_s`. Las dos funciones se comportan exactamente igual si el flujo se abre en modo ANSI.  `vfprintf_s` no admite actualmente la salida en un flujo UNICODE.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
> [!IMPORTANT]
>  Asegúrese de que `format` no es una cadena definida por el usuario.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_vftprintf_s`|`vfprintf_s`|`vfprintf_s`|`vfwprintf_s`|  
|`_vftprintf_s_l`|`_vfprintf_s_l`|`_vfprintf_s_l`|`_vfwprintf_s_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezados opcionales|  
|------------|--------------------------|----------------------------|  
|`vfprintf_s`, \_`vfprintf_s_l`|\<stdio.h\> y \<stdarg.h\>|\<varargs.h\>\*|  
|`vfwprintf_s`, \_`vfwprintf_s_l`|\<stdio.h\> o \<wchar.h\>, y \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* Necesario para la compatibilidad con UNIX V.  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [vprintf \(Funciones\)](../../c-runtime-library/vprintf-functions.md)   
 [fprintf, \_fprintf\_l, fwprintf, \_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg, va\_copy, va\_end, va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)
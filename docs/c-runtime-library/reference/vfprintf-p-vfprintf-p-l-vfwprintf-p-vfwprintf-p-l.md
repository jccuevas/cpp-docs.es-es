---
title: "_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vfprintf_p"
  - "_vfwprintf_p"
  - "_vfprintf_p_l"
  - "_vfwprintf_p_l"
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
  - "_vfwprintf_p_l"
  - "_vfprintf_p"
  - "vfwprintf_p_l"
  - "vfwprintf_p"
  - "vfprintf_p_l"
  - "_vfwprintf_p"
  - "_vftprintf_p"
  - "_vfprintf_p_l"
  - "vfprintf_p"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_vfprintf_p (función)"
  - "_vfprintf_p_l (función)"
  - "_vftprintf_p (función)"
  - "_vftprintf_p_l (función)"
  - "_vfwprintf_p (función)"
  - "_vfwprintf_p_l (función)"
  - "texto con formato [C++]"
  - "vfprintf_p (función)"
  - "vfprintf_p_l (función)"
  - "vftprintf_p (función)"
  - "vftprintf_p_l (función)"
  - "vfwprintf_p (función)"
  - "vfwprintf_p_l (función)"
ms.assetid: 4d4a0914-4175-4b65-9ca1-037c4ef29147
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribir con formato salida mediante un puntero a una lista de argumentos, con la capacidad de especificar el orden en que los argumentos se utilizan en la cadena de formato.  
  
## Sintaxis  
  
```  
int _vfprintf_p(  
   FILE *stream,  
   const char *format,  
   va_list argptr   
);  
int _vfprintf_p_l(  
   FILE *stream,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vfwprintf_p(  
   FILE *stream,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vfwprintf_p_l(  
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
 `_vfprintf_p` y `_vfwprintf_p` devuelven el número de caracteres escritos, sin incluir el carácter de terminación nulo, o un valor negativo si se produce un error de salida.  
  
## Comentarios  
 Cada una de estas funciones toma un puntero a una lista de argumentos y, a continuación, aplica formato a los datos determinados y los escribe en `stream`.  Estas funciones se diferencian de las versiones de `_vfprint_s` y de `_vfwprint_s` sólo en que admiten parámetros posicionales.  Para obtener más información, vea [printf\_p \(Parámetros de posición\)](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 `_vfwprintf_p` es la versión de caracteres anchos de `_vprintf_p`. Las dos funciones se comportan exactamente igual si el flujo se abre en modo ANSI.  `_vprintf_p` no admite actualmente la salida en un flujo UNICODE.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
> [!IMPORTANT]
>  Asegúrese de que `format` no es una cadena definida por el usuario.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
 Si `stream` o `format` es un puntero NULL, o si la cadena de formato contiene caracteres de formato no válidos, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, las funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_vftprintf_p`|`_vfprintf_p`|`_vfprintf_p`|`_vfwprintf_p`|  
|`_vftprintf_p_l`|`_vfprintf_p_l`|`_vfprintf_p_l`|`_vfwprintf_p_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezados opcionales|  
|------------|--------------------------|----------------------------|  
|`_vfprintf_p`, `_vfprintf_p_l`|\<stdio.h\> y \<stdarg.h\>|\<varargs.h\>\*|  
|`_vfwprintf_p`, `_vfwprintf_p_l`|\<stdio.h\> o \<wchar.h\>, y \<stdarg.h\>|\<varargs.h\>\*|  
  
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
 [printf\_p \(Parámetros de posición\)](../../c-runtime-library/printf-p-positional-parameters.md)   
 [\_fprintf\_p, \_fprintf\_p\_l, \_fwprintf\_p, \_fwprintf\_p\_l](../../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)   
 [\_vsprintf\_p, \_vsprintf\_p\_l, \_vswprintf\_p, \_vswprintf\_p\_l](../../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)   
 [\_sprintf\_p, \_sprintf\_p\_l, \_swprintf\_p, \_swprintf\_p\_l](../../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)
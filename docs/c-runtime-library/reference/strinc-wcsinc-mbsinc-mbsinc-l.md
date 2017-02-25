---
title: "_strinc, _wcsinc, _mbsinc, _mbsinc_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsinc"
  - "_wcsinc"
  - "_mbsinc_l"
  - "_strinc"
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
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "mbsinc_l"
  - "_strinc"
  - "strinc"
  - "_mbsinc"
  - "_wcsinc"
  - "wcsinc"
  - "mbsinc"
  - "_mbsinc_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsinc (función)"
  - "_mbsinc_l (función)"
  - "_strinc (función)"
  - "_tcsinc (función)"
  - "_wcsinc (función)"
  - "mbsinc (función)"
  - "mbsinc_l (función)"
  - "strinc (función)"
  - "tcsinc (función)"
  - "wcsinc (función)"
ms.assetid: 54685943-8e2c-45e9-a559-2d94930dc6b4
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _strinc, _wcsinc, _mbsinc, _mbsinc_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Hace avanzar un puntero de cadena un carácter.  
  
> [!IMPORTANT]
>  `_mbsinc` y `_mbsinc_l` no se pueden usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *_strinc(    const char *current,    _locale_t locale ); wchar_t *_wcsinc(    const wchar_t *current,    _locale_t locale ); unsigned char *_mbsinc(    const unsigned char *current  ); unsigned char *_mbsinc_l(    const unsigned char *current,    _locale_t locale );   
```  
  
#### Parámetros  
 `current`  
 Puntero de carácter.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cada una de estas rutinas devuelve un puntero al carácter que sigue inmediatamente a `current`.  
  
## Comentarios  
 La función `_mbsinc` devuelve un puntero al primer byte del carácter multibyte que sigue inmediatamente a `current`.  `_mbsinc` reconoce secuencias de caracteres multibyte en función de la [página de códigos multibyte](../../c-runtime-library/code-pages.md) que se usa actualmente; `_mbsinc_l` son idénticos salvo que en su lugar utiliza el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 La función de texto genérico `_tcsinc`, definida en Tchar.h, se asigna a `_mbsinc` si se ha definido `_MBCS`, o a `_wcsinc` si se ha definido `_UNICODE`.  De lo contrario, `_tcsinc` se asigna a `_strinc`.  `_strinc` y `_wcsinc` son versiones de caracteres de un solo byte y caracteres anchos de `_mbsinc`.  `_strinc` y `_wcsinc` se proporcionan solo para esta asignación y no deben usarse de otra manera.  Para obtener más información, vea [Usar asignaciones de texto genérico](../../c-runtime-library/using-generic-text-mappings.md) y [Asignaciones de texto genérico](../../c-runtime-library/generic-text-mappings.md).  
  
 Si `current` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve `EINVAL` y establece `errno` en `EINVAL`.  
  
> [!IMPORTANT]
>  Estas funciones pueden ser vulnerables a amenazas de saturación del búfer.  Las saturaciones del búfer se pueden usar para ataques del sistema, ya que pueden producir una elevación de privilegios no justificada.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbsinc`|\<mbstring.h\>|  
|`_mbsinc_l`|\<mbstring.h\>|  
|`_strinc`|\<tchar.h\>|  
|`_wcsinc`|\<tchar.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [\_strdec, \_wcsdec, \_mbsdec, \_mbsdec\_l](../../c-runtime-library/reference/strdec-wcsdec-mbsdec-mbsdec-l.md)   
 [\_strnextc, \_wcsnextc, \_mbsnextc, \_mbsnextc\_l](../../c-runtime-library/reference/strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)   
 [\_strninc, \_wcsninc, \_mbsninc, \_mbsninc\_l](../../c-runtime-library/reference/strninc-wcsninc-mbsninc-mbsninc-l.md)
---
title: "_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strnextc"
  - "_mbsnextc_l"
  - "_mbsnextc"
  - "_wcsnextc"
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
  - "strnextc"
  - "tcsnextc"
  - "_mbsnextc_l"
  - "_mbsnextc"
  - "mbsnextc_l"
  - "ftcsnextc"
  - "mbsnextc"
  - "_tcsnextc"
  - "_wcsnextc"
  - "_ftcsnextc"
  - "_strnextc"
  - "wcsnextc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsnextc (función)"
  - "_mbsnextc_l (función)"
  - "_strnextc (función)"
  - "_tcsnextc (función)"
  - "_wcsnextc (función)"
  - "mbsnextc (función)"
  - "mbsnextc_l (función)"
  - "strnextc (función)"
  - "tcsnextc (función)"
  - "wcsnextc (función)"
ms.assetid: e3086173-9eb5-4540-a23a-5d866bd05340
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Busca el siguiente carácter de una cadena.  
  
> [!IMPORTANT]
>  `_mbsnextc` y `_mbsnextc_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
unsigned int _strnextc(  
   const char *str  
);  
unsigned int _wscnextc(  
   const wchar_t *str  
);   
unsigned int _mbsnextc(  
   const unsigned char *str   
);  
unsigned int _mbsnextc_l(  
   const unsigned char *str,  
   _locale_t locale  
);  
  
```  
  
#### Parámetros  
 `str`  
 Cadena de origen.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve el valor entero del siguiente carácter de `str`*.*  
  
## Comentarios  
 La función `_mbsnextc` devuelve el valor entero del siguiente carácter multibyte de `str`, sin avanzar el puntero de cadena.  `_mbsnextc` reconoce las secuencias de caracteres multibyte de acuerdo con la [página de códigos multibyte](../../c-runtime-library/code-pages.md) actualmente en uso.  
  
 Si `str` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve \-0.  
  
 **Nota de seguridad** Esta API crea la posible amenaza de un problema de saturación del búfer.  Los problemas de saturación del búfer son un método frecuente de ataque del sistema, que produce una elevación de privilegios no justificada.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsnextc`|`_strnextc`|`_mbsnextc`|`_wcsnextc`|  
  
 `_strnextc` y `_wcsnextc` son versiones de cadena de carácter de un solo byte y de cadena de caracteres anchos de `_mbsnextc`.  `_wcsnextc` devuelve el valor entero del siguiente carácter ancho de `string`; `_strnextc` devuelve el valor entero del siguiente carácter de un solo byte de `string`.  `_strnextc` y `_wcsnextc` se proporcionan solo para esta asignación y no deben usarse de otra manera.  Para obtener más información, vea [Usar asignaciones de texto genérico](../../c-runtime-library/using-generic-text-mappings.md) y [Asignaciones de texto genérico](../../c-runtime-library/generic-text-mappings.md).  
  
 `_mbsnextc_l` es exactamente igual, salvo que usa el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbsnextc`|\<mbstring.h\>|  
|`_mbsnextc_l`|\<mbstring.h\>|  
|`_strnextc`|\<tchar.h\>|  
|`_wcsnextc`|\<tchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_strdec, \_wcsdec, \_mbsdec, \_mbsdec\_l](../../c-runtime-library/reference/strdec-wcsdec-mbsdec-mbsdec-l.md)   
 [\_strinc, \_wcsinc, \_mbsinc, \_mbsinc\_l](../../c-runtime-library/reference/strinc-wcsinc-mbsinc-mbsinc-l.md)   
 [\_strninc, \_wcsninc, \_mbsninc, \_mbsninc\_l](../../c-runtime-library/reference/strninc-wcsninc-mbsninc-mbsninc-l.md)
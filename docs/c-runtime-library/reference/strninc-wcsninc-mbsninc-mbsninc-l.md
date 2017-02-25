---
title: "_strninc, _wcsninc, _mbsninc, _mbsninc_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsninc"
  - "_mbsninc_l"
  - "_wcsninc"
  - "_strninc"
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
  - "strninc"
  - "wcsninc"
  - "mbsninc_l"
  - "_strninc"
  - "_tcsninc"
  - "mbsninc"
  - "_mbsninc_l"
  - "_ftcsninc"
  - "_wcsninc"
  - "_mbsninc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsninc (función)"
  - "_mbsninc_l (función)"
  - "_strninc (función)"
  - "_tcsninc (función)"
  - "_wcsninc (función)"
  - "mbsninc (función)"
  - "mbsninc_l (función)"
  - "strninc (función)"
  - "tcsninc (función)"
  - "wcsninc (función)"
ms.assetid: 6caace64-f9e4-48c0-afa8-ea51824ad723
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _strninc, _wcsninc, _mbsninc, _mbsninc_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Hace avanzar un puntero de cadena en `n` caracteres.  
  
> [!IMPORTANT]
>  `_mbsninc` y `_mbsninc_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *_strninc(  
   const char *str,  
   size_t count   
);  
wchar_t *_wcsninc(  
   const wchar_t *str,  
   size_t count   
);  
unsigned char *_mbsninc(  
   const unsigned char *str,  
   size_t count   
);  
unsigned char *_mbsninc(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `str`  
 Cadena de origen.  
  
 `count`  
 Número de caracteres que va a avanzar un puntero de cadena.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cada una de estas rutinas devuelve un puntero a `str` después de que `str` se ha incrementado en `count` o `NULL` si el puntero proporcionado es `NULL`.  Si `count` es mayor o igual que el número de caracteres de `str`, el resultado es indefinido.  
  
## Comentarios  
 La función `_mbsninc` aumenta `str` en el número de caracteres multibyte de `count`.  `_mbsninc` reconoce las secuencias de caracteres multibyte de acuerdo con la [página de códigos multibyte](../../c-runtime-library/code-pages.md) actualmente en uso.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsninc`|`_strninc`|`_mbsninc`|`_wcsninc`|  
  
 `_strninc` y `_wcsninc` son versiones de cadena de carácter de un solo byte y de cadena de caracteres anchos de `_mbsninc`.  `_wcsninc` y `_strninc` se proporcionan solo para esta asignación y no deben usarse de otra manera.  Para obtener más información, vea [Usar asignaciones de texto genérico](../../c-runtime-library/using-generic-text-mappings.md) y [Asignaciones de texto genérico](../../c-runtime-library/generic-text-mappings.md).  
  
 `_mbsninc_l` es exactamente igual, salvo que usa el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbsninc`|\<mbstring.h\>|  
|`_mbsninc_l`|\<mbstring.h\>|  
|`_strninc`|\<tchar.h\>|  
|`_wcsninc`|\<tchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_strdec, \_wcsdec, \_mbsdec, \_mbsdec\_l](../../c-runtime-library/reference/strdec-wcsdec-mbsdec-mbsdec-l.md)   
 [\_strinc, \_wcsinc, \_mbsinc, \_mbsinc\_l](../../c-runtime-library/reference/strinc-wcsinc-mbsinc-mbsinc-l.md)   
 [\_strnextc, \_wcsnextc, \_mbsnextc, \_mbsnextc\_l](../../c-runtime-library/reference/strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)
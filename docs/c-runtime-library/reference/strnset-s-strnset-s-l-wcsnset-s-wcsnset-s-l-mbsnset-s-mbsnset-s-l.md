---
title: "_strnset_s, _strnset_s_l, _wcsnset_s, _wcsnset_s_l, _mbsnset_s, _mbsnset_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsnset_s_l"
  - "_strnset_s"
  - "_mbsnset_s"
  - "_strnset_s_l"
  - "_wcsnset_s_l"
  - "_wcsnset_s"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_mbsnset_s_l"
  - "wcsnset_s"
  - "_tcsnset_s_l"
  - "_wcsnset_s"
  - "_mbsnset_s"
  - "_wcsnset_s_l"
  - "_strnset_s_l"
  - "strnset_s_l"
  - "_tcsnset_s"
  - "_strnset_s"
  - "strnset_s"
  - "mbsnset_s_l"
  - "mbsnset_s"
  - "wcsnset_s_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsnset_s (función)"
  - "_mbsnset_s_l (función)"
  - "_strnset_s (función)"
  - "_strnset_s_l (función)"
  - "_tcsnset_s (función)"
  - "_tcsnset_s_l (función)"
  - "_wcsnset_s (función)"
  - "inicializar caracteres"
  - "mbsnset_s (función)"
  - "mbsnset_s_l (función)"
  - "strnset_s (función)"
  - "strnset_s_l (función)"
  - "tcsnset_s (función)"
  - "tcsnset_s_l (función)"
  - "wcsnset_s (función)"
ms.assetid: 9cf1b321-b5cb-4469-b285-4c07cfbd8813
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# _strnset_s, _strnset_s_l, _wcsnset_s, _wcsnset_s_l, _mbsnset_s, _mbsnset_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Inicializa los caracteres de una cadena en un carácter dado.  Estas versiones de [\_strnset, \_strnset\_l, \_wcsnset, \_wcsnset\_l, \_mbsnset, \_mbsnset\_l](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  `_mbsnset_s` y `_mbsnset_s_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
errno_t _strnset_s(  
   char *str,  
   size_t numberOfElements,  
   int c,  
   size_t count   
);  
errno_t _strnset_s_l(  
   char *str,  
   size_t numberOfElements,  
   int c,  
   size_t count,  
   locale_t locale  
);  
errno_t _wcsnset_s(  
   wchar_t *str,  
   size_t numberOfElements,  
   wchar_t c,  
   size_t count   
);  
errno_t _wcsnset_s_l(  
   wchar_t *str,  
   size_t numberOfElements,  
   wchar_t c,  
   size_t count,  
   _locale_t locale  
);  
errno_t _mbsnset_s(  
   unsigned char *str,  
   size_t numberOfElements,  
   unsigned int c,  
   size_t count   
);  
errno_t _mbsnset_s_l(  
   unsigned char *str,  
   size_t numberOfElements,  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `str`  
 Cadena que se va a modificar.  
  
 `numberOfElements`  
 Tamaño del búfer `str`.  
  
 `c`  
 Especificación de carácter.  
  
 `count`  
 Número de caracteres que se va a establecer.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cero si es correcto, código de error en caso contrario.  
  
 Estas funciones validan sus argumentos.  Si `str` no es una cadena válida terminada en NULL o el argumento de tamaño es menor o igual que 0, entonces se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven un código de error y establecen `errno` en ese código de error.  El código de error predeterminado es `EINVAL` si no hay ningún valor más concreto.  
  
## Comentarios  
 Estas funciones establecen, como máximo, los primeros `count` caracteres de `str` en `c`.  Si `count` es mayor que el tamaño de `str`, se usa el tamaño de `str` en lugar de `count`.  Se produce un error si `count` es mayor que `numberOfElements` y los dos parámetros son mayores que el tamaño de `str`.  
  
 `_wcsnset_s` y `_mbsnset_s`  son versiones de caracteres anchos y multibyte de `_strnset_s`.  El argumento de cadena de `_wcsnset_s` es una cadena de caracteres anchos, y el de `_mbsnset_s` es una cadena de `` caracteres multibyte.  Estas tres funciones se comportan exactamente igual.  
  
 El valor de la categoría `LC_CTYPE`  de la configuración regional afecta al valor de salida; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Las versiones de depuración de estas funciones rellenan primero el búfer con 0xFD.  Para deshabilitar este comportamiento, use [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsnset_s`|`_strnset_s`|`_mbsnbset_s`|`_wcsnset_s`|  
|`_tcsnset_s_l`|`_strnset_s_l`|`_mbsnbset_s_l`|`_wcsnset_s_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_strnset_s`|\<string.h\>|  
|`_strnset_s_l`|\<tchar.h\>|  
|`_wcsnset_s`|\<string.h\> o \<wchar.h\>|  
|`_wcsnset_s_l`|\<tchar.h\>|  
|`_mbsnset_s`, `_mbsnset_s_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_strnset_s.c  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[15] = "This is a test";  
   /* Set not more than 4 characters of string to be *'s */  
   printf( "Before: %s\n", string );  
   _strnset_s( string, sizeof(string), '*', 4 );  
   printf( "After:  %s\n", string );  
}  
```  
  
  **Antes: This is a test**  
**Después: \*\*\*\* is a test**   
## Equivalente en .NET Framework  
 [System::String::Replace](https://msdn.microsoft.com/en-us/library/system.string.replace.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcat, wcscat, \_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp, wcscmp, \_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy, wcscpy, \_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [\_strset, \_strset\_l, \_wcsset, \_wcsset\_l, \_mbsset, \_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)
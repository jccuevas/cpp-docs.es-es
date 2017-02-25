---
title: "_strrev, _wcsrev, _mbsrev, _mbsrev_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wcsrev"
  - "_mbsrev"
  - "_strrev"
  - "_mbsrev_l"
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
  - "_strrev"
  - "_ftcsrev"
  - "_tcsrev"
  - "mbsrev"
  - "mbsrev_l"
  - "_wcsrev_fstrrev"
  - "_mbsrev"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ftcsrev (función)"
  - "_mbsrev (función)"
  - "_mbsrev_l (función)"
  - "_strrev (función)"
  - "_tcsrev (función)"
  - "_wcsrev (función)"
  - "caracteres [C++], invertir orden"
  - "caracteres [C++], conmutación"
  - "ftcsrev (función)"
  - "mbsrev (función)"
  - "mbsrev_l (función)"
  - "invertir caracteres en cadenas"
  - "cadenas [C++], invertir"
  - "strrev (función)"
  - "tcsrev (función)"
  - "wcsrev (función)"
ms.assetid: 87863e89-4fa0-421c-af48-25d8516fe72f
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# _strrev, _wcsrev, _mbsrev, _mbsrev_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Invierte los caracteres de una cadena.  
  
> [!IMPORTANT]
>  `_mbsrev` y `_mbsrev_l` no se pueden usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *_strrev(  
   char *str   
);  
wchar_t *_wcsrev(  
   wchar_t *str   
);  
unsigned char *_mbsrev(  
   unsigned char *str   
);  
unsigned char *_mbsrev_l(  
   unsigned char *str,  
   _locale_t locale   
);  
```  
  
#### Parámetros  
 `str`  
 Cadena terminada en NULL que se va a invertir.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve un puntero a la cadena modificada.  No se reserva ningún valor devuelto para indicar un error.  
  
## Comentarios  
 La función `_strrev` invierte el orden de los caracteres de `string`.  El carácter nulo de finalización no cambia de lugar.  `_wcsrev` y `_mbsrev` son versiones de caracteres anchos y multibyte de `_strrev`.  Los argumentos y el valor devuelto de `_wcsrev` son cadenas de caracteres anchos; los de `_mbsrev` son cadenas de caracteres multibyte.  En el caso de `_mbsrev`, el orden de los bytes de cada carácter multibyte de `string` no cambia.  Estas tres funciones se comportan exactamente igual.  
  
 `_mbsrev` valida sus parámetros.  Si `string1` o `string2` es un puntero nulo, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `_mbsrev` devuelve `NULL` y establece `errno` en `EINVAL`.  `_strrev` y `_wcsrev` no validan sus parámetros.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones son idénticas, salvo que las que no tienen el sufijo `_l` usan la configuración regional actual y las que tienen el sufijo `_l` usan el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
> [!IMPORTANT]
>  Estas funciones pueden ser vulnerables a amenazas de saturación del búfer.  Las saturaciones del búfer se pueden usar para ataques del sistema, ya que pueden producir una elevación de privilegios no justificada.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsrev`|`_strrev`|`_mbsrev`|`_wcsrev`|  
|**no disponible**|**no disponible**|`_mbsrev_l`|**no disponible**|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_strrev`|\<string.h\>|  
|`_wcsrev`|\<string.h\> o \<wchar.h\>|  
|`_mbsrev`, `_mbsrev_l`|\<mbstring.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_strrev.c  
// This program checks a string to see  
// whether it is a palindrome: that is, whether  
// it reads the same forward and backward.  
//  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char* string = "Able was I ere I saw Elba";  
   int result;  
  
   // Reverse string and compare (ignore case):  
   result = _stricmp( string, _strrev( _strdup( string ) ) );  
   if( result == 0 )  
      printf( "The string \"%s\" is a palindrome\n", string );  
   else  
      printf( "The string \"%s\" is not a palindrome\n", string );  
}  
```  
  
  **The string "Able was I ere I saw Elba" is a palindrome**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcpy, wcscpy, \_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [\_strset, \_strset\_l, \_wcsset, \_wcsset\_l, \_mbsset, \_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)
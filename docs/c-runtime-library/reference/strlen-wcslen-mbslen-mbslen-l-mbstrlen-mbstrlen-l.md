---
title: "strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l | Microsoft Docs"
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
  - "_mbslen"
  - "_mbslen_l"
  - "_mbstrlen"
  - "wcslen"
  - "_mbstrlen_l"
  - "strlen"
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
  - "_mbstrlen"
  - "wcslen"
  - "_tcslen"
  - "_ftcslen"
  - "strlen"
  - "_mbslen"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcslen (función)"
  - "_mbslen (función)"
  - "_mbslen_l (función)"
  - "_mbstrlen (función)"
  - "_mbstrlen_l (función)"
  - "_tcslen (función)"
  - "ftcslen (función)"
  - "longitudes, cadenas"
  - "mbslen (función)"
  - "mbslen_l (función)"
  - "mbstrlen (función)"
  - "mbstrlen_l (función)"
  - "longitud de cadena, obtener"
  - "cadenas [C++], obtener longitud"
  - "strlen (función)"
  - "tcslen (función)"
  - "wcslen (función)"
ms.assetid: 16462f2a-1e0f-4eb3-be55-bf1c83f374c2
caps.latest.revision: 32
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene la longitud de una cadena usando la configuración regional actual o una configuración regional especificada.  Hay disponibles versiones más seguras de estas funciones; vea [strnlen, strnlen\_s, wcsnlen, wcsnlen\_s, \_mbsnlen, \_mbsnlen\_l, \_mbstrnlen, \_mbstrnlen\_l](../../c-runtime-library/reference/strnlen-strnlen-s.md).  
  
> [!IMPORTANT]
>  `_mbslen`, `_mbslen_l`, `_mbstrlen` y `_mbstrlen_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
size_t strlen(    const char *str ); size_t wcslen(    const wchar_t *str  ); size_t _mbslen(    const unsigned char *str  ); size_t _mbslen_l(    const unsigned char *str,    _locale_t locale ); size_t _mbstrlen(    const char *str ); size_t _mbstrlen_l(    const char *str,    _locale_t locale );  
```  
  
#### Parámetros  
 `str`  
 Cadena terminada en un valor nulo.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve el número de caracteres de `str`, sin incluir el carácter `NULL` de terminación.  No se reserva ningún valor devuelto para indicar un error, a excepción de `_mbstrlen` y `_mbstrlen_l`, que devuelven `((size_t)(-1))` si la cadena contiene un carácter multibyte no válido.  
  
## Comentarios  
 `strlen` interpreta la cadena como una cadena de caracteres de un solo byte, de modo que el valor devuelto siempre es igual al número de bytes, incluso si la cadena contiene caracteres multibyte.  `wcslen` es una versión con caracteres anchos de `strlen`; el argumento de `wcslen` es una cadena de caracteres anchos y el recuento de caracteres está en caracteres anchos \(de dos bytes\).  Por lo demás, `wcslen` y `strlen` se comportan de forma idéntica.  
  
 **Nota de seguridad** Estas funciones representan una posible amenaza por un problema de saturación del búfer.  Los problemas de saturación del búfer son un método frecuente de ataque del sistema, que produce una elevación de privilegios no justificada.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcslen`|`strlen`|`strlen`|`wcslen`|  
|`_tcsclen`|`strlen`|`_mbslen`|`wcslen`|  
|`_tcsclen_l`|`strlen`|`_mbslen_l`|`wcslen`|  
  
 `_mbslen` y `_mbslen_l` devuelven el número de caracteres multibyte de una cadena de caracteres multibyte, pero no comprueban la validez de los caracteres multibyte.  `_mbstrlen` y `_mbstrlen_l` comprueban la validez de los caracteres multibyte y reconocen secuencias de caracteres multibyte.  Si la cadena que se pasa a `_mbstrlen` o `_mbstrlen_l` contiene un carácter multibyte no válido para la página de códigos, la función devuelve \-1 y establece `errno` en `EILSEQ`.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en su lugar.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strlen`|\<string.h\>|  
|`wcslen`|\<string.h\> o \<wchar.h\>|  
|`_mbslen`, `_mbslen_l`|\<mbstring.h\>|  
|`_mbstrlen`, `_mbstrlen_l`|\<stdlib.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_strlen.c  
// Determine the length of a string. For the multi-byte character  
// example to work correctly, the Japanese language support for  
// non-Unicode programs must be enabled by the operating system.  
  
#include <string.h>  
#include <locale.h>  
  
int main()  
{  
   char* str1 = "Count.";  
   wchar_t* wstr1 = L"Count.";  
   char * mbstr1;  
   char * locale_string;  
  
   // strlen gives the length of single-byte character string  
   printf("Length of '%s' : %d\n", str1, strlen(str1) );  
  
   // wstrlen gives the length of a wide character string  
   wprintf(L"Length of '%s' : %d\n", wstr1, wcslen(wstr1) );  
  
   // A multibyte string: [A] [B] [C] [katakana A] [D] [\0]  
   // in Code Page 932. For this example to work correctly,  
   // the Japanese language support must be enabled by the  
   // operating system.  
   mbstr1 = "ABC" "\x83\x40" "D";  
  
   locale_string = setlocale(LC_CTYPE, "Japanese_Japan");  
  
   if (locale_string == NULL)  
   {  
      printf("Japanese locale not enabled. Exiting.\n");  
      exit(1);  
   }  
   else  
   {  
      printf("Locale set to %s\n", locale_string);  
   }  
  
   // _mbslen will recognize the Japanese multibyte character if the  
   // current locale used by the operating system is Japanese  
   printf("Length of '%s' : %d\n", mbstr1, _mbslen(mbstr1) );  
  
   // _mbstrlen will recognize the Japanese multibyte character  
   // since the CRT locale is set to Japanese even if the OS locale  
   // isnot.   
   printf("Length of '%s' : %d\n", mbstr1, _mbstrlen(mbstr1) );  
   printf("Bytes in '%s' : %d\n", mbstr1, strlen(mbstr1) );     
  
}  
```  
  
  **Longitud de 'Count'.: 6**  
**Longitud de 'Count'.: 6**  
**Longitud de 'ABCァD': 5**  
**Longitud de 'ABCァD': 5**  
**Bytes de 'ABCァD': 6**   
## Equivalente en .NET Framework  
 [System::String::Length](https://msdn.microsoft.com/en-us/library/system.string.length.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcat, wcscat, \_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp, wcscmp, \_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcoll \(Funciones\)](../../c-runtime-library/strcoll-functions.md)   
 [strcpy, wcscpy, \_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strrchr, wcsrchr, \_mbsrchr, \_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset, \_strset\_l, \_wcsset, \_wcsset\_l, \_mbsset, \_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn, wcsspn, \_mbsspn, \_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)
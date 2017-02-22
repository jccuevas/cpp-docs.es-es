---
title: "_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsnbcnt_l"
  - "_mbsnccnt"
  - "_wcsncnt"
  - "_strncnt"
  - "_mbsnccnt_l"
  - "_mbsnbcnt"
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
  - "_mbsnbcnt"
  - "wcsncnt"
  - "_tcsnbcnt"
  - "_mbsnccnt"
  - "_ftcsnbcnt"
  - "mbsnbcnt"
  - "strncnt"
  - "mbsnbcnt_l"
  - "mbsnccnt_l"
  - "mbsnccnt"
  - "_strncnt"
  - "_wcsncnt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsnbcnt (función)"
  - "_mbsnbcnt_l (función)"
  - "_mbsnccnt (función)"
  - "_mbsnccnt_l (función)"
  - "_strncnt (función)"
  - "_tcsnbcnt (función)"
  - "_wcsncnt (función)"
  - "mbsnbcnt (función)"
  - "mbsnbcnt_l (función)"
  - "mbsnccnt (función)"
  - "mbsnccnt_l (función)"
  - "strncnt (función)"
  - "tcsnbcnt (función)"
  - "wcsncnt (función)"
ms.assetid: 2a022e9e-a307-4acb-a66b-e56e5357f848
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# _strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve el número de caracteres o bytes de un recuento especificado.  
  
> [!IMPORTANT]
>  `_mbsnbcnt`, `_mbsnbcnt_l`, `_mbsnccnt` y `_mbsnccnt_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
size_t _strncnt(  
   const char *str,  
   size_t count  
);  
size_t _wcsncnt(  
   const wchar_t *str,  
   size_t count  
);  
size_t _mbsnbcnt(  
   const unsigned char *str,  
   size_t count   
);  
size_t _mbsnbcnt_l(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
size_t _mbsnccnt(  
   const unsigned char *str,  
   size_t count  
);  
size_t _mbsnccnt_l(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
  
```  
  
#### Parámetros  
 `str`  
 Cadena que se va a examinar.  
  
 `count`  
 Número de caracteres o bytes que se van a examinar en `str`.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `_mbsnbcnt` y `_mbsnbcnt_l` devuelven el número de bytes que se encuentran en el primer `count` de caracteres multibyte de `str`.  `_mbsnccnt` y `_mbsnccnt_l` devuelven el número de caracteres que se encuentran en el primer `count` de bytes de `str`.  Si se encuentra un carácter nulo antes de que el examen de `str` haya terminado, devuelven el número de bytes o caracteres encontrados antes del carácter nulo.  Si `str` consta de menos caracteres o bytes que `count`, devuelven el número de caracteres o bytes de la cadena.  Si `count` es menor que cero, devuelven 0.  En versiones anteriores, estas funciones tenían un valor devuelto de tipo `int` en lugar de `size_t`.  
  
 `_strncnt` devuelve el número de caracteres de los primeros bytes de `count` de la cadena `str` de un solo byte.  `_wcsncnt` devuelve el número de caracteres de los primeros caracteres anchos de `count` de cadena de caracteres anchos `str`.  
  
## Comentarios  
 `_mbsnbcnt` y `_mbsnbcnt_l` cuentan el número de bytes que se encuentran en el primer `count` de caracteres multibyte de `str`.  `_mbsnbcnt` y `_mbsnbcnt_l` reemplazan `mtob` y deben usarse en lugar de `mtob`.  
  
 `_mbsnccnt` y `_mbsnccnt_l` cuentan el número de caracteres que se encuentran en el primer `count` de bytes de `str`.  Si `_mbsnccnt` y `_mbsnccnt_l` encuentran un valor NULL en el segundo byte de un carácter de doble byte, el primer byte también se considera NULL y no se incluye en el valor de recuento devuelto.  `_mbsnccnt` y `_mbsnccnt_l` reemplazan `btom` y deben usarse en lugar de `btom`.  
  
 Si `str` es un puntero nulo o `count` es 0, estas funciones invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md), `errno` se establece en `EINVAL` y la función devuelve 0.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en su lugar.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|------------|-------------------------------------|---------------------|------------------------|  
|`_tcsnbcnt`|`_strncnt`|`_mbsnbcnt`|`_wcsncnt`|  
|`_tcsnccnt`|`_strncnt`|`_mbsnbcnt`|`n/a`|  
|`_wcsncnt`|`n/a`|`n/a`|`_mbsnbcnt`|  
|`_wcsncnt`|`n/a`|`n/a`|`_mbsnccnt`|  
|`n/a`|`n/a`|`_mbsnbcnt_l`|`_mbsnccnt_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbsnbcnt`|\<mbstring.h\>|  
|`_mbsnbcnt_l`|\<mbstring.h\>|  
|`_mbsnccnt`|\<mbstring.h\>|  
|`_mbsnccnt_l`|\<mbstring.h\>|  
|`_strncnt`|\<tchar.h\>|  
|`_wcsncnt`|\<tchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_mbsnbcnt.c  
  
#include  <mbstring.h>  
#include  <stdio.h>  
  
int main( void )  
{  
   unsigned char str[] = "This is a multibyte-character string.";  
   unsigned int char_count, byte_count;  
   char_count = _mbsnccnt( str, 10 );  
   byte_count = _mbsnbcnt( str, 10 );  
   if ( byte_count - char_count )  
      printf( "The first 10 characters contain %d multibyte characters\n", char_count );  
   else  
      printf( "The first 10 characters are single-byte.\n");  
}  
```  
  
## Resultados  
  
```  
The first 10 characters are single-byte.  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbsnbcat, \_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)
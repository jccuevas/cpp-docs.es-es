---
title: "strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l | Microsoft Docs"
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
  - "strxfrm"
  - "_wcsxfrm_l"
  - "_strxfrm_l"
  - "wcsxfrm"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "strxfrm"
  - "_tcsxfrm"
  - "wcsxfrm"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_strxfrm_l (función)"
  - "_tcsxfrm (función)"
  - "_wcsxfrm_l (función)"
  - "comparación de cadenas [C++], transformar cadenas"
  - "cadenas [C++], comparar configuración regional"
  - "strxfrm (función)"
  - "strxfrm_l (función)"
  - "tcsxfrm (función)"
  - "wcsxfrm (función)"
  - "wcsxfrm_l (función)"
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Transforma una cadena basada en información configuración regional\- concreta.  
  
## Sintaxis  
  
```  
size_t strxfrm(  
   char *strDest,  
   const char *strSource,  
   size_t count   
);  
size_t wcsxfrm(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count   
);  
size_t _strxfrm_l(  
   char *strDest,  
   const char *strSource,  
   size_t count,  
   _locale_t locale  
);  
size_t wcsxfrm_l(  
   wchar_t *strDest,  
   const wchar_t *strSource,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `strDest`  
 Cadena de destino.  
  
 `strSource`  
 Cadena de origen.  
  
 `count`  
 Número máximo de caracteres al lugar de *`strDest`.*  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve la longitud de la cadena transformada, sin contar el carácter null de terminación.  Si el valor devuelto es mayor o igual que `count`, el contenido de `strDest` es imprevisible.  En un error, cada función establece `errno` y devuelve `INT_MAX`.  Para un carácter no válido, `errno` se establece en `EILSEQ`.  
  
## Comentarios  
 La función de `strxfrm` transforma la cadena indicada por a `strSource` en un nuevo formulario hace que se almacene en `strDest`.  No más que los caracteres de `count` , incluido el carácter null, se transforman y se colocan en la cadena resultante.  La transformación se crea utilizando el valor de categoría de `LC_COLLATE` de la configuración regional.  Para obtener más información sobre `LC_COLLATE`, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  `strxfrm` utiliza la configuración regional actual para su comportamiento configuración regional\-dependiente; `_strxfrm_l` es idéntico pero utiliza la configuración regional pasado en lugar de la configuración regional actual.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Después de la transformación, una llamada a `strcmp` con las dos cadenas transformadas produce los resultados idénticos a los de una llamada a `strcoll` aplicada a las dos cadenas originales.  Como con `strcoll` y `stricoll`, `strxfrm` controla automáticamente las cadenas de multibyte\- carácter según corresponda.  
  
 `wcsxfrm` es una versión con caracteres anchos de `strxfrm`; los argumentos de cadena de `wcsxfrm` son punteros de carácter ancho.  Para `wcsxfrm`, después de la transformación de la cadena, una llamada a `wcscmp` con las dos cadenas transformadas produce los resultados idénticos a los de una llamada a `wcscoll` aplicada a las dos cadenas originales.  Por lo demás, `wcsxfrm` y `strxfrm` se comportan de forma idéntica.  `wcsxfrm` utiliza la configuración regional actual para su comportamiento configuración regional\-dependiente; `_wcsxfrm_l` utiliza la configuración regional pasado en lugar de la configuración regional actual.  
  
 Estas funciones validan sus parámetros.  Si `strSource` es un puntero NULL, o `strDest` es un puntero nulo \(a menos que el recuento es cero\), o si `count` es mayor que `INT_MAX`, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md) .  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `INT_MAX`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsxfrm`|`strxfrm`|`strxfrm`|`wcsxfrm`|  
|`_tcsxfrm_l`|`_strxfrm_l`|`_strxfrm_l`|`_wcsxfrm_l`|  
  
 En la configuración regional “c”, el orden de los caracteres del juego de caracteres \(juego de caracteres ASCII\) es igual que el orden lexicográfico de caracteres.  Sin embargo, en configuraciones regionales, el orden de los caracteres del juego de caracteres puede diferir del orden lexicográfico de caracteres.  Por ejemplo, en algunas configuraciones regionales europeas, el carácter “a” \(valor 0x61\) precede el carácter '&\#x00E4; '\(valor 0xE4\) en el juego de caracteres, pero el carácter “ä” precede el carácter “a” lexicográficamente.  
  
 En configuraciones regionales para las que el juego de caracteres y el orden lexicográfico de caracteres difieren, utilice `strxfrm` en cadenas originales y después `strcmp` en las cadenas resultantes de generar una comparación lexicográfica de cadenas según el valor actual de la categoría de `LC_COLLATE` de la configuración regional.  Por tanto, comparar dos cadenas lexicográficamente en la configuración regional anterior, utilice `strxfrm` en cadenas originales, entonces `strcmp` en las cadenas resultantes.  Como alternativa, puede utilizar `strcoll` en lugar de `strcmp` en cadenas originales.  
  
 `strxfrm` es básicamente un contenedor de [LCMapString](http://msdn.microsoft.com/library/windows/desktop/dd318700) con `LCMAP_SORTKEY`.  
  
 El valor de la expresión siguiente es el tamaño de la matriz necesario para contener la transformación de `strxfrm` de la cadena de origen:  
  
```  
1 + strxfrm( NULL, string, 0 )  
```  
  
 En la configuración regional “c” se utiliza solo, `strxfrm` es equivalente a la siguiente:  
  
```  
strncpy( _string1, _string2, _count );  
return( strlen( _string1 ) );  
```  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strxfrm`|\<string.h\>|  
|`wcsxfrm`|\<string.h\> o \<wchar.h\>|  
|`_strxfrm_l`|\<string.h\>|  
|`_wcsxfrm_l`|\<string.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [strcoll \(Funciones\)](../../c-runtime-library/strcoll-functions.md)   
 [strcmp, wcscmp, \_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp, wcsncmp, \_mbsncmp, \_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)
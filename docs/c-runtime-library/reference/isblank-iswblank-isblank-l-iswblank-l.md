---
title: "isblank, iswblank, _isblank_l, _iswblank_l | Microsoft Docs"
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
  - "isblank"
  - "_isblank_l"
  - "iswblank"
  - "_iswblank_l"
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
  - "_iswblank_l"
  - "isblank"
  - "_istblank_l"
  - "_istblank"
  - "_isblank_l"
  - "iswblank"
dev_langs: 
  - "C++"
ms.assetid: 33ce96c0-f387-411a-8283-c3d2a69e56bd
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# isblank, iswblank, _isblank_l, _iswblank_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un entero representa un carácter en blanco.  
  
## Sintaxis  
  
```  
int isblank(  
   int c   
);  
int iswblank(  
   wint_t c   
);  
int _isblank_l(  
   int c,  
   _locale_t locale  
);  
int _iswblank_l(  
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `c`  
 Entero que se va a probar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cada una de estas rutinas devuelve un valor distinto de cero si `c` es una representación determinada de un espacio o un carácter de tabulación horizontal, o si es una de un conjunto de caracteres específico de la configuración regional que se utiliza para separar palabras de una línea de texto.  `isblank` devuelve un valor distinto de cero si `c` es un carácter de espacio \(0x20\) o el carácter de tabulación horizontal \(0x09\).  El resultado de la condición de prueba para las funciones `isblank` depende de la configuración de la categoría `LC_CTYPE` de la configuración regional; para obtener más información, vea [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual del comportamiento dependiente de la configuración regional; las versiones que tienen el sufijo `_l` son idénticas salvo que usan el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 `iswblank` devuelve un valor distinto de cero si `c` es un carácter ancho que corresponde a un espacio estándar o un carácter de tabulación horizontal.  
  
 El comportamiento de `isblank` e `_isblank_l` es indefinido si `c` no se encuentra al final del archivo o en el intervalo de 0 a 0xFF, incluidos.  Cuando se usa una biblioteca CRT de depuración y `c` no es uno de estos valores, las funciones generan una aserción.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_istblank`|`isblank`|[\_ismbcblank](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswblank`|  
|`_istblank_l`|`_isblank_l`|[\_ismbcblank\_l](../../c-runtime-library/reference/ismbcgraph-functions.md)|`_iswblank_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`isblank`|\<ctype.h\>|  
|`iswblank`|\<ctype.h\> o \<wchar.h\>|  
|`_isblank_l`|\<ctype.h\>|  
|`_iswblank_l`|\<ctype.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 [System::Char::IsWhiteSpace](https://msdn.microsoft.com/en-us/library/system.char.iswhitespace.aspx)  
  
## Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)
---
title: "isprint, iswprint, _isprint_l, _iswprint_l | Microsoft Docs"
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
  - "iswprint"
  - "isprint"
  - "_isprint_l"
  - "_iswprint_l"
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
  - "iswprint"
  - "_istprint"
  - "isprint"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_isprint_l (función)"
  - "_istprint (función)"
  - "_iswprint_l (función)"
  - "isprint (función)"
  - "isprint_l (función)"
  - "istprint (función)"
  - "iswprint (función)"
  - "iswprint_l (función)"
ms.assetid: a8bbcdb0-e8d0-4d8c-ae4e-56d3bdee6ca3
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# isprint, iswprint, _isprint_l, _iswprint_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un entero representa un carácter imprimible.  
  
## Sintaxis  
  
```  
int isprint(  
   int c   
);  
int iswprint(  
   wint_t c   
);  
int _isprint_l(  
   int c,  
   _locale_t locale  
);  
int _iswprint_l(  
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
 Cada una de estas rutinas devuelve un valor distinto de cero si `c` es una representación concreta de un carácter imprimible.  `isprint` devuelve un valor distinto de cero si `c` es un carácter imprimible, incluido el carácter de espacio \(0x20 – 0x7E\).  `iswprint` devuelve un valor distinto de cero si `c` es un carácter ancho imprimible, incluido el carácter ancho de espacio.  Cada una de estas rutinas devuelve 0 si `c` no cumple la condición de prueba.  
  
 El resultado de la condición de prueba para estas funciones depende del valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual del comportamiento dependiente de la configuración regional; las versiones que tienen el sufijo `_l` son idénticas salvo que usan el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 El comportamiento de `isprint` e `_isprint_l` es indefinido si `c` no se encuentra al final del archivo ni en el intervalo de 0 a 0xFF, incluidos.  Cuando se usa una biblioteca CRT de depuración y `c` no es uno de estos valores, las funciones generan una aserción.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_unicode definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|**\_** `istprint`|`isprint`|[\_ismbcprint](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswprint`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`isprint`|\<ctype.h\>|  
|`iswprint`|\<ctype.h\> o \<wchar.h\>|  
|`_isprint_l`|\<ctype.h\>|  
|`_iswprint_l`|\<ctype.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)
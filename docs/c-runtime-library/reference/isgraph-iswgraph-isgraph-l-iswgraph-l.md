---
title: "isgraph, iswgraph, _isgraph_l, _iswgraph_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "isgraph"
  - "iswgraph"
  - "_iswgraph_l"
  - "_isgraph_l"
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
  - "_isgraph_l"
  - "_iswgraph_l"
  - "_ismbcgraph_l"
  - "Isgraph"
  - "_istgraph_l"
  - "_istgraph"
  - "iswgraph"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_isgraph_l (función)"
  - "_ismbcgraph_l (función)"
  - "_istgraph (función)"
  - "_istgraph_l (función)"
  - "_iswgraph_l (función)"
  - "isgraph (función)"
  - "istgraph (función)"
  - "iswgraph (función)"
ms.assetid: 531a5f34-4302-4d0a-8a4f-b7ea150ad941
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# isgraph, iswgraph, _isgraph_l, _iswgraph_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un entero representa un carácter gráfico.  
  
## Sintaxis  
  
```  
int isgraph(  
   int c   
);  
int iswgraph(  
   wint_t c   
);  
int _isgraph_l(  
   int c,  
   _locale_t locale  
);  
int _iswgraph_l(  
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `c`  
 Entero que se va a probar.  
  
## Valor devuelto  
 Cada una de estas rutinas devuelve un valor distinto de cero si `c` es una representación concreta de un carácter imprimible que no sea un espacio.  `isgraph` devuelve un valor distinto de cero si `c` es un carácter imprimible que no sea un espacio.  `iswgraph` devuelve un valor distinto de cero si `c` es un carácter ancho imprimible que no sea un espacio de carácter ancho.  Cada una de estas rutinas devuelve 0 si `c` no cumple la condición de prueba.  
  
 Las versiones de estas funciones con el sufijo `_l` usan la configuración regional que se pasa en lugar de la configuración regional de su comportamiento dependiente de la configuración regional.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 El comportamiento de `isgraph` e `_isgraph_l` es indefinido si `c` no se encuentra al final del archivo ni en el intervalo de 0 a 0xFF, incluidos.  Cuando se usa una biblioteca CRT de depuración y `c` no es uno de estos valores, las funciones generan una aserción.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_istgraph`|`isgraph`|[\_ismbcgraph](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswgraph`|  
|`_istgraph_l`|`_isgraph_l`|[\_ismbcgraph\_l](../../c-runtime-library/reference/ismbcgraph-functions.md)|`_iswgraph_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`isgraph`|\<ctype.h\>|  
|`iswgraph`|\<ctype.h\> o \<wchar.h\>|  
|`_isgraph_l`|\<ctype.h\>|  
|`_iswgraph_l`|\<ctype.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)
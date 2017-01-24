---
title: "ispunct, iswpunct, _ispunct_l, _iswpunct_l | Microsoft Docs"
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
  - "ispunct"
  - "_iswpunct_l"
  - "iswpunct"
  - "_ispunct_l"
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
  - "iswpunct"
  - "_istpunct"
  - "ispunct"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ispunct_l (función)"
  - "_istpunct (función)"
  - "_iswpunct_l (función)"
  - "ispunct (función)"
  - "ispunct_l (función)"
  - "istpunct (función)"
  - "iswpunct (función)"
  - "iswpunct_l (función)"
ms.assetid: 94403240-85c8-40a4-9c2b-e3e95c729c76
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ispunct, iswpunct, _ispunct_l, _iswpunct_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un entero representa un carácter de puntuación.  
  
## Sintaxis  
  
```  
int ispunct(  
   int c   
);  
int iswpunct(  
   wint_t c   
);  
int _ispunct_l(  
   int c,  
   _locale_t locale  
);  
int _iswpunct_l(  
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
 Cada una de estas rutinas devuelve un valor distinto de cero si `c` es una representación concreta de un carácter de puntuación.  `ispunct` devuelve un valor distinto de cero para todo carácter imprimible que no sea un carácter de espacio o un carácter para el que `isalnum` es distinto de cero.  `iswpunct` devuelve un valor distinto de cero para cualquier carácter ancho imprimible que no sea ni el carácter ancho de espacio ni un carácter ancho para el que `iswalnum` es distinto de cero.  Cada una de estas rutinas devuelve 0 si `c` no cumple la condición de prueba.  
  
 El resultado de la condición de prueba para la función `ispunct` depende del valor de la categoría `LC_CTYPE` de la configuración regional; para obtener más información, vea [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual del comportamiento dependiente de la configuración regional; las versiones que tienen el sufijo `_l` son idénticas salvo que usan el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 El comportamiento de `ispunct` e `_ispunct_l` es indefinido si `c` no se encuentra al final del archivo ni en el intervalo de 0 a 0xFF, incluidos.  Cuando se usa una biblioteca CRT de depuración y `c` no es uno de estos valores, las funciones generan una aserción.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|**\_** `istpunct`|`ispunct`|[\_ismbcpunct](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswpunct`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`ispunct`|\<ctype.h\>|  
|`iswpunct`|\<ctype.h\> o \<wchar.h\>|  
|`_ispunct_l`|\<ctype.h\>|  
|`_iswpunct_l`|\<ctype.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)
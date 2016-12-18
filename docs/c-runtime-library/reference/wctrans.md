---
title: "wctrans | Microsoft Docs"
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
  - "wctrans"
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
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wctrans"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "códigos de caracteres, wctrans"
  - "caracteres, códigos"
  - "caracteres, convertir"
  - "wctrans (función)"
ms.assetid: 215404bf-6d60-489c-9ae9-880e6b586162
caps.latest.revision: 13
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wctrans
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina una asignación a partir de un conjunto de códigos de carácter a otro.  
  
## Sintaxis  
  
```  
wctrans_t wctrans(  
   const char *property   
);  
```  
  
#### Parámetros  
 `property`  
 Una cadena que especifica una de las transformaciones válidas.  
  
## Valor devuelto  
 Si la categoría de `LC_CTYPE` de la configuración regional actual no define una asignación cuyo nombre coincida con la cadena `property`de propiedades, la función devuelve cero.  De lo contrario, devuelve un valor distinto de cero adecuado para el uso como segundo argumento a una llamada subsiguiente a [towctrans](../../c-runtime-library/reference/towctrans.md).  
  
## Comentarios  
 Esta función determina una asignación a partir de un conjunto de códigos de carácter a otro.  
  
 Los siguientes pares de llamadas tienen el mismo comportamiento en todas las configuraciones regionales, pero es posible definir asignaciones adicionales incluso en la configuración regional “c”:  
  
|Función|Igual que|  
|-------------|---------------|  
|`tolower(`  `c`  `)`|`towctrans(`  `c` `, wctrans("towlower" ) )`|  
|`towupper(`  `c`  `)`|`towctrans(`  `c` `, wctrans( "toupper" ) )`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`wctrans`|\<wctype.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_wctrans.cpp  
// compile with: /EHsc  
// This example determines a mapping from one set of character  
// codes to another.   
  
#include <wchar.h>  
#include <wctype.h>  
#include <stdio.h>  
#include <iostream>  
  
int main()   
{  
    wint_t c = 'a';  
    printf_s("%d\n",c);  
  
    wctrans_t i = wctrans("toupper");  
    printf_s("%d\n",i);  
  
    wctrans_t ii = wctrans("towlower");  
    printf_s("%d\n",ii);  
  
    wchar_t wc = towctrans(c, i);  
    printf_s("%d\n",wc);  
}  
```  
  
  **97**  
**1**  
**0**  
**65**   
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)
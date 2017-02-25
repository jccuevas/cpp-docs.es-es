---
title: "_lrotl, _lrotr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_lrotl"
  - "_lrotr"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "lrotr"
  - "lrotl"
  - "_lrotr"
  - "_lrotl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_lrotl (función)"
  - "_lrotr (función)"
  - "bits"
  - "bits, rotar"
  - "lrotl (función)"
  - "lrotr (función)"
  - "girar bits"
ms.assetid: d42f295b-35f9-49d2-9ee4-c66896ffe68e
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# _lrotl, _lrotr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Activa los bits a la izquierda \(`_lrotl`\) o a la derecha \(`_lrotr`\).  
  
## Sintaxis  
  
```  
  
      unsigned long _lrotl(  
   unsigned long value,  
   int shift   
);  
unsigned long _lrotr(  
   unsigned long value,  
   int shift   
);  
```  
  
#### Parámetros  
 *valor*  
 Valor que se activará.  
  
 `shift`  
 Número de bits para el *valor*.  
  
## Valor devuelto  
 Ambas funciones devuelven el valor convertido.  No se devuelve ningún error.  
  
## Comentarios  
 Las funciones de `_lrotl` y de `_lrotr` giran *valor* por los bits de `shift` .  `_lrotl` gira el valor está desusado.  `_lrotr` gira la derecha del valor.  Los bits de ajuste de las funciones activados de un extremo *de valor* a otro proceso.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_lrotl`|\<stdlib.h\>|  
|`_lrotr`|\<stdlib.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_lrot.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   unsigned long val = 0x0fac35791;  
  
   printf( "0x%8.8lx rotated left eight times is 0x%8.8lx\n",   
            val, _lrotl( val, 8 ) );  
   printf( "0x%8.8lx rotated right four times is 0x%8.8lx\n",   
            val, _lrotr( val, 4 ) );  
}  
```  
  
## Resultados  
  
```  
0xfac35791 rotated left eight times is 0xc35791fa  
0xfac35791 rotated right four times is 0x1fac3579  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [\_rotl, \_rotl64, \_rotr, \_rotr64](../../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)
---
title: "_rotl, _rotl64, _rotr, _rotr64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_rotr64"
  - "_rotl"
  - "_rotr"
  - "_rotl64"
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
  - "_rotr64"
  - "rotl64"
  - "_rotl64"
  - "rotr64"
  - "rotr"
  - "_rotr"
  - "_rotl"
  - "rotl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_rotl (función)"
  - "_rotl64 (función)"
  - "_rotr (función)"
  - "_rotr64 (función)"
  - "bits, rotar"
  - "girar bits"
  - "rotl (función)"
  - "rotl64 (función)"
  - "rotr (función)"
  - "rotr64 (función)"
ms.assetid: cfce439b-366f-4584-8ab1-d527b13fcfc6
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _rotl, _rotl64, _rotr, _rotr64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Activa los bits a la izquierda \(`_rotl`\) o a la derecha \(`_rotr`\).  
  
## Sintaxis  
  
```  
  
      unsigned int _rotl(  
   unsigned int value,  
   int shift   
);  
unsigned __int64 _rotl64(  
   unsigned __int64 value,   
   int shift  
);  
unsigned int _rotr(  
   unsigned int value,  
   int shift   
);  
unsigned __int64 _rotr64(  
   unsigned __int64 value,  
   int shift  
);  
```  
  
#### Parámetros  
 *valor*  
 Valor que se activará.  
  
 `shift`  
 Número de bits que se va a mover.  
  
## Valor devuelto  
 El valor convertido.  No se devuelve ningún error.  
  
## Comentarios  
 Las funciones de `_rotl` y de `_rotr` gira *el valor* sin signo por los bits de `shift` .  `_rotl` gira el valor está desusado.  `_rotr` gira la derecha del valor.  Los bits de ajuste de las funciones activados de un extremo *de valor* a otro proceso.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|**\_rotl, \_rotl64**|\<stdlib.h\>|  
|**\_rotr, \_rotr64**|\<stdlib.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_rot.c  
/* This program shifts values to rotate an integer.  
 */  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   unsigned val = 0x0fd93;  
   __int64 val2 = 0x0101010101010101;  
  
   printf( "0x%4.4x rotated left three times is 0x%4.4x\n",   
           val, _rotl( val, 3 ) );  
   printf( "0x%4.4x rotated right four times is 0x%4.4x\n",   
           val, _rotr( val, 4 ) );  
  
   printf( "%I64x rotated left three times is %I64x\n",  
           val2, _rotl64( val2, 3 ) );  
   printf( "%I64x rotated right four times is %I64x\n",   
           val2, _rotr64( val2, 4 ) );  
}  
```  
  
## Resultados  
  
```  
0xfd93 rotated left three times is 0x7ec98  
0xfd93 rotated right four times is 0x30000fd9  
101010101010101 rotated left three times is 808080808080808  
101010101010101 rotated right four times is 1010101010101010  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [\_lrotl, \_lrotr](../../c-runtime-library/reference/lrotl-lrotr.md)
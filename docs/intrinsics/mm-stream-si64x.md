---
title: "_mm_stream_si64x | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_stream_si64x"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "movnti (instrucción)"
  - "_mm_stream_si64x (función intrínseca)"
ms.assetid: 114c2cd0-085f-41aa-846e-87bdd56c9ee7
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _mm_stream_si64x
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera la instrucción de MOVNTI.  Escribe los datos en `Source` a una ubicación de memoria especificada por `Dest`, sin la contaminación de cachés.  
  
## Sintaxis  
  
```  
void _mm_stream_si64x(   
   __int64 * Dest,   
   __int64 Source   
);  
```  
  
#### Parámetros  
 \[out\] `Dest`  
 Un puntero a la ubicación para escribir los datos de origen a.  
  
 \[in\] `Source`  
 Los datos que se va a escribir.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`_mm_stream_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Esta rutina sólo está disponible como intrínseco.  
  
## Ejemplo  
  
```  
// _mm_stream_si64x.c  
// processor: x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_mm_stream_si64x)  
  
int main()  
{  
    __int64 val = 0xFFFFFFFFFFFFI64;  
    __int64 a[10];  
  
    memset(a, 0, sizeof(a));  
    _mm_stream_si64x(a+1, val);  
    printf_s( "%I64x %I64x %I64x %I64x", a[0], a[1], a[2], a[3]);   
}  
```  
  
  **0 ffffffffffff 0 0**   
## Específico de Microsoft de FINAL  
  
## Vea también  
 [Cache Support for Streaming SIMD Extensions 2 Integer Operations](http://msdn.microsoft.com/es-es/a9c9b42f-de9e-4374-aeb6-5f65bfb669b6)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
---
title: "_mm_cvtsi64x_ss | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_cvtsi64x_ss"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cvtsi2ss (instrucción)"
  - "_mm_cvtsi64x_ss (función intrínseca)"
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _mm_cvtsi64x_ss
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] extendidas versión de entero de 64 bits convert a la instrucción de valor de punto flotante de precisión sencilla de Escalar \(`cvtsi2ss`\).  
  
## Sintaxis  
  
```  
__m128 _mm_cvtsi64x_ss(   
   __m128 a,   
   __int64 b   
);  
```  
  
#### Parámetros  
 \[in\] `a`  
 Una estructura de `__m128` que contiene cuatro valores de punto flotante de precisión simple.  
  
 \[in\] `b`  
 Un entero de 64 bits que se convertirá en un valor de punto flotante.  
  
## Valor devuelto  
 Una estructura de `__m128` cuyo primer valor de punto flotante es el resultado de la conversión.  Los otros tres valores se copian sin cambiar de `a`.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`_mm_cvtsi64x_ss`|x64|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 La estructura de `__m128` representa un registro de XMM, por lo que este intrínseco permite que el valor `b` memoria del sistema es movido a un registro de XMM.  
  
 Esta rutina sólo está disponible como intrínseco.  
  
## Ejemplo  
  
```  
// _mm_cvtsi64x_ss.cpp  
// processor: x64  
  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtsi64x_ss)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    a.m128_f32[0] = 0;  
    a.m128_f32[1] = 0;  
    a.m128_f32[2] = 0;  
    a.m128_f32[3] = 0;  
    a = _mm_cvtsi64x_ss(a, b);  
  
    printf_s( "%lf %lf %lf %lf\n",  
              a.m128_f32[0], a.m128_f32[1],   
              a.m128_f32[2], a.m128_f32[3] );  
}  
```  
  
  **54.000000 0.000000 0.000000 0.000000**   
## Específico de Microsoft de FINAL  
  
## Vea también  
 [\_\_m128](../cpp/m128.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
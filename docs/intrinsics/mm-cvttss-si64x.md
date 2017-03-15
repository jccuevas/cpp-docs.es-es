---
title: "_mm_cvttss_si64x | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_cvttss_si64x"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mm_cvttss_si64x (función intrínseca)"
  - "cvttss2si (instrucción)"
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _mm_cvttss_si64x
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Emite x64 extendidas versión convert con el número de punto flotante de precisión sencilla de Truncation a la instrucción entera de 64 bits \(de`cvttss2si`\).  
  
## Sintaxis  
  
```  
__int64 _mm_cvttss_si64x(   
   __m128 value   
);  
```  
  
#### Parámetros  
 \[in\] `value`  
 Una estructura de `__m128` que contiene valores de punto flotante de precisión simple.  
  
## Valor devuelto  
 El resultado de la conversión del primer valor de punto flotante a un entero de 64 bits.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`_mm_cvttss_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Intrínseco diferencia de `_mm_cvtss_si64x` sólo en que las conversiones inexactas se truncadas hacia cero.  Dado que la estructura de `__m128` representa un registro de XMM, la instrucción generada se mueve datos de un registro de XMM a la memoria del sistema.  
  
 Esta rutina sólo está disponible como intrínseco.  
  
## Ejemplo  
  
```  
// _mm_cvttss_si64x.cpp  
// processor: x64  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvttss_si64x)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    // _mm_load_ps requires an aligned buffer.  
    __declspec(align(16)) float af[4] = { 101.5, 200.75,  
                                          300.5, 400.5 };  
  
    // Load a with the floating point values.  
    // The values will be copied to the XMM registers.  
    a = _mm_load_ps(af);  
  
    // Extract the first element of a and convert to an integer  
    b = _mm_cvttss_si64x(a);  
  
    printf_s("%I64d\n", b);  
}  
```  
  
  **101**   
## Específico de Microsoft de FINAL  
  
## Vea también  
 [\_\_m128](../cpp/m128.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
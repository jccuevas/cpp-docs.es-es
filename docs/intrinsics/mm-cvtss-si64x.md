---
title: "_mm_cvtss_si64x | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_cvtss_si64x"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cvtss2si (función intrínseca)"
  - "_mm_cvtss_si64x (función intrínseca)"
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
caps.latest.revision: 13
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mm_cvtss_si64x
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] extendidas versión de número de Punto Flotante de precisión sencilla de Scalar convert a la instrucción entera de 64 bits \(de`cvtss2si`\).  
  
## Sintaxis  
  
```  
__int64 _mm_cvtss_si64x(   
   __m128 value   
);  
```  
  
#### Parámetros  
 \[in\] `value`  
 Una estructura de `__m128` que contiene punto\-valores de punto flotante.  
  
## Valor devuelto  
 Un entero de 64 bits, el resultado de la conversión del primer valor de punto flotante a un entero.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`_mm_cvtss_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 El primer elemento del valor de la estructura se convierte a un entero y devuelto.  Los bits del control que redondean en MXCSR se utilizan para determinar el comportamiento de redondeo.  El modo de redondeo predeterminado es alrededor cercana, se producían el número par si la parte decimal es 0,5.  Dado que la estructura de `__m128` representa un registro de XMM, este intrínseco contiene un valor de registro y de escrituras de XMM él la memoria del sistema.  
  
 Esta rutina sólo está disponible como intrínseco.  
  
## Ejemplo  
  
```  
// _mm_cvtss_si64x.cpp  
// processor: x64  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtss_si64x)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    // _mm_load_ps requires an aligned buffer.  
    __declspec(align(16)) float af[4] =  
                           { 101.25, 200.75, 300.5, 400.5 };  
  
    // Load a with the floating point values.  
    // The values will be copied to the XMM registers.  
    a = _mm_load_ps(af);  
  
    // Extract the first element of a and convert to an integer  
    b = _mm_cvtss_si64x(a);  
  
    printf_s("%I64d\n", b);  
}  
```  
  
  **101**   
## Específico de Microsoft de FINAL  
  
## Vea también  
 [\_\_m128d](../cpp/m128d.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
---
title: "_mm_stream_ss | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_stream_ss"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "movntss (instrucción)"
  - "_mm_stream_ss (función intrínseca)"
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _mm_stream_ss
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Escribe datos de 32 bits a una ubicación de memoria sin la contaminación de cachés.  
  
## Sintaxis  
  
```  
void _mm_stream_ss(  
   float * Dest,  
   __m128 Source  
);  
```  
  
#### Parámetros  
 \[out\] `Dest`  
 Un puntero a la ubicación donde se escriben los datos de origen.  
  
 \[in\] `Source`  
 Número de 128 bits que contiene el valor de `float` que se escriba en los bits inferior 32.  
  
## Valor devuelto  
 Ninguno.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`_mm_stream_ss`|SSE4a|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Este intrínseco genera la instrucción de `movntss`.  Para determinar la compatibilidad de hardware para esta instrucción, llame a intrínsecos de `__cpuid` con `InfoType=0x80000001`y compruebe el bit 6 de `CPUInfo[2] (ECX)`.  Este bit es 1 cuando se admite la instrucción, de lo contrario es 0.  
  
 Si ejecuta el código que utiliza intrínsecos de `_mm_stream_ss` en el hardware que no admite la instrucción de `movntss` , los resultados son imprevisibles.  
  
## Ejemplo  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
int main()  
{  
    __m128 vals;  
    float f[4];  
  
    f[0] = -1.;  
    f[1] = -2.;  
    f[2] = -3.;  
    f[3] = -4.;  
    vals.m128_f32[0] = 0.;  
    vals.m128_f32[1] = 1.;  
    vals.m128_f32[2] = 2.;  
    vals.m128_f32[3] = 3.;  
    _mm_stream_ss(&f[3], vals);  
    cout << "f[0] = " << f[0] << ", f[1] = " << f[1] << endl;  
    cout << "f[1] = " << f[1] << ", f[3] = " << f[3] << endl;  
}  
  
```  
  
  **f \[0\] \= \-1, f \-2 de f \[1\] \= \[2\] \= \-3, f \[3\] \= 3**   
## Específico de Microsoft de FINAL  
 Copyright 2007 por Advanced Micro Devices, Inc reservados todos los derechos.  Optimizado con permiso de Advanced Micro Devices, Inc  
  
## Vea también  
 [\_mm\_stream\_sd](../intrinsics/mm-stream-sd.md)   
 [\_mm\_stream\_ps](http://msdn.microsoft.com/es-es/f7af2f19-c0d4-43c6-b5f6-a658d2b1d869)   
 [\_mm\_store\_ss](http://msdn.microsoft.com/es-es/dfeeea35-8faf-4f54-8a9e-6723e226fb08)   
 [\_mm\_sfence](http://msdn.microsoft.com/es-es/b6c0d18e-3628-4318-826b-45f66782e870)   
 [Streaming SIMD Extensions that Support the Cache](http://msdn.microsoft.com/es-es/8f03493a-d5f5-4457-892e-0b6540494872)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
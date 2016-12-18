---
title: "_mm_stream_sd | Microsoft Docs"
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
  - "_mm_stream_sd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mm_stream_sd (función intrínseca)"
  - "movntsd (instrucción)"
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
caps.latest.revision: 14
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mm_stream_sd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Escribe datos 64 bits a una ubicación de memoria sin la contaminación de cachés.  
  
## Sintaxis  
  
```  
void _mm_stream_sd(  
   double * Dest,  
   __m128d Source  
);  
```  
  
#### Parámetros  
 \[out\]`Dest`  
 Un puntero a la ubicación donde los datos de origen se escriben.  
  
 \[in\] `Source`  
 Un valor de 128 bits que contiene el valor de `double` que se escriba en los bits inferior 64.  
  
## Valor devuelto  
 Ninguno.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`_mm_stream_sd`|SSE4a|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Este intrínseco genera la instrucción de `movntsd`.  Para determinar la compatibilidad de hardware para esta instrucción, llame a intrínsecos de `__cpuid` con `InfoType=0x80000001` y compruebe el bit 6 de `CPUInfo[2] (ECX)`.  Este bit es 1 si el hardware admite esta instrucción, y 0 de otra manera.  
  
 Si ejecuta el código que utiliza intrínsecos de `_mm_stream_sd` en el hardware que no admite la instrucción de `movntsd` , los resultados son imprevisibles.  
  
## Ejemplo  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
int main()  
{  
    __m128d vals;  
    double d[2];  
  
    d[0] = -1.;  
    d[1] = -2.;  
    vals.m128d_f64[0] = 0.;  
    vals.m128d_f64[1] = 1.;  
    _mm_stream_sd(&d[1], vals);  
    cout << "d[0] = " << d[0] << ", d[1] = " << d[1] << endl;  
}  
  
```  
  
  **d \[0\] \= \-1, d \[1\] \= 1**   
## Específico de Microsoft de FINAL  
 Copyright 2007 por Advanced Micro Devices, Inc reservados todos los derechos.  Optimizado con permiso de Advanced Micro Devices, Inc  
  
## Vea también  
 [\_mm\_stream\_ss](../intrinsics/mm-stream-ss.md)   
 [\_mm\_store\_sd](http://msdn.microsoft.com/es-es/8e672d0d-0a96-45b9-a783-392a2457de42)   
 [\_mm\_sfence](http://msdn.microsoft.com/es-es/b6c0d18e-3628-4318-826b-45f66782e870)   
 [Streaming SIMD Extensions that Support the Cache](http://msdn.microsoft.com/es-es/8f03493a-d5f5-4457-892e-0b6540494872)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
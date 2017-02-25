---
title: "_mm_extract_si64, _mm_extracti_si64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_extracti_si64"
  - "_mm_extract_si64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "extrq (instrucción)"
  - "_mm_extracti_si64 (función intrínseca)"
  - "_mm_extract_si64 (función intrínseca)"
ms.assetid: 459fdd72-cc54-4ee5-bbd5-d2c6067a88e7
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _mm_extract_si64, _mm_extracti_si64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera la instrucción de `extrq` de extraer los bits especificado de los bits de low 64 del primer argumento.  
  
## Sintaxis  
  
```  
__m128i _mm_extract_si64(  
   __m128i Source,  
   __m128i Descriptor  
);  
__m128i _mm_extracti_si64(  
   __m128i Source,  
   int Length,  
   int Index  
);  
```  
  
#### Parámetros  
 \[in\]`Source`  
 Un campo de bits 128 con datos de entrada en los 64 bits inferiores.  
  
 \[in\] `Descriptor`  
 Un campo de bits 128 que describe el campo de bits para extraer.  
  
 \[in\] `Length`  
 Un entero que especifica la longitud de campo para extraer.  
  
 \[in\] `Index`  
 Un entero que especifica el índice del campo para extraer  
  
## Valor devuelto  
 Un campo de bits 128 con el campo extraído en los bits menos significativos.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`_mm_extract_si64`|SSE4a|  
|`_mm_extracti_si64`|SSE4a|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Este intrínseco genera la instrucción de `extrq` de extraer los bits de `Source`. Hay dos versiones de este intrínseco: `_mm_extracti_si64` es la versión inmediata, y `_mm_extract_si64` es el no\-inmediato.  Cada versión extrae de `Source` un campo de bits definido por su longitud y el índice de su menos bit significativo.  Los valores de longitud y de índice son Mod tomada 64, para \-1 y 127 se interpreta como 63.  Si la suma de índice \(reducido\) y la longitud de campo \(baja\) es mayor que 64, los resultados son indefinidos.  Un valor de cero para la longitud de campo se interpreta como 64.  Si el índice de la longitud de campo y el bit es cero, el 63:0 de los bits de `Source` se extraen.  Si la longitud de campo es cero pero el índice de bits es distinto de cero, los resultados son indefinidos.  
  
 En una llamada a \_mm\_extract\_si64, `Descriptor` contiene el índice en 13:8 de bits y la longitud de campo de datos que se extraerán en 5:0 de los bits.  
  
 Si llama a `_mm_extracti_si64` con argumentos que el compilador no puede determinar para ser constantes enteras el compilador genera código para empaquetar estos valores en un registro de XMM \(`Descriptor`\) y llamar a `_mm_extract_si64`.  
  
 Para determinar la compatibilidad de hardware para la instrucción de `extrq` , llame a intrínsecos de `__cpuid` con `InfoType=0x80000001` y compruebe el bit 6 de `CPUInfo[2] (ECX)`.  Este bit será 1 si se admite la instrucción, y 0 de otra manera.  Si ejecuta el código que utiliza este hardware intrínseco que no admite la instrucción de `extrq` , los resultados son imprevisibles.  
  
## Ejemplo  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
union {  
    __m128i m;  
    unsigned __int64 ui64[2];  
} source, descriptor, result1, result2, result3;  
  
int  
main()  
{  
    source.ui64[0] =     0xfedcba9876543210ll;  
    descriptor.ui64[0] = 0x0000000000000b1bll;  
  
    result1.m = _mm_extract_si64 (source.m, descriptor.m);  
    result2.m = _mm_extracti_si64(source.m, 27, 11);  
    result3.ui64[0] = (source.ui64[0] >> 11) & 0x7ffffff;  
  
    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;  
    cout << "result2 = 0x" << result2.ui64[0] << endl;  
    cout << "result3 = 0x" << result3.ui64[0] << endl;  
}  
```  
  
  **result1 \= 0x30eca86 result2 \= 0x30eca86 result3 \= 0x30eca86**   
## Específico de Microsoft de FINAL  
 Copyright 2007 por Advanced Micro Devices, Inc reservados todos los derechos.  Optimizado con permiso de Advanced Micro Devices, Inc  
  
## Vea también  
 [\_mm\_insert\_si64, \_mm\_inserti\_si64](../intrinsics/mm-insert-si64-mm-inserti-si64.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
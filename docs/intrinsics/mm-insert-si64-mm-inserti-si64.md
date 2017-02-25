---
title: "_mm_insert_si64, _mm_inserti_si64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mm_inserti_si64"
  - "_mm_insert_si64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insertq (instrucción)"
  - "_mm_insert_si64 (función intrínseca)"
  - "_mm_inserti_si64 (función intrínseca)"
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _mm_insert_si64, _mm_inserti_si64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera la instrucción de `insertq` de insertar los bits del segundo operando del primer operando.  
  
## Sintaxis  
  
```  
__m128i _mm_insert_si64(  
   __m128i Source1,  
   __m128i Source2  
);  
__m128i _mm_inserti_si64(  
   __m128i Source1,  
   __m128i Source2  
   int Length,  
   int Index  
);  
```  
  
#### Parámetros  
 \[in\]`Source1`  
 Un campo de bits 128 con datos de entrada en los 64 bits inferiores en los que un campo se insertará.  
  
 \[in\] `Source2`  
 Un campo de bits 128 a datos a insertar en los bits bajos.  Para `_mm_insert_si64`, también contiene un campo descriptor en los altos bits.  
  
 \[in\] `Length`  
 Una constante entera que especifica la longitud de campo para insertar.  
  
 \[in\] `Index`  
 Una constante entera que especifica el índice de menos bit significativo del campo en el que los datos se insertarán.  
  
## Valor devuelto  
 Un campo de bits 128 cuyos 64 bits inferiores contienen los bits originales de low 64 de `Source1` con el campo de bits especificado se reemplazan por los bits bajos de `Source2`.  Los 64 bits superiores del valor devuelto son indefinidos.  
  
## Requisitos  
  
|Intrínseco|Arquitectura|  
|----------------|------------------|  
|`_mm_insert_si64`|SSE4a|  
|`_mm_inserti_si64`|SSE4a|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Este intrínseco genera la instrucción de `insertq` de insertar fragmentos de `Source2` en `Source1`.  Hay dos versiones de este intrínseco: `_mm_inserti_si64`, es la versión inmediata, y `_mm_insert_si64` es el no\-inmediato.  Cada versión extrae un campo de bits de una longitud especificada de Source2 y se inserta en Source1.  Los bits extraen son los bits menos significativos de Source2.  El campo Source1 en que estos bits se insertarán está definido por la longitud y el índice del bit menos significativo.  Los valores de longitud y de índice son Mod tomada 64, para \-1 y 127 se interpreta como 63.  Si la suma de \(reducido\) el índice y la longitud de campo \(baja\) es mayor de 64, los resultados son indefinidos.  Un valor de cero para la longitud de campo se interpreta como 64.  Si el índice de la longitud de campo y el bit es cero, el 63:0 de los bits de `Source2` se inserta en `Source1`.  Si la longitud de campo es cero pero el índice de bits es distinto de cero, los resultados son indefinidos.  
  
 En una llamada a \_mm\_insert\_si64, la longitud de campo se contiene en el 77:72 de los bits de Source2 y el índice en 69:64 de bits.  
  
 Si llama a `_mm_inserti_si64`con argumentos que el compilador no puede determinar para ser constantes de tipo entero, el compilador genera código para empaquetar estos valores en un registro de MMX y llamar a `_mm_insert_si64`.  
  
 Para determinar la compatibilidad de hardware para la instrucción de `insertq` llame a intrínsecos de `__cpuid` con `InfoType=0x80000001` y compruebe el bit 6 de `CPUInfo[2] (ECX)`.  Este bit será 1 si se admite la instrucción, y 0 de otra manera.  Si ejecuta el código que utiliza este intrínseco en el hardware que no admite la instrucción de `insertq` , los resultados son imprevisibles.  
  
## Ejemplo  
  
```  
// Compile this sample with: /EHsc  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
union {  
    __m128i m;  
    unsigned __int64 ui64[2];  
} source1, source2, source3, result1, result2, result3;  
  
int  
main()  
{  
  
    __int64 mask;  
  
    source1.ui64[0] = 0xffffffffffffffffll;  
    source2.ui64[0] = 0xfedcba9876543210ll;  
    source2.ui64[1] = 0xc10;  
    source3.ui64[0] = source2.ui64[0];  
  
    result1.m = _mm_insert_si64 (source1.m, source2.m);  
    result2.m = _mm_inserti_si64(source1.m, source3.m, 16, 12);  
    mask = 0xffff << 12;  
    mask = ~mask;  
    result3.ui64[0] = (source1.ui64[0] & mask) |  
                      ((source2.ui64[0] & 0xffff) << 12);  
  
    cout << hex << "result1 = 0x" << result1.ui64[0] << endl;  
    cout << "result2 = 0x" << result2.ui64[0] << endl;  
    cout << "result3 = 0x" << result3.ui64[0] << endl;  
  
}  
```  
  
  **result1 \= 0xfffffffff3210fff result2 \= 0xfffffffff3210fff result3 \= 0xfffffffff3210fff**   
## Específico de Microsoft de FINAL  
 Copyright 2007 por Advanced Micro Devices, Inc reservados todos los derechos.  Optimizado con permiso de Advanced Micro Devices, Inc  
  
## Vea también  
 [\_mm\_extract\_si64, \_mm\_extracti\_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
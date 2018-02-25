---
title: _mm_insert_si64, _mm_inserti_si64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _mm_inserti_si64
- _mm_insert_si64
dev_langs:
- C++
helpviewer_keywords:
- insertq instruction
- _mm_insert_si64 intrinsic
- _mm_inserti_si64 intrinsic
ms.assetid: 897a4b36-8b08-4b00-a18f-7850f5732d7d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc85f56660702afe1c05f3626b3b28b0b566dbd5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="mminsertsi64-mminsertisi64"></a>_mm_insert_si64, _mm_inserti_si64
**Específicos de Microsoft**  
  
 Genera el `insertq` instrucción para insertar los bits de su segundo operando en su primer operando.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 [in] `Source1`  
 Un campo de 128 bits con datos de entrada en sus en la que se insertará un campo de 64 bits inferiores.  
  
 [in]  `Source2`  
 Un campo de 128 bits con los datos que se va a insertar en sus bits inferiores.  Para `_mm_insert_si64`, también contiene un descriptor de campo en sus bits superiores.  
  
 [in]  `Length`  
 Una constante entera que especifica la longitud del campo que desea insertar.  
  
 [in]  `Index`  
 Una constante entera que especifica el índice del bit menos significativo del campo en el que se van a insertar datos.  
  
## <a name="return-value"></a>Valor devuelto  
 Un campo de 128 bits cuyos 64 bits inferiores contienen los 64 bits inferiores originales de `Source1` con el campo de bits especificado reemplazados por los bits inferiores del `Source2`. Los 64 bits superiores del valor devuelto son indefinidos.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`_mm_insert_si64`|SSE4a|  
|`_mm_inserti_si64`|SSE4a|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Esta función intrínseca genera el `insertq` instrucción para insertar los bits de `Source2` en `Source1`. Hay dos versiones de este intrínsecas: `_mm_inserti_si64`, es la versión inmediata, y `_mm_insert_si64` es el que no es inmediato.  Cada versión extrae origen2 en un campo de bits de una longitud dada y lo inserta en Source1.  Los bits extraídos son los bits menos significativos de origen2.  El origen1 de campo en el que se van a insertar estos bits se define mediante la longitud y el índice de su bit menos significativo.  Los valores de la longitud y el índice se toman mod 64, lo que -1 y 127 se interpretan como 63. Si la suma de los bits (reducida) índice y la longitud de campo (reducida) es mayor que 64, los resultados son indefinidos. Un valor de cero para la longitud de campo se interpreta como 64.  Si el índice de bits y de longitud de campo es ambos cero, 63:0 de bits de `Source2` se insertan en `Source1`.  Si la longitud de campo es cero, pero el índice de bits es distinto de cero, los resultados son indefinidos.  
  
 En una llamada a _mm_insert_si64, la longitud de campo se encuentra en 77:72 de bits de origen2 y el índice en 69:64 de bits.  
  
 Si se llama a `_mm_inserti_si64` con argumentos que el compilador no puede determinar como constantes de tipo entero, el compilador genera código que se va a empaquetar esos valores en un registro de registros de XMM como llamar a `_mm_insert_si64`.  
  
 Para determinar la compatibilidad de hardware con el `insertq` llamada la `__cpuid` intrínseco con `InfoType=0x80000001` y comprobar bit 6 de `CPUInfo[2] (ECX)`. Este bit será 1 si se admite la instrucción y 0 en caso contrario. Si ejecuta el código que usa esta función intrínseca en hardware que no es compatible con la `insertq` instrucciones, los resultados son imprevisibles.  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
result1 = 0xfffffffff3210fff  
result2 = 0xfffffffff3210fff  
result3 = 0xfffffffff3210fff  
```  
  
**FIN de Específicos de Microsoft**  
 Copyright 2007 por Advanced Micro Devices, Inc. Todos los derechos reservados. Reprodujo con permiso de Advanced Micro Devices, Inc.  
  
## <a name="see-also"></a>Vea también  
 [_mm_extract_si64, _mm_extracti_si64](../intrinsics/mm-extract-si64-mm-extracti-si64.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
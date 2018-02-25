---
title: _mm_stream_ss | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _mm_stream_ss
dev_langs:
- C++
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 420952d58bb46012741ee95ced4cf39c12d381cd
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="mmstreamss"></a>_mm_stream_ss  
  
**Específicos de Microsoft**  
  
 Escribe datos de 32 bits en una ubicación de memoria sin dañar las memorias caché.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _mm_stream_ss(  
   float * Dest,  
   __m128 Source  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
  
 [out] `Dest`  
 Un puntero a la ubicación donde se escriben los datos de origen.  
  
 [in] `Source`  
 Un número de 128 bits que contiene el `float` valor que se escribirá en la parte inferior de 32 bits...  
  
## <a name="return-value"></a>Valor devuelto  
  
 Ninguno.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`_mm_stream_ss`|SSE4a|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
  
Esta función intrínseca genera el `movntss` instrucción. Para determinar la compatibilidad de hardware con esta instrucción, llame a la `__cpuid` intrínseco con `InfoType=0x80000001` y comprobar bit 6 de `CPUInfo[2] (ECX)`. Este bit es 1 cuando se admite la instrucción y 0 en caso contrario.  
  
Si se ejecuta código que utiliza el `_mm_stream_ss` intrínseco en hardware que no es compatible con la `movntss` instrucciones, los resultados son imprevisibles.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
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
  
```Output  
f[0] = -1, f[1] = -2  
f[2] = -3, f[3] = 3  
```  
  
**FIN de Específicos de Microsoft**  

Copyright 2007 por Advanced Micro Devices, Inc. Todos los derechos reservados. Reprodujo con permiso de Advanced Micro Devices, Inc.  
  
## <a name="see-also"></a>Vea también  
 [_mm_stream_sd](../intrinsics/mm-stream-sd.md)   
 [_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)   
 [_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)   
 [_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
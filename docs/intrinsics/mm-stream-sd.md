---
title: _mm_stream_sd | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_stream_sd
dev_langs:
- C++
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e8a65066ad19b78319867782255d70da8d5b721
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="mmstreamsd"></a>_mm_stream_sd
**Específicos de Microsoft**  
  
 Escribe datos de 64 bits en una ubicación de memoria sin dañar las memorias caché.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _mm_stream_sd(  
   double * Dest,  
   __m128d Source  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `Dest`  
 Un puntero a la ubicación donde se escribirán los datos de origen.  
  
 [in] `Source`  
 Un valor de 128 bits que contiene el `double` valor que se escribirá en la parte inferior de 64 bits...  
  
## <a name="return-value"></a>Valor devuelto  
 Ninguno.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`_mm_stream_sd`|SSE4a|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Esta función intrínseca genera el `movntsd` instrucción. Para determinar la compatibilidad de hardware con esta instrucción, llame a la `__cpuid` intrínseco con `InfoType=0x80000001` y comprobar bit 6 de `CPUInfo[2] (ECX)`. Este bit es 1 si el hardware es compatible con esta instrucción y 0 en caso contrario.  
  
 Si se ejecuta código que utiliza el `_mm_stream_sd` intrínseco en hardware que no es compatible con la `movntsd` instrucciones, los resultados son imprevisibles.  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
d[0] = -1, d[1] = 1  
```  
  
**FIN de Específicos de Microsoft**  
 Copyright 2007 por Advanced Micro Devices, Inc. Todos los derechos reservados. Reprodujo con permiso de Advanced Micro Devices, Inc.  
  
## <a name="see-also"></a>Vea también  
 [_mm_stream_ss](../intrinsics/mm-stream-ss.md)   
 [_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)   
 [_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
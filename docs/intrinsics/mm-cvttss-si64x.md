---
title: _mm_cvttss_si64x | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _mm_cvttss_si64x
dev_langs:
- C++
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2e9667f93f6255ce1e1bc42b5fac1e8e68543e8e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="mmcvttsssi64x"></a>_mm_cvttss_si64x
**Específicos de Microsoft**  
  
 Emite el x64 extendidos versión de la función Convert con el número de punto flotante de precisión sencilla de truncamiento en el entero de 64 bits (`cvttss2si`) instrucción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__int64 _mm_cvttss_si64x(   
   __m128 value   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `value`  
 Un `__m128` estructura que contiene los valores de punto flotante de precisión sencilla.  
  
## <a name="return-value"></a>Valor devuelto  
 El resultado de la conversión del primer valor de punto flotante en un entero de 64 bits.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`_mm_cvttss_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Difiere de la función intrínseca de `_mm_cvtss_si64x` sólo en esa inexactos conversiones se truncan hacia cero. Dado que el `__m128` estructura representa un registro de registros de XMM, la instrucción genera mueve los datos de un registro XMM en la memoria del sistema.  
  
 Esta rutina solo está disponible como función intrínseca.  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
101  
```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [__m128](../cpp/m128.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
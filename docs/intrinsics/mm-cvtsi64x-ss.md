---
title: _mm_cvtsi64x_ss | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _mm_cvtsi64x_ss
dev_langs:
- C++
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae300569c4aa04a313f44a23fe988f1de7b826a1
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42538748"
---
# <a name="mmcvtsi64xss"></a>_mm_cvtsi64x_ss
**Específicos de Microsoft**  
  
 Genera el x64 extendidos versión del entero de convertir de 64 bits para el valor de punto flotante de precisión sencilla escalares (`cvtsi2ss`) instrucción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__m128 _mm_cvtsi64x_ss(   
   __m128 a,   
   __int64 b   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `a`  
 Un `__m128` estructura que contiene cuatro valores de punto flotante de precisión sencilla.  
  
 [in] `b`  
 Un entero de 64 bits se conviertan en un valor de punto flotante.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `__m128` estructura cuyo primer valor de punto flotante es el resultado de la conversión. Los tres valores se copian sin cambios desde `a`.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`_mm_cvtsi64x_ss`|x64|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 El `__m128` estructura representa un registro XMM, por lo tanto, esta función intrínseca permite que el valor `b` desde la memoria del sistema que desea mover a un XMM registre.  
  
 Esta rutina solo está disponible como función intrínseca.  
  
## <a name="example"></a>Ejemplo  
  
```  
// _mm_cvtsi64x_ss.cpp  
// processor: x64  
  
#include <intrin.h>  
#include <stdio.h>  
  
#pragma intrinsic(_mm_cvtsi64x_ss)  
  
int main()  
{  
    __m128 a;  
    __int64 b = 54;  
  
    a.m128_f32[0] = 0;  
    a.m128_f32[1] = 0;  
    a.m128_f32[2] = 0;  
    a.m128_f32[3] = 0;  
    a = _mm_cvtsi64x_ss(a, b);  
  
    printf_s( "%lf %lf %lf %lf\n",  
              a.m128_f32[0], a.m128_f32[1],   
              a.m128_f32[2], a.m128_f32[3] );  
}  
```  
  
```Output  
54.000000 0.000000 0.000000 0.000000  
```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [__m128](../cpp/m128.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
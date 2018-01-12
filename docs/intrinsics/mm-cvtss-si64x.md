---
title: _mm_cvtss_si64x | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mm_cvtss_si64x
dev_langs: C++
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f55ecac0a9f6318b5d60a372003e548ce41c713
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mmcvtsssi64x"></a>_mm_cvtss_si64x
**Específicos de Microsoft**  
  
 Genera el [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] versión extendida de la convertir escalar único precisión número de punto flotante a entero de 64 bits (`cvtss2si`) instrucción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__int64 _mm_cvtss_si64x(   
   __m128 value   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `value`  
 Un `__m128` estructura que contiene los valores de punto flotante.  
  
## <a name="return-value"></a>Valor devuelto  
 Un entero de 64 bits, el resultado de la conversión del primer valor de punto flotante en un entero.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`_mm_cvtss_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 El primer elemento del valor de la estructura se convierte en un entero y se devuelve. Los bits de control de redondeo de MXCSR se usan para determinar el comportamiento de redondeo. El modo de redondeo predeterminado es redondeo al más cercano, redondear al número par si la parte decimal es 0,5. Dado que el `__m128` estructura representa un registro de registros de XMM, esta función intrínseca toma un valor desde el registro de registros de XMM y lo escribe en la memoria del sistema.  
  
 Esta rutina solo está disponible como función intrínseca.  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
101  
```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [__m128d](../cpp/m128d.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
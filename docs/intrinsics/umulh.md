---
title: __umulh | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __umulh
dev_langs:
- C++
helpviewer_keywords:
- __umulh intrinsic
ms.assetid: d241b53a-e6f7-4af1-9f6e-84e149158f03
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a3c9ebcf5e512f75e6e9fc66d5019273e1626f6a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="umulh"></a>__umulh
**Específicos de Microsoft**  
  
 Devolver los 64 bits superiores del producto de dos enteros sin signo de 64 bits.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned __int64 __umulh(   
   unsigned __int64 a,   
   unsigned __int64 b   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `a`  
 El primer número que se va a multiplicar.  
  
 [in] `b`  
 El segundo número que se va a multiplicar.  
  
## <a name="return-value"></a>Valor devuelto  
 Los 64 bits superiores del resultado de 128 bits de la multiplicación.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__umulh`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Estas rutinas solo están disponibles como intrínsecos.  
  
## <a name="example"></a>Ejemplo  
  
```  
// umulh.cpp  
// processor: X64  
#include <cstdio>  
#include <intrin.h>  
  
int main()  
{  
    unsigned __int64 i = 0x10;  
    unsigned __int64 j = 0xFEDCBA9876543210;  
    unsigned __int64 k = i * j; // k has the low 64 bits  
                                // of the product.  
    unsigned __int64 result;  
    result = __umulh(i, j); // result has the high 64 bits  
                            // of the product.  
    printf_s("0x%I64x * 0x%I64x = 0x%I64x%I64x \n", i, j, result, k);  
    return 0;  
}  
```  
  
```Output  
0x10 * 0xfedcba9876543210 = 0xfedcba98765432100   
```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
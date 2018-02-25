---
title: __mulh | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __mulh
dev_langs:
- C++
helpviewer_keywords:
- __mulh intrinsic
ms.assetid: cd2ab093-9ef6-404d-ac34-0bee033882f3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 92dabc2c3172d16a0b165b8560554d2151318ee4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="mulh"></a>__mulh
**Específicos de Microsoft**  
  
 Devuelve los 64 bits superiores del producto de dos enteros de 64 bits con signo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__int64 __mulh(   
   __int64 a,   
   __int64 b   
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
|`__mulh`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Esta rutina solo está disponible como función intrínseca.  
  
## <a name="example"></a>Ejemplo  
  
```  
// mulh.cpp  
// processor: x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic (__mulh)  
  
int main()  
{  
    __int64 a = 0x0fffffffffffffffI64;  
    __int64 b = 0xf0000000I64;  
  
    __int64 result = __mulh(a, b); // the high 64 bits  
    __int64 result2 = a * b; // the low 64 bits  
  
    printf_s(" %#I64x * %#I64x = %#I64x%I64x\n",  
             a, b, result, result2);  
}  
```  
  
```Output  
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000  
```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
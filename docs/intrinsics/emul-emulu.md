---
title: __emul, __emulu | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __emulu_cpp
- __emul
- __emul_cpp
- __emulu
dev_langs:
- C++
helpviewer_keywords:
- __emul intrinsic
- __emulu intrinsic
ms.assetid: 79545236-cca2-40b8-a4e1-8abce9b26311
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba97b1160b9b0bff9e6014d73d1c79bf4627139c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="emul-emulu"></a>__emul, __emulu
**Específicos de Microsoft**  
  
 Lleva a cabo multiplicaciones que lo que puede contener un entero de 32 bits un desbordamiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__int64 __emul(  
   int a,  
   int b  
);  
unsigned __int64 __emulu(  
   unsigned int a,  
   unsigned int b  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `a`  
 El primer operando de entero de la multiplicación.  
  
 [in] `b`  
 El segundo operando de entero de la multiplicación.  
  
## <a name="return-value"></a>Valor devuelto  
 El resultado de la multiplicación.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__emul`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__emulu`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 `__emul` toma dos valores de 32 bits con signo y devuelve el resultado de la multiplicación como un valor entero de 64 bits con signo.  
  
 `__emulu` toma dos valores enteros de 32 bits sin signo y devuelve el resultado de la multiplicación como un valor entero sin signo de 64 bits.  
  
## <a name="example"></a>Ejemplo  
  
```  
// emul.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__emul)  
#pragma intrinsic(__emulu)  
  
int main()  
{  
   int a = -268435456;   
   int b = 2;   
  
   __int64 result = __emul(a, b);  
  
   cout << a << " * " << b << " = " << result << endl;  
  
   unsigned int ua = 0xFFFFFFFF; // Dec value: 4294967295  
   unsigned int ub = 0xF000000;  // Dec value: 251658240  
  
   unsigned __int64 uresult = __emulu(ua, ub);  
  
   cout << ua << " * " << ub << " = " << uresult << endl;  
  
}  
```  
  
## <a name="output"></a>Salida  
  
```  
-268435456 * 2 = -536870912  
4294967295 * 251658240 = 1080863910317260800  
```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
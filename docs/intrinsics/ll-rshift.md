---
title: __ll_rshift | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
dev_langs:
- C++
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e404375eefaf456ae22d2eca5cb66a13dd6a72ae
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="llrshift"></a>__ll_rshift
**Específicos de Microsoft**  
  
 Desplaza un valor de 64 bits especificado por el primer parámetro a la derecha el número de bits especificado por el segundo parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__int64 __ll_rshift(  
   __int64 Mask,  
   int nBit  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `Mask`  
 El valor del entero de 64 bits para desplazamiento a la derecha.  
  
 [in] `nBit`  
 El número de bits de desplazamiento, módulo 64 en x64 y módulo 32 en x86.  
  
## <a name="return-value"></a>Valor devuelto  
 Desplace hacia la máscara `nBit` bits.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__ll_rshift`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Si el segundo parámetro es mayor que 64 en x64 (32 en x86), ese número se toma módulo 64 (32 en x86) para determinar el número de bits de desplazamiento. El `ll` prefijo indica que esta es una operación en `long long`, otro nombre para `__int64`, el tipo entero con signo de 64 bits.  
  
## <a name="example"></a>Ejemplo  
  
```  
// ll_rshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_rshift)  
  
int main()  
{  
   __int64 Mask = - 0x100;  
   int nBit = 4;  
   cout << hex << Mask << endl;  
   cout << " - " << (- Mask) << endl;  
   Mask = __ll_rshift(Mask, nBit);  
   cout << hex << Mask << endl;  
   cout << " - " << (- Mask) << endl;  
}  
```  
  
## <a name="output"></a>Salida  
  
```  
ffffffffffffff00  
 - 100  
fffffffffffffff0  
 - 10  
```  
  
 **Tenga en cuenta** si `_ull_rshift` ha sido utilizado, el MSB desplazado a la derecha del valor de la habría sido cero, por lo que el resultado deseado no habría obtenido en el caso de un valor negativo.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [__ll_lshift](../intrinsics/ll-lshift.md)   
 [__ull_rshift](../intrinsics/ull-rshift.md)
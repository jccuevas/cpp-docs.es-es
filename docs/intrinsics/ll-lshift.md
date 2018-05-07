---
title: __ll_lshift | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
dev_langs:
- C++
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94cf50287c28fe530df939488c4e707d17aede03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="lllshift"></a>__ll_lshift
**Específicos de Microsoft**  
  
 Desplaza el valor de 64 bits proporcionado a la izquierda el número especificado de bits.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned __int64 __ll_lshift(  
   unsigned __int64 Mask,  
   int nBit  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `Mask`  
 Valor entero de 64 bits que se desplazan hacia la izquierda.  
  
 [in] `nBit`  
 El número de bits que se va a desplazar.  
  
## <a name="return-value"></a>Valor devuelto  
 La máscara desplazado a la izquierda `nBit` bits.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__ll_lshift`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Si compila el programa mediante la arquitectura de 64 bits y `nBit` es superior a 63, el número de bits de desplazamiento es `nBit` módulo 64. Si compila el programa mediante la arquitectura de 32 bits y `nBit` es mayor que 31, el número de bits de desplazamiento es `nBit` módulo 32.  
  
 El `ll` en el nombre indica que se trata de una operación en `long long` (`__int64`).  
  
## <a name="example"></a>Ejemplo  
  
```  
// ll_lshift.cpp  
// compile with: /EHsc  
// processor: x86, x64  
#include <iostream>  
#include <intrin.h>  
using namespace std;  
  
#pragma intrinsic(__ll_lshift)  
  
int main()  
{  
   unsigned __int64 Mask = 0x100;  
   int nBit = 8;  
   Mask = __ll_lshift(Mask, nBit);  
   cout << hex << Mask << endl;  
}  
```  
  
## <a name="output"></a>Salida  
  
```  
10000  
```  
  
 **Tenga en cuenta** hay ninguna versión sin signo de la operación de desplazamiento a la izquierda. Esto es porque `__ll_lshift` ya utiliza un parámetro de entrada sin signo. A diferencia de desplazamiento a la derecha, no hay ninguna dependencia de inicio de sesión para el desplazamiento a la izquierda, porque el bit menos significativo en el resultado siempre se establece en cero independientemente del signo del valor desplazado.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [__ll_rshift](../intrinsics/ll-rshift.md)   
 [__ull_rshift](../intrinsics/ull-rshift.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
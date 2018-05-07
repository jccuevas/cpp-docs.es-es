---
title: __rdtsc | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __rdtsc
dev_langs:
- C++
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81b47a76b3045465d8c3c5c21a87020ee1e74a69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="rdtsc"></a>__rdtsc
**Específicos de Microsoft**  
  
 Genera el `rdtsc` instrucción, que devuelve la marca de tiempo de procesador. La marca de tiempo de procesador registra el número de ciclos de reloj desde el último restablecimiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
unsigned __int64 __rdtsc();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Entero de 64 bits sin signo que representa un recuento de pasos.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|  
|---------------|------------------|  
|`__rdtsc`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h >  
  
## <a name="remarks"></a>Comentarios  
 Esta rutina solo está disponible como función intrínseca.  
  
 La interpretación del valor TSC en esta generación de hardware difiere del comportamiento en las versiones anteriores de [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]. Consulte los manuales de hardware para obtener más información.  
  
## <a name="example"></a>Ejemplo  
  
```  
// rdtsc.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__rdtsc)  
  
int main()  
{  
    unsigned __int64 i;  
    i = __rdtsc();  
    printf_s("%I64d ticks\n", i);  
}  
```  
  
```Output  
3363423610155519 ticks  
```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)
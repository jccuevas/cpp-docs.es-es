---
title: "Funciones intrínsecas _InterlockedCompareExchangePointer | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _InterlockedCompareExchangePointer_HLERelease
- _InterlockedCompareExchangePointer_rel
- _InterlockedCompareExchangePointer_acq_cpp
- _InterlockedCompareExchangePointer
- _InterlockedCompareExchangePointer_cpp
- _InterlockedCompareExchangePointer_np
- _InterlockedCompareExchangePointer_rel_cpp
- _InterlockedCompareExchangePointer_HLEAcquire
- _InterlockedCompareExchangePointer_acq
- _InterlockedCompareExchangePointer_nf
dev_langs:
- C++
helpviewer_keywords:
- InterlockedCompareExchangePointer_acq intrinsic
- _InterlockedCompareExchangePointer_rel intrinsic
- _InterlockedCompareExchangePointer_acq intrinsic
- InterlockedCompareExchangePointer_rel intrinsic
- InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_HLERelease intrinsic
- _InterlockedCompareExchangePointer_HLEAcquire intrinsic
- _InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_nf intrinsic
- _InterlockedCompareExchangePointer_np intrinsic
ms.assetid: 97fde59d-2bf9-42aa-a0fe-a5b6befdd44b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a75c25caef43a0f1908cfe326b5b194480c3190c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="interlockedcompareexchangepointer-intrinsic-functions"></a>Funciones intrínsecas _InterlockedCompareExchangePointer
**Específicos de Microsoft**  
  
 Realiza una operación atómica que almacena la dirección `Exchange` en la dirección `Destination` si `Comparand` y la dirección `Destination` son iguales.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void * _InterlockedCompareExchangePointer (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_acq (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_HLEAcquire (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_HLERelease (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_nf (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
void * _InterlockedCompareExchangePointer_np (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
long _InterlockedCompareExchangePointer_rel (  
   void * volatile * Destination,  
   void * Exchange,  
   void * Comparand  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in, out] `Destination`  
 Puntero a un puntero al valor de destino. El signo se omite.  
  
 [in] `Exchange`  
 Puntero de intercambio. El signo se omite.  
  
 [in] `Comparand`  
 Puntero que se compara con el destino. El signo se omite.  
  
## <a name="return-value"></a>Valor devuelto  
 El valor devuelto es el valor inicial del destino.  
  
## <a name="requirements"></a>Requisitos  
  
|Función intrínseca|Arquitectura|Header|  
|---------------|------------------|------------|  
|`_InterlockedCompareExchangePointer`|x86, ARM, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<INTRIN.h >|  
|`_InterlockedCompareExchangePointer_acq`, `_InterlockedCompareExchangePointer_nf`, `_InterlockedCompareExchangePointer_rel`|ARM|\<iiintrin.h>|  
|`_InterlockedCompareExchangePointer_HLEAcquire`, `_InterlockedCompareExchangePointer_HLERelease`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h>|  
  
## <a name="remarks"></a>Comentarios  
 `_InterlockedCompareExchangePointer` realiza una comparación atómica de la dirección `Destination` con la dirección `Comparand`. Si la dirección `Destination` es igual a la dirección `Comparand`, la dirección `Exchange` se almacena en la dirección especificada por `Destination`. De lo contrario, no se realiza ninguna operación.  
  
 `_InterlockedCompareExchangePointer` proporciona compatibilidad intrínseca del compilador para Win32 [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] [_InterlockedCompareExchangePointer](http://msdn.microsoft.com/library/ff547863.aspx) (función).  
  
 Para obtener un ejemplo de cómo usar `_InterlockedCompareExchangePointer`, consulte [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).  
  
 En plataformas ARM, utilice los intrínsecos con sufijos `_acq` y `_rel` si necesita adquirir y liberar semántica, como al principio y al final de una sección crítica. Los intrínsecos ARM con un sufijo `_nf` ("sin límite") no actúan como una barrera de memoria.  
  
 Los intrínsecos con un sufijo `_np` ("sin captura previa") impiden que el compilador inserte una posible operación de captura previa.  
  
 En las plataformas de Intel que admiten instrucciones de Elisión de bloqueo de Hardware (HLE), los intrínsecos con sufijos `_HLEAcquire` y `_HLERelease` incluyen una sugerencia para el procesador que puede acelerar el rendimiento mediante la eliminación de un paso de escritura de bloqueo en el hardware. Si se llama a estos intrínsecos en plataformas que no son compatibles con HLE, se omite la sugerencia.  
  
 Estas rutinas solo están disponibles como intrínsecos.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md)   
 [Palabras clave](../cpp/keywords-cpp.md)
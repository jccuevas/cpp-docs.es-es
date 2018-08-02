---
title: 'Comptrref:: operator! = (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator!=
dev_langs:
- C++
ms.assetid: ab3093cc-6fbd-4039-890a-6df1cde992b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7ebe71706ce1091ee21fc6fbd63e65b201c096b5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462929"
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator!= (Operador)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
bool operator!=(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   const Details::ComPtrRef<ComPtr<U>>& b  
);  
  
bool operator!=(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   decltype(__nullptr)  
);  
  
bool operator!=(  
   decltype(__nullptr),  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
  
bool operator!=(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   void* b  
);  
  
bool operator!=(  
   void* b,  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *a*  
 Una referencia a un **ComPtrRef** objeto.  
  
 *b*  
 Una referencia a otro **ComPtrRef** objeto o un puntero a un objeto anónimo (`void*`).  
  
## <a name="return-value"></a>Valor devuelto  
 El primer rendimientos de operador **true** si objeto *un* no es igual al objeto *b*; en caso contrario, **false**.  
  
 Los operadores de la segundo y terceros yield **true** si objeto *un* no es igual a **nullptr**; en caso contrario, **false**.  
  
 El cuarto y quinto operadores producen **true** si objeto *un* no es igual al objeto *b*; en caso contrario, **false**.  
  
## <a name="remarks"></a>Comentarios  
 Indica si dos **ComPtrRef** objetos no son iguales.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Wrl Namespace](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtrRef (clase)](../windows/comptrref-class.md)
---
title: 'Comptrref:: operator! = (operador) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::Details::ComPtrRef::operator!=
dev_langs: C++
ms.assetid: ab3093cc-6fbd-4039-890a-6df1cde992b6
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7a9c9572ece0f60971449f2e1b519ec662f9867f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator!= (Operador)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
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
 `a`  
 Una referencia a un objeto ComPtrRef.  
  
 `b`  
 Una referencia a otro objeto ComPtrRef o un puntero a un objeto anónimo (`void*`).  
  
## <a name="return-value"></a>Valor devuelto  
 La primera genera operador `true` si objeto `a` no es igual al objeto `b`; en caso contrario, `false`.  
  
 El segundo y tercer operador produce `true` si objeto `a` no es igual a `nullptr`; en caso contrario, `false`.  
  
 Los operadores cuarto y quinto producen `true` si objeto `a` no es igual al objeto `b`; en caso contrario, `false`.  
  
## <a name="remarks"></a>Comentarios  
 Indica si dos objetos ComPtrRef no son iguales.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Namespace wrl](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtrRef (clase)](../windows/comptrref-class.md)
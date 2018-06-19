---
title: 'Comptrref:: operator == (operador) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator==
dev_langs:
- C++
ms.assetid: 95fcf781-b473-4317-88cd-e938778d3c3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0b7cc1d89a0e113164530245467afd94becdc1e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880786"
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator== (Operador)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   const Details::ComPtrRef<ComPtr<U>>& b  
);  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   decltype(__nullptr)  
);  
  
bool operator==(  
   decltype(__nullptr),  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   void* b  
);  
  
bool operator==(  
   void* b,  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `a`  
 Una referencia a un objeto ComPtrRef.  
  
 `b`  
 Una referencia a otro objeto ComPtrRef o un puntero a un tipo anónimo (`void*`).  
  
## <a name="return-value"></a>Valor devuelto  
 La primera genera operador `true` si objeto `a` es igual al objeto `b`; en caso contrario, `false`.  
  
 El segundo y tercer operador produce `true` si objeto `a` es igual a `nullptr`; en caso contrario, `false`.  
  
 Los operadores cuarto y quinto producen `true` si objeto `a` es igual al objeto `b`; en caso contrario, `false`.  
  
## <a name="remarks"></a>Comentarios  
 Indica si dos objetos ComPtrRef son iguales.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Namespace wrl](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtrRef (clase)](../windows/comptrref-class.md)
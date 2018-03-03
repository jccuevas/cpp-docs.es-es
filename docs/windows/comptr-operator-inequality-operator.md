---
title: 'Comptr:: operator! = (operador) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator!=
dev_langs:
- C++
ms.assetid: 63647240-dec7-4eb9-9272-96c07d01493c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e2610061fcb7266ae5457935d680f7bce82797c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="comptroperator-operator"></a>ComPtr::operator!= (Operador)
Indica si dos objetos de ComPtr son diferentes.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
bool operator!=(  
   const ComPtr<T>& a,  
   const ComPtr<U>& b  
);  
  
bool operator!=(  
   const ComPtr<T>& a,  
   decltype(__nullptr)  
);  
  
bool operator!=(  
   decltype(__nullptr),  
   const ComPtr<T>& a  
);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `a`  
 Una referencia a un objeto de ComPtr.  
  
 `b`  
 Una referencia a otro objeto de ComPtr.  
  
## <a name="return-value"></a>Valor devuelto  
 La primera genera operador `true` si objeto `a` no es igual al objeto `b`; en caso contrario, `false`.  
  
 El segundo y tercer operador produce `true` si objeto `a` no es igual a `nullptr`; en caso contrario, `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft:: wrl Namespace](../windows/microsoft-wrl-namespace.md)   
 [ComPtr (clase)](../windows/comptr-class.md)
---
title: 'Hstringreference:: operator&lt; operador | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
dev_langs:
- C++
ms.assetid: 55aa48e8-7c96-4123-9ebe-42b4cd8b9377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b486157fb42883af724f2356e7f85701e405035
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="hstringreferenceoperatorlt-operator"></a>Hstringreference:: operator&lt; (operador)
Indica si el primer parámetro es menor que el segundo parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline bool operator<(  
    const HStringReference& lhs,   
    const HStringReference& rhs) throw()  
```  
  
#### <a name="parameters"></a>Parámetros  
 `lhs`  
 El primer parámetro para comparar. `lhs` puede ser una referencia a un HStringReference.  
  
 `rhs`  
 El segundo parámetro para comparar.  `rhs` puede ser una referencia a un HStringReference.  
  
## <a name="return-value"></a>Valor devuelto  
 `true` Si el `lhs` parámetro es menor que el `rhs` parámetro; en caso contrario, `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HStringReference (clase)](../windows/hstringreference-class.md)
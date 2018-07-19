---
title: 'Hstring:: operator&lt; operador | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
dev_langs:
- C++
ms.assetid: 48a051cb-4609-42be-b48c-d35fc99d1eab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8fae7195f048cd680be513bd54b635e2e1e9bbf7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875115"
---
# <a name="hstringoperatorlt-operator"></a>Hstring:: operator&lt; (operador)
Indica si el primer parámetro es menor que el segundo parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline bool operator<(  
    const HString& lhs,   
    const HString& rhs) throw()  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `lhs`  
 El primer parámetro para comparar. `lhs` puede ser una referencia a HString.  
  
 `rhs`  
 El segundo parámetro para comparar. `rhs` puede ser una referencia a HString.  
  
## <a name="return-value"></a>Valor devuelto  
 `true` Si el `lhs` parámetro es menor que el `rhs` parámetro; en caso contrario, `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HString (clase)](../windows/hstring-class.md)
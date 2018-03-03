---
title: 'Hstringreference:: operator == (operador) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
dev_langs:
- C++
ms.assetid: cad3d52d-cd67-4194-a270-5239b1121a09
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4e9c9c9edcd5c53ee3e26f89ed467140d1509e13
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator== (Operador)
Indica si los dos parámetros son iguales.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline bool operator==(  
               const HStringReference& lhs,   
               const HStringReference& rhs) throw()  
  
inline bool operator==(  
               const HSTRING& lhs,   
               const HStringReference& rhs) throw()  
  
inline bool operator==(  
               const HStringReference& lhs,   
               const HSTRING& rhs) throw()  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `lhs`  
 El primer parámetro para comparar. `lhs`puede ser un objeto HStringReference o un controlador HSTRING.  
  
 `rhs`  
 El segundo parámetro para comparar.  `rhs`puede ser un objeto HStringReference o un controlador HSTRING.  
  
## <a name="return-value"></a>Valor devuelto  
 Es `true` si los parámetros `lhs` y `rhs` son iguales; en caso contrario, es `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HStringReference (clase)](../windows/hstringreference-class.md)
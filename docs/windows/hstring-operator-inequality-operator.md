---
title: 'Hstring:: operator! = (operador) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
dev_langs:
- C++
ms.assetid: dcdd2aca-e7d6-4bf1-b2de-03efbb430a93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 74fc15d10818d14467b866ec37c9e353348ce882
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="hstringoperator-operator"></a>HString::Operator!= (Operador)
Indica si los dos parámetros no son iguales.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline bool operator!=( const HString& lhs,   
                        const HString& rhs) throw()  
  
inline bool operator!=( const HStringReference& lhs,   
                        const HString& rhs) throw()  
  
inline bool operator!=( const HString& lhs,   
                        const HStringReference& rhs) throw()  
  
inline bool operator!=( const HSTRING& lhs,   
                        const HString& rhs) throw()  
  
inline bool operator!=( const HString& lhs,   
                        const HSTRING& rhs) throw()  
```  
  
#### <a name="parameters"></a>Parámetros  
 `lhs`  
 El primer parámetro para comparar. `lhs` puede ser un objeto HString o HStringReference, o bien un controlador HSTRING.  
  
 `rhs`  
 El segundo parámetro para comparar.`rhs` puede ser un objeto HString o HStringReference, o bien un controlador HSTRING.  
  
## <a name="return-value"></a>Valor devuelto  
 Es `true` si los parámetros `lhs` y `rhs` no son iguales; en caso contrario, es `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HString (clase)](../windows/hstring-class.md)
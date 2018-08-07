---
title: 'Hstring:: operator == (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator==
dev_langs:
- C++
ms.assetid: 77ff4c1a-e62a-4256-bf9d-0f017137c630
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c21e9f79673cc888f8661803a8cc4bb9053870c4
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604569"
---
# <a name="hstringoperator-operator"></a>HString::Operator== (Operador)
Indica si los dos parámetros son iguales.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline bool operator==(  
               const HString& lhs,   
               const HString& rhs) throw()  
  
inline bool operator==(  
                const HString& lhs,   
                const HStringReference& rhs) throw()  
  
inline bool operator==(  
                const HStringReference& lhs,   
                const HString& rhs) throw()  
  
inline bool operator==(  
                 const HSTRING& lhs,   
                 const HString& rhs) throw()  
  
inline bool operator==(  
                 const HString& lhs,   
                 const HSTRING& rhs) throw()  
```  
  
### <a name="parameters"></a>Parámetros  
 *LHS*  
 El primer parámetro para comparar. *LHS* puede ser un **HString** o `HStringReference` objeto o un identificador HSTRING.  
  
 *RHS*  
 El segundo parámetro para comparar. *rhs* puede ser un **HString** o `HStringReference` objeto o un identificador HSTRING.  
  
## <a name="return-value"></a>Valor devuelto  
 **True** si el *lhs* y *rhs* parámetros son iguales; en caso contrario, **false**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HString (clase)](../windows/hstring-class.md)